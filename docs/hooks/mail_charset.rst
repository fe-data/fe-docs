fast_events_mail_charset
========================
This filter is called when an email is sent. Change the character set used in the email.
This filter is only used by the SMTP mailer.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_mail_charset( $charset, $order_id, $payment_status, $event_id, $name, $email ) {
     // Do your manipulation here
     return $charset;
   }

   add_filter( 'fast_events_mail_charset', 'your_filter_mail_charset', 10, 6 );
   
----

Parameters
----------
**$charset**
    (*string*) The default is the character set used by the WordPress installation.
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
(*string*) Character set.

----

Changelog
---------
.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "2.1.0", "Introduced."
