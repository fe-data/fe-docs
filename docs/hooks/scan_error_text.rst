fast_events_scan_error_text
===========================
This filter is called if there is a scan error. Normally the API returns the localized error, but you can override it and create your own version.
You can make the error-string even more specific by using the scancode that is linked to a specific entrance. See the `Scan keys overview <../usage/events.html#scan-keys>`__.

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
    4. ‘*This scan has already been done*’. The level 1 or 9 scan has already been carried out.
    5. ‘*This event does not support tracking*’. The tracking flag is not enabled or the tracking info is not present.
    6. ‘*Invalid tracking window*’. The finish scan was done outside the tracking window.
    7. ‘*Invalid signing key*’. The finish scan produced an invalid signing key.
    8. ‘*Invalid scan key*’. The scan key is not found. This is configuration error of the Scan App.
    9. ‘*Wrong type of qrcode*’. The qrocde presented is not one that was generated for a tracking event.
    10. ‘*Invalid track signature*’. The FE Scan App submitted an invalid track signature.
    11. ‘*Invalid finish API key*’. An invalid API key (not level 9) was used in the FE Scan App
    12. ‘*You cannot scan this checkpoint*’. The 'Force Tracking App' is set; no level 0 and level 1 scans are possible with the Scan App, they  need to uploaded automatically by the Tracking App.
    13. ‘*Ticket already temporarily left the event*’. A level 7 (Temporarily leave) scan was already done.
    14. ‘*Ticket already re-entered the event*’. A level 8 (Re-enter) scan was already done.

**$scancode**
    (*string*) The scancode used.

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
   "2.4.0", "Introduced message #13 and #14."

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
