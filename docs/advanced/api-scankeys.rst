Scan keys
~~~~~~~~~

List all scan keys
++++++++++++++++++

.. http:get:: /fast-events/v1/admin/events/(integer:id)/scan_keys

    List all scan keys of the selected event.

    **Optional query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``key,level``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        [
            {
                "key": "GTIeWqKGtvLsWhP7",
                "level": 0,
                "tickets": "",
                "date_format": "l, j F H:i:s",
                "location": "Main entrance",
                "_links": {
                    "self": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys/GTIeWqKGtvLsWhP7"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys"
                        }
                    ]
                }
            },
            {
                "key": "zzFms83MjBsNEM6Y",
                "level": 1,
                "tickets": "Gold (Backstage)",
                "date_format": "l, j F H:i:s",
                "location": "Backstage entrance",
                "_links": {
                    "self": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys/zzFms83MjBsNEM6Y"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys"
                        }
                    ]
                }
            },
            {
                "key": "kJj05xtvIIO6RQAQ",
                "level": 1,
                "tickets": "Gold (Backstage)",
                "date_format": "l, j F H:i:s",
                "location": "Free cocktail",
                "_links": {
                    "self": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys/kJj05xtvIIO6RQAQ"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys"
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

       "1.0", "Introduced."

----

List scan key
+++++++++++++


.. http:get:: /fast-events/v1/admin/events/(integer:id)/scan_keys/(scan_key)

    Retrieve details of a single scan key.

    **Query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``key,level``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys/zzFms83MjBsNEM6Y

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys/zzFms83MjBsNEM6Y';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys/zzFms83MjBsNEM6Y'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "key": "zzFms83MjBsNEM6Y",
            "level": 1,
            "tickets": "Gold (Backstage)",
            "date_format": "l, j F H:i:s",
            "location": "Backstage entrance",
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys/zzFms83MjBsNEM6Y"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys"
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

Update scan key
+++++++++++++++

.. http:patch:: /fast-events/v1/admin/events/(integer:id)/scan_keys/(scan_key)

    Update a scan key. It is possible to change the scan key by including the ``key`` parameter in the payload.
    It must be exactly 16 characters long and can only contain the following characters: a-z, A-Z or 0-9

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PATCH \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"location": "Free tropical cocktail"}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys/kJj05xtvIIO6RQAQ

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys/kJj05xtvIIO6RQAQ';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PATCH");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "location" => "Free tropical cocktail",
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys/kJj05xtvIIO6RQAQ'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'location': 'Free tropical cocktail'}
            response = requests.patch(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "key": "kJj05xtvIIO6RQAQ",
            "level": 1,
            "tickets": "Gold (Backstage)",
            "date_format": "l, j F H:i:s",
            "location": "Free tropical cocltail",
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys/zzFms83MjBsNEM6Y"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys"
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

Delete scan key
+++++++++++++++

.. http:delete:: /fast-events/v1/admin/events/(integer:id)/scan_keys/(scan_key)

    Delete a single scan key.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys/zzFms83MjBsNEM6Y

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys/zzFms83MjBsNEM6Y';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys/zzFms83MjBsNEM6Y'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "deleted": true,
            "previous": {
                "key": "zzFms83MjBsNEM6Y",
                "level": 1,
                "tickets": "Gold (Backstage)",
                "date_format": "l, j F H:i:s",
                "location": "Backstage entrance"
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Create scan key
+++++++++++++++

.. http:post:: /fast-events/v1/admin/events/(integer:id)/scan_keys

    **Example request**

    You can set a new key by including the ``key`` parameter in the payload. It must be exactly 16 characters long and can only contain the following characters: a-z, A-Z or 0-9
    If the ``key`` field is omitted, the system generates a unique key.

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PATCH \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"level":1,"tickets":"Gold (Backstage)","location": "Free tropical cocktail"}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PATCH");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "level" => 1,
                "tickets" => "Gold (Backstage)",
                "location" => "Free tropical cocktail",
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/scan_keys'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'level': 1, 'tickets': 'Gold (Backstage)', 'location': 'Free tropical cocktail'}
            response = requests.patch(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "key": "UT2gIFkepRB5BQTn",
            "level": 1,
            "tickets": "Gold (Backstage)",
            "date_format": "l, j F H:i:s",
            "location": "Backstage entrance",
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys/UT2gIFkepRB5BQTn"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/scan_keys"
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
