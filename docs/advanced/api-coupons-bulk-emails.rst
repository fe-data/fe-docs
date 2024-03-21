Coupon Bulk Emails
~~~~~~~~~~~~~~~~~~

List selected ids
+++++++++++++++++

.. http:post:: /fast-events/v1/admin/coupons/bulk/emails/list

    Select all ids that meet the selection criteria to send a free format email with coupon information.
    There are 2 selection methods: based on ``emaillists`` or based on ``coupons`` associated with an email address.

    **Emaillists**

    Make sure you have 1 or more `emaillists <../usage/tools.html#email-lists>`_ associated with a number of events.
    In this case, everyone on the email list will receive the same coupon and therefore the same conditions will apply to everyone.
    Make sure you define a coupon that can be used as a template.

    **Coupons**

    In this situation, everyone receives their own unique coupon linked to an email address.


    **Mandatory parameters**

    *bulk_source*
        **'0'** = ``emaillist`` as source and **'1'** = ``coupons`` as source.
    *event_ids*
        A comma separated list of event ids e.g. '4,9,11'.
    *template_code*
        An existing coupon code used as template. Only used if the source is ``emaillist``.
    *code_prefix*
        Only coupon codes with this prefix are selected. Only used if the source is ``coupons``.
    *code_suffix*
        Only coupon codes with this suffix are selected. Only used if the source is ``coupons``.
    *date_from*
        Select coupons valid from this date. Only used if the source is ``coupons``.
    *date_to*
        Select coupons valid until this date. Only used if the source is ``coupons``.
    *tickets_minimum*
        Select coupons with this minimum number of tickets. Only used if the source is ``coupons``.
    *tickets_maximum*
        Select coupons with this maximum number of tickets. Only used if the source is ``coupons``.
    *amount_minimum*
        Select coupons with this minimum amount. Only used if the source is ``coupons``.
    *amount_maximum*
        Select coupons with this maximum amount. Only used if the source is ``coupons``.
    *subject*
        The subject of the email.
    *body*
        The html email body of the email. Any `keywords <../apps/admin.html#id3>`_ in the email will be replaced with the information from the coupon.

    .. note:: All parameters must be included in the request. Even if they are not used.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"bulk_source":"0", \
                "event_ids":"2,3,4,9,10", \
                "template_code":"cp01", \
                "date_from":"2023-09-01 00:00:00", \
                "date_to":"2024-10-07 00:00:00", \
                "tickets_minimum":1, \
                "tickets_maximum":100, \
                "amount_minimum":1.00, \
                "amount_maximum":200.00, \
                "subject":"Coupon email subject", \
                "body":"Html email body with keywords ..."}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/bulk/emails/list

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/bulk/emails/list';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "bulk_source" => "0",
                "event_ids" => "2,3,4,9,10",
                "template_code" => "cp01",
                "date_from" => "2023-09-01 00:00:00",
                "date_to" => "2024-10-07 00:00:00",
                "tickets_minimum" => 1,
                "tickets_maximum" => 100,
                "amount_minimum" => 1.00,
                "amount_maximum" => 200.00,
                "subject" => "Coupon email subject",
                "body" => "Html email body with keywords ..."
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/bulk/emails/list'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'bulk_source':'0',
                'event_ids':'2,3,4,9,10',
                'template_code':'cp01',
                'date_from':'2023-09-01 00:00:00',
                'date_to':'2024-10-07 00:00:00',
                'tickets_minimum':1,
                'tickets_maximum':100,
                'amount_minimum':1.00,
                'amount_maximum':200.00,
                'subject':'Coupon email subject',
                "body":"Html email body with keywords ..."}
            response = requests.post(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "bulk_source": "0",
            "event_ids": "2,3,4,9,10",
            "template_code": "cp01",
            "code_prefix": "",
            "code_suffix": "",
            "date_from": "2023-09-01 00:00:00",
            "date_to": "2024-10-07 00:00:00",
            "tickets_minimum": 1,
            "tickets_maximum": 100,
            "amount_minimum": 1,
            "amount_maximum": 200,
            "batch_size": 25,
            "ids": [
                16,
                14,
                15
            ]
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.2.0", "Introduced."

----

Send email to ids
+++++++++++++++++

.. http:post:: /fast-events/v1/admin/coupons/bulk/emails/send

    Send a free format email to all ids in the ``ids`` array field.
    The maximum number of ids in the array cannot exceed the ``batch_size`` field
    which is returned as part of the ``list`` api call.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"bulk_source":"0", \
                "template_code":"cp01", \
                "ids":[14,15,16], \
                "subject":"The subject of the email", \
                "body":"The body of the email"}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/bulk/emails/send

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/bulk/emails/send';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "bulk_source" => "0",
                "template_code" => "cp01",
                "ids" => [14,15,16],
                "subject" => "The subject of the email",
                "body" => "The body of the email"
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/bulk/emails/send'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'bulk_source':'0',
                'template_code':'cp01',
                'order_ids':[14,15,16],
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

       "2.2.0", "Introduced."

----

Send example email
++++++++++++++++++

.. http:post:: /fast-events/v1/admin/coupons/bulk/emails/send-example

    Send a sample email to a specified email address to see how the email looks.

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
              https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/bulk/emails/send-example

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/bulk/emails/send-example';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/coupons/bulk/emails/send-example'
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

       "2.2.0", "Introduced."
