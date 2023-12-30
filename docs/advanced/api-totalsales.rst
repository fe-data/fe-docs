Total sales
~~~~~~~~~~~

Total sales
+++++++++++

.. http:get:: /fast-events/v1/admin/events/(integer:id)/sales

    Retrieve the total tickets sold on event level per payment-status and ticket-type.

    **Optional query parameters**:

    *_fields*
        A comma separated string of fields included in the response. For example ``id,orders``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/29/sales

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/29/sales';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/29/sales'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": 29,
            "orders": [
                {
                    "payment_status": "paid",
                    "total_orders": 3,
                    "total_amount": 120,
                    "total_tickets": 5,
                    "tickets": [
                        {
                            "ticket_type": "Silver",
                            "sold": 4,
                            "orders": 2,
                            "amount": 60
                        },
                        {
                            "ticket_type": "Gold (Backstage)",
                            "sold": 1,
                            "orders": 1,
                            "amount": 60
                        },
                    ]
                },
                {
                    "payment_status": "dashboard",
                    "total_orders": 1,
                    "total_amount": 20,
                    "total_tickets": 1,
                    "tickets": [
                        {
                            "ticket_type": "Silver",
                            "sold": 1,
                            "orders": 1,
                            "amount": 20
                        },
                        {
                            "ticket_type": "Gold (Backstage)",
                            "sold": 0,
                            "orders": 0,
                            "amount": 0
                        },
                    ]
                },
            ],
            "_links": {
                "self": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/events/29/sales"
                    }
                ]
            }
        }

    .. note::

        The ``sold`` field can contain a higher value than the sum of active tickets. This can happen if you have another event
        and you have linked stock control to this event. Eg. any tickets sold with the other event are counted in this event as well.

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Total sales in event group
++++++++++++++++++++++++++

.. http:get:: /fast-events/v1/admin/events/(integer:id)/sales

    Retrieve the total tickets sold on event level per payment-status and ticket-type of all events in the same group.

    **Optional query parameters**:

    *_fields*
        A comma separated string of fields included in the response. For example ``event_group,orders``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/29/sales/group

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/29/sales/group';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/29/sales/group'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "event_group": "Openair",
            "orders": [
                {
                    "payment_status": "paid",
                    "total_orders": 3,
                    "total_amount": 120,
                    "total_tickets": 5,
                    "tickets": [
                        {
                            "ticket_type": "Silver",
                            "sold": 4,
                            "orders": 2,
                            "amount": 60
                        },
                        {
                            "ticket_type": "Gold (Backstage)",
                            "sold": 1,
                            "orders": 1,
                            "amount": 60
                        },
                    ]
                },
                {
                    "payment_status": "dashboard",
                    "total_orders": 1,
                    "total_amount": 20,
                    "total_tickets": 1,
                    "tickets": [
                        {
                            "ticket_type": "Silver",
                            "sold": 1,
                            "orders": 1,
                            "amount": 20
                        },
                        {
                            "ticket_type": "Gold (Backstage)",
                            "sold": 0,
                            "orders": 0,
                            "amount": 0
                        },
                    ]
                },
            ],
            "_links": {
                "self": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/events/29/sales/group"
                    }
                ]
            }
        }

    .. note::

        The ``sold`` field can contain a higher value than the sum of active tickets. This can happen if you have another event
        and you have linked stock control to this event. Eg. any tickets sold with the other event are counted in this event as well.

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."
