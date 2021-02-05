Public API
==========
The *Fast Events* public API uses :abbr:`REST (Representational State Transfer)` and
JSON is returned by all API responses including errors
and HTTP response status codes are to designate success and failure.

.. contents:: Table of contents
   :local:
   :backlinks: none
   :depth: 3


API v1
--------------------------------
Requests to the *Fast Events* public API is for private information and all endpoints require authentication.


Resources
---------
This section shows all the resources that are currently available in APIv1.
All endpoints require an API key in a HTTP header and most use WordPress application passwords in the ``Authorization`` HTTP header.
By using application passwords (as of WordPress 5.6) you have a great deal of flexibility.
You can either create 1 WordPress user and use a single application password for all clients or an application password per client. But you can also create a WordPress user for each client with an application password.
In WordPress you can then easily revoke the rights per client. The API KEY can be used as a kind of kill switch. By changing this, all clients will be blocked for the specific endpoint.
For the username in the ``Authorization`` HTTP header you can use the login name or the emailaddress.

:scans:

   You need to include the ``X-FE-API-KEY`` and its value in a HTTP header. The value can be found in the `Scan  tab <../usage/events.html#scan-tab>`_.
   The :doc:`Scan app <../apps/scan>` is using these endpoints.

:payments:

   You need to include the ``X-FE-API-KEY`` and its value in a HTTP header. The value can be found in the `settings <../getting-started/settings.html#settings-for-instant-payments>`_ of the plugin.
   The endpoint also needs an application password. The :doc:`Payment app <../apps/payment>` is using these endpoints.

:admin:

   You need to include the ``X-FE-API-KEY`` and its value in a HTTP header for all ``admin`` endpoints. The value can be found in the `plugin settings <../getting-started/settings.html#rest-api-settings>`_.
   These endpoint also needs an application password.

.. tip::

   You can browse the full API by accessing every endpoint with an http ``OPTIONS`` request. Use `Postman <https://www.postman.com/downloads/>`_ to look at the individual fields of an endpoint and its format.
   Use it also for testing. For example: you WordPress hosting environment is located at ``https://exampledomain.com``, the REST URL for a new scan request will be ``https://exampledomain.com/wp-json/fast-events/v1/scans``.

----

Scans
~~~~~
New scan
++++++++

