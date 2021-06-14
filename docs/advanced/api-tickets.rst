Tickets
~~~~~~~

Ticket details
++++++++++++++

.. http:get:: /fast-events/v1/admin/tickets/(integer:id)

    Retrieve ticket details of an order. You can limit the result-set by setting query-parameters.

    **Optional query parameters**:

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
            from requests.auth import HTTPBasicAuth
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
                            "level": 0,
                            "date": "2021-01-12 14:13:36",
                            "location": "Main entrance"
                        },
                        {
                            "level": 1,
                            "date": "2021-01-12 14:19:21",
                            "location": "Backstage entrance"
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

    Create new tickets for an order. When a new order is created, tickets are automatically generated after payment or if it is a dashboard order.
    But you can use this function, for example, to first invalidate all tickets by deleting them (`Delete tickets`_) and then calling this function so that all tickets get a new unique id.

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
            from requests.auth import HTTPBasicAuth
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
            from requests.auth import HTTPBasicAuth
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