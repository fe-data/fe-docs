Payment App
===========
If you want to receive mobile online payments quickly and securely with, for example, mobile ticket sales, collecting a contribution at home from members, etc., use the “*FE Payment*” app.
No need to rent expensive payment terminals anymore. The app shows the user a qrcode that can be scanned with the camera. Dutch and Belgium banking apps can scan this qrcode directly in the bank app.

The App is available for Android 7.0 and later and IOS 13.0 and later.

.. list-table::

    * - .. image:: ../_static/images/apps/Payment-Android.png
           :scale: 50%
           :target: https://play.google.com/store/apps/details?id=nl.fe_data.ideal  
      - .. image:: ../_static/images/apps/Payment-IOS.png
           :scale: 50%
           :target: https://apps.apple.com/app/fe-payment/id1496549728
   
Settings
--------
First make sure you have configured the ``Settings for online payments`` in the `settings <../getting-started/settings.html#settings-for-instant-payments>`_ of the plugin.

You can share the qrcode on the settings page of the plugin with the App to configure the :guilabel:`Server URL` and :guilabel:`API Key` parameters.
Email the configuration qrcode as an attachment to the user, which can than be shared with the App to configure it.

Of course, you can also scan the configuration qrcode with the App by pressing the qrcode symbol in the settings screen.
The :guilabel:`Server URL` and :guilabel:`API Key` are then filled in automatically.

Still the other parameters have be configured manually.

Here are the settings of the app:

**User**
    The username or emailaddress of the WordPress user.

    .. warning:: Do **not** use admin users.

**Password**
    The ``application password``. Mind you, this is not the user password. By using application passwords (as of WordPress 5.6) you have a great deal of flexibility.
    You can either create 1 WordPress user and use a single application password or an application password per client. But you can also create a WordPress user for each client with an application password.
    In WordPress you can then easily revoke the rights per client. The API KEY can be used as a kind of kill switch. By changing this, all clients will be blocked.

    Don't forget to give the WordPress user the right permissions in the `authorization settings <../getting-started/settings.html#authorization-settings>`_. To use this app you have to add the ``pay_app`` controller.
**Server URL**
    The URL where you WordPress install lives. Eg. ``https://yourdomain.com``
**API Key**
    The secret key that is configured in the plugin settings.
**Description**
    A default description used for the payment.
**Payment type**
    You have 3 possible options:
    
    - **Netherlands (iDEAL)** -> use this in the Netherlands. All Dutch banking apps can scan qrcodes directly.
    - **Belgium (Bancontact)** -> use this in the Belgium for Bancontact customers.
    - **Other** -> The app generates a general qrcode that can be scanned by a camera or scan app to make the payment
    
Still, for every individual payment you can change the :guilabel:`Description` and :guilabel:`Payment type`.

Making a payment
----------------
Fill in the amount and optional change the ``Description`` and/or ``Payment type`` and press :guilabel:`GET QRCODE`. The next screen pops up and let the user scan the qrcode. If the user has payed and has landed on the “*Thank you*”-page of your website, press :guilabel:`CHECK PAYMENT STATUS`. If the payment succeeded, the screen will turn green and a beep will sound. If the payment is not confirmed (yet), the phone will vibrate.

If the customer cannot scan the qrcode, there is still a possibility to share the payment link via the share button (top right) via eg WhatsApp or another application.

.. list-table::

    * - .. image:: ../_static/images/apps/Payment-entry.png
           :target: ../_static/images/apps/Payment-entry.png
           :alt: New payment
      - .. image:: ../_static/images/apps/Payment-qrcode.png
           :target: ../_static/images/apps/Payment-qrcode.png
           :alt: Payment qrcode
      - .. image:: ../_static/images/apps/Payment-check.png
           :target: ../_static/images/apps/Payment-check.png
           :alt: Check payment

