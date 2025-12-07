Email webhooks
==============

Preparations
------------
Email provider webhooks can notify *Fast Events* about key message events such as ``bounces``, ``deliveries``, ``opens``,
``clicks``, ``spam complaints`` and more. The names of the events differ depending on the email provider.
Each request contains a JSON object with information about the event.

Some events are labeled as errors by *Fast Events* and can be found for the order in the `Error log <orders.html#error-log>`_ menu.
Usually these are bounce events caused, for example, by an incorrect email address, but there can be other reasons as well.
The `Email <orders.html#email>`_ menu provides an overview of the email details and all events in chronological order.

Email webhooks are not available for the :guilabel:`Email-server type` ``Host email``, ``SMTP``, ``Amazon SES API`` and ``Sparkpost``.

Use the following steps to configure email webhooks:

#. Check the ``Webhook`` checkbox in the `Email Settings <../getting-started/settings.html#email-webhooks>`_.
#. Create a new *Fast Events* user. Choose :guilabel:`Tools` → :guilabel:`Admin Accounts`. Do **not** create a WordPress user yourself.
   Use any name (eg. webhook) and a random, non‑existent email address. No further configuration of the user is required.
   Click :guilabel:`Save` and store the application password in a safe place. You’ll need it later when configuring webhooks with the email provider.
#. Log in to the mail provider used for *Fast Events*.
#. Configure the webhooks. Below, it explains for each email provider how it should be configured.

----

Warning
-------
All email providers offer the ability to send open events and click events.
Open events are sent as soon as the email is opened, and click events are sent when the user clicks a URL in the email.
If you want to receive these events, there are a couple of things to keep in mind:

#. The number of events, especially click events, can be large. After all, a user may open an email multiple times and click on a URL several times.
   Each individual event results in a REST‑API call to your WordPress system.
#. Some email clients can be configured not to send read receipts, so no open event is generated.
   For click events, browser ad‑blocker extensions can block the events.
   Therefore, there’s no guarantee that these events will be received by *Fast Events*.

Email providers
---------------

Brevo webhook settings
^^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Brevo dashboard <https://www.brevo.com/>`_.

#. Choose :guilabel:`Settings` → :guilabel:`Webhook`.
#. Create a new :guilabel:`Outbound webhook`.
#. Any name will do.
#. The endpoint is: ``https://fillinyourdomain.com/wp-json/fast-events/v1/email/webhook/smtp2go``
#. The :guilabel:`Authentication method` should be ``Basic``
#. Use the name and the application password we created earlier as the :guilabel:`Username` and :guilabel:`Password`.
#. The :guilabel:`Event category` should be ``Transactional email``
#. Choose the events you want to receive.

The following events are marked as error events:  ``soft_bounce``, ``hard_bounce``, ``spam``, ``invalid_email``,
``deferred``, ``blocked``, ``error`` and ``unsubscribed``.
They are visible in the :guilabel:`Error log` of the order menu for a specific order or in the :guilabel:`Error log` of the ``Tools`` section.

----

Mailgun webhook settings
^^^^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Mailgun dashboard <https://www.mailgun.com/>`_.

#. In the left sidebar, select :guilabel:`Send`, then choose :guilabel:`Webhooks`.
#. Click :guilabel:`Add webhook`
#. Choose the event you want
#. The URL is: ``https://user:password@fillinyourdomain.com/wp-json/fast-events/v1/email/webhook/mailgun``.
   Use the name and the application password we created earlier as the ``user`` and ``password`` in the URL.
   First remove the spaces from the application password.
#. Repeat these steps if you want to receive more than one event type.

The following events are marked as error events: ``failed``, ``complained`` and ``unsubscribed``.
They are visible in the :guilabel:`Error log` of the order menu for a specific order or in the :guilabel:`Error log` of the ``Tools`` section.

----

Mailjet webhook settings
^^^^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Mailjet dashboard <https://www.mailjet.com/>`_.

