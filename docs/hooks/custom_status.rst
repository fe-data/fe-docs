fast_events_custom_status
=========================
This filter is called after a custom order status change from the order contextmenu. It can only be used if the ‘Custom order statuses’ field has been set in the plugin settings.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_custom_status( $attr ) {
     // Do what you need to do
   }
   
   add_filter( 'fast_events_custom_status', 'your_filter_custom_status', 10, 1 );
   
----

Parameters
----------
**$attr['id']**
    (*int*) The id of the event. This value is *read-only*.
**$attr['event_name']**
    (*string*) The name of the event. This value is *read-only*.
**$attr['name']**
    (*string*) The name of the person placing the order.
**$attr['email']**
    (*string*) The emailaddress of the person placing the order. This value is *read-only*.
**$attr['payment_status']**
    (*string*) The payment status of the event. This value is *read-only*.
**$attr['custom_status']**
    (*string*) The new custom status of the event. This value is *read-only*.
**$attr['total']**
    (*string*) The total order value. For example ``6.50``. This value is *read-only*.
**$attr['total_vat']**
    (*string*) The total order VAT value. For example ``2.50``. This value is *read-only*.
**$attr['fields']**
    *array* of input fields.
       
    #. **'name'** (*string, case sensitive*) The name of the input field.
    #. **'value'** (*string*) The value of the input field.
**$attr['tickets']**
    *array* of ticket-types ordered.
       
    #. **'name'** (*string, case sensitive*) The name of the ticket-type.
    #. **'price'** (*string*) The ticket price. Example ``6.25``.
    #. **'vat'** (*string*) VAT.
    #. **'count'** (*int*) The number of tickets ordered.
**$attr['message']**
    (*string*) The message shown in the popup dialog. Default value is: “``Custom status set to: …``”.
    
----

Return
------
**$attr**
    A filter can only change ``$attr['message']``. You can return HTML if necessary and it will be shown as popup dialog. The message will be purified to prevent XSS-attacks.

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
Send email and create shipping-label
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
See :doc:`Examples </usage/examples>` (*Ship a signed photo book*) for a more detailed description. For readability not all input-fields that are needed to create a shipping-label, are included. The order of the fields is as they are defined in the ‘Input -tab‘.

.. code-block:: php
   :linenos:
   
   <?php
   function your_filter_custom_status( $attr ) {
     if ( 'processing' === $attr['custom_status'] ) {
       $message = '<p>Dear ' . $attr['name'] . ',</p>' .
         '<p>We are processing your order with id <b>' . $attr['order_id'] . '.</b> '.
         'You wil receive another email if we ship your order.</p>' .
         '<p>Vintage Vinyl Open Air 2019 team</p>';
       fe_helper_func()->send_email( $attr['email'], "We are processing your order", $message );
     }
     if ( 'shipped' === $attr['custom_status'] ) {
       $html = '<input type="text" name="email" value="' . $attr['email'] . '"><br>' .
         '<input type="text" name="person" value="' . $attr['name'] . '"><br>' .
         '<input type="text" name="zipcode" value="' . $attr['fields'][0]['value'] . '"><br>' .
         '<input type="text" name="number" value="' . $attr['fields'][1]['value'] . '"><br>' .
         '<input type="text" name="addition" value="' . $attr['fields'][2]['value'] . '"><br>';
       $attr['message'] = $html;
     }
     return $attr;
   }

   add_filter( 'fast_events_custom_status', 'your_filter_custom_status', 10, 1 );

