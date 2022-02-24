Public API
==========

API v1
------
The *Fast Events* public API uses :abbr:`REST (Representational State Transfer)` and
:abbr:`JSON (JavaScript Object Notation)` is returned by all API responses including errors
and HTTP response status codes are to designate success and failure.

.. contents:: Table of contents
   :local:
   :backlinks: none
   :depth: 3

Requests to the *Fast Events* public API is for private information and all endpoints require authentication.


Requirements
------------
Some endpoints require an API key in a HTTP header and most use WordPress application passwords in the ``Authorization`` HTTP header.
By using application passwords (as of WordPress 5.6) you have a great deal of flexibility.
You can either create 1 WordPress user and use a single application password for all clients or an application password per client. But you can also create a WordPress user for each client with an application password.
In WordPress you can then easily revoke the rights per client. The API KEY can be used as a kind of kill switch. By changing this, all clients will be blocked for the specific endpoint.
For the username in the ``Authorization`` HTTP header you can use the login name or the emailaddress. Overview per resource:

:scans:

   You need to include the ``X-FE-API-KEY`` and its value in a HTTP header. The value can be found in the `Scan  tab <../usage/events.html#scan-tab>`_.
   The :doc:`Scan app <../apps/scan>` is using these endpoints.

:payments:

   You need to include the ``X-FE-API-KEY`` and its value in a HTTP header. The value can be found in the `settings <../getting-started/settings.html#settings-for-instant-payments>`_ of the plugin.
   The endpoint also needs an application password. The :doc:`Payment app <../apps/payment>` is using these endpoints.

:admin:

   You need to include the ``X-FE-API-KEY`` and its value in a HTTP header for all ``admin`` endpoints. The value can be found in the `plugin settings <../getting-started/settings.html#rest-api-settings>`_.
   These endpoint also needs an application password.

:ordering:

   If you want to use this API, you first need to enable the Ordering API in het `Miscellaneous settings <../getting-started/settings.html#miscellaneous-settings>`_.
   And don't forget to add the shortcodes to generate the order from or status information.

   You can use the API if the frontend of your website is completely separated from the WordPress backend and your frontend runs, for example, as a static website on Cloudflare Pages, Netlify, etc.
   In this way the WordPress backend has been completely transformed into a 100% REST API server for all client traffic.

.. tip::

   You can browse the schemas by accessing every endpoint with an http ``OPTIONS`` request. Use `Postman <https://www.postman.com/downloads/>`_ to look at the individual fields of an endpoint and its format.
   Use it also for testing. For example: if your WordPress hosting environment is located at ``https://exampledomain.com``, the REST URL for a new scan request will be ``https://exampledomain.com/wp-json/fast-events/v1/scans``.

.. warning::

   Default values in the schemas are only applicable if a new object is created and if not all fields all provided in the REST request.

----

Resources
---------
* :doc:`Scans <api-scans>`
* :doc:`Payments <api-payments>`
* :doc:`Events <api-events>`
* :doc:`Input fields <api-inputfields>`
* :doc:`Ticket types <api-tickettypes>`
* :doc:`Scankeys <api-scankeys>`
* :doc:`Total sales <api-totalsales>`
* :doc:`Total scans <api-totalscans>`
* :doc:`Orders <api-orders>`
* :doc:`Tickets <api-tickets>`
* :doc:`Ordering <api-ordering>`

.. toctree::
   :maxdepth: 1
   :hidden:

   api-scans
   api-payments
   api-events
   api-inputfields
   api-tickettypes
   api-scankeys
   api-totalsales
   api-totalscans
   api-orders
   api-tickets
   api-ordering
