Orders
~~~~~~

List orders
+++++++++++

.. http:get:: /fast-events/v1/admin/orders

    Retrieve all orders. You can limit the result-set by setting query-parameters.

    **Optional query parameters**

    *event_id*
        A comma separated string of event ids. For example ``22,45``. Only orders belonging to these events will be included.
    *_fields*
        A comma separated string of fields included in the response. For example ``id,name,email``.
    *per_page*
        Only return this many items. The default is ``10`` and the maximum is ``100``.
    *offset*
        Offset the result set by a specific number of orders.
    *page*
        The page number in the collection.
    *search*
        Search the ``email`` field. If the string is found in the field the order is included.
    *include*
        A comma separated string of order ids. For example ``14732,15341``. Only orders with these ids will be included in the result.
    *exclude*
        A comma separated string of order ids. For example ``14732,15341``. Orders with these ids will be excluded from the result.
    *orderby*
        Order the result set by ``id``, ``event_id`` or ``email``. The default is ``id``.
    *order*
        Ascending (``asc``) is the default. You can set it to ``desc``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/orders

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/orders';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/orders'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        [
            {
                "id": 14779,
                "event_id": 29,
                "event_date": "2020-12-31 09:00:00",
                "payment_id": "tr_r89Jcb5UMC",
                "payment_status": "paid",
                "custom_status": "",
                "created_at": "2020-12-22 16:21:36",
                "uid": "hdP6RYdGgWkmoYc4189Cf7qPHF3VT5OhnRDtN7OT",
                "name": "John Doe",
                "email": "John@Doe999.com",
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
                "ip_address": "84.120.12.4",
                "_links": {
                    "self": [
                        {
                            "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/orders"
                        }
                    ],
                    "tickets": [
                        {
                            "embeddable": true,
                            "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779"
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

        You can include the ticket-details and scan-details in the same response by using the ``_embed`` query parameter.
        This will save you extra calls to the API.

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Order details
+++++++++++++

.. http:get:: /fast-events/v1/admin/orders/(integer:id)

    Retrieve details of a single order.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": 14779,
            "event_id": 29,
            "event_date": "2020-12-31 09:00:00",
            "payment_id": "tr_r89Jcb5UMC",
            "payment_status": "paid",
            "custom_status": "",
            "created_at": "2020-12-22 16:21:36",
            "uid": "hdP6RYdGgWkmoYc4189Cf7qPHF3VT5OhnRDtN7OT",
            "name": "John Doe",
            "email": "John@Doe999.com",
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
            "ip_address": "84.120.12.4",
            "_links": {
                "self": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779"
                    }
                ],
                "collection": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/orders"
                    }
                ],
                "tickets": [
                    {
                        "embeddable": true,
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Order update
++++++++++++

.. http:patch:: /fast-events/v1/admin/orders/(integer:id)

    Update a single order. Only the fields ``custom_status``, ``name`` and ``email`` can be changed.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PATCH \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"name":"Harry Doe"}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PATCH");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "name" => "Harry Doe",
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'name': 'Harry Doe'}
            response = requests.patch(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "custom_status": "",
            "name": "Harry Doe",
            "email": "John@Doe999.com",
            "_links": {
                "self": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779"
                    }
                ],
                "collection": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/orders"
                    }
                ]
            }
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

.. http:delete:: /fast-events/v1/admin/orders/(integer:id)

    Delete a single order.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14779'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "deleted": true,
            "previous": {
                "custom_status": "",
                "name": "John Doe",
                "email": "John@Doe999.com"
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Create order
++++++++++++

.. http:post:: /fast-events/v1/admin/orders

    Create an order. The unique id must be used for both the additional input fields and the number of tickets per type.
    You can find these unique ids in the :doc:`input_fields <api-inputfields>` and :doc:`ticket_types <api-tickettypes>` endpoints.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"event_id":65,"name":"John Doe","email":"John999@doe999.com","fields":[],"tickets":[{"v24a1f":1}]}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/orders

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/orders';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "event_id" => 65,
                "name"     => "John Doe",
                "email"    => "John999@doe999.com",
                "fields"   => [],
                "tickets"  => [
                    [
                        "v24a1f" => 1
                    ]
                ]
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/orders'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {
                'event_id': 65,
                'name': 'John Doe',
                'email': 'John999@doe999.com',
                'fields': [],
                'tickets': [
                    {'v24a1f': 1}
                ]
            }
            response = requests.post(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": 14824,
            "event_id": 65,
            "event_date": "2021-01-31 09:00:00",
            "payment_id": "",
            "payment_status": "dashboard",
            "custom_status": "",
            "created_at": "2021-01-05 09:24:35",
            "uid": "mhQhzs4HV1u3GcJUIhmccHvJQtldxWkRBmqpU3Hv",
            "name": "John Doe",
            "email": "John999@doe999.com",
            "input_fields": {
                "fields": [],
                "tickets": [
                    {
                        "name": "Silver",
                        "price": 40.25,
                        "vat": 0,
                        "is_counted": true,
                        "number": 1
                    }
                ]
            },
            "num_tickets": 1,
            "total": 40.25,
            "ip_address": "3.14.17.20",
            "_links": {
                "self": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/orders/14824"
                    }
                ],
                "collection": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/orders"
                    }
                ],
                "tickets": [
                    {
                        "embeddable": true,
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14824"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."
