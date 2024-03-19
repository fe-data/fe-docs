Coupons
~~~~~~~
List all coupons
++++++++++++++++

.. http:get:: /fast-events/v1/admin/coupons

    List all coupons.

    **Optional query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``code,description``.
    *per_page*
        Only return this many items. The default is ``10`` and the maximum is ``100``.
    *offset*
        Offset the result set by a specific number of orders.
    *page*
        The page number in the collection.
    *search*
        Search the ``email`` field. If the string is found in the field the order is included.
    *include*
        A comma separated string of coupon ids. For example ``1472,1541``. Only coupons with these ids will be included in the result.
    *exclude*
        A comma separated string of coupon ids. For example ``1472,1541``. Coupons with these ids will be excluded from the result.
    *orderby*
        Order the result set by ``id``, ``code`` or ``email``. The default is ``id``.
    *order*
        Ascending (``asc``) is the default. You can set it to ``desc``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/coupons

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        [
            {
                "id": 1,
                "code": "MARCH24",
                "description": "Discount of 10% in march",
                "date_created": "2024-02-21 12:01:28",
                "date_modified": "2024-02-21 16:11:02",
                "type": "percent",
                "amount": 10,
                "usage_limit": 1000,
                "usage_limit_per_user": 0,
                "used": 0,
                "last_used": "",
                "start_date": "2024-03-01 00:00:00",
                "end_date": "2024-03-31 23:59:59",
                "events": "",
                "tickets": "",
                "minimum_tickets": 0,
                "maximum_tickets": 0,
                "minimum_amount": 0,
                "maximum_amount": 0,
                "email": "",
                "_links": {
                    "self": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons/1"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons"
                        }
                    ]
                }
            },
            {
                "id": 2,
                "code": "MEMBERS0024",
                "description": "One free Silver ticket for members",
                "date_created": "2024-02-01 12:01:28",
                "date_modified": "2024-02-02 16:11:02",
                "type": "fixed",
                "amount": 25,
                "usage_limit": 1,
                "usage_limit_per_user": 1,
                "used": 0,
                "last_used": "",
                "start_date": "2024-03-01 00:00:00",
                "end_date": "2024-03-31 23:59:59",
                "events": "4",
                "tickets": "Silver",
                "minimum_tickets": 1,
                "maximum_tickets": 0,
                "minimum_amount": 0,
                "maximum_amount": 0,
                "email": "johndoe@exampledomain.com",
                "_links": {
                    "self": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons/2"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons"
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

       "2.2.0", "Introduced."

----

List coupon
+++++++++++


.. http:get:: /fast-events/v1/admin/coupons/(integer:id)

    Retrieve details of a single coupon.

    **Query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example `code,description``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": 1,
            "code": "MARCH24",
            "description": "Discount of 10% in march",
            "date_created": "2024-02-21 12:01:28",
            "date_modified": "2024-02-21 16:11:02",
            "type": "percent",
            "amount": 10,
            "usage_limit": 1000,
            "usage_limit_per_user": 0,
            "used": 0,
            "last_used": "",
            "start_date": "2024-03-01 00:00:00",
            "end_date": "2024-03-31 23:59:59",
            "events": "",
            "tickets": "",
            "minimum_tickets": 0,
            "maximum_tickets": 0,
            "minimum_amount": 0,
            "maximum_amount": 0,
            "email": "",
            "_links": {
                "self": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons/1"
                    }
                ],
                "collection": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.2.0", "Introduced."

----

Update coupon
++++++++++++++

.. http:put:: /fast-events/v1/admin/coupons/(integer:id)

    Update a coupon.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PUT \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"end_date": "2024-03-21 09:00:00"}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, false);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "end_date" => "2024-03-21 09:00:00",
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'end_date': "2024-03-21 09:00:00"}
            response = requests.put(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "id": 1,
            "code": "MARCH24",
            "description": "Discount of 10% in march",
            "date_created": "2024-02-21 12:01:28",
            "date_modified": "2024-02-21 16:11:02",
            "type": "percent",
            "individual_use": false,
            "amount": 10,
            "usage_limit": 1000,
            "usage_limit_per_user": 0,
            "used": 0,
            "last_used": "",
            "start_date": "2024-03-01 00:00:00",
            "end_date": "2024-03-21 09:00:00",
            "events": "",
            "tickets": "",
            "minimum_tickets": 0,
            "maximum_tickets": 0,
            "minimum_amount": 0,
            "maximum_amount": 0,
            "email": "",
            "_links": {
                "self": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons/1"
                    }
                ],
                "collection": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.2.0", "Introduced."

----

Delete coupon
++++++++++++++

.. http:delete:: /fast-events/v1/admin/coupons/(integer:id)

    Delete a single coupon.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "deleted": true,
            "previous": {
                "id": 1,
                "code": "MARCH24",
                "description": "Discount of 10% in march",
                "date_created": "2024-02-21 12:01:28",
                "date_modified": "2024-02-21 16:11:02",
                "type": "percent",
                "individual_use": false,
                "amount": 10,
                "usage_limit": 1000,
                "usage_limit_per_user": 0,
                "used": 0,
                "last_used": "",
                "start_date": "2024-03-01 00:00:00",
                "end_date": "2024-03-21 09:00:00",
                "events": "",
                "tickets": "",
                "minimum_tickets": 0,
                "maximum_tickets": 0,
                "minimum_amount": 0,
                "maximum_amount": 0,
                "email": ""
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.2.0", "Introduced."

----

Create coupon
+++++++++++++

.. http:post:: /fast-events/v1/admin/coupons

    Create a new coupon.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"code":"MARCH24","description":"Discount of 10% in march","type":"percent","amount":10,"start_date":"2024-03-01 00:00:00","end_date":"2024-03-21 09:00:00"}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/coupons

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "code" => "MARCH24",
                "description" => "Discount of 10% in march",
                "type" => "percent",
                "amount" => 10,
                "start_date" => "2024-03-01 00:00:00",
                "end_date" => "2024-03-21 09:00:00",
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'code':'MARCH24','description':'Discount of 10% in march','type':'percent','amount':10,'start_date':'2024-03-01 00:00:00','end_date':'2024-03-21 09:00:00'}
            response = requests.post(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "id": 3,
            "code": "MARCH24",
            "description": "Discount of 10% in march",
            "date_created": "2024-02-21 12:01:28",
            "date_modified": "2024-02-21 16:11:02",
            "type": "percent",
            "individual_use": false,
            "amount": 10,
            "usage_limit": 1000,
            "usage_limit_per_user": 0,
            "used": 0,
            "last_used": "",
            "start_date": "2024-03-01 00:00:00",
            "end_date": "2024-03-21 09:00:00",
            "events": "",
            "tickets": "",
            "minimum_tickets": 0,
            "maximum_tickets": 0,
            "minimum_amount": 0,
            "maximum_amount": 0,
            "email": "",
            "_links": {
                "self": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons/3"
                    }
                ],
                "collection": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.2.0", "Introduced."

----

Reset counters
++++++++++++++

.. http:get:: /fast-events/v1/admin/coupons/(integer:id)/reset-counters

    Reset all counters.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/6'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "id": 1,
            "code": "MARCH24",
            "description": "Discount of 10% in march",
            "date_created": "2024-02-21 12:01:28",
            "date_modified": "2024-02-21 16:11:02",
            "type": "percent",
            "individual_use": false,
            "amount": 10,
            "usage_limit": 1000,
            "usage_limit_per_user": 0,
            "used": 0,
            "last_used": "",
            "start_date": "2024-03-01 00:00:00",
            "end_date": "2024-03-21 09:00:00",
            "events": "",
            "tickets": "",
            "minimum_tickets": 0,
            "maximum_tickets": 0,
            "minimum_amount": 0,
            "maximum_amount": 0,
            "email": "",
            "_links": {
                "self": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons/1"
                    }
                ],
                "collection": [
                    {
                        "href": "https://debug.fast-events.eu/wordpress/wp-json/fast-events/v1/admin/coupons"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.2.0", "Introduced."
