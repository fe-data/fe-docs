Ordering
~~~~~~~~

Get orderform
+++++++++++++

.. http:get:: /fast-events/v1/ordering/form/(string:token)

    Get the order form for this token.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "Content-Type: application/json" \
              https://exampledomain.com/wp-json/fast-events/v1/ordering/form/vintage

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/ordering/form/vintage';
            curl_setopt($ch, CURLOPT_URL, $urls);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json')
            );
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/ordering/form/vintage'
            response = requests.get(URL, headers=HEADERS, json=JSON)
            print(response.json())


    **Example response**

    .. sourcecode:: json

        {
            "form": "\t\t<div class=\"fast-events-form-container\">\n\t  ......  <div id=\"fast-events-event-info\"></div>\n\n\t\t",
        }

    The ``form`` field is truncated. It will be empty if the shortcode can't be found.

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.3.0", "Introduced."

----

Get orderstatus
+++++++++++++++

.. http:get:: /fast-events/v1/ordering/status/(string:uid)

    Retrieve the HTML-content for this order uid.
    The API checks to which event id the order belongs and then looks for a token that starts with 'status' supplemented with the event id. So for example 'status2'.

    **Example request**

    .. tabs::

        .. code-tab:: bash

            $ curl \
              -H "Content-Type: application/json" \
              https://exampledomain.com/wp-json/fast-events/v1//ordering/status/WzJQDnAvm7yswYzfSGVvro45q0IOScEXmdzzqO0K

        .. code-tab:: php

            <?php
            $ch = curl_init();
            $url = 'https://exampledomain.com/wp-json/fast-events/v1/ordering/status/WzJQDnAvm7yswYzfSGVvro45q0IOScEXmdzzqO0K';
            curl_setopt($ch, CURLOPT_URL, $url);
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            curl_setopt($ch, CURLOPT_HTTPHEADER, array(
                'Content-Type: application/json')
            );
            $result = curl_exec($ch);
            echo $result;

        .. code-tab:: python

            import requests
            URL = 'https://exampledomain.com/wp-json/fast-events/v1/ordering/status/WzJQDnAvm7yswYzfSGVvro45q0IOScEXmdzzqO0K'
            response = requests.get(URL, headers=HEADERS)
            print(response.json())

    **Example response**

    .. sourcecode:: json

        {
            "success": true,
            "form": "<img src=  ....  tickets</a>",
        }

    The ``form`` field is truncated. If the uid is not found or it doesnt have the right payment status the ``form`` field is empty
    and the ``success`` field is :guilabel:`false`.

    **Changelog**

    .. csv-table::
       :header: "Version", "Description"
       :width: 100%
       :widths: auto

       "1.3.0", "Introduced."