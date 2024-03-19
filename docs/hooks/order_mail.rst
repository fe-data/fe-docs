fast_events_order_mail
======================
The filter is called for every new order. Filter the email address and return a WP_Error if necessary.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_order_mail( $email ) {
     if ( str_ends_with( $email, 'exampledomain.com' ) ) {
         return new WP_Error( 'invalid_email', 'An email address from this domain is not allowed', array( 'status' => 400 ) );
     }
     return $email;
   }

   add_filter( 'fast_events_order_mail', 'your_filter_order_mail', 10, 1 );
   
----

Parameters
----------
**$email**
    (*string*) Email address of the buyer.

----

Return
------
(*string | WP_Error*) The email address or WP_Error.

----

Changelog
---------
.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "2.2.0", "Introduced."
