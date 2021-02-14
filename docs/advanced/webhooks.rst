Webhooks
========
Webhooks are used for sending data to a URL when an event happens in *Fast Events*. An example event is when a new order is added, updated, deleted, ...

.. contents:: Table of contents
   :local:
   :backlinks: none
   :depth: 3

----


How does it work?
-----------------
Action scheduler
~~~~~~~~~~~~~~~~
*Fast Events* uses the `Action scheduler <https://actionscheduler.org>`_, which is widely used by other WordPress plugins including `Woocommerce <https://woocommerce.com#>`_.
*Fast Events* uses it for Webhooks, email retries and RSVP events if confirmation emails are configured and if the customer doesn't respond in time, the Action scheduler will remove the order.

The *Action scheduler* will run every minute and is triggered by the WordPress `WP-Cron <http://codex.wordpress.org/Function_Reference/wp_cron>`_ system.
So you need to make sure WP-Cron is enabled in your WordPress installation, but this is always the case if you have a standard installation.

You can inspect the job queue in the WordPress :guilabel:`Tools` menu under :guilabel:`Scheduled actions`. There is no need to cleanup ``Completed`` jobs manually as the system removes them automatically after 30 days.
This value can be changed in the `Action scheduler settings <../getting-started/settings.html#action-scheduler>`_.

Requirements for consumers
~~~~~~~~~~~~~~~~~~~~~~~~~~
#. Only ``https`` is supported.
#. *Fast Event* always uses the ``POST`` method.
#. The body payload is always a JSON encoded string.
#. Consumers must be able to process multiple requests simultaneously.
#. Consumers must respond to a :guilabel:`Ping URL` (See contextmenu) with a HTTP 200. This request has an empty body!
#. Consumers must return a HTTP 200 as soon as possible, and not first do all kind of internal operations (database, ...).
   Make sure the response time is a fraction of a second and not close to a second or even higher. Test it with :guilabel:`Ping URL` in the contextmenu.
   The ``Duration`` is part of the output.
#. Consumers must also respond with a HTTP 200 if the signature is invalid and not respond with something like *Invalid signature*.
   This prevents information from being revealed to pranksters if they happen to know your URL.

HTTP request
~~~~~~~~~~~~
Every HTTP POST has a number of unique HTTP headers:

**User-Agent**
   It will show the version-number of the *Fast Events* plugin and WordPress.
   Example: ``Fast-Events/1.0 (WordPress/5.6.1)``
**X-FE-Webhook-ID**
   The id of the webhook. You can find the id in the `Webhooks overview`_.
**X-FE-Webhook-Source**
   The location where your WordPress installation lives. Example ``https://vinyl-openair.com/``.
**X-FE-Webhook-Topic**
   The topic that triggered the webhook. See `Webhooks overview`_.
**X-FE-Webhook-Resource**
   The resource can be: ``event``, ``order`` order ``scan``
**X-FE-Webhook-Event**
   See `Webhooks overview`_ and look for the second part in the ``Topic``.
**X-FE-Webhook-Delivery-ID**
   A unique id for every request. Used for debugging purposes to lookup the right request.
**X-FE-Webhook-Signature**
   A unique signature based on the Webhook secret and the body content. Before you start processing the request always first check if the signature does match.
   Here are some examples how you can very the signature.
   Use the raw input from the body and do *not* include any possible newlines at the end.

   .. tabs::

    .. code-tab:: javascript

        // NodeJS example

        const crypto = require('crypto');
        const secret = 'yoursharedsecret';
        const payload = 'The JSON payload';
        let signature = crypto.createHmac("sha256", secret).update(payload).digest().toString('base64');

    .. code-tab:: php

        <?php
        $secret = 'yoursharedsecret';
        $payload = 'The JSON payload';

        $signature = base64_encode( hash_hmac( 'sha256', $payload, $secret, true ) );
        echo $signature;

    .. code-tab:: python

        import hashlib
        import hmac
        import base64

        secret = bytes('yoursharedsecret', 'utf-8')
        payload = bytes('Your JSON payload', 'utf-8')

        signature = base64.b64encode(hmac.new(secret, payload, digestmod=hashlib.sha256).digest())
        print(signature)

Before activating a webhook, always check that all conditions (see `Requirements for consumers`_) are met and that the duration (see :guilabel:`Ping URL` contextmenu in `Webhooks overview`_) is a fraction of a second.

----


Maintaining webhooks
--------------------
Webhooks overview
~~~~~~~~~~~~~~~~~
.. list-table::

    * - .. image:: ../_static/images/advanced/Webhooks-overview.png
           :target: ../_static/images/advanced/Webhooks-overview.png
           :alt: Overview webhooks

The top-left button bar has the following functionality:

- Hide/show columns in the table view.
- Add a new webhook. Most of the time it’s more convenient to use the ``Duplicate webhook`` in the context menu, rather than starting with an empty webhook.

