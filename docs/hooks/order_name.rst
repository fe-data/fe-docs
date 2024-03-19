fast_events_order_name
======================
The filter is called for every new order. Filter the name and return a WP_Error if necessary.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_order_name( $name ) {
     if ( in_array( $name, array( 'Idiot', 'Moron' ) ) ) {
         return new WP_Error( 'invalid_name', 'This name is not allowed', array( 'status' => 400 ) );
     }
     return $name;
   }

   add_filter( 'fast_events_order_name', 'your_filter_order_name', 10, 1 );
   
----

Parameters
----------
**$name**
    (*string*) Name of the buyer.

----

Return
------
(*string | WP_Error*) The name or WP_Error.

----

Changelog
---------
.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "2.2.0", "Introduced."
