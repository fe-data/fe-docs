Settings
========
The plugin's settings apply to all events. Before you start selling etickets, make sure that all necessary settings have been entered.

By clicking on the tabs on the left you can change various parts of the settings. Then press :guilabel:`Save` to save the settings.

.. list-table::

    * - .. image:: ../_static/images/getting-started/Settings.png
           :target: ../_static/images/getting-started/Settings.png
           :alt: Settings - Payment provider

----

Payment provider account
------------------------
*Fast Events* is integrated with `Mollie <https://my.mollie.com/dashboard/signup/5835294>`_ as payment provider, providing a variety of payment options.
As such the plugin is only available for associations/companies residing in a `SEPA country <https://wiki.xmldation.com/Support/EPC/List_of_SEPA_countries>`_.
With Mollie there are no fixed recurring costs, you only pay for successful transactions. The prices are very competitive.
The transactions of, for example, iDEAL (the Netherlands) cost only € 0.29 excluding VAT. Press the button below to create your free Mollie account.

.. image:: ../_static/images/getting-started/Mollie.png
   :target: https://my.mollie.com/dashboard/signup/5835294
   :alt: Mollie

After you have created your free account, you will receive an email from Mollie with your login details. Confirm the email with the button in the email.

Log in to the Mollie dashboard and go through the wizard to enter all data (Your personal info, chamber of commerce id, bankaccount, VAT number (if applicable),
your identification (passport), website where you want use payments and finally the payment methods.
During the process you will be asked to transfer 1 cent from your company’s bank account to prove that you are the owner.

Live API-key and Test API-key
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Copy the keys from the Mollie :guilabel:`Dashboard` -> :guilabel:`Developers` into the ``Live API-key`` and ``Test API-key`` fields.

Currency
^^^^^^^^
For example ``€``.

Refund costs
^^^^^^^^^^^^
If you do refunds in the :doc:`Orders overview <../usage/orders>`. This amount is deducted from the reimbursement.

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

SaaS mode
^^^^^^^^^
With SaaS mode, it is possible to use *Fast Events* as a ticketing platform to which multiple organizations. associations, ... can be connected.
Each organization then has its own event(s) and its own WordPress account on the platform.
If you want to start using this mode you will first have to register your Application (= *Fast Events* ) once in the
`Mollie Dashboard <https://my.mollie.com/dashboard/signup/5835294>`_ via the menu Developers->Apps. When entering the data, the ``Redirect URL`` should look like this ``https://example.com/wp-json/fast-events/v1/saas/authorize``.
Once the registration is complete, the :guilabel:`Client-ID` and :guilabel:`Client-secret` can be entered below.

Steps required to connect a new organization to the platform:

1. Create a WordPress account for the new organization in the `Admin accounts <../usage/tools.html#admin-accounts>`_ tool in the ``Tools``-section.
   Do **not** create the account in the WordPress dashboard.
2. Add the events for this organization and select the username created under step 1 in the `Saas menu <../usage/events.html#saas>`_.
3. If necessary, change the sender in the `Email tab <../usage/events.html#address-subject>`_.
   Verify that the email provider being used can work with this new sender.
4. Set ``Permissions`` in the `Admin accounts <../usage/tools.html#admin-accounts>`_ menu for the user created in step 1
   and also limit usage to the event ids defined in step 2.
5. The customer can now use the `FE Admin App <../apps/admin.html#regular-accounts>`__ to authorize the platform to process payment information on behalf of the customer.
6. Agree the application fee with the client. Below you can specify this for all organizations, but it can be changed for each event.
   This fee is automatically retained by `Mollie <https://my.mollie.com/dashboard/signup/5835294>`_ and assigned to the service provider hosting *Fast Events*.

Client ID
^^^^^^^^^
The ID you got when registering the App. It usually starts with ``app_``.

Client secret
^^^^^^^^^^^^^
The secret you got when registering the App.

Client fee
^^^^^^^^^^
This is the fee (including VAT) that Mollie retains and allocates to whoever hosts the *Fast Events* plugin in SaaS mode.

Client fee per
^^^^^^^^^^^^^^
The fee can be per order or per ticket.

----

Email settings
--------------

.. list-table::

    * - .. image:: ../_static/images/getting-started/Settings-email.png
           :target: ../_static/images/getting-started/Settings-email.png
           :alt: Settings - email

Email-server type
^^^^^^^^^^^^^^^^^
If you choose ``Host email`` then it is sufficient to fill in the :guilabel:`Sender name` and :guilabel:`Sender email`.
This setting is the default after installation of the plugin.

But choosing the right :guilabel:`Email-server type` depends to a large extent on how many emails can be sent per day.
Check with you hosting provider how many emails you can send per day (or any other period) and compare this with how many orders (= 1 email) you expect per day.
If the expected amount is more than you can send per day you have to go back to your hosting provider to check if you can upgrade your hosting-package with more emails?
Or you can use professional companies that can send your email, such as `Amazon SES <https://aws.amazon.com/ses/>`_, `Mailgun <https://www.mailgun.com/>`_,
`Sendgrid <https://sendgrid.com/>`_, `Postmark App <https://postmarkapp.com/>`_, … and many more. If you go down this path, you can choose for
the other :guilabel:`Email-server type` options. ``SMTP`` is always possible for all email providers, but we have a number of native implementation as well,
which are the faster counterpart of SMTP as this is a rather ‘*chatty*’ protocol.

Sender name and email
^^^^^^^^^^^^^^^^^^^^^
The name and emailaddress you recipients will see in the received tickets email.

Email retries
^^^^^^^^^^^^^
*Fast Events* can be configured to keep retrying to send new order emails. Checking this option is only wise if you are using SMTP or one of the native APIs.
The ``Host email`` solution uses the MTA on the host itself and, if everything is configured correctly, will never return an error.
With ``Host email`` possible hard-bounces (for example: emailaddress doesn't exists) or soft-bounces (for example: mailbox full) will be send back to the sender (Send email).

With SMTP or the native API’s there can be errors. For example the host may be (temporary) unreachable, too many request per time-period, … Consult you API provider for other possible errors. In case of errors you have 2 options:

#. Use the :doc:`fast_events_email_api_result <../hooks/email_api_result>` webhook to inform the WordPress Admin (or another user) that something went wrong
#. Check the checkbox :guilabel:`Email retries` and *Fast Events* will retry sending the email to the SMTP or API-provider again.
   It will use the ``Retry scheme`` to schedule the next retry.

Retry scheme
^^^^^^^^^^^^
The default value is ``2,4,8,16,32,64,128``, which means the first retry is scheduled after 2 minutes, and then 4 minutes, and so on.
You can define your own scheme.

Consult you SMTP or API provider how it handles hard-bounces and soft-bounces. Usually they provide webhooks to process these bounces.

Email webhooks
^^^^^^^^^^^^^^
Enable this if you want include error notification events (bounces, spam reports, ...) from the email-provider, in the errorlog.
Potential error-events are visible in the ``Tools`` section of the ``FE Admin`` App.
For the moment webhooks are only supported for ``Postmark``, ``Mailgun``, ``Mailjet`` and ``Sendgrid``. See below for the details.
     
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
The settings can be found in the `Amazon console dashboard <https://console.aws.amazon.com/>`_.
If you still need to create a SES account, make sure you create it in the ``EU`` region as the plugin is only supported in the `European SEPA countries <https://wiki.xmldation.com/Support/EPC/List_of_SEPA_countries>`_ if online payments are used.
You can find/create in the Amazon IAM (Identity and Access Management) menu the :guilabel:`Access key` and :guilabel:`Secret key`. Make sure the secret key has the right permissions to send email.

Mailgun API settings
^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Mailgun dashboard <https://www.mailgun.com/>`_. If for example your domain is ``somedomain.com``. The server URL would be:

.. code-block:: html

   https://api.eu.mailgun.net/v3/mg.somedomain.com/messages
   
If you create a new sending domain, make sure you create it in the ``EU`` space of Mailgun as this plugin can only be used by the
`European SEPA countries <https://wiki.xmldation.com/Support/EPC/List_of_SEPA_countries>`_.
If you don’t host your domain in the European union (USA flag in dashboard), you have to strip the ``eu`` part from the URL.
This of course will also works, but it adds some latency to the API request. The ‘mg‘ part depends on your DNS settings.

It is possible to log Mailgun '*Spam complaints*', '*Permanent failures*', '*Temporary failures*' and '*Unsubscribe*' events in the log-table of *Fast Events*.
You can configure this in the webhooks section of the Mailgun dashboard.
For the moment other events are discarded.
Use this as URL ``https://user:password@fillinyourdomain.com/wp-json/fast-events/v1/email/webhook/mailgun``.
Use a valid WordPress user and an application password in the url and remove the spaces from the application password.

Mailjet API settings
^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Mailjet dashboard <https://www.mailjet.com/>`_. The URL for the server is:

.. code-block:: html

   https://api.mailjet.com/v3.1/send
   
The :guilabel:`Mailjet API key` is the combination of the user identifier and API key, separated by a colon. For example ``7a8e12:1234a1``

It is possible to log Mailjet '*Bounce*', '*Spam*' and '*Blocked*' events in the log-table of *Fast Events*.
You can configure this in the webhooks section of the Mailjet dashboard. For the moment other events are discarded.
Use this as URL ``https://user:password@fillinyourdomain.com/wp-json/fast-events/v1/email/webhook/mailjet``.
Use a valid WordPress user and an application password in the url and remove the spaces from the application password.
Do not group webhooks. So uncheck these in the Mailjet webhooks dashboard.

Postmark API settings
^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Postmark dashboard <https://postmarkapp.com/>`_. The URL for the server is:

.. code-block:: html

   https://api.postmarkapp.com/email

It is possible to log Postmark '*Bounce*', '*Spam complaint*', '*Subscription change*' and '*Manual suppression*' events in the log-table of *Fast Events*.
You can configure this in the webhooks section of the Postmark dashboard. For the moment other events are discarded.
Use this as URL ``https://fillinyourdomain.com/wp-json/fast-events/v1/email/webhook/postmark``. Furthermore: make sure you enable
Basic authentication and use a valid WordPress user and an application password.
Do **not** include the message content in the webhook!
   
Sendgrid API settings
^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Sendgrid dashboard <https://sendgrid.com/>`_. The URL for the server is:

.. code-block:: html

   https://api.sendgrid.com/v3/mail/send

It is possible to log Sendgrid '*Deferred*', '*Bounce*', '*Dropped*', '*Spam report*', '*Unsubscribe*' and '*Group unsubscribe*' events in the log-table of *Fast Events*.
You can configure this in the webhooks section of the Sendgrid dashboard. For the moment other events are discarded.
Use this as URL ``https://user:password@fillinyourdomain.com/wp-json/fast-events/v1/email/webhook/sendgrid``.
Use a valid WordPress user and an application password in the url and remove the spaces from the application password.
   
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
   
If you create a new sending domain, make sure you create it in the ``EU`` space of Sparkpost as this plugin can only be used by the `European SEPA countries <https://wiki.xmldation.com/Support/EPC/List_of_SEPA_countries>`_.
If you don’t host your domain in the European union, you have to strip the ``eu`` part from the URL. This of course will also works, but it adds some latency to the API request.

----

ReCAPTCHA settings
------------------

.. list-table::

    * - .. image:: ../_static/images/getting-started/Settings-recaptcha.png
           :target: ../_static/images/getting-started/Settings-recaptcha.png
           :alt: Settings - recaptcha

At RSVP events it can of course occur that sick minds spam you with all kind of different real or bogus emailaddresses, even if you have confirmations enabled.
Worse, they may give you a bad reputation, and receiving domains can flag you as spammer. For these cases you can use `Google reCAPTCHA <https://developers.google.com/recaptcha/>`_.
Sign in and setup up your domain; *Fast Events* only supports v2 at the moment. Once setup, copy the keys to the :guilabel:`Site key` and :guilabel:`Secret key`.
Switch on the :guilabel:`ReCaptcha` flag in the `Event settings <../usage/events.html#event-settings>`_ and the booking screen will have a ReCaptcha.

----

REST API settings
-----------------

.. list-table::

    * - .. image:: ../_static/images/getting-started/Settings-rest.png
           :target: ../_static/images/getting-started/Settings-rest.png
           :alt: Settings - rest

These settings work together with the `FE Admin App <../apps/admin.html#administrator-accounts>`__ and WordPress users who have an ``administrator`` role.
The App can be used on your mobile/tablet or desktop browser to perform event and order management and access to all tools

API key
^^^^^^^
The secret key the FE Admin App has to use to secure the communication.
You can use the button to generate a new secure token.
If printed or shown, users can scan it with the camera to configure a new server in the app.

----

Action scheduler
----------------

.. list-table::

    * - .. image:: ../_static/images/getting-started/Settings-as.png
           :target: ../_static/images/getting-started/Settings-as.png
           :alt: Settings - action scheduler

*Fast Events* uses the *Action scheduler* for delivering webhook information, retries to send emails and timed RSVP events.

Do not make any changes to these parameters until you have a good understanding of how the *Action scheduler* works and the consequences of the changes.
You can find `here more information <https://actionscheduler.org/perf/>`_ for a detailed explanation. In case you do fully understand it, make the changes and test!

Bear in mind that the *Action scheduler* can be used by multiple plugins. Make sure to know how these plugins interact with the *Action scheduler*.

The defaults will do fine for small events, but if you have an event with thousands of orders in a short time frame or scanning requests **and** webhook consumers for these events, you may consider different settings.

Purge days
^^^^^^^^^^
After 30 days completed actions will be removed from the logs. With the *Fast Events* plugin you could bring this value down to a lower level.
Check for the longest retry schedule you use in sending your email, in webhooks or timed RSVP events. But also check other plugins using the *Action scheduler*, if any.

Time limit
^^^^^^^^^^
Most shared hosting environments allow a maximum of 30 seconds execution time for a job. If this is different in your situation you can change this.
But don't forget: long running actions also tie up resources for a long time!

Batch size
^^^^^^^^^^
By default if a queue starts running it processes 25 actions. This means with the previous parameter ``Time limit``,
that the system has 30 seconds to process the 25 actions.
But the actions issued by *Fast Events* should finish in a fraction of a second.
If you hook up new webhook consumers tell them to return a HTTP 200 response as soon as possible and
not do first all kinds of processing and then return a HTTP 200. If you switch on logging for a webhook,
you can find the full analysis of the webhook including the ``duration``.
If this is close to 1 second or even bigger, then there is a serious issue.

Concurrent batches
^^^^^^^^^^^^^^^^^^
The default is 1. You could increase this, but before you do make sure your webhook consumers can coop with multiple simultaneous connections.
This parameter works together with the next one.

Additional runners
^^^^^^^^^^^^^^^^^^
Because the *Action scheduler* is only triggered at most once every minute by WP Cron, it rarely happens that multiple concurrent batches are running at the same time.
With this parameter you can force *Action scheduler* to start additional queues at the same time.

Clear queues
^^^^^^^^^^^^
The :guilabel:`Clear queues` button removes all tasks in all *Fast Events* plugin queues and resets the periodic cleanup job.

----

Miscellaneous settings
----------------------

.. list-table::

    * - .. image:: ../_static/images/getting-started/Settings-misc.png
           :target: ../_static/images/getting-started/Settings-misc.png
           :alt: Settings - miscellaneous

Cache time statistics queries
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Some queries, such as a scan overview and the overview of payment statuses, are fairly intensive according to the amount of orders that are there.
This option allows you to cache the results for a certain period of time. The default value is 60 seconds.

Custom order statuses
^^^^^^^^^^^^^^^^^^^^^
A list of custom statutes separated by a comma. The length of a single status should be 32 characters or less.
You can use the custom status fields in the contextmenu of the order-table.
Fi. use it as reminder for calling back a customer after an earlier call. For example, the field could be filled with ``callback,call finished``.
You can then easily find the actions by searching in the orders overview.
It is added at the end of the ``Order status`` field as, for example, :guilabel:`paid (processing)`.

But you can also use it if you occasionally want to sell a book or whatever. Then use, for example, the statuses ``processing, shipped``.

Use ordering API
^^^^^^^^^^^^^^^^
Use the Ordering API added for generating order forms and order status forms, so that the client frontend can be integrated with other,
non WordPress, development environments.
See :doc:`ordering API <../advanced/api-ordering>` for the specification.

Cache time orderscreen
^^^^^^^^^^^^^^^^^^^^^^
Optional specify how many seconds the orderform needs to be cached.
This option is not using WordPress as cache, but relies on an intermediate cache like Cloudflare or others.
For example, if you specify 60 (=60 seconds), an HTTP header is generated such as: ``Cache-Control: public, max-age=60, s-max-age=60``.

Ordering shortcodes
^^^^^^^^^^^^^^^^^^^
Per line you can specify which token should use which shortcode. This setting is only used if the setting :guilabel:`Use ordering API` in this section is switched on.

.. code-block:: text

  token:shortcode

  Example
  =======
  vintage:[fast_events id=2]
  cycle:[fast_events group="fast"]
  status2:[fe_download showimage="yes" downloadtext="Download tickets"]

The tokens **vintage** and **cycle** can be used in the ordering API to generate the orderform. To call this API, do as follows:

.. code-block:: text

   https://exampledomain.com/wp-json/fast-events/v1/ordering/form/vintage

You can then embed this orderform in your own frontend.
To get it working, you also need the ``fe-payment.js`` or ``fe-payment.min.js`` library, which is part of the Fast Events plugin.
The library is 100% javascript and has no other dependencies.

Query the order status by using the order uid.
The API checks to which event id the order belongs and then looks for a token that starts with 'status' supplemented with the event id.
So for example 'status2'. ``LabpCiOAl9a4n4TaVpxI4Gdei63M76zPeDCFfs1N`` is an order that is part of event number 2.

.. code-block:: text

   https://exampledomain.com/wp-json/fast-events/v1/ordering/status/LabpCiOAl9a4n4TaVpxI4Gdei63M76zPeDCFfs1N

The order status lines are **optional**. If not present the default is ``[fe_download showimage="no" downloadtext="Download tickets"]``

----

Management interface
--------------------
.. panels::
   :container: container-lg
   :column: col-lg-6 col-md-12 col-sm-12

   .. figure:: ../_static/images/getting-started/Settings-mgt-install.png
      :target: ../_static/images/getting-started/Settings-mgt-install.png
      :alt: Installation management interface

      Installation management interface
   ---
   .. figure:: ../_static/images/getting-started/Settings-mgt-update.png
      :target: ../_static/images/getting-started/Settings-mgt-update.png
      :alt: Maintenance management interface

      Maintenance management interface

|

As of version 2.0, the plugin's management interface is no longer part of the plugin.
The management interface can be installed separately in this menu and kept up-to-date automatically.
The other option is to use the :doc:`FE Admin App <../apps/admin>` for Android and IOS phones/tablets and not install the Web interface.
This App contains exactly the same functionality as the Web interface.

To install the App for WordPress ``administrator`` users, click `here <../apps/admin.html#administrator-accounts>`_.

But of course you can also do both, i.e. use both the Web interface and the App.

If you install the web version, you can specify whether you want it to update automatically by selecting the auto-update checkbox.
You can also check manually by pressing the ``Check for new version`` button.
If a new version is available, you will be asked if you want to install it.
