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
            "order_id": 739,
            "qrcode": "KnRpypng4OLq2FrY",
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
       "1.9.3", "Added order_id and qrcode."

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
            "order_id": 739,
            "qrcode": "KnRpypng4OLq2FrY",
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
       "1.9.3", "Added order_id and qrcode."