.. http:post:: /fast-events/v1/scans

    Validate a new scan request.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -d '{"id":"sXKkY8pzI8srxfiY"}' \
              https://exampledomain.com/wp-json/fast-events/v1/scans

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/scans';
            curl_setopt($ch, CURLOPT_URL, $urls);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_POST, true);
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([ "id" => "sXKkY8pzI8srxfiY" ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/scans'
            HEADERS = {'X-FE-API-KEY': '3zo58AUYP9zOE6YT'}
            JSON = {'id': 'sXKkY8pzI8srxfiY'}
            response = requests.post(URL, headers=HEADERS, json=JSON)
            print(response.json())


    **Example response**

    .. sourcecode:: json

        {
            "event": "Vintage Vinyl Open Air 2021",
            "name": "John Doe",
            "email": "john.doe@exampledomain.com",
            "level": 0,
            "type": "Gold (Backstage)",
            "status": true,
            "date": "2021-01-12 14:13:36",
            "location": "Main entrance"
        }

    The ``status`` field indicates whether the scan is correct (*true*) or not (*false*).
    If the ``status`` is *false*, the other fields indicate when the scan took place and where.
    If a seating plan is used, the seating info is appended to the ``type`` field.
    The format of the ``date`` field is set by the ``Date format`` field in the `Scan  tab <../usage/events.html#scan-tab>`_

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

List scans
++++++++++

.. http:get:: /fast-events/v1/scans/(string:id)

    Retrieve all scans of a single ticket.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              https://exampledomain.com/wp-json/fast-events/v1/scans/sXKkY8pzI8srxfiY

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/scans/sXKkY8pzI8srxfiY';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/scans/sXKkY8pzI8srxfiY'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            response = requests.get(URL, headers=HEADERS)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "event_name": "Vintage Vinyl Open Air 2021",
            "ticket_type": "Gold (Backstage)",
            "name": "John Doe",
            "email": "john.doe@exampledomain.com",
            "scans": [
                {
                    "scan_level": 0,
                    "scan_date": "2021-01-12 14:13:36",
                    "scan_location": "Main entrance"
                },
                {
                    "scan_level": 1,
                    "scan_date": "2021-01-12 14:19:21",
                    "scan_location": "Backstage entrance"
                },
                {
                    "scan_level": 9,
                    "scan_date": "2021-01-12 14:13:36",
                    "scan_location": "Exit Vinyl Open Air"
                }
            ]
        }

    If a seating plan is used, the seating info is appended to the ``ticket_type`` field.
    The format of the ``scan_date`` field is set by the ``Date format`` field in the `Scan  tab <../usage/events.html#scan-tab>`_

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Payments
~~~~~~~~
New payment
+++++++++++

.. http:post:: /fast-events/v1/payments

    Create a new payment request.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: pcXFwrEhmATzplQZ" \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"amount":20.00,"description":"1 Silver ticket","direct_type":1}' \
               https://exampledomain.com/wp-json/fast-events/v1/payments

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/payments';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_POST, true);
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: pcXFwrEhmATzplQZ')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "amount" => 20.00,
                "description" => "1 Silver ticket",
                "direct_type" => 1
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/payments'
            HEADERS = {'X-FE-API-KEY':'pcXFwrEhmATzplQZ'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'amount': 20.00, 'description': '1 Silver ticket', 'direct_type': 1}
            response = requests.post(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())


    **Example response**

    .. sourcecode:: json

        {
            "order_id": 14794,
            "qrcode": "https://ideal.nl/ideal-qr/qr/get/b35e32ab-f298-4103-8866-78e2e820123b",
            "email": "john.doe@exampledomain.com",
            "checkout_url": "https://mollie.com/paymentscreen/issuer/select/ideal/Wpgujc9R6s",
            "payment_status": "open"
        }

    The ``qrcode`` field contains the link to a qrcode image that can be scanned by a customer.

    .. warning::

        The ``qrcode`` field can also contain a data uri. For example ``data:image/png;base64,iVBORw0KGgoAAAAN...``

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Payment status
++++++++++++++

.. http:get:: /fast-events/v1/payments/(integer:id)

    Retrieve the status of a payment.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: pcXFwrEhmATzplQZ" \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
               https://exampledomain.com/wp-json/fast-events/v1/payments/14794

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/payments/14794';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: pcXFwrEhmATzplQZ')
            );
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/payments/14794'
            HEADERS = {'X-FE-API-KEY':'pcXFwrEhmATzplQZ'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "order_id": 14794,
            "payment_status": "paid"
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Orders
~~~~~~

List orders
+++++++++++

.. http:get:: /fast-events/v1/admin/orders

    Retrieve all orders. You can limit the result-set by setting query-parameters.

    **Query parameters**

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

Tickets
~~~~~~~

Ticket details
++++++++++++++

.. http:get:: /fast-events/v1/admin/tickets/(integer:id)

    Retrieve ticket details of an order. You can limit the result-set by setting query-parameters.

    **Query parameters**:

    *_fields*
        A comma separated string of fields included in the response. For example ``order_id,name,email``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "order_id": 14779,
            "name": "John Doe",
            "email": "John@Doe999.com",
            "created_at": "2021-01-02 16:00:35",
            "tickets": [
                {
                    "ticket_id": "q990U4b5PRVDy6bO",
                    "event_id": 29,
                    "event_name": "Vintage Vinyl Open Air 2021",
                    "event_date": "2021-01-12 09:00:00",
                    "ticket_type": "Gold (Backstage)",
                    "scans": [
                        {
                            "scan_level": 0,
                            "scan_date": "2021-01-12 14:13:36",
                            "scan_location": "Main entrance"
                        },
                        {
                            "scan_level": 1,
                            "scan_date": "2021-01-12 14:19:21",
                            "scan_location": "Backstage entrance"
                        }
                    ]
                },
                {
                    "ticket_id": "A940U4b5PRd0y6b6",
                    "event_id": 29,
                    "event_name": "Vintage Vinyl Open Air 2021",
                    "event_date": "2021-01-12 09:00:00",
                    "ticket_type": "Silver",
                    "scans": []
                }
            ],
            "_links": {
                "self": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779"
                    }
                ],
                "download": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/tickets/CkahdLnL6QauwpXicy1o07niUsqYb7UudhFonMq9"
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

Create tickets
++++++++++++++

.. http:post:: /fast-events/v1/admin/tickets/(integer:id)

    Create new tickets for an order.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.post(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "order_id": 14779,
            "name": "John Doe",
            "email": "John@Doe999.com",
            "created_at": "2021-01-22 19:06:01",
            "tickets": [
                {
                    "ticket_id": "JeOHejnySpMAJ0hg",
                    "event_id": 29,
                    "event_name": "Vintage Vinyl Open Air 2021",
                    "event_date": "2021-01-12 09:00:00",
                    "ticket_type": "Gold (Backstage)",
                    "scans": []
                },
                {
                    "ticket_id": "VB43Hbax4J8jlHbA",
                    "event_id": 29,
                    "event_name": "Vintage Vinyl Open Air 2021",
                    "event_date": "2021-01-12 09:00:00",
                    "ticket_type": "Silver",
                    "scans": []
                }
            ],
            "_links": {
                "self": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779"
                    }
                ],
                "download": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/tickets/hdP6RYPGgWkmoYb4189Cf7LPHF3VT5OhnRDtN7OT"
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

Delete tickets
++++++++++++++

.. http:delete:: /fast-events/v1/admin/tickets/(integer:id)

    Delete all tickets of an order.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/tickets/14779'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "deleted": true,
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."