There is a context-menu if you scroll through the webhooks; **use the right mouse-button** to make it visible and the chosen action is applied on the webhook where you did the right click.

**Edit webhook**
   In a popup window you can edit the webhook. It’s also possible to double-click on the webhook to edit it.
**Delete webhook**
   Deletion of the webhook. Keep in mind if you delete a webhook, any remaining ``pending`` actions will be ignored. The system will flag this in the logfile if there where still ``pending`` actions..
**Duplicate webhook**
   Duplicate an existing webhook. The new webhook is *disabled* by default.
**Counters overview**
   A detailed overview of some counters and dates.

   .. list-table::

       * - .. image:: ../_static/images/advanced/Webhooks-counters.png
              :target: ../_static/images/advanced/Webhooks-counters.png
              :alt: Overview webhook counters

**Reset counter**
   All counters and dates are reset to zero.
**Ping URL**
   A handy utility to check the connection to a webhook consumer. It will show all debugging output in a popup window.

   .. list-table::

       * - .. image:: ../_static/images/advanced/Webhooks-ping.png
              :target: ../_static/images/advanced/Webhooks-ping.png
              :alt: Debugging info

----

Add/update webhooks
~~~~~~~~~~~~~~~~~~~
.. list-table::

    * - .. image:: ../_static/images/advanced/Webhooks-add.png
           :target: ../_static/images/advanced/Webhooks-add.png
           :alt: Add/update webhooks

**Webhook name**
   The name of the webhook.
**URL**
   A valid URL provided by the webhook consumer. Mind you only ``https`` is supported.
**Topic**
   Which event is the consumer interested in. At the moment the following events are available:

   #. New event
   #. Update event
   #. Delete event
   #. New order
   #. Order update
   #. Delete order
   #. Refund order
   #. New scan
**Enabled**
   Check this box if the consumer is actively listening for new requests. The system will check if the URL is live.
   It does a ``ping request`` and if no HTTP 200 is received, it will not activate the URL.
**Logging**
   Retries and failures will always be logged, but if you check this checkbox, all messages will be logged.
**Secret**
   The shared secret to create a signature of the body content.
**Retry scheme**
   A comma separated string of integers. For instance ``1,2,4``. Which means that if the webhook could not be executed successfully (*no HTTP 200 returned*) it will retry after 1 minute,
   if it fails again it will retry in 2 minutes, and so on. Every retry is counted and if the final retry fails it is counted as a failure and the request is logged and not retried again.
**Failure threshold**
   After this number of failures the webhook is disabled and no new request will be accepted.

----

Topics
------
This section shows all the topics that are currently available as webhook.

----

Events
~~~~~~
New event
+++++++++

**Triggered by**

#. Choose for :guilabel:`New event (+)` in the icon-menu of the events-dashboard
#. Choose for :guilabel:`Duplicate event` in the context-menu of the events-dashboard.

**Example payload**

.. sourcecode:: json

    {
        "id": 2,
        "event_name": "Vinyl Open Air 2021",
        "event_date": "2021-02-28 14:00:00",
        "event_date_format": "Y-m-d H:i",
        "start_date": "2021-02-01 00:00:00",
        "end_date": "2021-02-28 14:00:00",
        "event_type": 1,
        "stock": 10000,
        "stock_link": 0,
        "sold": 4,
        "group_type": 0,
        "event_group": "",
        "redirect": "http://192.168.2.18/order-thankyou/",
        "email": {
            "bcc": "",
            "subject": "Your Vinyl Open Air 2021 tickets",
            "body": "HTML truncated ..."
        },
        "email_confirmation": {
            "bcc": "",
            "subject": "",
            "body": "",
            "redirect": ""
        },
        "emails_needed": false,
        "tickets_needed": true,
        "invoice_needed": true,
        "unique_users_needed": false,
        "unique_event_ids": [
            2
        ],
        "user_groups_needed": false,
        "recaptcha_needed": false,
        "confirmation_emails_needed": false,
        "confirmation_timeout": 0,
        "add_dashboard_orders_needed": true,
        "test_payments_needed": true,
        "seats_needed": false,
        "webhooks_needed": true,
        "terms": "I agree to <a href=\"\" target=\"_blank\" rel=\"noreferrer noopener\">Terms and Conditions</a>",
        "pdf_fields": {
            "ticket": {
                "attachment_id": 5,
                "x_position": 40,
                "y_position": 150,
                "rotation": 0,
                "template_per_type": false,
                "ticket_types ": [
                    {
                        "ticket_type": "Silver",
                        "attachment_id": 5
                    },
                    {
                        "ticket_type": "Gold (Backstage)",
                        "attachment_id": 5
                    }
                ]
            },
            "invoice": {
                "attachment_id": 6,
                "use_vat": true,
                "name_position": {
                    "x_position": 27,
                    "y_position": 64
                },
                "invoice_number_position": {
                    "x_position": 127,
                    "y_position": 64
                },
                "first_line_position": {
                    "x_position": 25,
                    "y_position": 92
                }
            }
        },
        "scan_date_format": "l, j F H:i:s",
        "scan_keys": [
            {
                "scan_key": "Rg4lCMXWwpyhgbTy",
                "scan_level": 0,
                "scan_location": "Main entrance",
                "scan_tickets": []
            },
            {
                "scan_key": "1DsCwYDOzWnqgU9v",
                "scan_level": 1,
                "scan_location": "Backstage entrance",
                "scan_tickets": [
                    "Gold (Backstage)"
                ]
            }
        ],
        "order_submit_text": "Pay",
        "extra_input_fields": [],
        "ticket_fields": [
            {
                "stock_control": false,
                "name": "Silver",
                "price": 25,
                "vat": 21,
                "minimum_to_order": 0,
                "maximum_to_order": 50,
                "is_counted": true
            },
            {
                "stock_control": true,
                "stock": 100,
                "name": "Gold (Backstage)",
                "price": 40,
                "vat": 21,
                "minimum_to_order": 0,
                "maximum_to_order": 50,
                "is_counted": true
            }
        ],
        "user_group_info": {
            "group_type": 0
        }
    }

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."

