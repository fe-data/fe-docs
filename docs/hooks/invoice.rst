fast_events_invoice
===================
This action is called if the invoice download URL is triggered.
Download your own designed invoice possibly using an external financial accounting package.
Make sure the right HTTP headers are generated to download a PDF file.

.. code-block:: php
   :linenos:

   <?php
   function your_action_invoice( $attr ) {
     // Do what you need to do
   }
   
   add_action( 'fast_events_invoice', 'your_action_invoice', 10, 1 );
   
----

Parameters
----------
**$attr['id']**
    (*string*) The unique order id.
**$attr['event_id']**
    (*string*) The unique order id.
**$attr['tickets']**
    *array* of ticket-types ordered.

    1. **'name'** (*string, case sensitive*) The name of the ticket-type.
    2. **'price'** (*string*) The ticket price. Example ``6.25``.
    3. **'vat'** (*string*) VAT.
    4. **'count'** (*int*) The number of tickets ordered.
**$attr['invoice']**
    *array* of invoice data.

    1. **'company'** The name of the company. Can be empty,
    2. **'vat'** The VAT-id of the company. Can be empty,
    3. **'name'** (*string*) The name of the person.
    4. **'street'** (*string*) The street address.
    5. **'postcode'** (*string*) The postcode.
    6. **'city'** (*string*) The city.
**$attr['name']**
    (*string*) The name of the person placing the order.
**$attr['email']**
    (*string*) The emailaddress of the person placing the order. This value is *read-only*.
**$attr['created_at']**
    (*string*) The datetime of the order.
**$attr['event_name']**
    (*string*) The name of the event.
**$attr['event_date']**
    (*string*) The date of the event.
**$attr['event_date_format']**
    (*string*) The date format of the event. The `placeholders can be found here <https://www.php.net/manual/en/datetime.format.php#refsect1-datetime.format-parameters>`_.

    
----

Return
------
None

----

Changelog
---------
.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "2.1.0", "Introduced."

----
  
Examples
--------
Acumulus invoice
^^^^^^^^^^^^^^^^
Send invoice data to `Acumulus accounting <https://www.siel.nl/acumulus/>`_.
Put your contract information in the snippet and the right template name.
Mind you, the snippet doesn't do any error checking.
You can find `here <https://www.siel.nl/acumulus/API/Invoicing/Add_Invoice/>`_ the specification how to add an invoice.

Once you have submitted the data the return info will give you a token that can be used to retrieve the PDF.
You can find `here <https://www.siel.nl/acumulus/API/Invoicing/Get_PDF_Invoice/>`_ the specification how to retrieve the PDF.
Generate the right download HTTP headers and 'write' the PDF to the standard output.

.. code-block:: php
   :linenos:
   
   <?php
   function your_action_invoice( $attr ) {
     $xml  = '<?xml version="1.0" encoding="UTF-8"?>';
     $xml .= '<myxml>';
   
     $xml .= '<format>xml</format>';
     $xml .= '<testmode>0</testmode>';
   
     $xml .= '<contract>';
     $xml .= '<contractcode>YOUR_CONTRACT_NUMBER</contractcode>';
     $xml .= '<username>YOUR_USERNAME</username>';
     $xml .= '<password>YOUR_PASSWORD</password>';
     $xml .= '<emailonerror>YOUR_EMAIL</emailonerror>';
     $xml .= '<emailonwarning>YOUR_EMAIL</emailonwarning>';
     $xml .= '</contract>';
   
     $xml .= '<customer>';
     $xml .= '<fullname>' . $attr['invoice']['name'] . '</fullname>';
     $xml .= '<companyname1>' . $attr['invoice']['company'] . '</companyname1>';
     $xml .= '<vatnumber>' . $attr['invoice']['vat'] . '</vatnumber>';
     $xml .= '<address1>' . $attr['invoice']['street'] . '</address1>';
     $xml .= '<postalcode>' . $attr['invoice']['postcode'] . '</postalcode>';
     $xml .= '<city>' . $attr['invoice']['city'] . '</city>';
     $xml .= '<countrycode>NL</countrycode>';
     $xml .= '<email>' . $attr['email'] . '</email>';
     $xml .= '<invoice>';
     $xml .= '<description>Etickets</description>';
     $xml .= '<paymentstatus>2</paymentstatus>';
     $xml .= '<template>YOUR_TEMPLATE_NAME</template>';
     
     foreach ( $attr['tickets'] as $key => $value ) {
       $xml .= '<line>';
       $xml .= '<product>' . $value['name'] . '</product>';
       $xml .= '<nature>Service</nature>';
       $price_no_vat = (float) $value['price'] / ( 1 + ( (float) $value['vat'] / 100 ) );
       $xml .= '<unitprice>' . number_format( $price_no_vat, 4, '.', '' ) . '</unitprice>';
       $xml .= '<vatrate>' . $value['vat'] . '</vatrate>';
       $xml .= '<quantity>' . $value['count'] . '</quantity>';
       $xml .= '</line>';
     }
                      
     $xml .= '<emailaspdf>';
     $xml .= '<emailto>' . $attr['email'] . '</emailto>';
     $xml .= '</emailaspdf>';
   
     $xml .= '</invoice>';

     $xml .= '</customer>';
     $xml .= '</myxml>';

     $ch = curl_init();
     curl_setopt($ch, CURLOPT_URL, 'https://api.sielsystems.nl/acumulus/stable/invoices/invoice_add.php');
     curl_setopt($ch, CURLOPT_POST, 1);
     curl_setopt($ch, CURLOPT_SSLVERSION, 'CURL_SSLVERSION_TLSv1_2');
     curl_setopt($ch, CURLOPT_POSTFIELDS, 'xmlstring=' . urlencode($xml));
     curl_setopt($ch, CURLOPT_TIMEOUT, 10);
     curl_exec($ch);
     curl_close($ch);
   }
   
   add_action( 'fast_events_invoice', 'your_action_invoice', 10, 1 );
