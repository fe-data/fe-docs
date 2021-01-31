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
All endpoints require an API key in a HTTP header and some use WordPress application passwords in the ``Authorization`` HTTP header.
By using application passwords (as of WordPress 5.6) you have a great deal of flexibility.
You can either create 1 WordPress user and use a single application password or an application password per client. But you can also create a WordPress user for each client with an application password.
In WordPress you can then easily revoke the rights per client. The API KEY can be used as a kind of kill switch. By changing this, all clients will be blocked for the specific endpoint.
For the username in the ``Authorization`` HTTP header you can use the login name or the emailaddress.

:scans:

   You need to include the ``X-FE-API-KEY`` and its value in a HTTP header. The value can be found in the `Scan  tab <../usage/events.html#scan-tab>`_.
   The :doc:`Scan app <../apps/scan>` is using these endpoints.

:payments:

   You need to include the ``X-FE-API-KEY`` and its value in a HTTP header. The value can be found in the `settings <../getting-started/settings.html#settings-for-instant-payments>`_ of the plugin.
   The endpoint also needs an application password. The :doc:`Payment app <../apps/payment>` is using these endpoints.

.. tip::

   You can browse the full API by accessing every endpoint with an http ``OPTIONS`` request. Use `Postman <https://www.postman.com/downloads/>`_ to look at the individual fields of an endpoint and its format.
   Use it also for testing. For example: you WordPress hosting environment is located at ``https://exampledomain.com``, the REST URL for a new scan request will be ``https://exampledomain.com/wp-json/fast-events/v1/scans``.

Scans
~~~~~
New scan
++++++++

.. http:post:: /fast-events/v1/scans

    Validate a new scan request.

    **Example request**:

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


    **Example response**:

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

List scans
++++++++++

.. http:get:: /fast-events/v1/scans/(string:id)

    Retrieve all scans of a single ticket.

    **Example request**:

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

    **Example response**:

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

Payments
~~~~~~~~
New payment
+++++++++++

.. http:post:: /fast-events/v1/payments

    Create a new payment request.

    **Example request**:

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


    **Example response**:

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

Payment status
++++++++++++++

.. http:get:: /fast-events/v1/payments/(integer:id)

    Retrieve the status of a payment.

    **Example request**:

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

    **Example response**:

    .. sourcecode:: json

        {
            "order_id": 14794,
            "payment_status": "paid"
        }
