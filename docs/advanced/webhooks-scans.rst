Scans
~~~~~
New scan
++++++++

**Triggered by**

#. Scan App
#. REST API (`Scan request <api-scans.html#new-scan>`_)
#. Choose for :guilabel:`Tickets -> Checkin` in the popupmenu of the orders-dashboard

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
