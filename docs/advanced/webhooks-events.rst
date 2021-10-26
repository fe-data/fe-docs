Events
~~~~~~

New event
+++++++++

**Triggered by**

#. Choose for :guilabel:`New event (+)` in the icon-menu of the events-dashboard
#. Choose for :guilabel:`Duplicate event` in the context-menu of the events-dashboard.
#. REST API (`Create event <api-events.html#create-event>`_)

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
        "group_type": 0,
        "event_group": "",
        "redirect": "https://vinyl-openair.com/order-thankyou/",
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
        "unique_event_ids": "",
        "user_groups_needed": false,
        "recaptcha_needed": false,
        "confirmation_emails_needed": false,
        "confirmation_timeout": 0,
        "add_dashboard_orders_needed": true,
        "test_payments_needed": true,
        "seats_needed": false,
        "webhooks_needed": true,
        "reload_on_exit_needed": false,
        "terms": "I agree to <a href=\"\" target=\"_blank\" rel=\"noreferrer noopener\">Terms and Conditions</a>",
        "pdf_fields": {
            "ticket": {
                "attachment_id": 5,
                "x_position": 40,
                "y_position": 150,
                "rotation": 0,
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
                    "y_position": 92,
                    "line_width": 158
                }
            }
        },
        "scan_keys": [
            {
                "key": "Rg4lCMXWwpyhgbTy",
                "level": 0,
                "tickets": [],
                "location": "Main entrance",
                "date_format": "l, j F H:i:s"
            },
            {
                "key": "1DsCwYDOzWnqgU9v",
                "level": 1,
                "tickets": [
                    "Gold (Backstage)"
                ],
                "location": "Backstage entrance",
                "date_format": "l, j F H:i:s",
            }
        ],
        "order_submit_text": "Pay",
        "input_fields": [],
        "ticket_types": [
            {
                "id": "v1f567",
                "name": "Silver",
                "price": 25,
                "vat": 21,
                "stock_control": false,
                "minimum_to_order": 0,
                "maximum_to_order": 50,
                "is_counted": true,
                "attachment_id": 5
            },
            {
                "id": "v2a0df",
                "name": "Gold (Backstage)",
                "price": 40,
                "vat": 21,
                "stock_control": true,
                "stock": 100,
                "minimum_to_order": 0,
                "maximum_to_order": 50,
                "is_counted": true,
                "attachment_id": 5
            }
        ],
        "user_groups": {
            "group_type": 0
        },
         "seats": {
            "number": 0,
            "format": "",
            "config": "",
            "linked_event": 0
        },
        "tracking": {
            "start_tracking": "2021-04-08 08:00",
            "stop_tracking": "2021-05-01 18:00",
            "geofence_radius": 300,
            "distance_filter": 10,
            "no_entry_scan": false,
            "force_tracking_app": false,
            "tr_help_url": "https://vinyl-openair.com/info/",
            "tr_help_tel": "0123456789",
            "location_sharing": true,
            "maximum_shares": 1,
            "minutes_trigger": 0,
            "distance_trigger": 0
        }
    }

**Changelog**

.. csv-table::
   :header: "Version", "Description"
   :width: 100%
   :widths: auto

   "1.0", "Introduced."
   "1.2", "Added '*maximum_shares*'."

----

Update event
++++++++++++

**Triggered by**

#. Admin App
#. Choose for :guilabel:`Change event` in the contextmenu of the events-dashboard
#. REST API (`Update event <api-events.html#event-update>`_)
#. REST API (update, delete or create a `scan key <api-scankeys.html#scan-keys>`_)
#. REST API (update, delete or create an `input field <api-inputfields.html#input-fields>`_)
#. REST API (update, delete or create an `ticket types <api-tickettypes.html#input-fields>`_)

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
#. REST API (`Delete event request <api-events.html#delete-event>`_)

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