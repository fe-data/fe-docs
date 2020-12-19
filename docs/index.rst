Fast Events Ticketing
=====================

.. meta::
   :description lang=en: WordPress e-ticketing plugin for sport events, festivals, congresses, seminars, you local party, ...
   
.. image:: _static/images/Headline.png
   :alt: Headline

.. note:: If online payments are used, the plugin currently only works for companies, associations, foundations ... located in a `SEPA country <https://wiki.xmldation.com/Support/EPC/List_of_SEPA_countries>`_.
   There is no region restriction for free tickets or RSVP meetings.
   
Getting started
---------------

A global overview of the :doc:`features <getting-started/introduction>` that Fast Events supports and how to :doc:`install <getting-started/installation>` and :doc:`configure <getting-started/settings>` the plugin.

* **Feature overview of Fast Events**:
  :doc:`Introduction <getting-started/introduction>`
* **Install the Fast Events plugin**:
  :doc:`Installation <getting-started/installation>`
* **Overview**:
  :doc:`Usage overview <getting-started/overview>`
* **Global Settings**:
  :doc:`Settings <getting-started/settings>`
* **Changelog**:
  :doc:`Changelog <getting-started/changelog>`


.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: Getting started

   getting-started/introduction
   getting-started/installation
   getting-started/overview
   getting-started/settings
   getting-started/changelog
   
Usage
-----

How to use the different menu choices.

* **Error logging**:
  :doc:`Errors <usage/errorlog>`
* **Events menu**:
  :doc:`Edit events <usage/events>`
* **Tools menu**:
  :doc:`Tools <usage/tools>`
* **Order menu**:
  :doc:`Orders <usage/orders>`


.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: Usage

   usage/events
   usage/orders
   usage/tools
   usage/errorlog
   usage/examples
   
Apps
-----
With Fast Events you can use our free scan app for Android and IOS. No need for expensive scanning equipment, just use your phone.
There is also a free payment app. The user scans a QR code and the payment is carried out easily and securely.

For Android there is also an Admin App available. You can view events and orders and change them on the go. Or show the stats of sold tickets and scanned tickets. And much more ...

* **Scan App**:
  :doc:`scanning <apps/scan>`
* **Payment App**:
  :doc:`payment <apps/payment>`
* **FE Admin App**:
  :doc:`admin <apps/admin>`

.. toctree::
   :maxdepth: 3
   :hidden:
   :caption: Apps

   apps/scan
   apps/payment
   apps/admin
   
Advanced features
-----------------
Most things perform better when they’re maintained. We have pulled together a number of recommendations in the field of security, performance and tools for data analysis. This list is by no means complete, but we urge you to keep an eye on security and performance in order to safely and in a performant way run the software.

* **Data analysis**:
  :doc:`analysis <advanced/analysis>`
* **Security**:
  :doc:`security <advanced/security>`
* **Performance**:
  :doc:`performance <advanced/performance>`

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Advanced features

   advanced/analysis
   advanced/security
   advanced/performance
   
Hooks
-----
*Fast Events* has a number of :doc:`action- and filter hooks </hooks/usage>` that can be used to inject custom specific code.

:doc:`fast_events_custom_status <hooks/custom_status>`
    This filter is called after a custom order status change from the order contextmenu. It can only be used if the ‘Custom order statuses’ field has been set in the plugin settings.
:doc:`fast_events_email_api_result <hooks/email_api_result>`
    This action is called after an order email has been send to the email-provider (Host-email, SMTP, Amazon SES, Mailgun, …). This call is made with both a successful email and an incorrect email (submission failed).
:doc:`fast_events_input_fields <hooks/input_fields>`
    This filter is called after a basic check of all input and ticket fields.
:doc:`fast_events_new_order <hooks/new_order>`
    This action is called after the payment has been received and the customer has already received an email.
:doc:`fast_events_new_order_text <hooks/new_order_text>`
    Filter the default error text while processing the order and change the text if necessary.
:doc:`fast_events_scan_error_text <hooks/scan_error_text>`
    This filter is called if there is a scan error. Normally the API returns the localized error, but you can override it and create your own version. You can make the error-string even more specific by using the scancode that is linked to a specific entrance.
:doc:`fast_events_scan_filter_output <hooks/scan_filter_output>`
    This filter is called just before the output is sent back to the Android or IOS scan app. You can change any of the text lines in the qrcode block.
:doc:`fast_events_scan_ticket <hooks/scan_ticket>`
    This action is called after the ticket has been scanned.
:doc:`fast_events_ticket_text <hooks/ticket_text>`
    This filter is called just before the text of the qrcode block is printed on the ticket template.

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Hooks

   hooks/usage
   hooks/custom_status
   hooks/email_api_result
   hooks/input_fields
   hooks/new_order
   hooks/new_order_text
   hooks/scan_error_text
   hooks/scan_filter_output
   hooks/scan_ticket
   hooks/ticket_text

Miscellaneous
-------------
Developing, improving and maintaining an plugin like Fast Events takes and mobile apps for Android and IOS takes a lot of time. Please consider sponsoring the development of this plugin or a :doc:`one-off donation </misc/donate>` if you have successfully executed an event.

* **Donate**:
  :doc:`donate <misc/donate>`
* **FAQ**:
  :doc:`faq <misc/faq>`
* **License**:
  :doc:`license <misc/license>`

.. toctree::
   :maxdepth: 0
   :hidden:
   :caption: Miscellaneous

   misc/donate
   misc/faq
   misc/license

