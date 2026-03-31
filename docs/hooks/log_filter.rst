fast_events_log_filter
======================
This filter is called before the log message is written to the database.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_log_filter( $attr ) {
     // Do your manipulation here
     return $attr;
   }

   add_filter( 'fast_events_log_filter', 'your_filter_errorlog_filter', 10, 2 );
   
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
**$attr**
    See `Parameters`_.

----

Changelog
---------
.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "2.5.0", "Introduced."
   "3.0.0", "Using PSR-3 method properties."
