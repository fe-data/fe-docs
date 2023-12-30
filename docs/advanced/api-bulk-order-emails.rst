Bulk Order Emails
~~~~~~~~~~~~~~~~~

List selected order ids
+++++++++++++++++++++++

.. http:post:: /fast-events/v1/admin/bulk/order-emails/list

    Select all order ids that meet the selection conditions for resending the 'new order` email.

    **Mandatory parameters**

    *dates*
        Order was created between ``date_from`` and ``date_to``.
    *tickets*
        The number of tickets the order has is between ``tickets_minimum`` and ``tickets_maximum``.
    *amount*
        The total amount of the order is between ``ammount_minimum`` and ``amount_maximum``.
    *event ids*
        If the ``event_ids`` field is empty the selection works across all authorised events.
        You can specify a selection of events by a comma-separated list of event ids.
        For example ``34,56,86``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"date_from":"2022-09-01 00:00:00", \
                "date_to":"2023-10-07 00:00:00", \
                "event_ids":"", \
                "tickets_minimum":1, \
                "tickets_maximum":100, \
                "amount_minimum":1.00, \
                "amount_maximum":200.00}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/order-emails/list

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/order-emails/list';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "date_from" => "2022-09-01 00:00:00",
                "date_to" => "2023-10-07 00:00:00",
                "event_ids" => "",
                "tickets_minimum" => 1,
                "tickets_maximum" => 100,
                "amount_minimum" => 1.00,
                "amount_maximum" => 200.00
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/order-emails/list'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'date_from':'2022-09-01 00:00:00',
                'date_to':'2023-10-07 00:00:00',
                'event_ids':'',
                'tickets_minimum':1,
                'tickets_maximum':100,
                'amount_minimum':1.00,
                'amount_maximum':200.00}
            response = requests.post(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "event_ids": "",
            "date_from": "2022-09-01 00:00:00",
            "date_to": "2023-10-07 00:00:00",
            "tickets_minimum": 1,
            "tickets_maximum": 100,
            "amount_minimum": 1,
            "amount_maximum": 200,
            "batch_size": 25,
            "order_ids": [
                1,
                2,
                4,
                5,
                6,
                7,
                32,
                33
            ]
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

Send selected order ids
+++++++++++++++++++++++

.. http:post:: /fast-events/v1/admin/bulk/order-emails/send

    Send an order email confirmation to all order ids in the ``order_ids`` array field.
    The maximum number of order ids in the array cannot exceed the ``batch_size`` field
    which is returned as part of the ``list`` api call.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"order_ids": [1,200,201]}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/order-emails/send

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/order-emails/send';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "order_ids" => [1,200,201]
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/order-emails/send'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'order_ids':[1,200,201]}
            response = requests.post(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "errors": [
                {
                    "order_id": 200,
                    "error": "Order not found"
                },
                {
                    "order_id": 201,
                    "error": "Order not found"
                }
            ]
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."
