Total scans
~~~~~~~~~~~

Total scans
+++++++++++

.. http:get:: /fast-events/v1/admin/events/(integer:id)/scans

    Retrieve the total number of scans per ticket type.

    **Optional query parameters**:

    *_fields*
        A comma separated string of fields included in the response. For example ``id,sold,tickets``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/29/scans

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/29/scans';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/29/scans'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": 29,
            "event_name": "Vinyl Open Air 2020",
            "stock": 15000,
            "sold": 9,
            "stock_link": 0,
            "tickets": [
                {
                    "ticket_type": "Gold (Backstage)",
                    "scans": [
                        {
                            "scan_location": "Main entrance",
                            "scan_level": 0,
                            "scan_total": 3
                        },
                        {
                            "scan_location": "Backstage entrance",
                            "scan_level": 1,
                            "scan_total": 2
                        },
                        {
                            "scan_location": "Free cocktail",
                            "scan_level": 1,
                            "scan_total": 2
                        }
                    ]
                },
                {
                    "ticket_type": "Silver",
                    "scans": [
                        {
                            "scan_location": "Main entrance",
                            "scan_level": 0,
                            "scan_total": 2
                        }
                    ]
                },
            ],
            "_links": {
                "self": [
                    {
                        "href": "https://ijsclubdwarsgracht.nl/wp-json/fast-events/v1/admin/events/29/scans"
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
