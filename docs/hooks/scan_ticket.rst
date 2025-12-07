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
**$attr['order_id']**
    (*int*) The unique order id.
**$attr['qrcode']**
    (*string*) The unique qrcode of the ticket.
**$attr['status']**
    (*boolean*) Scan result is ``true`` or ``false``. If false, *$attr[‘date’]* and *$attr[‘location’]* will contain the date and location where the ticket was already scanned.
**$attr['event']**
    (*string*) The name of the event.
**$attr['type']**
    (*string*) The name of the ticket.
**$attr['name']**
    (*string*) The name of the person who placed the order.
**$attr['email']**
    (*string*) The emailaddress of the person who placed the order.
**$attr['level']**
    (*int*) **0** = entrance scan, **1** = staged scan, **6** = Reset, **7** = Temporarily leave, **8** = Re-enter and **9** = exit scan.
**$attr['date']**
    (*string*) The date when the ticket was scanned. Format ``YYYY-MM-DD HH:MM:SS``.
**$attr['location']**
    (*string*) The location the ticket was scanned.
**$scans**
    (*array*) Scans ordered by ‘*scan_date*‘
       
    1. **'level'** (*int*)  **0** = Entry scan, **1** = staged scan, **7** = Temporarily leave, **8** = Re-enter and **9** = exit scan
    2. **'scan_date'** (*string*) Uses the date format defined in `Date of sale Overview <../usage/events.html#date-of-sale>`_.
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
   "1.9.3", "Added order_id and qrcode."

----
  
Examples
--------
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