----

Update event
++++++++++++

**Triggered by**

#. Admin App
#. Choose for :guilabel:`Change event` in the contextmenu of the events-dashboard

**Example payload**
   See `New event`_.


**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."

----

Delete event
++++++++++++

**Triggered by**

#. Choose for :guilabel:`Delete event` in the contextmenu of the event-dashboard

**Example payload**

.. sourcecode:: json

    {
        "id": 2
    }

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."

----

Orders
~~~~~~
New order
+++++++++

**Triggered by**

#. Admin App (New order)
#. Choose for :guilabel:`New order (+)` in the icon-menu of the orders-dashboard
#. Orders placed via order-pages. The webhook is not executed until the order has been paid.

**Example payload**

.. sourcecode:: json

    {
        "id": 14810,
        "event_id": 44,
        "event_date": "2021-01-28 09:00:00",
        "payment_id": "tr_s86ed95uHD",
        "payment_status": "paid",
        "custom_status": "",
        "created_at": "2021-01-09 15:21:24",
        "uid": "ha9hrHI7jPzb1Q01sjW68KbWsA2we9E1PxDwvWgJ",
        "name": "John Doe",
        "email": "john.doe@exampledomain.com",
        "input_fields": {
            "fields": [],
            "tickets": [
                {
                    "name": "Gold (Backstage)",
                    "price": 40,
                    "vat": 21,
                    "is_counted": true,
                    "number": 2
                }
            ]
        },
        "num_tickets": 2,
        "total": 80,
        "ip_address": "1.2.3.4"
    }

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."

----

Update order
++++++++++++

**Triggered by**

#. Admin App (Change credentials)
#. REST API (`Update order request <api.html#order-update>`_)
#. Choose for :guilabel:`Change credentials` in the contextmenu of the orders-dashboard
#. Choose for :guilabel:`Custom order status` in the contextmenu of the orders-dashboard

**Example payload**

.. sourcecode:: json

    {
        "id": 14782,
        "custom_status": "processing",
        "name": "John Doe",
        "email": "john.doe@exampledomain.com"
    }

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."

----

Delete order
++++++++++++

**Triggered by**

#. Admin App
#. REST API (`Delete order request <api.html#delete-order>`_)
#. Choose for :guilabel:`Delete order` in the contextmenu of the orders-dashboard

**Example payload**

.. sourcecode:: json

    {
        "id": 14810
    }

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."

----

Refund order
++++++++++++

**Triggered by**

#. Admin App
#. Choose for :guilabel:`Refund` in the contextmenu of the orders-dashboard

**Example payload**

.. sourcecode:: json

    {
        "ids": [
            14783
        ],
        "refunds": [
            {
                "refund_amount": 14.25,
                "refund_date": "2021-01-09 14:59:54"
            }
        ]
    }

.. note::

   The payload can contain multiple order ids. This will happen if the order is part of a multi-select group, e.g. multiple events grouped together.

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."

----

Scans
~~~~~
New scan
++++++++

**Triggered by**

#. Scan App
#. REST API (`Scan request <api.html#post--fast-events-v1-scans>`_)
#. Choose for :guilabel:`Checkin` in the contextmenu of the orders-dashboard

**Example payload**

.. sourcecode:: json

    {
        "event_id": 94,
        "order_id": 14810,
        "name": "John Doe",
        "email": "john.doe@exampledomain.com",
        "qrcode": "aImTVXZx1u8Wb9S8",
        "ticket_type": "Gold (Backstage)",
        "scan_level": 0,
        "scan_date": "2021-01-09 15:29:40",
        "scan_location": "Main entrance"
    }

.. note::

   Seating information is appended to the ``ticket_type`` if the events uses a seating plan.

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."

