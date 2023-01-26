FE Admin App
============
With the FE Admin app, you can quickly view details of events and orders on your mobile phone and change settings if you are authorised to do so.
It is also possible to resend orders by email, or to refund an order amount, delete and re-create tickets for an order or even create new orders.

FE Admin can also support you to help configure users’ :doc:`FE Scanner App <scan>` or :doc:`FE Payment App <payment>`.

You can also quickly view the number of tickets sold or the number of tickets scanned at different locations.
You can also change the stock and the window for ticket sales.

Full list of capabilities
-------------------------
Depending on the permissions configuration, users can only see the components they are allowed to see. The full list of components is shown below.
Permissions can be configured in `Authorization Settings <../getting-started/settings.html#authorization-settings>`_

Events
^^^^^^
#. Detailed overview.
#. Change event and ticket inventory.
#. Change dates.
#. Change various setting flags.
#. Synchronise parts of an event with another event.
#. Show scan information and configuration QR code for the :doc:`FE Scanner App <scan>`.
#. Detailed information about tickets sold.
#. Detailed information on scanning tickets in progress.

Orders
^^^^^^
#. Detailed overview of the order.
#. Search across all orders.
#. Email the order.
#. Change the name and email address of the order.
#. Share tickets using Android Sharing.
#. Remove tickets.
#. Create tickets.
#. Remove an order.
#. Refund and order.
#. Add new orders.

Tools
^^^^^
#. Sales dashboard.
#. Export orders to Excel format.
#. Export tickets to Excel format.
#. Scan a ticket to see its details. This is an informational scan only.
#. Add, modify and delete input fields.
#. Add, modify and delete ticket types.
#. Upload new ticket PDF template.
#. Configure the :doc:`FE Payment App <payment>`.

The App is available for Android 8.0 and above. The IOS version is currently not available.

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
The ``three dots`` on the right of a an event or order can be pressed to display a context menu. See example screenshot.

In the orders tab you to quickly search for an order. Just start typing and the result will be displayed.
Searches are performed on all fields except the number of tickets and amount.

.. list-table::

    * - .. image:: ../_static/images/apps/Admin-login.png
           :target: ../_static/images/apps/Admin-login.png
           :alt: FE Admin login
      - .. image:: ../_static/images/apps/Admin-events.png
           :target: ../_static/images/apps/Admin-events.png
           :alt: Events overview
      - .. image:: ../_static/images/apps/Admin-add-order.png
           :target: ../_static/images/apps/Admin-add-order.png
           :alt: Add a new order

.. list-table::

    * - .. image:: ../_static/images/apps/Admin-order-details.png
           :target: ../_static/images/apps/Admin-order-details.png
           :alt: Show order details
      - .. image:: ../_static/images/apps/Admin-scan-keys.png
           :target: ../_static/images/apps/Admin-scan-keys.png
           :alt: Overview scan keys
      - .. image:: ../_static/images/apps/Admin-tools.png
           :target: ../_static/images/apps/Admin-tools.png
           :alt: Tools

