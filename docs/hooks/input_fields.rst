fast_events_input fields
========================
This filter is called after a basic check of all input and ticket fields.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_input_fields( $attr ) {
     // Do your manipulation here
     return $attr;
   }
   
   add_filter( 'fast_events_input_fields', 'your_filter_input_fields', 10, 1 );

----

Parameters
----------
**$attr['id']**
    (*int*) The id of the event. This value is *read-only*.
**$attr['name']**
    (*string*) The name of the person placing the order.
**$attr['email']**
    (*string*) The emailaddress of the person placing the order. This value is *read-only*.
**$attr['total']**
    (*string*) The total order value. For example ``6.50``. This value is *read-only*.
**$attr['total_vat']**
    (*string*) The total order VAT value. For example ``2.50``. This value is *read-only*.
**$attr['fields']**
    *array* of input fields.
       
    1. **'name'** (*string, case sensitive*) The name of the input field.
    2. **'value'** (*string*) The value of the input field.
**$attr['tickets']**
    *array* of ticket-types ordered.
       
    1. **'name'** (*string, case sensitive*) The name of the ticket-type.
    2. **'price'** (*string*) The ticket price. Example ``6.25``.
    3. **'vat'** (*string*) VAT.
    4. **'count'** (*int*) The number of tickets ordered.

----

Return
------
**$attr**
    A filter can add an ``errors`` attribute to ``$attr``. So for example ``$attr['errors'] = 'Wrong value'``. Fast Events will check and stop processing the order by returning the error. See the `Check password`_ example.

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
Discount between dates
^^^^^^^^^^^^^^^^^^^^^^
Give a discount of 10% (in this example; see the 0.9) on every ticket-type between 2 dates.

.. code-block:: php
   :linenos:
   
   <?php
   function your_filter_input_fields( $attr ) {
     if ( time() > strtotime('2019-12-10 00:00:00') && time() < strtotime('2019-12-24 18:00:00') ) {
       foreach ( $attr['tickets'] as $key => $value ) {
         $attr['tickets'][$key]['price'] = number_format( 0.9 * (float) $value['price'], 2, '.', '' );
       }
     }
     return $attr;
   }
   
   add_filter( 'fast_events_input_fields', 'your_filter_input_fields', 10, 1 );

Discount if more than 3 tickets
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Give a discount of 20% if you order more than 3 ``Silver`` tickets.

.. code-block:: php
   :linenos:
   
   <?php
   function your_filter_input_fields_2( $attr ) {
     foreach ( $attr['tickets'] as $key => $value ) {
       if ( 'Silver' === $value['name'] && 3 < $value['count'] ) {
         $attr['tickets'][$key]['price'] = number_format( 0.8 * (float) $value['price'], 2, '.', '' );
       }
     }
     return $attr;
   }
   
   add_filter( 'fast_events_input_fields', 'your_filter_input_fields_2', 10, 1 );

Free ticket
^^^^^^^^^^^
Get 1 free ``Silver`` ticket if you order 2 or more ``Gold (Backstage)`` tickets.

.. code-block:: php
   :linenos:
   
   <?php
   function your_filter_input_fields_3( $attr ) {
     foreach ( $attr['tickets'] as $key => $value ) {
       if ( 'Gold (Backstage)' === $value['name'] && 2 <= $value['count'] ) {
         $silver_key = array_search('Silver', array_column($attr['tickets'], 'name'));
         $old_total  = $attr['tickets'][$silver_key]['count'] * (float) $attr['tickets'][$silver_key]['price'];
         $new_price  = $old_total / ( $attr['tickets'][$silver_key]['count'] + 1 );
         $attr['tickets'][$silver_key]['price'] = number_format( $new_price, 2, '.', '' );
         $attr['tickets'][$silver_key]['count']++;
       }
     }
     return $attr;
   }
   
   add_filter( 'fast_events_input_fields', 'your_filter_input_fields_3', 10, 1 );

Check password
^^^^^^^^^^^^^^
Check the password against a database table. This requires you to define an input field ``Password`` that is used in this snippet. A wrong password or a non-existing user will result in an error. Finding the user is done with the emailaddress.

.. code-block:: php
   :linenos:
   
   <?php
   function your_filter_input_fields_4( $attr ) {
     // Search for user
     $user = $wpdb->get_row( $wpdb->prepare( "SELECT password FROM put_your_tablename_here WHERE email = '%s'", $attr['email'] ) );
     if ( empty( $user ) ) {
	   $attr['errors'] = 'Unknown user';
	   return $attr;
     }
  
     $pwd_key = array_search('Password', array_column($attr['fields'], 'name'));
     if ( ! password_verify( $attr['fields'][$pwd_key]['value'], $user->password ) ) {
       $attr['errors'] = 'Wrong password';
     }
     return $attr;
   }
   
   add_filter( 'fast_events_input_fields', 'your_filter_input_fields_4', 10, 1 );

