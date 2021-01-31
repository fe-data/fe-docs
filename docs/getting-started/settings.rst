Settings
========
The plugin's settings apply to all events. Before you start selling etickets, make sure that all necessary settings have been entered.

By clicking on the tabs on the left you can change various parts of the settings. Then press :guilabel:`Save` to save the settings.

.. list-table::

    * - .. image:: ../_static/images/getting-started/Settings.png
           :target: ../_static/images/getting-started/Settings.png
           :alt: Event groups

----

Payment provider account
------------------------
*Fast Events* is integrated with `Mollie <https://www.mollie.com/dashboard/signup/5835294>`_ as payment provider, providing a variety of payment options. As such the plugin is only available for associations/companies residing in a `SEPA country <https://wiki.xmldation.com/Support/EPC/List_of_SEPA_countries>`_. With Mollie there are no fixed recurring costs, you only pay for successful transactions. The prices are very competitive. The transactions of, for example, iDEAL (the Netherlands) cost only € 0.29 excluding VAT. Press the button below to create your free Mollie account.

.. image:: ../_static/images/getting-started/Mollie.png
   :target: https://www.mollie.com/dashboard/signup/5835294
   :alt: Mollie

After you have created your free account, you will receive an email from Mollie with your login details. Confirm the email with the button in the email.

