Downloads
~~~~~~~~~
Tickets download
++++++++++++++++

**Triggered by**

#. Link in user email for downloading tickets
#. Choose for :guilabel:`Share -> PDF with tickets` in the popupmenu of the orders-dashboard

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
        "num_tickets": 4,
        "total": 130,
        "qrcodes": [
            "FBlnicFSAODgfUfi",
            "ZoyKSTQGXRfMvlZ4",
            "JO4KuKyUp1FUcmUD",
            "cTf7j9jA1vqdtBJ6"
        ],
        "ip_address": "1.2.3.4"
    }

.. warning::

   If the :guilabel:`Tickets` flag is not set in the `Basics tab <../usage/events.html#basics-tab>`_, this webhook can't be used.

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."

----

Invoice download
++++++++++++++++

**Triggered by**

#. Link in user email for downloading invoice
#. Choose for :guilabel:`Share -> PDF invoice` in the popupmenu of the orders-dashboard

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
        "num_tickets": 4,
        "total": 130,
        "ip_address": "1.2.3.4"
    }

.. warning::

   If the :guilabel:`Invoice` flag is not set in the `Basics tab <../usage/events.html#basics-tab>`_, this webhook can't be used.

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."
