fast_events_scan_reset_filter
=============================
This action is triggered by scan level 6 (Reset) right before all scan entries are deleted.
You can return a WP_Error here. In that case, the scan is aborted with the specified error message, and the existing scan entries are not deleted.
Another option is to return the integer 9, in which case the ticket isn’t reset; instead, a normal exit scan is performed.
Be careful not to include code that has a long execution time as it directly influences the response time of the mobile scan app.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_scan_reset_filter( $attr, $scans ) {
     // Do what you need to do
     $return $attr;
   }
   
   add_filter( 'fast_events_scan_reset_filter', 'your_filter_scan_reset_filter', 10, 2 );
   
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
$attr, (int) 9 or WP_Error

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
Non-member forced to exit
^^^^^^^^^^^^^^^^^^^^^^^^^
The email address is used to determine whether someone is a member or not.
For members, all scans are deleted, and for non‑members a normal level 9 (exit) scan is performed.

.. code-block:: php
   :linenos:
   
   <?php
   function your_filter_scan_reset_filter( $attr, $scans ) {
     global $wpdb;

     $count = $wpdb->get_var(
       $wpdb->prepare(
          "SELECT COUNT(*) FROM your_private_table WHERE email = %s",
          $attr['email']
       )
     );
     if ( 0 === $count ) {
       return 9;
     }
   }
   
   add_filter( 'fast_events_scan_reset_filter', 'your_filter_scan_reset_filter', 10, 2 );

Log the emailaddress and date of reset
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Log the email address and the departure date in a private database table, if the email domain used in the emailaddress belongs to 'company.com' .

.. code-block:: php
   :linenos:

   <?php
   function your_filter_scan_reset_filter( $attr, $scans ) {
     global $wpdb;

     if ( str_ends_with( $attr['email'], 'company.com' ) ) {
       $wpdb->insert(
         'your_private_table',
         array(
           'email' => $attr['email'],
           'date'  => $attr['date'],
         )
       );
     } else {
       return new WP_Error( 'invalid_user', 'This user is not a member of the organisation', array( 'status' => 406 ) );
     }
   }

   add_filter( 'fast_events_scan_reset_filter', 'your_filter_scan_reset_filter', 10, 2 );