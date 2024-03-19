Public API
==========

API v2
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
Some endpoints require an API key in a HTTP header but most use WordPress application passwords in the ``Authorization`` HTTP header and use the API key.
Use the ``Accounts`` tool in the :guilabel:`Tools` section of the Web interface or FE Admin App for management of the API key and application password of the accounts.
You can also limit functionality and limit the number of visible events in the ``Accounts`` tool.

In all api descriptions we provide examples in ``php`` and ``python`` how to supply these HTTP headers. But if you use another environment,
make sure you include these headers:

.. code-block:: text

   Content-Type: application/json
   X-FE-API-KEY: PUT_YOUR_API_KEY_HERE
   Authorization: Basic Base64Encode USERNAME:APPLICATION_PASSWORD

A real live example:

.. code-block:: text

   Content-Type: application/json
   X-FE-API-KEY: rtQOChtCjj2Nmbei
   Authorization: Basic ZHdhcnNncmFjaHQ6djBkRSBkYXlaIGVPV0wgQzhKUyBhVWtSIEIyZ3g=

.. tip::

   You can browse the schemas by accessing every endpoint with an http ``OPTIONS`` request. Use `Postman <https://www.postman.com/downloads/>`_ to look at the individual fields of an endpoint and its format.
   Use it also for testing. For example: if your WordPress hosting environment is located at ``https://exampledomain.com``, the REST URL for a new scan request will be ``https://exampledomain.com/wp-json/fast-events/v1/scans``.

.. warning::

   Default values in the schemas are only applicable if a new object is created and if not all fields are provided in the REST request.

----

Resources
---------
* :doc:`Bulk emails <api-bulk-emails>`
* :doc:`Bulk order emails <api-bulk-order-emails>`
* :doc:`Bulk refunds <api-bulk-refunds>`
* :doc:`Coupons <api-coupons>`
* :doc:`Email lists <api-emaillists>`
* :doc:`Events <api-events>`
* :doc:`Input fields <api-inputfields>`
* :doc:`Error logs <api-logs>`
* :doc:`Ordering <api-ordering>`
* :doc:`Orders <api-orders>`
* :doc:`PDF templates <api-pdf-templates>`
* :doc:`Scans <api-scans>`
* :doc:`Scankeys <api-scankeys>`
* :doc:`Tickets <api-tickets>`
* :doc:`Ticket types <api-tickettypes>`
* :doc:`Total sales <api-totalsales>`
* :doc:`Total scans <api-totalscans>`
* :doc:`Webhooks <api-webhooks>`

.. toctree::
   :maxdepth: 1
   :hidden:

   api-bulk-emails
   api-bulk-order-emails
   api-bulk-refunds
   api-coupons
   api-emaillists
   api-events
   api-inputfields
   api-logs
   api-ordering
   api-orders
   api-pdf-templates
   api-scans
   api-scankeys
   api-tickets
   api-tickettypes
   api-totalsales
   api-totalscans
   api-webhooks
