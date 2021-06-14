Ticket types
~~~~~~~~~~~~

List all ticket types
+++++++++++++++++++++

.. http:get:: /fast-events/v1/admin/events/(integer:id)/ticket_types

    List all ticket types of the selected event.

    **Optional query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``name,price``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        [
            {
                "id": "v05ef7",
                "name": "Silver",
                "price": 20.25,
                "vat": 21,
                "stock_control": false,
                "minimum_to_order": 0,
                "maximum_to_order": 10,
                "is_counted": true,
                "attachment_id": 260,
                "_links": {
                    "self": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket_types/v05ef7"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket_types"
                        }
                    ]
                }
            },
            {
                "id": "v24a1f",
                "name": "Gold (Backstage)",
                "price": 40.5,
                "vat": 0,
                "stock_control": true,
                "stock": 100,
                "minimum_to_order": 0,
                "maximum_to_order": 1,
                "is_counted": true,
                "attachment_id": 60,
                "_links": {
                    "self": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket_types/v24a1f"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket_types"
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

List ticket type
++++++++++++++++


.. http:get:: /fast-events/v1/admin/events/(integer:id)/ticket_types/(ticket_type)

    Retrieve details of a single ticket type.

    **Query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``name,price``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types/v24a1f

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types/v24a1f';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types/v24a1f'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": "v24a1f",
            "name": "Gold (Backstage)",
            "price": 40.5,
            "vat": 0,
            "stock_control": true,
            "stock": 100,
            "minimum_to_order": 0,
            "maximum_to_order": 1,
            "is_counted": true,
            "attachment_id": 60,
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket_types/v24a1f"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket_types"
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

Update ticket type
++++++++++++++++++

.. http:patch:: /fast-events/v1/admin/events/(integer:id)/ticket_types/(ticket_type)

    Update a ticket type. Only include in the payload the fields you want to change.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PATCH \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"attachment_id": 160}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types/v24a1f

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types/v24a1f';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PATCH");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "attachment_id" => 160,
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types/v24a1f'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'attachment_id': 160}
            response = requests.patch(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "id": "v24a1f",
            "name": "Gold (Backstage)",
            "price": 40.5,
            "vat": 0,
            "stock_control": true,
            "stock": 100,
            "minimum_to_order": 0,
            "maximum_to_order": 1,
            "is_counted": true,
            "attachment_id": 160,
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket_types/v24a1f"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket_types"
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

Delete ticket type
++++++++++++++++++

.. http:delete:: /fast-events/v1/admin/events/(integer:id)/ticket_types/(ticket_type)

    Delete a single ticket type.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types/v24a1f

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types/v24a1f';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types/v24a1f'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "deleted": true,
            "previous": {
                "name": "Gold (Backstage)",
                "price": 40.5,
                "vat": 0,
                "stock_control": true,
                "stock": 100,
                "minimum_to_order": 0,
                "maximum_to_order": 1,
                "is_counted": true,
                "attachment_id": 160
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."

----

Create ticket type
++++++++++++++++++

.. http:post:: /fast-events/v1/admin/events/(integer:id)/ticket_types

    Create a new ticket type.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PATCH \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"name":"Gold (Backstage)", "price":40.3, "attachment_id":170}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PATCH");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "name" => "Gold (Backstage)",
                "price" => 40.3,
                "attachment_id" => 170,
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket_types'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'name': 'Gold (Backstage)', 'price': 40.3,  'attachment_id': 170}
            response = requests.patch(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "id": "v2f34a",
            "name": "Gold (Backstage)",
            "price": 40.3,
            "vat": 0,
            "stock_control": true,
            "stock": 100,
            "minimum_to_order": 0,
            "maximum_to_order": 1,
            "is_counted": true,
            "attachment_id": 170,
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket_types/v24a1f"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket_types"
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
