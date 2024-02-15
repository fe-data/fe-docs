fast_events_mail_from_name
==========================
This filter is called when an email is sent. Change the From address name based on order information.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_mail_from_name( $from_name, $order_id, $payment_status, $event_id, $name, $email ) {
     // Do your manipulation here
     return $from_name;
   }

   add_filter( 'fast_events_mail_from_name', 'your_filter_mail_from_name', 10, 6 );
   
----

Parameters
----------
**$from_name**
    (*string*) Default is the name from the settings or the 'sender name' defined at event level.
**$order_id**
    (*int*) Unique id of the order.
**$payment_status**
    (*string*) The payment status of the order.
**$event_id**
    (*int*) Unique id of the event.
**$name**
    (*string*) The name of the person placing the order.
**$email**
    (*string*) The email address of the person placing the order.

----

Return
------
(*string*) From email address name.

----

Changelog
---------
.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "2.1.0", "Introduced."
