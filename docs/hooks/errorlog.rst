fast_events_error_log
=====================
This action is called after the error has been written to the database.

.. code-block:: php
   :linenos:

   <?php
   function your_action_errorlog( $attr ) {
     // Do what you need to do
   }

   add_action( 'fast_events_errorlog', 'your_action_errorlog', 10, 1 );
   
----

Parameters
----------
**$attr['event_id']**
    (*int*) The id of the event. Keep in mind that the value can be 0.
**$attr['order_id']**
    (*int*) The id of the order. Keep in mind that the value can be 0.
**$attr['type']**
    (*string*) The type of error. Usually a very short identity string.
**$attr['desc']**
    (*string*) The error description. Can be JSON.

----

Return
------
None.

----

Changelog
---------
.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "2.5.0", "Introduced."

----

Examples
--------
Send a notification to admin if an order email bounced
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Send an email to the WordPress administrator when an SMTP2GO webhook reports a bounce event.

.. code-block:: php
   :linenos:

   <?php
   function your_action_errorlog( $attr ) {
     if ( 'Email-SMTP2GO' === $attr['type'] && str_contains( $attr['desc'], 'bounce' ) ) {
       $subject = 'Order #' . $attr['order_id'] . ' bounced';
       wp_mail( 'admin@yourdomain.com', $subject, $attr['desc'] );
     }
   }

   add_action( 'fast_events_errorlog', 'your_action_errorlog', 10, 1 );