Log in to the Mollie dashboard and go through the wizard to enter all data (Your personal info, chamber of commerce id, bankaccount, VAT number (if applicable), your identification (passport), website where you want use payments and finally the payment methods. During the process you will be asked to transfer 1 cent from your company’s bank account to prove that you are the owner.

Live API-key and Test API-key
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Copy the keys from the Mollie :guilabel:`Dashboard` -> :guilabel:`Developers` into the ``Live API-key`` and ``Test API-key`` fields.

Currency
^^^^^^^^
For example ``€``.

Refund costs
^^^^^^^^^^^^
If you do refunds in the :doc:`Orders menu <../usage/orders>`. This amount is deducted from the reimbursement.

Refund per
^^^^^^^^^^
The refund costs can be per ``Order`` or per ``Ticket``.

Error page
^^^^^^^^^^
The :guilabel:`Error page` is the page where users end up if:

- The customer cancels the payment or if they left the payment-screen open for a long time and it times out. Timeout periods can differ per payment method.
- The customer did pay, but the Payment provider has not yet informed the plugin that the payment succeeded. You can provide a shortcode in the page, so the user can check again if the payment came through. See example below.

.. list-table::

    * - .. image:: ../_static/images/getting-started/Error-page.png
           :target: ../_static/images/getting-started/Error-page.png
           :alt: Error page

----

Email settings
--------------

Email-server type
^^^^^^^^^^^^^^^^^
If you choose ``Host email`` then it is sufficient to fill in the :guilabel:`Sender name` and :guilabel:`Sender email`. This setting is the default after installation of the plugin.

But choosing the right :guilabel:`Email-server type` depends to a large extent on how many emails can be sent per day. Check with you hosting provider how many emails you can send per day (or any other period) and compare this with how many orders (= 1 email) you expect per day. If the expected amount is more than you can send per day you have to go back to your hosting provider to check if you can upgrade your hosting-package with more emails?
Or you can use professional companies that can send your email, such as `Amazon SES <https://aws.amazon.com/ses/>`_, `Mailgun <https://www.mailgun.com/>`_, `Sendgrid <https://sendgrid.com/>`_, `Postmark App <https://postmarkapp.com/>`_, … and many more. If you go down this path, you can choose for the other :guilabel:`Email-server type` options. ``SMTP`` is always possible for all email providers, but we have a number of native implementation as well, which are the faster counterpart of SMTP as this is a rather ‘*chatty*’ protocol.

Sender name and email
^^^^^^^^^^^^^^^^^^^^^
The name and emailaddress you recipients will see in the received tickets email.

Email retries
^^^^^^^^^^^^^
*Fast Events* can be configured to keep retrying to send new order emails. Checking this option is only wise if you are using SMTP or one of the native APIs. The ``Host email`` solution uses the MTA on the host itself and, if everything is configured correctly, will never return an error. With ‘Host email‘ possible hard-bounces (for example: emailaddress doesn't exists) or soft-bounces (for example: mailbox full) will be send back to the sender (Send email).

With SMTP or the native API’s there can be errors. For example the host may be (temporary) unreachable, too many request per time-period, … Consult you API provider for other possible errors. In case of errors you have 2 options:

#. Use the :doc:`fast_events_email_api_result <../hooks/email_api_result>` webhook to inform the WordPress Admin (or another user) that something went wrong
#. Check the checkbox :guilabel:`Email retries` and *Fast Events* will retry sending the email to the SMTP or API-provider again. It will retry the first hour every 15 minutes and after that it will retry every hour for 3 hours. If it still fails after 4 hours *Fast Events* will inform the WordPress Admin user with an email.

Consult you SMTP or API provider how it handles hard-bounces and soft-bounces. Usually they provide webhooks to process these bounces.
     
SMTP settings
^^^^^^^^^^^^^
**Host email**
   Check this box if you want use your hosting platform the send emails
**Email server**
   The name of the server. Check with your email-provider.
**User**
   Most of the time this takes the form of an emailadress. Check with your email-provider.
**Password**
   The password of the account. Check with your email-provider.
**Verify peer**
   Disabling it and you’ll be vulnerable to a Man-in-the-Middle Attack. Incidentally you may disable it if you are fi. testing with an internal SMTP host with a self-signed certificate.
**Port number**
   Most of the time port ``465`` or ``587`` is used. Check with your email-provider.
**Security protocol**
   Use ``ssl`` or ``tls``. Check with your email-provider.

Amazon SES API settings
^^^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Amazon console dashboard <https://console.aws.amazon.com/>`_. If you still need to create a SES account, make sure you create it in the ``EU`` region as the plugin is only supported in the `European SEPA countries <https://wiki.xmldation.com/Support/EPC/List_of_SEPA_countries>`_ if online payments are used.
You can find/create in the Amazon IAM (Identity and Access Management) menu the :guilabel:`Access key` and :guilabel:`Secret key`. Make sure the secret key has the right permissions to send email.

Mailgun API settings
^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Mailgun dashboard <https://www.mailgun.com/>`_. If for example your domain is ``somedomain.com``. The server URL would be:

.. code-block:: html

   https://api.eu.mailgun.net/v3/mg.somedomain.com/messages
   
If you create a new sending domain, make sure you create it in the ``EU`` space of Mailgun as this plugin can only be used by the `European SEPA countries <https://wiki.xmldation.com/Support/EPC/List_of_SEPA_countries>`_. If you don’t host your domain in the European union (USA flag in dashboard), you have to strip the ``eu`` part from the URL. This of course will also works, but it adds some latency to the API request. The ‘mg‘ part depends on your DNS settings.

Mailjet API settings
^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Mailjet dashboard <https://www.mailjet.com/>`_. The URL for the server is:

.. code-block:: html

   https://api.mailjet.com/v3.1/send
   
The :guilabel:`Mailjet API key` is the combination of the user identifier and API key, separated by a colon. For example ``7a8e12:1234a1``

Postmark API settings
^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Postmark dashboard <https://postmarkapp.com/>`_. The URL for the server is:

.. code-block:: html

   https://api.postmarkapp.com/email
   
Sendgrid API settings
^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Sendgrid dashboard <https://sendgrid.com/>`_. The URL for the server is:

.. code-block:: html

   https://api.sendgrid.com/v2/mail/send
   
Sendinblue API settings
^^^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Sendinblue dashboard <https://www.sendinblue.com/>`_. The URL for the server is:

.. code-block:: html

   https://api.sendinblue.com/v3/smtp/email
   
Sparkpost API settings
^^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Sparkpost dashboard <https://www.sparkpost.com/>`_. The URL for the server is:

.. code-block:: html

   https://api.eu.sparkpost.com/api/v1/transmissions
   
If you create a new sending domain, make sure you create it in the ``EU`` space of Sparkpost as this plugin can only be used by the `European SEPA countries <https://wiki.xmldation.com/Support/EPC/List_of_SEPA_countries>`_. If you don’t host your domain in the European union, you have to strip the ``eu`` part from the URL. This of course will also works, but it adds some latency to the API request.

----

ReCAPTCHA settings
------------------
At RSVP events it can of course occur that sick minds spam you with all kind of different real or bogus emailaddresses, even if you have confirmations enabled. Worse, they may give you a bad reputation, and receiving domains can flag you as spammer. For these cases you can use `Google reCAPTCHA <https://developers.google.com/recaptcha/>`_. Sign in and setup up your domain; *Fast Events* only supports v2 at the moment. Once setup, copy the keys to the :guilabel:`Site key` and :guilabel:`Secret key`.
Switch on the :guilabel:`ReCaptcha` flag in the `Basics tab <../usage/events.html#basics-tab>`_ and the booking screen will have a ReCaptcha.

----

Settings for instant payments
-----------------------------
These settings work together with the :doc:`Payment app <../apps/payment>`. The app generates a qrcode which the customer can scan with the camera or a banking app (Netherlands and Belgium) to make a payment. The ‘*Payment app*’ shows immediately if a payment succeeded or not.

Event-id
^^^^^^^^
This is the id of a special event you have to define. The event is just used for reporting purposes. Set the following fields:

- Basic tab
   - ``Name`` "*Online payments*". You can of course translate this.
   - ``Available start/end date`` make the window large enough
   - ``Stock`` 0
   - ``Redirect after booking`` Set a valid URL to thank the user for the payment
   - Don’t use the other settings
- Type tab
   - ``Event type`` No date
   - ``Group type`` No group
- 'Email tab' and 'Confirmation email tab': don’t use
- 'Input tab': add 2 text-fields ``Account`` and ``Description``. Do **not** translate these fields

Minimum amount
^^^^^^^^^^^^^^
The minimum amount to use for a payment with a qrcode. If you enter a lower value in the app, an error will be returned an no qrcode is generated.

API key
^^^^^^^
The secret key the :doc:`Payment app <../apps/payment>` has to use to secure the communication. You can use the button to generate a new secure token. Copy the qrcode and send it as an attachment in an email to the users of the Payment App. Users can than “*Share*” the qrcode with the Payment App to configure it.

Or they can scan the qrcode to configure the :doc:`Payment app <../apps/payment>`.

----

Settings for the FE Admin App
-----------------------------
These settings work together with the :doc:`FE Admin App <../apps/admin>`. The App can be used on your mobile (for now only on Android) to view the basic information of events and orders. But you can also resend orders, refund, configure the scan app or payment app, and much more …

API key
^^^^^^^
The secret key the :doc:`FE Admin App <../apps/admin>` has to use to secure the communication. You can use the button to generate a new secure token. Copy the qrcode and send it as an attachment in an email to the users of the FE Admin App. Users can than “*Share*” the qrcode with the FE Admin App to configure it. But if printed or shown, users can also scan it with the camera to configure the app.

Or they can scan the qrcode to configure the :doc:`FE Admin App <../apps/admin>`.

----

Authorization settings
----------------------
In the standard installation, only admin users can change all parts of the *Fast Events* plugin, which is usually good enough. But there may be situation where you want to delegate some functionality to non-admin users. The pre-condition is that users need to have an account on your WordPress site with valid login credentials.

Per line you can specify which user is authorized for which actions. Its format is:

.. code-block:: text

   emailaddress:controller1(action1|action2|...),controller2(action3|action4|...),...
   
The following controllers and actions are available. If you you want to grant all actions of a single controller, you can also specify a ***** (asterisk):

Settings controller
^^^^^^^^^^^^^^^^^^^

- ``read`` All settings can be read
- ``write`` Settings can be saved

Errorlog controller
^^^^^^^^^^^^^^^^^^^

- ``read`` Read the errorlog

Events controller
^^^^^^^^^^^^^^^^^
- ``read`` Read events
- ``update`` Change events
- ``add`` Add new events
- ``duplicate`` Duplicate events
- ``set_zero`` Set all counters to zero
- ``remove_all`` Remove all orders from an event
- ``test_email`` Send test emails
- ``user_group_read`` Read closed user groups
- ``user_group_upload`` Upload new user groups
- ``user_group_delete`` Delete user groups
- ``example_ticket`` Create an example ticket
- ``example_invoice`` Create an example invoice
- ``bulk_copy`` Copy changes from 1 event to many other events
- ``export`` Expert events and related pages and templates
- ``import`` Import events and related pages and templates

Tools controller
^^^^^^^^^^^^^^^^
- ``orders`` Resend confirmation emails
- ``email`` Send free format emails
- ``refund`` Refund orders

Qrcode controller
^^^^^^^^^^^^^^^^^
- ``admin_app_read`` Read the qrcode for the Admin App
- ``payment_app_read`` Read the qrcode for the Payment App
- ``scan_app_read`` Read the qrcode for the Scan App
- ``admin_app_change`` Change the qrcode for the Admin App
- ``payment_app_change`` Change the qrcode for the Payment App
- ``scan_app_change`` Change the qrcode for the Scan App

Orders controller
^^^^^^^^^^^^^^^^^
- ``read`` Read orders
- ``dashboard_order`` Add new orders
- ``email`` Resend the order by email
- ``change_email`` Change the user credentials
- ``custom_status`` Set a custom status
- ``delete`` Delete the order
- ``delete_tickets`` Delete the tickets
- ``create_tickets`` Create new tickets
- ``download_tickets`` Download the PDF tickets
- ``download_invoice`` Download the PDF invoice
- ``refund`` Refund the order

Admin_app controller
^^^^^^^^^^^^^^^^^^^^
- ``event_read`` Read events
- ``change_stock`` Change stock of event and/or tickets
- ``change_dates`` Change date of sales
- ``total_sales`` Overview of total sales
- ``total_scans`` Overview of all scans
- ``order_read`` Read orders
- ``order_details`` Show order details
- ``order_email`` Resend the order confirmation
- ``change_email`` Change the user credentials of the order
- ``delete_order`` Delete the order
- ``delete_tickets`` Delete the tickets from the order
- ``create_tickets`` Create new tickets for the selected order
- ``refund`` Refund the order
- ``dashboard_order`` A new orders
- ``payment_app_read`` Show the qrcode for the Payment App
- ``scan_app_read`` Show the qrcode for the Scan App
- ``payment_app_change`` Change the qrcode for the Payment App
- ``scan_app_change`` Change the qrcode for the Scan App

Pay_app controller
^^^^^^^^^^^^^^^^^^
- ``create`` Create a new direct payment

Suppose you want to give a customer services representative the option to see orders details, resend the confirmation, change credentials en refund orders, the authorization line would be:

.. code-block:: text

   any_email@domain.com:orders(details|email|change_email|refund)

----

Miscellaneous settings
----------------------
**Custom order statuses**
   A list of custom statutes separated by a comma. The length of a single status should be 32 characters or less. You can use the custom status fields in the contextmenu of the order-table.
   Fi. use it as reminder for calling back a customer after an earlier call. For example, the field could be filled with ``callback,call finished``.
   You can then easily find the actions by sorting on this field in the order table.

   But you can also use it if you occasionally want to sell a book or whatever. Then use, for example, the statuses ``processing, shipped``.
   You can then send the customer an email update with the custom filter :doc:`fast_events_custom_status <../hooks/custom_status>` if the status has changed.
   A simple solution if you do this occasionally, but if it is more structural then a solution like `WooCommerce <https://wordpress.org/plugins/woocommerce/>`_ is recommended.
