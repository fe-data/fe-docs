Error logs
~~~~~~~~~~

List all errors
+++++++++++++++

.. http:get:: /fast-events/v1/admin/logs

    List all errors.

    **Optional query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``id,event_id``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/logs

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/logs';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/logs'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        [
            {
                "id": 141,
                "event_id": 2,
                "order_id": 1,
                "created_at": "2023-09-21 13:35:34",
                "log_type": "REST API",
                "description": "Mollie API: [2023-09-21T11:35:34+0000] Invalid payment ID: ''. A payment ID should start with 'tr_'.",
                "_links": {
                    "self": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/logs/141"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/logs"
                        }
                    ]
                }
            },
            {
                "id": 140,
                "event_id": 2,
                "order_id": 32,
                "created_at": "2023-09-21 11:40:00",
                "log_type": "REST API",
                "description": "Mollie API: [2023-09-21T09:40:00+0000] Invalid API key: ''. An API key must start with 'test_' or 'live_' and must be at least 30 characters long.",
                "_links": {
                    "self": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/logs/140"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/logs"
                        }
                    ]
                }
            }
        ]

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

List all errors of a single order
+++++++++++++++++++++++++++++++++

.. http:get:: /fast-events/v1/admin/logs/order/(integer:id)

    List all errors of a single order.

    **Optional query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``id,event_id``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/logs/order/32

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/logs/order/32';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/logs/order/32'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        [
            {
                "id": 141,
                "event_id": 2,
                "order_id": 32,
                "created_at": "2023-09-21 13:35:34",
                "log_type": "REST API",
                "description": "Mollie API: [2023-09-21T11:35:34+0000] Invalid payment ID: ''. A payment ID should start with 'tr_'.",
                "_links": {
                    "self": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/logs/141"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/logs/order/32"
                        }
                    ]
                }
            },
            {
                "id": 140,
                "event_id": 2,
                "order_id": 32,
                "created_at": "2023-09-21 11:40:00",
                "log_type": "REST API",
                "description": "Mollie API: [2023-09-21T09:40:00+0000] Invalid API key: ''. An API key must start with 'test_' or 'live_' and must be at least 30 characters long.",
                "_links": {
                    "self": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/logs/140"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/logs/order/32"
                        }
                    ]
                }
            }
        ]

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

Delete log entry
++++++++++++++++

.. http:delete:: /fast-events/v1/admin/logs/(integer:id)

    Delete a single log entry.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/logs/144

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/logs/144';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/logs/144'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "deleted": true,
            "previous": {
                "id": 138,
                "event_id": 2,
                "order_id": 32,
                "created_at": "2023-09-21 11:32:53",
                "log_type": "REST API",
                "description": "Mollie API: [2023-09-21T09:32:53+0000] Invalid API key: ''. An API key must start with 'test_' or 'live_' and must be at least 30 characters long."
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."
