fast_events_errorlog_filter
===========================
This filter is called before the error is written to the database.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_errorlog_filter( $attr ) {
     // Do your manipulation here
     return $attr;
   }

   add_filter( 'fast_events_errorlog_filter', 'your_filter_errorlog_filter', 10, 1 );
   
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
