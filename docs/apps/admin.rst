FE Admin App
============
With the FE Admin app you can quickly view the details of events and orders on your mobile. It is also possible to resend orders by email, or to refund an order amount, delete and re-create tickets for an order or even create new orders.

FE Admin can also support you to help configure users’ :doc:`FE Scanner App <scan>` or :doc:`FE Payment App <payment>`.

There is also quick insight into the number of tickets sold or the number of tickets that have been scanned at the different locations. Or change the stock and window of selling tickets.

The App is available for Android 7.0 and later. The IOS version is not available at the moment.

.. image:: ../_static/images/apps/Admin-Android.png
   :target: https://play.google.com/store/apps/details?id=nl.fe_data.admin
   :alt: FE Admin App
   :scale: 50%
   
Settings
--------
First make sure you have configured the ``Settings for the FE Admin app`` in the `settings <../getting-started/settings.html#settings-for-the-fe-admin-app>`_ of the plugin.

You can share the qrcode on the settings page of the plugin with the App to configure the :guilabel:`Server URL` and :guilabel:`API Key` parameters. Email the configuration qrcode as an attachment to the user, which can than be shared with the App to configure it. Still the other parameters have be configured manually.

Users of the App need an account in the WordPress environment. If the user doesn't have the role of '*admin*', you have to make sure to authorize the use in the `Authorization settings <../getting-started/settings.html#authorization-settings>`_.

Usage
-----
The way the App works is pretty straight forward. You can use the bottom buttons to switch between orders, events and configuring the Payment App. In the orders and events tab you can swipe down to refresh the content. The ``three dots`` on the right of a an event or order can be pushed to show a context menu. See example screenshot.

In the orders tab you can quickly search an order. Just start typing and the result will be shown. Searching is done on all fields except the number of tickets and amount.

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
      - .. image:: ../_static/images/apps/Admin-edit-scan.png
           :target: ../_static/images/apps/Admin-edit-scan.png
           :alt: Edit scan key

