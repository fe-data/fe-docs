Tracking
~~~~~~~~
Ticket download
+++++++++++++++

**Triggered by**

#. Deeplink in user email for downloading a ticket into the FE Tracking App
#. Deeplink in the ``Thank you page`` for downloading a ticket into the FE Tracking App

**Example payload**

.. sourcecode:: json

    {
        "order_id": 1,
        "event_id": 2,
        "event_date": "2021-01-18 14:00:00",
        "payment_id": "",
        "payment_status": "dashboard",
        "custom_status": "",
        "created_at": "2021-01-04 15:48:01",
        "downloaded_at": "2021-01-06 10:46:43",
        "uid": "1ooxa53368kx1vp5h4o8ZXXy2UzQo9h1XAXGu8oE",
        "name": "John Doe",
        "email": "JohnDoe@JohnDoe12.com",
        "qrcode": "FBlnicFSAODgfUfi",
        "ticket_type": "Silver",
        "ip_address": "1.2.3.4"
    }

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."
