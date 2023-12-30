Webhooks
~~~~~~~~
List all webhooks
+++++++++++++++++

.. http:get:: /fast-events/v1/admin/webhooks

    List all webhooks.

    **Optional query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``name,topic``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        [
            {
                "id": 6,
                "name": "Demo webhook 1",
                "url": "https://detsws7x2mntaaq.m.pipedream.net",
                "secret": "asasasasas",
                "topic": "tickets.downloaded",
                "enabled": true,
                "retry_scheme": "1,1,2,4,8",
                "failure_threshold": 60,
                "pending": 0,
                "delivered": 1,
                "retries": 0,
                "failed": 0,
                "last_success": "2023-10-04 15:18:47",
                "last_retry": "0000-00-00 00:00:00",
                "last_failure": "0000-00-00 00:00:00",
                "date_created": "2023-10-04 11:51:35",
                "_links": {
                    "self": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks/6"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks"
                        }
                    ]
                }
            },
            {
                "id": 8,
                "name": "Demo webhook 2",
                "url": "https://eoqdlr0x2mnsdtq.m.pipedream.net",
                "secret": "Secret23",
                "topic": "event.created",
                "enabled": false,
                "retry_scheme": "1,1,2,4,8",
                "failure_threshold": 0,
                "pending": 0,
                "delivered": 0,
                "retries": 0,
                "failed": 0,
                "last_success": "0000-00-00 00:00:00",
                "last_retry": "0000-00-00 00:00:00",
                "last_failure": "0000-00-00 00:00:00",
                "date_created": "2023-10-04 11:51:35",
                "_links": {
                    "self": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks/8"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks"
                        }
                    ]
                }
            },
        ]

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

List webhook
++++++++++++


.. http:get:: /fast-events/v1/admin/webhooks/(integer:id)

    Retrieve details of a single webhook.

    **Query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``name,topic``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": 6,
            "name": "Demo webhook 1",
            "url": "https://detsws7x2mntaaq.m.pipedream.net",
            "secret": "asasasasas",
            "topic": "tickets.downloaded",
            "enabled": true,
            "retry_scheme": "1,1,2,4,8",
            "failure_threshold": 60,
            "pending": 0,
            "delivered": 1,
            "retries": 0,
            "failed": 0,
            "last_success": "2023-10-04 15:18:47",
            "last_retry": "0000-00-00 00:00:00",
            "last_failure": "0000-00-00 00:00:00",
            "date_created": "2023-10-04 11:51:35",
            "_links": {
                "self": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks/6"
                    }
                ],
                "collection": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

Update webhook
++++++++++++++

.. http:put:: /fast-events/v1/admin/webhooks/(integer:id)

    Update a webhook.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PUT \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"enabled": false}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, false);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "enabled" => false,
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'enabled': true}
            response = requests.put(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "id": 6,
            "name": "Demo webhook 1",
            "url": "https://detsws7x2mntaaq.m.pipedream.net",
            "secret": "asasasasas",
            "topic": "tickets.downloaded",
            "enabled": false,
            "retry_scheme": "1,1,2,4,8",
            "failure_threshold": 60,
            "pending": 0,
            "delivered": 1,
            "retries": 0,
            "failed": 0,
            "last_success": "2023-10-04 15:18:47",
            "last_retry": "0000-00-00 00:00:00",
            "last_failure": "0000-00-00 00:00:00",
            "date_created": "2023-10-04 11:51:35",
            "_links": {
                "self": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks/6"
                    }
                ],
                "collection": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

Delete webhook
++++++++++++++

