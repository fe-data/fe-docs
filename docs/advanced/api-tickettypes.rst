Ticket types
~~~~~~~~~~~~

List all ticket types
+++++++++++++++++++++

.. http:get:: /fast-events/v1/admin/events/(integer:id)/ticket-types

    List all ticket types of the selected event.
    The ``personalise`` field is a comma-separated list of input field names that need to be personalised after the order is placed.
    Each member of this list must have an input field name with the ``is_personalised`` set to **true**.

    The ``layout`` field is a comma-separated list of input field names that can be printed in the qrcode info block of a PDF ticket.
    If empty the default plugin layout will be used. You can use up to 6 fields.
    It is also possible to include **Order-id**, **Name** and **Email** as a field. These fields are taken from the order.

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
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types'
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
                "volume_price": [
                    {
                        "4": 20
                    },
                    {
                        "10": 18.75
                    },
                    {
                        "15": 18.25
                    }
                ],
                "vat": 21,
                "stock_control": false,
                "sold": 2,
                "minimum_to_order": 0,
                "maximum_to_order": 10,
                "is_counted": true,
                "attachment_id": 260,
                "personalise": "",
                "layout": "",
                "_links": {
                    "self": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket-types/v05ef7"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket-types"
                        }
                    ]
                }
            },
            {
                "id": "v14a1f",
                "name": "Gold (Backstage)",
                "price": 40.5,
                "volume_price": [],
                "vat": 0,
                "stock_control": true,
                "stock": 100,
                "sold": 4,
                "minimum_to_order": 0,
                "maximum_to_order": 1,
                "is_counted": true,
                "attachment_id": 60,
                "personalise": "",
                "layout": "",
                "_links": {
                    "self": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket-types/v14a1f"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket-types"
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
       "2.1.0", "Added personalise and layout fields."
       "2.2.0", "Added volume_price field."

----

List ticket type
++++++++++++++++


.. http:get:: /fast-events/v1/admin/events/(integer:id)/ticket-types/(ticket_type)

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
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types/v14a1f

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types/v14a1f';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types/v14a1f'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": "v14a1f",
            "name": "Gold (Backstage)",
            "price": 40.5,
            "volume_price": [],
            "vat": 0,
            "stock_control": true,
            "stock": 100,
            "sold": 4,
            "minimum_to_order": 0,
            "maximum_to_order": 1,
            "is_counted": true,
            "attachment_id": 60,
            "personalise": "",
            "layout": "",
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket-types/v14a1f"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket-types"
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
       "2.1.0", "Added personalise and layout fields."
       "2.2.0", "Added volume_price field."

----

Update ticket type
++++++++++++++++++

.. http:put:: /fast-events/v1/admin/events/(integer:id)/ticket-types/(ticket_type)

    Update a ticket type. Only include in the payload the fields you want to change.

    If ``stock_control`` is set to :guilabel:`false`, don't include the ``stock`` field.

    You can lookup the ``attachment_id`` in the :doc:`PDF templates API <api-pdf-templates>`

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PUT \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"attachment_id": 160}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types/v14a1f

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types/v14a1f';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types/v14a1f'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'attachment_id': 160}
            response = requests.put(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "id": "v14a1f",
            "name": "Gold (Backstage)",
            "price": 40.5,
            "volume_price": [],
            "vat": 0,
            "stock_control": true,
            "stock": 100,
            "sold": 4,
            "minimum_to_order": 0,
            "maximum_to_order": 1,
            "is_counted": true,
            "attachment_id": 160,
            "personalise": "",
            "layout": "",
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket-types/v14a1f"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket-types"
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
       "2.1.0", "Added personalise and layout fields."
       "2.2.0", "Added volume_price field."

----

Delete ticket type
++++++++++++++++++

.. http:delete:: /fast-events/v1/admin/events/(integer:id)/ticket-types/(ticket_type)

    Delete a single ticket type.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types/v14a1f

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types/v14a1f';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types/v14a1f'
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
                "volume_price": [],
                "vat": 0,
                "stock_control": true,
                "stock": 100,
                "sold": 4,
                "minimum_to_order": 0,
                "maximum_to_order": 1,
                "is_counted": true,
                "attachment_id": 160,
                "personalise": "",
                "layout": ""
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."
       "2.1.0", "Added personalise and layout fields."
       "2.2.0", "Added volume_price field."

----

Create ticket type
++++++++++++++++++

.. http:post:: /fast-events/v1/admin/events/(integer:id)/ticket-types

    Create a new ticket type.

    If ``stock_control`` is set to :guilabel:`false`, don't include the ``stock`` field.

    You can lookup the ``attachment_id`` in the :doc:`PDF templates API <api-pdf-templates>`

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"name":"Gold (Backstage)", "price":40.3, "attachment_id":170}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "name" => "Gold (Backstage)",
                "price" => 40.3,
                "attachment_id" => 170,
                "personalise" => "Year",
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/ticket-types'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'name': 'Gold (Backstage)', 'price': 40.3,  'attachment_id': 170}
            response = requests.post(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "id": "v1f34a",
            "name": "Gold (Backstage)",
            "price": 40.3,
            "volume_price": [],
            "vat": 0,
            "stock_control": true,
            "stock": 100,
            "minimum_to_order": 0,
            "maximum_to_order": 1,
            "is_counted": true,
            "attachment_id": 170,
            "personalise": "Year",
            "layout": "",
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket-types/v14a1f"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/65/ticket-types"
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
       "2.1.0", "Added personalise and layout fields."
       "2.2.0", "Added volume_price field."
