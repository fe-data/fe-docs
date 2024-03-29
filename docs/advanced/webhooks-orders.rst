Orders
~~~~~~

New order
+++++++++

**Triggered by**

#. Choose for the :guilabel:`New order (+)` button of the orders-dashboard
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
        "discount": 0,
        "ip_address": "1.2.3.4"
    }

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."
   "2.2.0", "Added '*discount*' field."

----

Update order
++++++++++++

**Triggered by**

#. Choose for :guilabel:`Edit customer` in the popupmenu of the orders-dashboard
#. REST API (`Update order request <api-orders.html#order-update>`_)

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

#. Choose for :guilabel:`Delete order` in the popupmenu of the orders-dashboard
#. REST API (`Delete order request <api-orders.html#delete-order>`_)

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

#. Choose for :guilabel:`Refund` in the popupmenu of the orders-dashboard

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
