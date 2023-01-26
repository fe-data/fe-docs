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
3. Send the configuration QR code to the user as an email attachment. The user can then select the QR code and share it with the Scan application.

The easiest way to configure the app is to scan a configuration qrcode that can be copied from the `Scan  tab <../usage/events.html#scan-tab>`_ when changing an event.
Use the Settings button (top right) and then press the QR Code button (bottom right) in the Settings screen.
It is also possible to share a configuration qrcode from email applications with the Scan application.

**Server URL**
    The URL where you have installed WordPress. For example ``https://exampledomain.com``. Only secure connections (https) are allowed.
**API Key**
    The ``Scan key`` as defined in the `Scan  tab <../usage/events.html#scan-tab>`_.
**Autoclose timeout**
    Normally you will need to press :guilabel:`Continue` after each scan to start a new scan.
    You can also let the dialogue box close automatically.
    If you enter :guilabel:`1000` here, the dialogue will close after 1 second and the :guilabel:`Continue` button will not be displayed.
    This allows you to operate the phone with one hand. However, if a scan is invalid, it will require manual action and the :guilabel:`Continue` button will be displayed.
    
Usage
-----
One of the advantages of using QR codes is that it doesn't matter how the QR code is presented to you, upside down, diagonally, it will always deliver a scan.

If the scan is valid, a green bar will appear and the phone will make a short beep.
If the QR code has already been scanned, a red bar is displayed, together with the date and location where the ticket was previously scanned.
The phone will not make a sound, but will vibrate.

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
           
   
You can scan a step by step. For example: you can only scan the ‘*Gold (Backstage)*‘ ticket at the backstage entrance if it has already been scanned at the main entrance.
It requires a different ``Scan key`` at the main entrance and the backstage entrance. See the screenshot in the `Scan  tab <../usage/events.html#scan-tab>`_.
The first entry will scan all tickets at the Main Entrance and the second entry will scan only ‘*Gold (Backstage)*‘ tickets at the Backstage Entrance.
If the ‘*Gold (Backstage)*‘ ticket is first presented at the Backstage Entrance first, it will result in an invalid scan as it has not been scanned at the Main Entrance.

You can get an overview of all scans after a valid or invalid scan by pressing the info button (bottom right).
This can be useful, for example, if you are organising a cycle race (or any other event) where participants pass through several checkpoints along the route, where their ticket is scanned.
At the end (finish), the participants receive a medal if they have passed all the checkpoints. You can easily check this with the info button after an exit scan.

If the scanner can't read the QR code for whatever reason, you can enter the ticket ID manually as a fallback.
Press the pencil-button (top-bar), enter the ticket id (found under the QR code) and press :guilabel:`OK`.

