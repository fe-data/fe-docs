fast_events_new_order
=====================
This action is called after the payment has been received and the customer has already received an email.

.. code-block:: php
   :linenos:

   <?php
   function your_action_new_order( $attr ) {
     // Do what you need to do
   }
   
   add_action( 'fast_events_new_order', 'your_action_new_order', 10, 1 );
   
----

Parameters
----------
**$attr['order_ids']**
    (*int[]*) Array of order id's.
**$attr['event_ids']**
    (*int[]*) Array of event id's.
**$attr['id']**
    (*int*) The id of the event. This value is *read-only*.
**$attr['name']**
    (*string*) The name of the person placing the order.
**$attr['email']**
    (*string*) The emailaddress of the person placing the order. This value is *read-only*.
**$attr['total']**
    (*string*) The total order value. For example ``6.50``. This value is *read-only*.
**$attr['total_vat']**
    (*string*) The total order VAT value. For example ``2.50``. This value is *read-only*.
**$attr['fields']**
    *array* of input fields.
       
    1. **'name'** (*string, case sensitive*) The name of the input field.
    2. **'value'** (*string*) The value of the input field.
**$attr['tickets']**
    *array* of ticket-types ordered.
       
    1. **'name'** (*string, case sensitive*) The name of the ticket-type.
    2. **'price'** (*string*) The ticket price. Example ``6.25``.
    3. **'vat'** (*string*) VAT.
    4. **'count'** (*int*) The number of tickets ordered.
    
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

   "1.0", "Introduced."

----
  
Examples
--------
Acumulus invoice
^^^^^^^^^^^^^^^^
Send invoice data to `Acumulus accounting <https://www.siel.nl/acumulus/>`_. Put your contract information in the snippet and the right template name. Mind you, the snippet doesn't do any error checking. You can find `here <https://www.siel.nl/acumulus/API/Invoicing/Add_Invoice/>`_ the specification how to add an invoice.

.. code-block:: php
   :linenos:
   
   <?php
   function your_action_new_order( $attr ) {
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
     $xml .= '<fullname>' . $attr['name'] . '</fullname>';
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
   
   add_action( 'fast_events_new_order', 'your_action_new_order', 10, 1 );
