Ordering
~~~~~~~~

Get orderform
+++++++++++++

.. http:get:: /fast-events/v1/ordering/form/(string:token)

    Get the order form for this token. You can use this API to embed the ordering form in you own html-code.

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

        .. code-tab:: html

            // This will inject the orderform in you frontend HTML and load the payment JS file.
            <div id="fast-events-order-form"></div>
            <script>
                document.addEventListener("DOMContentLoaded", async () => {

                    const checkElement = async selector => {
                        while (document.getElementById(selector) === null ) {
                            await new Promise(resolve => requestAnimationFrame(resolve))
                        }
                        return document.getElementById(selector)
                    }

                    try {
                        document.body.style.cursor = 'progress'
                        let response = await fetch('https://example.com/wp-json/fast-events/v1/ordering/form/vinyl')
                        const json = await response.json();
                        if (response.ok) {
                            document.getElementById('fast-events-order-form').innerHTML = json.form
                            checkElement('fast-events-form-submit').then((selector) => {
                                let js = document.createElement('script')
                                js.src = '/js/fe-payment.min.js'
                                document.head.appendChild(js)
                            })
                        } else {
                            alert(json.message)
                        }
                    } catch (error) {
                        alert('Error: ' + error)
                    } finally {
                        document.body.style.cursor = 'default'
                    }
                });
            </script>


    **Example response**

    .. sourcecode:: json

        {
            "form": "\t\t<div class=\"fast-events-form-container\">\n\t  ......  <div id=\"fast-events-event-info\"></div>\n\n\t\t",
        }

    The ``form`` field is truncated. It will be empty if the shortcode can't be found.

    **Example implementation**

    Below is sample implementation on how to use this REST API call in your own html page.
    After the *Fast Event* html order form is loaded, the javascript code in ``fe-payment.min.js`` is also loaded.
    This javascript code is part of the *Fast Events* plugin and can be found in the :guilabel:`assets/js` directory of the plugin.
    You should copy it to your own site.

    .. code-block:: html

       <div id="fast-events-order-form"></div>
       <script>
           document.addEventListener("DOMContentLoaded", async () => {

               const checkElement = async selector => {
                   while (document.getElementById(selector) === null ) {
                       await new Promise(resolve => requestAnimationFrame(resolve))
                   }
                   return document.getElementById(selector)
               }

               try {
                   document.body.style.cursor = 'progress'
                   let response = await fetch('https://exampledomain.com/wp-json/fast-events/v1/ordering/form/vintage')
                   const json = await response.json();
                   if (response.ok) {
                       document.getElementById('fast-events-order-form').innerHTML = json.form
                       checkElement('fast-events-form-submit').then((selector) => {
                           let js = document.createElement('script')
                           js.src = '/js/fe-payment.min.js'
                           document.head.appendChild(js)
                       })
                   } else {
                       if (json.code === 'rest_no_route') {
                           document.getElementById('fast-events-order-form').innerHTML =
                               '<div style="font-size:18px;color:#141619;background:#d4d4d4;margin-bottom:0!important;padding:1rem;border:1px solid rgb(188,190,191);border-radius:0.375rem">\
                                   <p>The ticket system is currently inactive.</p>\
                               </div>'
                       } else {
                           alert(json.message)
                       }
                   }
               } catch (error) {
                   alert('Error: ' + error)
               } finally {
                   document.body.style.cursor = 'default'
               }
           });
       </script>

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
              https://exampledomain.com/wp-json/fast-events/v1/ordering/status/WzJQDnAvm7yswYzfSGVvro45q0IOScEXmdzzqO0K

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
