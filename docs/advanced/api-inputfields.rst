Input fields
~~~~~~~~~~~~
List all input fields
+++++++++++++++++++++

.. http:get:: /fast-events/v1/admin/events/(integer:id)/input-fields

    List all input fields of the selected event.
    If ``is_personalised`` is **false**, the input field is used on the order level.
    Users need to fill it in when ordering.

    If the value is **true**, each ticket must be personalised after ordering.
    You cannot download tickets unless all tickets are personalised.

    **Optional query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``name,type``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        [
            {
                "id": "v0f446",
                "name": "Country",
                "type": "text",
                "value": "France",
                "min": "",
                "max": "30",
                "is_required": false,
                "is_personalised": false,
                "_links": {
                    "self": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/input-fields"
                        }
                    ]
                }
            },
            {
                "id": "v19e73",
                "name": "Public transport",
                "type": "select",
                "value": "Yes,No",
                "min": "",
                "max": "30",
                "is_required": true,
                "is_personalised": false,
                "_links": {
                    "self": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/input-fields/v19e73"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/input-fields"
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
       "2.1.0", "Added min, max and is_personalised."

----

List input field
++++++++++++++++


.. http:get:: /fast-events/v1/admin/events/(integer:id)/input-fields/(input_field)

    Retrieve details of a single input field.

    **Query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``name,type``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": "v0f446",
            "name": "Country",
            "type": "text",
            "value": "France",
            "min": "",
            "max": "30",
            "is_required": false,
            "is_personalised": false,
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/input-fields"
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
       "2.1.0", "Added min, max and is_personalised."

----

Update input field
++++++++++++++++++

.. http:put:: /fast-events/v1/admin/events/(integer:id)/input-fields/(input_field)

    Update a input field.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PUT \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"value": "Netherlands"}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "value" => "Netherlands",
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'value': 'Netherlands'}
            response = requests.put(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "name": "Country",
            "type": "text",
            "value": "Netherlands",
            "min": "",
            "max": "30",
            "is_required": false,
            "is_personalised": false,
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/input-fields"
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
       "2.1", "Added min, max and is_personalised."

----

Delete input field
++++++++++++++++++

.. http:delete:: /fast-events/v1/admin/events/(integer:id)/input-fields/(input_field)

    Delete a single input field.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields/v0f446'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "deleted": true,
            "previous": {
                "name": "Country",
                "type": "text",
                "value": "Netherlands",
                "min": "",
                "max": "30",
                "is_required": false,
                "is_personalised": false,
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.0", "Introduced."
       "2.1", "Added min, max and is_personalised."

----

Create input field
++++++++++++++++++

.. http:post:: /fast-events/v1/admin/events/(integer:id)/input-fields

    Create a new input field.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X POST \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"name":"Country"}' \
              https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "POST");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "name" => "Country",
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/events/54/input-fields'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'name': 'Country'}
            response = requests.post(URL, headers=HEADERS, auth=AUTH, json=JSON)
            print(response.json())

    **Example response**


    .. sourcecode:: json

        {
            "id": "v3f5e6",
            "name": "Country",
            "type": "text",
            "value": "",
            "min": "",
            "max": "",
            "is_required": false,
            "is_personalised": false,
            "_links": {
                "self": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/input-fields/v3f5e6"
                    }
                ],
                "collection": [
                    {
                        "href": "https://vinyl-openair.com/wp-json/fast-events/v1/admin/events/54/input-fields"
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
       "2.1", "Added min, max and is_personalised."
