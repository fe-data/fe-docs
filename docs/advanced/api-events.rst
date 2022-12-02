Events
~~~~~~

List events
+++++++++++

.. http:get:: /fast-events/v1/admin/events

    Retrieve all events. You can limit the result-set by setting query-parameters.

    **Optional query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``id,stock,event_date``.
    *per_page*
        Only return this many items. The default is ``10`` and the maximum is ``100``.
    *offset*
        Offset the result set by a specific number of events.
    *page*
        The page number in the collection.
    *search*
        Search the ``event_name`` field. If the string is found in the field the event is included.
    *include*
        A comma separated string of event ids. For example ``147,153``. Only events with these ids will be included in the result.
    *exclude*
        A comma separated string of event ids. For example ``147,153``. Events with these ids will be excluded from the result.
    *orderby*
        Order the result set by ``id``, ``event_date``, ``start_date`` or ``end_date``. The default is ``id``.
    *order*
        Ascending (``asc``) is the default. You can set it to ``desc``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        [
            {
                "id": 122,
                "event_name": "Vinyl Openair 2021",
                "event_date": null,
                "event_date_format": "%Y-%m-%d %H:%M",
                "start_date": "2021-03-01 10:02:00",
                "end_date": "2021-03-01 13:02:00",
                "event_type": 1,
                "stock": 9000,
                "stock_link": 0,
                "saas_fee": 0.05,
                "saas_user_id": 2,
                "saas_user_id": 16,
                "group_type": 0,
                "event_group": "",
                "redirect": "https://vinyl-openair.com/thx-for-your-order/",
                "email": {
                    "sender_name": "",
                    "sender_email": "",
                    "bcc": "",
                    "subject": "Here are your tickets",
                    "body": "HTML truncated ..."
                },
                "email_confirmation": {
                    "bcc": "",
                    "subject": "",
                    "body": "",
                    "redirect": ""
                },
                "emails_needed": true,
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
                "webhooks_needed": false,
                "reload_on_exit_needed": false,
                "terms": "",
                "pdf_fields": {
                    "ticket": {
                        "attachment_id": 260,
                        "x_position": 13,
                        "y_position": 58,
                        "rotation": 0
                    },
                    "invoice": {
                        "attachment_id": 55,
                        "use_vat": false,
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
                "order_submit_text": "Pay",
                "user_groups": {
                    "group_type": 0
                },
                "seats": {
                    "number_of_seats": 0,
                    "seats_format": "",
                    "seats_config": "",
                    "linked_event": 0
                },
                "tracking": {
                    "start_tracking": "2021-04-30 08:00",
                    "stop_tracking": "2021-04-30 18:00",
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
                },
                "_links": {
                    "self": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/122"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events"
                        }
                    ],
                    "input_fields": [
                        {
                            "embeddable": true,
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/122/input_fields"
                        }
                    ],
                    "ticket_types": [
                        {
                            "embeddable": true,
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/122/ticket_types"
                        }
                    ],
                    "scan_keys": [
                        {
                            "embeddable": true,
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/122/scan_keys"
                        }
                    ],
                    "sales_totals": [
                        {
                            "embeddable": true,
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/122/sales"
                        }
                    ],
                    "scan_totals": [
                        {
                            "embeddable": true,
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/122/scans"
                        }
                    ],
                    "wp:attachment": [
                        {
                            "embeddable": true,
                            "href": "https://vinyl-openair.com/wp-json/wp/v2/media/260"
                        },
                        {
                            "embeddable": true,
                            "href": "https://vinyl-openair.com/wp-json/wp/v2/media/55"
                        }
                    ]
                }
            }
        ]

    The HTTP headers of the response contains additional information about the collection.

    *X-WP-Total*
        This header contains the total number of rows in the collection.
    *X-WP-TotalPages*
        This header contains the total number of pages. It depends on the query parameter ``per_page``.
    *Link*
        This header contains the links to the the previous and next page, if applicable.

    .. tip::

        You can include the ``_links`` in the same response by using the ``_embed`` query parameter.
        It is possible to limit the embeddable endpoints to a single endpoint, eg. ``_embed=sales_totals`` or multiple eg. ``_embed=sales_totals,scan_totals``.
        This will save you extra calls to the API.

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."
       "1.2", "Added '*maximum_shares*'."
       "1.4", "Added '*saas_fee*', '*saas_user_id*', '*email->sender_name*' and '*email->sender_email*'."

----

Event details
+++++++++++++

.. http:get:: /fast-events/v1/admin/events/(integer:id)

    Retrieve details of a single event.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/147

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/147';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/147'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    See example response `List Events`_.

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Event update
++++++++++++

.. http:patch:: /fast-events/v1/admin/events/(integer:id)

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PATCH \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"stock": 6000}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/147

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/147';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PATCH");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "stock" => 6000,
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/147'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'stock': 6000}
            response = requests.patch(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**

    See example response `List Events`_.

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Delete event
++++++++++++

.. http:delete:: /fast-events/v1/admin/events/(integer:id)

    Delete a single event.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/147

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/147';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "DELETE");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/147'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: text

        {
            "deleted": true,
            "previous": {
                "See example response List Events",
                ...
                ...
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Create Event
++++++++++++

.. http:post:: /fast-events/v1/admin/events

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PATCH \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"event_name":"Openair 2022","event_date":"2022-03-30 09:00:00","stock": 6000}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PATCH");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "event_name" => "Openair 2022",
                "event_date" => "2022-03-30 09:00:00",
                "stock" => 6000,
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'event_name': 'Openair 2022', 'event_date': '2022-03-30 09:00:00', 'stock': 6000}
            response = requests.patch(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**

    See example response `List Events`_.

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."
