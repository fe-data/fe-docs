fast_events_mail_from
=====================
This filter is called when an email is sent. Change the From address based on order information.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_mail_from( $from_email, $order_id, $payment_status, $event_id, $name, $email ) {
     // Do your manipulation here
     return $from_email;
   }

   add_filter( 'fast_events_mail_from', 'your_filter_mail_from', 10, 6 );
   
----

Parameters
----------
**$from_email**
    (*string*) Default is the address from the settings or the 'sender email address' defined at event level.
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
(*string*) From email address.

----

Changelog
---------
.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "2.1.0", "Introduced."
