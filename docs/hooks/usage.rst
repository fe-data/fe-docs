Actions & filters
=================

Usage
-----
*Fast Events* has a number of action- and filter hooks that can be used to inject custom specific code. Take a look at the examples paragraph of the functions to get an idea how to use them.

If you want to use the filter and action hooks, there are generally a few options.

#. You add your code to the ``functions.php`` file of your theme. The downside of this approach is that every time your theme gets an update you have to redo your changes.
#. Add it to a function in a child theme. This way you don’t have to redo your code if the theme gets an update, but it requires more knowledge.
#. Write you own plugin. You have to be a seasoned developer to go down this path.
#. Or…. use a plugin that does most of the magic for you. If you just want to use a limited set of filters and or action hooks we strongly advice you to take this route. Install the `Code snippets <https://wordpress.org/plugins/code-snippets/>`_ plugin. All the examples in the functions can be easy copied into ``Snippets`` of this plugin. Most examples are easy to understand and easy to adjust.

.. tip:: If you have made a nice snippet yourself, let us know, and we will include it in the documentation as an example.

Reference
---------

:doc:`fast_events_email_api_result <email_api_result>`
    This action is called after an order email has been send to the email-provider (Host-email, SMTP, Amazon SES, Mailgun, …). This call is made with both a successful email and an incorrect email (submission failed).
:doc:`fast_events_errorlog <errorlog>`
    This action is called after the error has been written to the database.
:doc:`fast_events_errorlog_filter <errorlog_filter>`
    This filter is called before the error is written to the database.
:doc:`fast_events_input_fields <input_fields>`
    This filter is called after a basic check of all input and ticket fields.
:doc:`fast_events_invoice <invoice>`
    Download your own designed invoice possibly using an external financial accounting package.
:doc:`fast_events_mail_charset <mail_charset>`
    This filter is called when an email is sent. Change the character set used in the email.
:doc:`fast_events_mail_from <mail_from>`
    This filter is called when an email is sent. Change the From address based on order information.
:doc:`fast_events_mail_from_name <mail_from_name>`
    This filter is called when an email is sent. Change the From address name based on order information.
:doc:`fast_events_new_order <new_order>`
    This action is called after the payment has been received and the customer has already received an email.
:doc:`fast_events_new_order_text <new_order_text>`
    Filter the default error text while processing the order and change the text if necessary.
:doc:`fast_events_order_mail <order_mail>`
    The filter is called for every new order. Filter the email address and return a WP_Error if necessary.
:doc:`fast_events_order_name <order_name>`
    The filter is called for every new order. Filter the name and return a WP_Error if necessary.
:doc:`fast_events_scan_error_text <scan_error_text>`
    This filter is called if there is a scan error. Normally the API returns the localized error, but you can override it and create your own version. You can make the error-string even more specific by using the scancode that is linked to a specific entrance.
:doc:`fast_events_scan_filter_output <scan_filter_output>`
    This filter is called just before the output is sent back to the Android or IOS scan app. You can change any of the text lines in the qrcode block.
:doc:`fast_events_scan_reset_filter <scan_reset_filter>`
    This filter is called just before the scan entries are deleted. Used by scan level 6 (Reset).
:doc:`fast_events_scan_ticket <scan_ticket>`
    This action is called after the ticket has been scanned.
:doc:`fast_events_ticket_text <ticket_text>`
    This filter is called just before the text of the qrcode block is printed on the ticket template.

.. toctree::
   :maxdepth: 1
   :hidden:

   email_api_result
   errorlog
   errorlog_filter
   input_fields
   invoice
   mail_charset
   mail_from
   mail_from_name
   new_order
   new_order_text
   order_mail
   order_name
   scan_error_text
   scan_filter_output
   scan_reset_filter
   scan_ticket
   ticket_text
