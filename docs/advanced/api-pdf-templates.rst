PDF templates
~~~~~~~~~~~~~

List PDF templates
++++++++++++++++++

.. http:get:: /fast-events/v1/admin/pdf-templates

    Retrieve all PDF templates. Users with the ``administrator`` role will see all templates.
    Other users will only see the templates they own.

    **Optional query parameters**

    *_fields*
        A comma separated string of fields included in the response. For example ``id,title``.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        [
            {
                "id": 30,
                "title": "Eticket template OpenAir",
                "type": "ticket",
                "author_id": 1,
                "created": "2023-05-01 17:05:15",
                "modified": "2023-05-01 17:05:15",
                "url": "https://exampledomain.com/wp-content/uploads/2023/05/OpenAir-Eticket.pdf",
                "username": "d4k12lqw",
                "_links": {
                    "self": [
                        {
                            "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/30"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates"
                        }
                    ]
                }
            },
            {
                "id": 31,
                "title": "Eticket template Forest to Forest",
                "type": "ticket",
                "author_id": 1,
                "created": "2023-05-01 17:05:15",
                "modified": "2023-05-01 17:05:15",
                "url": "https://exampledomain.com/wp-content/uploads/2023/05/F2ftour.pdf",
                "username": "d4k12lqw",
                "_links": {
                    "self": [
                        {
                            "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31"
                        }
                    ],
                    "collection": [
                        {
                            "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates"
                        }
                    ]
                }
            }
        ]

    The HTTP headers of the response contains additional information about the collection.

    *X-WP-Total*
        This header contains the total number of rows in the collection.
    *X-WP-TotalPages*
        This header contains the total number of pages. This is always 1.

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

Get a single PDF template
+++++++++++++++++++++++++

.. http:get:: /fast-events/v1/admin/pdf-templates/(integer:id)

    Retrieve details of a single PDF template.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.get(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": 31,
            "title": "Eticket template Forest to Forest",
            "type": "ticket",
            "author_id": 1,
            "created": "2023-05-01 17:05:15",
            "modified": "2023-05-01 17:05:15",
            "url": "https://exampledomain.com/wp-content/uploads/2023/05/F2ftour.pdf",
            "username": "d4k12lqw",
            "_links": {
                "self": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31"
                    }
                ],
                "collection": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

Update PDF template
+++++++++++++++++++

.. http:put:: /fast-events/v1/admin/pdf-templates/(integer:id)

    Update a single PDF template. Only the fields ``title`` and ``type`` can be changed. If the API user has the ``administrator`` role,
    you can also change the ``author_id``. Effectively changing the owner of the PDF template.
    Optionally, you can also replace the PDF template with a new one.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PUT \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"title":"Improved eticket template"}' \
              -F "file=@path/to/local/file/F2ftour.pdf" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "file" => curl_file_create ("./F2ftour.pdf");
                "title" => "Improved eticket template",
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            dfile = open("F2ftour.pdf", "rb")
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'title': 'Improved eticket template'}
            response = requests.put(URL, headers=HEADERS, auth=AUTH, json=JSON, files={"file": dfile})
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": 31,
            "title": "Improved eticket template",
            "type": "ticket",
            "author_id": 1,
            "created": "2023-05-01 17:05:15",
            "modified": "2023-05-03 10:23:09",
            "url": "https://exampledomain.com/wp-content/uploads/2023/05/F2ftour.pdf",
            "username": "d4k12lqw",
            "_links": {
                "self": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31"
                    }
                ],
                "collection": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

Delete a PDF template
+++++++++++++++++++++

.. http:delete:: /fast-events/v1/admin/pdf-templates/(integer:id)

    Delete a single PDF template.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X DELETE \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31';
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
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            response = requests.delete(URL, headers=HEADERS, auth=AUTH)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "deleted": true,
            "previous": {
                "id": 31,
                "title": "Improved eticket template",
                "type": "ticket",
                "author_id": 1,
                "created": "2023-05-01 17:05:15",
                "modified": "2023-05-03 10:23:09",
                "url": "https://exampledomain.com/wp-content/uploads/2023/05/F2ftour.pdf",
                "username": "d4k12lqw",
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."

----

Upload a new PDF template
+++++++++++++++++++++++++

.. http:post:: /fast-events/v1/admin/pdf-templates

    Create/upload a new PDF template.

    **How to create a template?**
       Use for example Word, LibreOffice, … and design a single-page A4 e-ticket. Leave a 120 mm x 40 mm block somewhere on the page.
       You can position it either vertical or horizontal or even in any angle you want.
       This is the block where *Fast Events* will print the qrcode block and some other information.
       It is possible to scale down the qrcode block.
    **Recommendations**
       Keep the PDF as small as possible, preferable below 200kb for a single eticket.
       Don’t use full blown images. Bring them back to an acceptable resolution.
       And pull them first through sites like https://kraken.io to squeeze the size.
       An image resolution of 150 DPI for etickets is enough.
       Make use of use the `pdf system fonts <https://kbpdfstudio.qoppa.com/standard-14-pdf-fonts/>`_.
       For example use for your text the ``Helvetica`` font.
       Try to prevent the use of special fonts, because these are embedded in the PDF and then the PDF becomes larger.
       You can analyse your `PDF here <http://pdf-analyser.edpsciences.org/>`_.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -X PUT \
              -H "X-FE-API-KEY: 3zo58AUYP9zOE6YT"  \
              -H "Content-Type: application/json" \
              -u "test:4ZAN O5OY OAvZ FZb2 Lslv JnJG" \
              -d '{"title":"Eticket template Forest to Forest"}' \
              -F "file=@path/to/local/file/F2ftour.pdf" \
              https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "PUT");
            curl_setopt($ch, CURLOPT_USERPWD, 'test:4ZAN O5OY OAvZ FZb2 Lslv JnJG');
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json',
                'X-FE-API-KEY: 3zo58AUYP9zOE6YT')
            );
            curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode([
                "file" => curl_file_create ("./F2ftour.pdf");
                "title" => "Eticket template Forest to Forest",
            ]));
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            from requests.auth import HTTPBasicAuth
            dfile = open("F2ftour.pdf", "rb")
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates'
            HEADERS = {'X-FE-API-KEY':'3zo58AUYP9zOE6YT'}
            AUTH = HTTPBasicAuth('test', '4ZAN O5OY OAvZ FZb2 Lslv JnJG')
            JSON = {'title': 'Eticket template Forest to Forest'}
            response = requests.put(URL, headers=HEADERS, auth=AUTH, json=JSON, files={"file": dfile})
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "id": 31,
            "title": "Eticket template Forest to Forest",
            "type": "ticket",
            "author_id": 1,
            "created": "2023-05-01 17:05:15",
            "modified": "2023-05-01 17:05:15",
            "url": "https://exampledomain.com/wp-content/uploads/2023/05/F2ftour.pdf",
            "username": "d4k12lqw",
            "_links": {
                "self": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates/31"
                    }
                ],
                "collection": [
                    {
                        "href": "https://exampledomain.com/wp-json/fast-events/v1/admin/pdf-templates"
                    }
                ]
            }
        }

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "2.0", "Introduced."