#. Navigate to :guilabel:`Settings` → :guilabel:`Event Tracking` (or :guilabel:`Account Settings` → :guilabel:`Webhooks`).
#. Click :guilabel:`Add webhook`
#. The URL is: ``https://user:password@fillinyourdomain.com/wp-json/fast-events/v1/email/webhook/mailjet``.
   Use the name and the application password we created earlier as the ``user`` and ``password`` in the URL.
   First remove the spaces from the application password.
#. Select the events you wish to receive.

.. warning::
   **Do not** use :guilabel:`Use event grouping` which is ``Version=2`` to batch multiple events in single requests.

The following events are marked as error events: ``bounce``, ``spam`` and ``blocked``.
They are visible in the :guilabel:`Error log` of the order menu for a specific order or in the :guilabel:`Error log` of the ``Tools`` section.

----

Postmark webhook settings
^^^^^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Postmark dashboard <https://postmarkapp.com/>`_.

#. Select the ``Server`` and choose :guilabel:`Default Transactional Stream` → :guilabel:`Webhooks`.
#. Click :guilabel:`Add webhook`
#. The URL is: ``https://fillinyourdomain.com/wp-json/fast-events/v1/email/webhook/postmark``.
#. Expand :guilabel:`Custom headers and basic auth`
#. Use the name and the application password we created earlier as the :guilabel:`Username` and :guilabel:`Password` as the ``Basic auth credentials``.
#. Choose the events you want to receive.

The following events are marked as error events: ``Bounce``, ``Spam complaint``, ``Subscription change`` and ``Manual suppression``.
They are visible in the :guilabel:`Error log` of the order menu for a specific order or in the :guilabel:`Error log` of the ``Tools`` section.

----

Sendgrid webhook settings
^^^^^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `Sendgrid dashboard <https://sendgrid.com/>`_.

#. In the left sidebar, select :guilabel:`Settings`, then choose :guilabel:`Mail Settings`.
#. Click :guilabel:`Event Webhooks`
#. Click :guilabel:`Create new webhook`
#. Any name will do.
#. The URL is: ``https://user:password@fillinyourdomain.com/wp-json/fast-events/v1/email/webhook/sendgrid``.
   Use the name and the application password we created earlier as the ``user`` and ``password`` in the URL.
   First remove the spaces from the application password.
#. Select the events you wish to receive.

.. warning::
   **Do not** enable :guilabel:`Enable Signed Event Webhook` or :guilabel:`Enable OAuth`.

The following events are marked as error events: ``Deferred``, ``Bounce``, ``Dropped``, ``Spam report``, ``Unsubscribe`` and ``Group unsubscribe``.
They are visible in the :guilabel:`Error log` of the order menu for a specific order or in the :guilabel:`Error log` of the ``Tools`` section.

----

SMTP2GO webhook settings
^^^^^^^^^^^^^^^^^^^^^^^^
The settings can be found in the `SMTP2GO dashboard <https://app.smtp2go.com/>`_.

#. In the left sidebar, select :guilabel:`Settings`, then choose :guilabel:`Webhooks`.
#. Click :guilabel:`Add webhook`
#. The URL is: ``https://fillinyourdomain.com/wp-json/fast-events/v1/email/webhook/smtp2go``.
#. Select ``Basic`` for :guilabel:`Authorization header`.
#. Add the Base64‑encoded string that consists of the username and application password.
   Some websites can do this encoding for you online.
   For example, `this one <https://mixedanalytics.com/tools/basic-authentication-generator/>`_.
#. Use ``All users selected`` for :guilabel:`Users` and ``JSON`` as :guilabel:`Output type`.
#. Select the events you wish to receive.
#. Add the custom headers ``X_fast_events_event_id``, ``X_fast_events_order_id`` and ``X_fast_events_name`` to :guilabel:`Email headers`.
   After typing each one, press Enter.

The following events are marked as error events: ``bounce``, ``spam``, ``unsubscribe``, ``resubscribe`` and ``reject``.
They are visible in the :guilabel:`Error log` of the order menu for a specific order or in the :guilabel:`Error log` of the ``Tools`` section.

