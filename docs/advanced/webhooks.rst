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

The *Action scheduler* will run every minute and is triggered by the WordPress `WP-Cron <https://codex.wordpress.org/Function_Reference/wp_cron>`_ system.
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
   Example: ``Fast-Events/1.0 (WordPress/5.7.2)``
**X-FE-Webhook-ID**
   The id of the webhook. You can find the id in the `Webhooks overview`_.
**X-FE-Webhook-Source**
   The location where your WordPress installation lives. Example ``https://vinyl-openair.com/``.
**X-FE-Webhook-Topic**
   The topic that triggered the webhook. See `Webhooks overview`_.
**X-FE-Webhook-Resource**
   The resource can be: ``event``, ``order``, ``scan`` order ``download``
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
   #. Tickets downloaded
   #. Invoice downloaded
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
* :doc:`Events <webhooks-events>`
* :doc:`Orders <webhooks-orders>`
* :doc:`Scans <webhooks-scans>`
* :doc:`Downloads <webhooks-downloads>`

.. toctree::
   :maxdepth: 1
   :hidden:

   webhooks-events
   webhooks-orders
   webhooks-scans
   webhooks-downloads
