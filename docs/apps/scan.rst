Scan App
========
Check in visitors easily with our Android or IOS App; no need to use (expensive) scanning terminals.
The App is available for Android 7.0 and later and IOS 13.0 and later.
    
.. list-table::

    * - .. image:: ../_static/images/apps/Scan-Android.png
           :scale: 50%
           :target: https://play.google.com/store/apps/details?id=nl.fe_data.scanner  
      - .. image:: ../_static/images/apps/Scan-IOS.png
           :scale: 50%
           :target: https://apps.apple.com/app/fe-scan/id1496549803
   
Configuration
-------------
There are 3 possibilities to configure the app:

1. Manual configuration
2. Scan a configuration qrcode
3. Send users the configuration qrcode as an attachment via email. The user can then select the qrocde and share it with the Scan app.

The easiest way to configure the app is by scanning a configuration qrcode that can be copied from the `Scan  tab <../usage/events.html#scan-tab>`_ when changing an event. Use the settings-button (top-right) and subsequently press the qrcode-button (bottom-right) in the settings screen. It is also possible to share a configuration qrcode from email apps with the Scan app.

**Server URL**
    The URL where you have installed WordPress. For example ``https://exampledomain.com``. Only secure connections (https) are allowed.
**API Key**
    The ``Scan key`` as defined in the `Scan  tab <../usage/events.html#scan-tab>`_.
**Autoclose timeout**
    Normally after each scan you have to press :guilabel:`Continue` to do a new scan.
    But you can also let the dialog close automatically. If you enter here :guilabel:`1000`,
    the dialog will close after 1 second and the :guilabel:`Continue` button is not shown.
    This way you can operate the phone single handed. Still, if a scan is invalid, it requires manual action and the :guilabel:`Continue` button wil be shown.
    
Usage
-----
One of the benefits of using qrcodes, is that it doesn't matter how the qrcode is presented to you, upside down, slanted, it will always deliver a scan.

If the scan is valid a green bar will be shown and the phone will sound a short beep.
If the qrcode was already scanned, a red bar will be shown together with the date and location where the eticket was scanned before.
The phone will not make a sound but instead it will vibrate.

.. list-table::

    * - .. image:: ../_static/images/apps/Scan-ok.jpg
           :target: ../_static/images/apps/Scan-ok.jpg
           :alt: Scan Ok
      - .. image:: ../_static/images/apps/Scan-wrong.jpg
           :target: ../_static/images/apps/Scan-wrong.jpg
           :alt: Scan wrong
      - .. image:: ../_static/images/apps/Scan-info.jpg
           :target: ../_static/images/apps/Scan-info.jpg
           :alt: Scan info
           
   
You can make a step-by-step scan. For example: you can only scan the ‘*Gold (Backstage)*‘ ticket at the backstage entrance if it has been scanned at the main entrance first. It requires a different ``Scan key`` at the main entrance and backstage entrance. See the screenshot in the `Scan  tab <../usage/events.html#scan-tab>`_. The first entry scans all tickets at the main entrance and the second entry only scans ‘*Gold (Backstage)*‘ tickets at the backstage entrance.
If the ‘*Gold (Backstage)*‘ ticket is first presented at the backstage entrance, it will result in an invalid scan because it was not scanned at the main entrance.

You can get an overview of all scans after a valid scan or invalid scan by pressing the info-button (bottom-right). This can be useful if, for example, you have a bicycle tour (or whatever event) where the participants pass several checkpoints during the tour, where their ticket is scanned. At the end (finish), the participants receive a medal when they passed all checkpoints. You can easily check this with the info-button after an exit-scan.

If the scanner can’t read the qrcode for whatever reason, you have as fallback scenario the option to enter the ticket id manually. Press the pencil-button (top-bar), enter the ticket id (which is below the qrcode) and press :guilabel:`OK`.

