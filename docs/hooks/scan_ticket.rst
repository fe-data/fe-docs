fast_events_scan_ticket
=======================
This action is called after the ticket has been scanned. Be careful not to include code that has a long execution time as it directly influences the response time of the mobile scan app.

.. code-block:: php
   :linenos:

   <?php
   function your_action_scan_ticket( $attr, $scans ) {
     // Do what you need to do
   }
   
   add_action( 'fast_events_scan_ticket', 'your_action_scan_ticket', 10, 2 );
   
----

Parameters
----------
**$attr['status']**
    (*boolean*) Scan result is ``true`` or ``false``. If false, *$attr[‘date’]* and *$attr[‘location’]* will contain the date and location where the ticket was already scanned.
**$attr['event']**
    (*string*) The name of the event. Comes from `Basics tab <../usage/events.html#basics-tab>`_.
**$attr['type']**
    (*string*) The name of the ticket. Comes from `Tickets tab <../usage/events.html#tickets-tab>`_.
**$attr['name']**
    (*string*) The name of the person who placed the order.
**$attr['email']**
    (*string*) The emailaddress of the person who placed the order.
**$attr['level']**
    (*int*) **0** = entrance scan, **1** = staged scan, **9** = exit scan.
**$attr['date']**
    (*string*) The date when the ticket was scanned. Format ``YYYY-MM-DD HH:MM:SS``.
**$attr['location']**
    (*string*) The location the ticket was scanned.
**$attr['scans']**
    (*array*) Scans ordered by ‘*scan_date*‘
       
    1. **'level'** (*int*)  **0** = Entry scan, **1** = staged scan, **9** = exit scan
    2. **'scan_date'** (*string*) Uses the date format defined in ‘Scan -tab‘.
    3. **'scan_location'** (*string*) The location of the scan.
    
----

Return
------
None

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
Google Analytics scan event
^^^^^^^^^^^^^^^^^^^^^^^^^^^
All scan data is entered in `Google Analytics <https://analytics.google.com/>`_, so you get valuable real-time insight into the scanning activities. `Install Google Analytics <https://play.google.com/store/apps/details?id=com.google.android.apps.giant>`_ on your mobile and you will always have the scan-data available at your fingertips.

.. code-block:: php
   :linenos:
   
   <?php
   function your_action_scan_ticket( $attr ) {
     wp_remote_post( 'https://www.google-analytics.com/collect', [
       'timeout' => 3,
       'body'    => [
         'v'   => 1,
         't'   => 'event',
         'tid' => 'UA-XXXXXXXXX-X',  // Put your own tracking ID here
         'ds'  => 'Fast Events',
         'cid' => hash( 'adler32', $attr['email'] ) . '-1a05-49d7-b876-2b884d0f825b',
         'ec'  => 'scan-' . ( true === (bool) $attr['status'] ? '1' : '0' ),
         'ea'  => $attr['location'] . ' - ' . $attr['type'],
         'el'  => $attr['type'],
         'ev'  => 1
       ]
     ]);
   }
   
   add_action( 'fast_events_scan_ticket', 'your_action_scan_ticket', 10, 1 );

Send “Thank you” email after exit scan
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Send a “*Thank you for visiting*” email to users who pass the exit scan (level = 9). You can of course trigger on another level or any other attribute. Use the internal function ``fe_helper_func()->send_email()`` to send an email which will use the credentials defined in the plugin settings.

.. code-block:: php
   :linenos:
   
   <?php
   function your_action_scan_ticket( $attr, $scans ) {
     if ( 9 === $attr['level'] ) {
       $message = '<p>Dear ' . $attr['name'] . ',</p>' .
         '<p>Thank you for visiting our event. Hope to see you <b>next</b> year</p>' .
         '<p>Vintage Vinyl Open Air 2019 team</p>';
       fast_events_helper_func()->send_email( $attr['email'], "Thank you for visiting Vintage Vinyl Open Air 2019", $message );
     }
   }
   
   add_action( 'fast_events_scan_ticket', 'your_action_scan_ticket', 10, 2 );

Send “Thank you” email with detailed scan info
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Send a “*Thank you for visiting*” email to users who pass the exit scan (level = 9) and also email them the detailed info on when they passed all checkpoints during the bicycle tour. You can of course trigger on another level or any other attribute. Use the internal function ``fe_helper_func()->send_email()`` to send an email which will use the credentials defined in the plugin settings.

.. code-block:: php
   :linenos:
   
   <?php
   function your_action_scan_ticket( $attr, $scans ) {
     if ( 9 === $attr['level'] ) {
       $message = '<p>Dear ' . $attr['name'] . ',</p>' .
         '<p>Thank you for participating in our bicycle tour. Hope to see you <b>next</b> year.' .
         'Below are the times when you passed the checkpoints.</p><table>';
       foreach( $scans as $key => $value ) {
         $message .= '<tr><td>' . $value->scan_date . '</td><td>' . $value->scan_location . '</td></tr>';
       }
       $message .= '</table><p>The National bicycle tour team</p>';
       fast_events_helper_func()->send_email( $attr['email'], "Thank you for participating in our bicycle tour", $message );
     }
   }
   
   add_action( 'fast_events_scan_ticket', 'your_action_scan_ticket', 10, 2 );

