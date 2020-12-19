fast_events_ticket_text
=======================
This filter is called just before the text of the qrcode block is printed on the ticket template.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_ticket_text( $attr ) {
     // Do your manipulation here
     return $attr;
   }
   
   add_filter( 'fast_events_ticket_text', 'your_filter_ticket_text', 10, 1 );
   
----

Parameters
----------
**$attr['event_name']**
    (*string*) The name of the event. Comes from `Basics tab <../usage/events.html#basics-tab>`_.
**$attr['ticket_type']**
    (*string*) The name of the ticket. Comes from `Tickets tab <../usage/events.html#tickets-tab>`_.
**$attr['event_date']**
    (*string*) The date of the event. Comes from the `Type tab <../usage/events.html#type-tab>`_ using the defined format.
**$attr['order_id']**
    (*string*) The order id. Example ‘*Order #2914*’. Mind you the word ``Order`` may be translated.
**$attr['name']**
    (*string*) The name of the person who placed the order.
**$attr['email']**
    (*string*) The emailaddress of the person who placed the order.
    
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

----
  
Examples
--------
Remove order-id from tickets
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Remove the order-id string from the ticket qrcode info-block.

.. code-block:: php
   :linenos:
   
   <?php
   function your_filter_ticket_text( $attr ) {
     $attr['order_id'] = '';
     return $attr;
   }
   
   add_filter( 'fast_events_ticket_text', 'your_filter_ticket_text', 10, 1 );

