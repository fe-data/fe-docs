fast_events_new_order_text
==========================
Filter the default error text while processing the order and change the text if necessary.

.. code-block:: php
   :linenos:

   <?php
   function your_filter_new_order_text( $message, $type ) {
     // Do your manipulation here
     return $message;
   }
   
   add_filter( 'fast_events_new_order_text', 'your_filter_new_order_text', 10, 2 );

----

Parameters
----------
**$message**
    (string) The localized message-string.
**$type**
    (*int*) The type of message.
    
    0. ‘*Choose event*’. Used during a single select.
    1. ‘*Choose 1 or more events*’. The user can select multiple events during ordering.
    2. ‘*Mandatory input not available*’. Name and/or emailaddress are not available.
    3. ‘*Invalid emailaddress*’.
    4. ‘*Name is too long (Max 50 chars)*’.
    5. ‘*Emailaddress is too long (Max 100 chars)*’.
    6. ‘*WordPress nonce error, please reload the order form and try again*’.
    7. ‘*You must agree to the terms*’.
    8. ‘*Wrong reCAPTCHA*’.
    9. ‘*Mandatory input is not available*’. Extra input fields are not filled or no event selected.
    10. ‘*No event selected*’.
    11. ‘*Event does not exist*’.
    12. ‘*Invalid event ids*’. One of the selected events is not valid.
    13. ‘*You already have a booking/order*’. The user is trying to order again whilst this is not allowed.
    14. ‘*Event %d does not exists*’. Caution: make sure you include ‘%d’, which will be substituted with the event id.
    15. ‘*Event %d is not active*’.
    16. ‘*Filter corrupted output*’. The :doc:`fast_events_input_fields </hooks/input_fields>` filter was used and it corrupted the output.
    17. ‘*You are not allowed to book/order*’. A user group check prohibited the user from placing an order.
    18. ‘*You can book a maximum of %d tickets*’. A user group check did limit the number of tickets a user can order. Make sure you include ‘%d’.
    19. ‘*No more stock available for “%s”*‘. The ‘%s’ is substituted with the event name. Make sure it is included in your message.
    20. ‘*Stock update failed for “%s”*‘.
    21. ‘*Not enough stock available for ticket-type: %1$s (%2$s)*’. Make sure you include the string ‘%1$s (%2$s)‘, which represents the ticket-name and event name.
    22. ‘*No child events found for passe-partout*’. You defined a passe-partout, but did not include events.
    23. ‘*Unknown user*’. The WordPress user is unknown.
    24. ‘*Invalid password*’. The password for the WordPress user is invalid.
    25. ‘*User role mismatch*’. The user role did not match the one(s) defined in the user group.
    26. ‘*Missing ticket type:*’. The ticket type is not present in the input. The name of the ticket is appended after the colon.
    27. ‘*Missing extra input fields for this event*’. The extra input fields are not submitted.
    28. ‘*Required extra input fields not available*’. The required extra input fields are not submitted.
    29. ‘*No tickets ordered*’.
    30. ‘*Not enough stock for linked event-id %d*’.
    31. ‘*Illegal value extra input field*’. This may happen in case of a 'select' field.
    32. ‘*Wrong amount for this ticket type:*’. The amount is too low or too high. The name of the ticket is appended after the colon.
    33. ‘*Coupon code %s not found*’. The coupon code does not exist.
    34. ‘*The discount code is not yet active*’.
    35. ‘*The discount code has expired*’.
    36. ‘*The maximum number of times the discount code can be used has been reached*’.
    37. ‘*This discount code is linked to another email address*’.
    38. ‘*This discount code is not linked to this event*’.
    39. ‘*This discount code requires a minimum of %1$s tickets %2$s*’. The first parameter is the minimum number of tickets. The second a comma-separated list of ticket types.
    40. ‘*This discount code allows a maximum of%1$s tickets %2$s*’. The first parameter is the maximum number of tickets. The second a comma-separated list of ticket types.
    41. ‘*A minimum amount of %1$s %2$s is required for this discount code*’.The first parameter is the minimum amount. The second a comma-separated list of ticket types.
    42. ‘*A maximum amount of %1$s %2$s is allowed for this discount code*’.The first parameter is the maximum amount. The second a comma-separated list of ticket types.
    43. ‘*The maximum number of times the discount code can be used is: %s*’.

----

Return
------
(string) Message string.

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
Change description of selecting an event
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
If the user has the option to select 1 dance evening from a select box, the standard description is ‘*Choose event*‘.

.. code-block:: php
   :linenos:
   
   <?php
   function your_filter_new_order_text( $message, $type ) {
     if ( 0 === $type ) {
  	   return "Choose your dance evening";
     }
     return $message;
   }
   
   add_filter( 'fast_events_new_order_text', 'your_filter_new_order_text', 10, 2 );
