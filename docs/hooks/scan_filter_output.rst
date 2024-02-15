fast_events_scan_filter_output
==============================
This filter is called just before the output is sent back to the Android or IOS scan app. You can change any of the text lines in the qrcode block.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_scan_filter_output( $attr ) {
     // Do your manipulation here
     return $attr;
   }
   
   add_filter( 'fast_events_scan_filter_output', 'your_filter_scan_filter_output', 10, 1 );
   
----

Parameters
----------
**$attr['order_id']**
    (*int*) The unique order id. This value is *read-only*.
**$attr['qrcode']**
    (*string*) The unique qrcode of the ticket. This value is *read-only*.
**$attr['event']**
    (*string*) The name of the event.
**$attr['type']**
    (*string*) The ticket type (Eg. ``Silver``, ``Backstage``, …).
**$attr['name']**
    (*string*) The name of the person placing the order.
**$attr['email']**
    (*string*) The emailaddress of the person placing the order. This value is *read-only*.
**$attr['date']**
    (*string*) The date when the ticket was scanned. Format ``YYYY-MM-DD HH:MM:SS``.
**$attr['location']**
    (*string*) The location where the ticket was scanned.

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

   "1.0", "Introduced."
   "1.9.3", "Added order_id and qrcode (read-only)."

----
  
Examples
--------
Filter scan output
^^^^^^^^^^^^^^^^^^
For privacy reasons remove the name and emailaddress from the output.

.. code-block:: php
   :linenos:
   
   <?php
   function your_filter_scan_filter_output( $attr ) {
     $attr['name']  = '';
     $attr['email'] = '';
     return $attr;
   }
   
   add_filter( 'fast_events_scan_filter_output', 'your_filter_scan_filter_output', 10, 1 );

