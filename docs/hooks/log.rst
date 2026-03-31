fast_events_log
===============
This action is called after the log message has been written to the database.

.. code-block:: php
   :linenos:

   <?php
   function your_action_log( $context ) {
     // Do what you need to do
   }

   add_action( 'fast_events_log', 'your_action_errorlog', 10, 2 );
   
----

Parameters
----------
**$message**
    (*string*) The log message.
**$context['event_id']**
    (*int*) The id of the event. Keep in mind that the value can be 0.
**$context['order_id']**
    (*int*) The id of the order. Keep in mind that the value can be 0.
**$context['type']**
    (*string*) The type of error. Usually a very short identity string.
**$context['level']**
    (*string*) Can be: emergency, alert, critical, error, warning, notice, info or debug.
**$context['data']**
    (*mixed*) Optional additional information.

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
   "3.0.0", "Using PSR-3 method properties."

----

Examples
--------
Send a notification to admin if an order email bounced
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Send an email to the WordPress administrator when an SMTP2GO webhook reports a bounce event.

.. code-block:: php
   :linenos:

   <?php
   function your_action_log( $message, $context ) {
     if ( 'Email-SMTP2GO' === $context['type'] && str_contains( $message, 'bounce' ) ) {
       $subject = 'Order #' . $context['order_id'] . ' bounced';
       wp_mail( 'admin@yourdomain.com', $subject, $message );
     }
   }

   add_action( 'fast_events_log', 'your_action_log', 10, 2 );