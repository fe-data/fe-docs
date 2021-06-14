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
