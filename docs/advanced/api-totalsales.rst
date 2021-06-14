Total sales
~~~~~~~~~~~

Total sales
+++++++++++

.. http:get:: /fast-events/v1/admin/events/(integer:id)/sales

    Retrieve the total tickets sold on event level per payment-status and ticket-type.

    **Optional query parameters**:

    *_fields*
        A comma separated string of fields included in the response. For example ``id,sold,orders``.

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
            "event_name": "Vinyl Open Air 2020",
            "stock": 15000,
            "sold": 6,
            "stock_link": 0,
            "orders": [
                {
                    "payment_status": "paid",
                    "total_orders": 3,
                    "total_amount": 120,
                    "total_tickets": 5,
                    "tickets": [
                        {
                            "ticket_type": "Silver",
                            "stock_control": false,
                            "sold": 4
                        },
                        {
                            "ticket_type": "Gold (Backstage)",
                            "stock_control": true,
                            "stock": 500,
                            "sold": 1
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
                            "stock_control": false,
                            "sold": 1
                        },
                        {
                            "ticket_type": "Gold (Backstage)",
                            "stock_control": true,
                            "stock": 500,
                            "sold": 0
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
