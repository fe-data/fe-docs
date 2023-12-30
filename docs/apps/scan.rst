Scan App
========
Check in visitors easily with our Android or IOS App; no need to use (expensive) scanning terminals.
The App is available for Android 9.0 and later and IOS 14.0 and later.
    
.. list-table::

    * - .. image:: ../_static/images/apps/Scan-Android.png
           :scale: 50%
           :target: https://play.google.com/store/apps/details?id=nl.fe_data.scanner  
      - .. image:: ../_static/images/apps/Scan-IOS.png
           :scale: 50%
           :target: https://apps.apple.com/app/fe-scan/id1496549803
   
Configuration
-------------

Add/edit checkpoints
^^^^^^^^^^^^^^^^^^^^
There are 3 possibilities to configure the app:

1. Manual configuration
2. Scan a configuration qrcode
3. Scan the configuration qrcode from an image file.

.. list-table::

    * - .. image:: ../_static/images/apps/Scan-checkpoints.png
           :target: ../_static/images/apps/Scan-checkpoints.png
           :alt: Checkpoints overview
      - .. image:: ../_static/images/apps/Scan-edit.png
           :target: ../_static/images/apps/Scan-edit.png
           :alt: Add/edit checkpoint
      - .. image:: ../_static/images/apps/Scan-settings.png
           :target: ../_static/images/apps/Scan-settings.png
           :alt: Edit settings

Adding or changing checkpoints is the first menu item in the navigation drawer (top left).
You can add a new checkpoint by pressing the new checkpoint button (bottom right) or change an existing checkpoint by pressing the pencil button.
The easiest way to configure the App is to scan a configuration qrcode,
which can be copied from the ``Qrcode`` popupmenu item in the `Scan keys <../usage/events.html#scan-keys>`_ overview when changing an event.
Pressing the qrcode button (top right) in the add/edit checkpoint gives you the option to
to scan a configuration QRcode with the camera or to scan a configuration QRcode from an image file.

**Server URL**
    The URL where you have installed WordPress. For example ``https://exampledomain.com``. Only secure connections (https) are allowed.
**API Key**
    The ``Scan key`` as defined in the `Scan keys overview <../usage/events.html#scan-keys>`_.

Settings
^^^^^^^^
The Settings menu is located in the navigation drawer (top left icon).

**Autoclose timeout**
    Normally you will need to press :guilabel:`Continue` after each scan to start a new scan.
    You can also set the dialogue box to close automatically.
    If you enter :guilabel:`1000` here, the dialogue box will close after 1 second and the :guilabel:`Continue` button will not be displayed.
    This allows you to operate the phone with one hand.
    However, if a scan is invalid, manual intervention is required and the :guilabel:`Continue` button will be displayed.
**Duplicates timer**
    If a qrcode is scanned within this time window, the qrcode will be ignored. 1000 equals to 1 second.
    
Usage
-----
One of the advantages of using QR codes is that it doesn't matter how the QR code is presented to you - upside down, diagonally - it will always deliver a scan.

If the scan is valid, a green bar will appear and the phone will make a short beep.
If the QR code has already been scanned, a red bar will appear along with the date and location where the ticket was previously scanned.
The phone will not make a sound, but will vibrate.

.. list-table::

    * - .. image:: ../_static/images/apps/Scan-ok.png
           :target: ../_static/images/apps/Scan-ok.png
           :alt: Scan Ok
      - .. image:: ../_static/images/apps/Scan-wrong.png
           :target: ../_static/images/apps/Scan-wrong.png
           :alt: Scan wrong
      - .. image:: ../_static/images/apps/Scan-info.png
           :target: ../_static/images/apps/Scan-info.png
           :alt: Scan info
           
   
You can scan one step at a time.
For example: you can only scan the ‘*Gold (Backstage)*‘ ticket at the backstage entrance if it has already been scanned at the main entrance.
This requires a different ``Scan key`` at the main entrance and the backstage entrances.
See this `screenshot <../usage/events.html#scan-keys>`_.
The first entry will scan all tickets at the Main Entrance and the second entry will scan only ‘*Gold (Backstage)*‘ tickets at the Backstage Entrance.
If the ‘*Gold (Backstage)*‘ ticket is first presented at the Backstage Entrance first, it will result in an invalid scan as it has not been scanned at the Main Entrance.

You can get an overview of all scans after a valid or invalid scan by pressing the info button (bottom right).
This can be useful, for example, if you are organising a cycle race (or any other event) where participants pass through several checkpoints along the route, where their ticket is scanned.
At the end (finish), the participants receive a medal if they have passed all the checkpoints. You can easily check this with the info button after an exit scan.

If for some reason the scanner can't read the QR code, you can enter the Ticket ID manually as a fallback.
Press the tripe-dots-button (top right) and choose :guilabel:`Enter qrcode` to enter the Ticket ID (found under the QR code) and press :guilabel:`OK`.

