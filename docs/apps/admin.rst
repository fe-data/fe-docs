FE Admin App
============
With the FE Admin app, you can quickly view details of events and orders on your mobile phone and change various
components of events and/or orders, if you are authorised to do so.

Full list of capabilities
-------------------------
Depending on the permissions configuration on the webserver hosting the Fast Events WordPress plugin,
users will only see the components they are allowed to see. The full list of components is shown below.
Permissions can be configured in `Authorization Settings <../getting-started/settings.html#authorization-settings>`_

Below is a list of menu options. The permission required for each item is shown after it.

Events
^^^^^^
#. Detailed overview (:guilabel:`event_read`).
#. Change event stock (:guilabel:`event_update`).
#. Change event dates (:guilabel:`event_update`).
#. Change various setting flags (:guilabel:`event_update`).
#. Synchronise parts of an event with another event (:guilabel:`event_sync`).
#. Show scan information and configuration QR code for the :doc:`FE Scanner App <scan>` (:guilabel:`scan_app_read`).
#. Detailed information about tickets sold (:guilabel:`total_sales`).
#. Detailed information on scanning tickets in progress (:guilabel:`total_scans`).

Orders
^^^^^^
#. Detailed overview of the order (:guilabel:`order_read` and :guilabel:`scan_app_read`).
#. Email the order (:guilabel:`order_email`).
#. Change the name and email address of the order (:guilabel:`order_update`).
#. Share tickets using Android Sharing (:guilabel:`order_read`).
#. Delete an order (:guilabel:`order_delete`).
#. Delete tickets (:guilabel:`tickets_delete`).
#. Create tickets (:guilabel:`tickets_create`).
#. Refund and order (:guilabel:`order_refund`).
#. Add new orders (:guilabel:`order_add`).

Tools
^^^^^
#. Show and delete logging entries (:guilabel:`log_read` and :guilabel:`log_delete` for deleting an entry).
#. Scan a ticket to see its details. This is an informational scan only (:guilabel:`tickets_read`).
#. Show, add, modify and delete input fields (:guilabel:`input_fields_read` and :guilabel:`input_fields_change` for add, modify or delete).
#. Show, add, modify and delete ticket types (:guilabel:`ticket_types_read` and :guilabel:`ticket_types_change` for add, modify or delete).
#. Show, add, modify and delete scan keys (:guilabel:`scan_app_read` and :guilabel:`scan_app_change` for add, modify or delete).
#. Sales dashboard (:guilabel:`total_sales`).
#. Export orders to Excel format (:guilabel:`order_export`).
#. Export tickets to Excel format (:guilabel:`tickets_export`).

The App is available for Android 9.0 and above and IOS 13 and above.

.. image:: ../_static/images/apps/Admin-Android.png
   :target: https://play.google.com/store/apps/details?id=nl.fe_data.admin
   :alt: FE Admin App
   :scale: 50%
   
Server accounts
---------------
The first time you start the application it will display the ``Server account`` page where you can configure a new server. Press the ``+`` button to add a new server.

First, make sure you have configured the ``REST API settings`` in the `settings <../getting-started/settings.html#rest-api-settings>`_ of the plugin.
To configure a new server you can scan this QR code to fill in the :guilabel:`Server URL` and :guilabel:`API Key` parameters.

Users of the App need an account in the WordPress environment. The App uses WordPress application password.
You can either create 1 WordPress user and use a single application password for all clients or an application password per client.
You can also create a WordPress user for each client with an application password.
In WordPress you can then easily revoke the rights per client.
The API KEY can be used as a kind of kill switch. Changing it will block all clients.
Make sure to authorize the use in the `Authorization settings <../getting-started/settings.html#authorization-settings>`_ and, if needed, limit the access to certain events.

If :guilabel:`SaaS mode` has been checked in the `Payment provider settings <../getting-started/settings.html#saas-mode>`_, every sub-merchant **must have** it's own WordPress account!

.. warning:: Users with the role of '**admin**' are not allowed.

**Name**
   The name of the account. Choose one of your own.
**Server URL**
   This is the location of your WordPress installation resides. Typically something like https://www.exampledomain.com.
**API key**
   The unique REST API key. You can find it in the Settings.
**User**
   The user login name.
**Password**
   The application password.

Once you have entered the server details, save them and press the server card to log in.
To switch between accounts, simply press the top-right circle and select a different account.

Usage
-----
The first time the App is launched and if *Fast Events* is running in ``SaaS mode`` and the sub-merchant has not yet
authorized access to its payment information, a ``Connect with Mollie`` screen will be displayed to authorise access.

The way the App works is pretty straightforward. You can use the buttons at the bottom to switch between ``Orders``, ``Events`` and ``Tools``.
In the orders and events tab you can swipe down to refresh the content.
The ``three dots`` on the right of a an event or order can be pressed to display a context menu. See example screenshots.

In the orders tab you to quickly search for an order. Just start typing and the result will be displayed.
Searches are performed on all fields except the number of tickets and amount.

.. list-table::

    * - .. image:: ../_static/images/apps/Admin-accounts.png
           :target: ../_static/images/apps/Admin-accounts.png
           :alt: FE Admin login
      - .. image:: ../_static/images/apps/Admin-edit-account.png
           :target: ../_static/images/apps/Admin-edit-account.png
           :alt: Edit account
      - .. image:: ../_static/images/apps/Admin-events.png
           :target: ../_static/images/apps/Admin-events.png
           :alt: Events

.. list-table::

    * - .. image:: ../_static/images/apps/Admin-orders.png
           :target: ../_static/images/apps/Admin-orders.png
           :alt: Orders
      - .. image:: ../_static/images/apps/Admin-order-detail.png
           :target: ../_static/images/apps/Admin-order-detail.png
           :alt: Order details
      - .. image:: ../_static/images/apps/Admin-tools.png
           :target: ../_static/images/apps/Admin-tools.png
           :alt: Tools

