fast_events_scan_error_text
===========================
This filter is called if there is a scan error. Normally the API returns the localized error, but you can override it and create your own version. You can make the error-string even more specific by using the scancode that is linked to a specific entrance. See the ‘Scan-tab‘.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_scan_error_text( $error, $type, $scancode ) {
     // Do your manipulation here
     return $error;
   }
   
   add_filter( 'fast_events_scan_error_text', 'your_filter_scan_error_text', 10, 3 );

----

Parameters
----------
**$message**
    (string) The localized message-string.
**$type**
    (*int*) The type of message.
    
    0. ‘*Ticket not found*’.
    1. ‘*‘Invalid ticket for this entrance*’. The ticket was found, but it is not allowed to use it at this entrance.
    2. ‘*No entrance scan performed*’. This is a staged scan, but the ticket was not scanned at the main entrance.
    3. ‘*Ticket already left the event*’. An exit scan was done earlier, no scanning possible anymore.

**$scancode**
    (*string*) The scancode used. Comes from the `Scan tab <../usage/events.html#scan-tab>`_.

----

Return
------
(string) Error string.

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
Change error strings for scan errors
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Change the error string if a customer with a wrong ticket type tries to enter the Backstage tour.

.. code-block:: php
   :linenos:
   
   <?php
   function your_filter_scan_error_text( $error, $type, $scancode ) {
     if ( 1 === $type && $scancode === 'p5TbVsTrsdLFYO3Y' ) {
  	   return "This ticket is not valid for a Backstage tour.";
     }
     return $error;
   }
   
   add_filter( 'fast_events_scan_error_text', 'your_filter_scan_error_text', 10, 3 );
