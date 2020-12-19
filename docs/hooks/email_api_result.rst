fast_events_email_api_result
============================
This action is called after an order email has been send to the email-provider (Host-email, SMTP, Amazon SES, Mailgun, …). This call is made with both a successful email and an incorrect email (submission failed).

.. code-block:: php
   :linenos:

   <?php
   function your_action_email_api( $http_code, $order_id, $email, $result ) {
     // Do what you need to do
   }
   
   add_action( 'fast_events_email_api_result', 'your_action_email_api', 10, 4 );

----

Parameters
----------
**$http_code**
    (*int*) The http resultcode. Consult the Mail Provider API for the right codes. The code may be in the 2xx-range (processing went ok) or an error (usually in the 4xx-range). For ``Host-email`` and ``SMTP`` this is 200 (*Success*) or 400 (*Failure*)
**$order_id**
    (*int*) The id of the order.
**$email**
    (*string*) The emailaddress of the recipient.
**$result**
    (*string*) The result body after the Mail Provider API call. Consult your Mail Provider API for the format and content.

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
Send notification to admin if sending email failed
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Send an email to the WordPress admin if there is an error sending the order email.

.. code-block:: php
   :linenos:
   
   <?php
   function your_action_email_api( $http_code, $order_id, $email, $result ) {
     if ( $http_code >= 200 && $http_code <= 299 ) {
       $subject = 'Order #' . $order_id . ', ' . $email;
       wp_mail( 'admin@yourdomain.com', $subject, $result );
     }
   }
   
   add_action( 'fast_events_email_api_result', 'your_action_email_api', 10, 4 );

