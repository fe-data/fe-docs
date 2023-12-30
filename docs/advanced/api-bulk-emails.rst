Bulk Emails
~~~~~~~~~~~

List selected order ids
+++++++++++++++++++++++

.. http:post:: /fast-events/v1/admin/bulk/emails/list

    Select all order ids that meet the selection conditions for sending a free format email.

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
    *scanned*
        If the ``scanned`` parameter is `true`, only orders with scanned tickets are included in the selection.

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
                "scanned":false, \
                "tickets_minimum":1, \
                "tickets_maximum":100, \
                "amount_minimum":1.00, \
                "amount_maximum":200.00}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/emails/list

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/emails/list';
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
                "scanned" => false,
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/emails/list'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'date_from':'2022-09-01 00:00:00',
                'date_to':'2023-10-07 00:00:00',
                'event_ids':'',
                'scanned':false,
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
            "amount_maximum": 200,
            "scanned": false,
            "order_ids": [
                1,
                2,
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

Send email to order ids
+++++++++++++++++++++++

.. http:post:: /fast-events/v1/admin/bulk/emails/send

    Send a free format email to all order ids in the ``order_ids`` array field.
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
              -d '{"order_ids":[1,2,32,22], \
                "subject":"The subject of the email", \
                "body":"The body of the email"}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/emails/send

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/emails/send';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "order_ids" => [1,2,32,22],
                "subject" => "The subject of the email",
                "body" => "The body of the email"
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/emails/send'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'order_ids':[1,2,32,22],
                'subject':'The subject of the email',
                'body':'The body of the email'}
            response = requests.post(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "errors": [
                {
                    "order_id": 22,
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

----

Send example email
++++++++++++++++++

.. http:post:: /fast-events/v1/admin/bulk/emails/send-example

    Send a sample email to a specified email address to assess how the email looks.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"email":"johndoe@exampledomain.com", \
                "subject":"The subject of the email", \
                "body":"The body of the email"}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/emails/send-example

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/emails/send-example';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "email" => "johndoe@exampledomain.com",
                "subject" => "The subject of the email",
                "body" => "The body of the email"
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/bulk/emails/send-example'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'email':'johndoe@exampledomain.com',
                'subject':'The subject of the email',
                'body':'The body of the email'}
            response = requests.post(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "errors": []
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."