.. http:delete:: /fast-events/v1/admin/webhooks/(integer:id)

    Delete a single input field.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "deleted": true,
            "previous": {
                "id": 6,
                "name": "Demo webhook 1",
                "url": "https://detsws7x2mntaaq.m.pipedream.net",
                "secret": "asasasasas",
                "topic": "tickets.downloaded",
                "enabled": false,
                "retry_scheme": "1,1,2,4,8",
                "failure_threshold": 60,
                "pending": 0,
                "delivered": 1,
                "retries": 0,
                "failed": 0,
                "last_success": "2023-10-04 15:18:47",
                "last_retry": "0000-00-00 00:00:00",
                "last_failure": "0000-00-00 00:00:00",
                "date_created": "2023-10-04 11:51:35"
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

Create webhook
++++++++++++++

.. http:post:: /fast-events/v1/admin/webhooks

    Create a new webhook.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"name":"Webhook 10","url":"https://detsws7x2mntaaq.m.pipedream.net","secret":"xx","topic":"tickets.downloaded"}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "name" => "Webhook 10",
                "url" => "https://detsws7x2mntaaq.m.pipedream.net",
                "secret" => "xx",
                "topic" => "tickets.downloaded",
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'name':'Webhook 10','url':'https://detsws7x2mntaaq.m.pipedream.net','secret':'xx','topic':'tickets.downloaded'}
            response = requests.post(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "id": 7,
            "name": "Webhook 1",
            "url": "https://detsws7x2mntaaq.m.pipedream.net",
            "secret": "xx",
            "topic": "tickets.downloaded",
            "enabled": false,
            "retry_scheme": "1,1,2,4,8",
            "failure_threshold": 60,
            "pending": 0,
            "delivered": 0,
            "retries": 0,
            "failed": 0,
            "last_success": "0000-00-00 00:00:00",
            "last_retry": "0000-00-00 00:00:00",
            "last_failure": "0000-00-00 00:00:00",
            "date_created": "2023-10-04 11:51:35",
            "_links": {
                "self": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks/7"
                    }
                ],
                "collection": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

Reset counters
++++++++++++++

.. http:get:: /fast-events/v1/admin/webhooks/(integer:id)/reset-counters

    Reset all counters and dates to zero.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "id": 6,
            "name": "Demo webhook 1",
            "url": "https://detsws7x2mntaaq.m.pipedream.net",
            "secret": "asasasasas",
            "topic": "tickets.downloaded",
            "enabled": false,
            "retry_scheme": "1,1,2,4,8",
            "failure_threshold": 60,
            "pending": 0,
            "delivered": 0,
            "retries": 0,
            "failed": 0,
            "last_success": "0000-00-00 00:00:00",
            "last_retry": "0000-00-00 00:00:00",
            "last_failure": "0000-00-00 00:00:00",
            "date_created": "2023-10-04 11:51:35",
            "_links": {
                "self": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks/6"
                    }
                ],
                "collection": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/webhooks"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

Test a webhook
++++++++++++++

.. http:get:: /fast-events/v1/admin/webhooks/(integer:id)/ping

    Test a webhook by sending an empty request to the consumer.
    The full request and response in JSON format is returned for analysis.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6/ping

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6/ping';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/webhooks/6/ping'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "Webhook Delivery": {
                "Delivery ID": "4f3df8fce1018627192bc85df8962b5e",
                "Date": "2023-10-06 11:48:58 GMT",
                "URL": "https://detsws7x2mntaaq.m.pipedream.net",
                "Duration": "1.10836 seconds",
                "Request": {
                    "Method": "POST",
                    "Headers": {
                        "User-Agent": "Fast-Events/2.0.0 (WordPress/6.3.1)",
                        "Content-Type": "application/json",
                        "X-FE-Webhook-Source": "https://exampledomain.com/wordpress/",
                        "X-FE-Webhook-Topic": "tickets.downloaded",
                        "X-FE-Webhook-Resource": "tickets",
                        "X-FE-Webhook-Event": "downloaded",
                        "X-FE-Webhook-ID": "6",
                        "X-FE-Webhook-Delivery-ID": "4f3df8fce1018627192bc85df8962b5e",
                        "X-FE-Webhook-Signature": "ilKgiWuuu0YM/W+GmUyzsMahSp46Np07K7+Agsv/RMQ="
                    },
                    "Body": ""
                },
                "Response": {
                    "Code": 200,
                    "Message": "OK",
                    "Headers": {
                        "date": "Fri, 06 Oct 2023 11:48:58 GMT",
                        "content-type": "application/json; charset=utf-8",
                        "content-length": "408",
                        "x-powered-by": "Express",
                        "access-control-allow-origin": "*"
                    },
                    "Body": {
                        "about": "Pipedream is the fastest way to connects APIs. Build and run workflows with code-level control when you need it — and no code when you don't.",
                        "event_id": "2WO9p4Q0F2dYBrKKyZ3QjKuJAzC",
                        "workflow_id": "p_PAgGDeG",
                        "owner_id": "o_wpIViqe",
                        "deployment_id": "d_WpsgArBNm",
                        "timestamp": "2023-10-06T11:48:58.344Z",
                        "inspect": "https://pipedream.com/@/p_PACGDeG",
                        "quickstart": "https://pipedream.com/quickstart/"
                    }
                }
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."