Firebase
========
If your event is a sporting event and uses tracks then the *FE Tracking* App can be used, as described in the `tracking tab <../usage/events.html#tracking-tab>`_.

However, you can go one step further with your event by providing real-time track updates real-time news messages from the event organizer to the users of the *FE Tracking* App.
It is also possible to give users the option of sharing their track in real time with family and friends as they travel it. These features require *FE Tracking v1.3 or higher*.
The benefits for users of the *FE Tracking* App are:

#. Always the right track
#. If the organisation updates the Info screen in the *FE Tracking* App, this is also immediately available
#. News messages from the event organisation are immediately available and can be played via Text-To-Speech while the App is recording the track in the background.
   Of course, this only works if you are wearing a (Bluetooth) headset when, for example, you have the phone in a bracelet.
#. Family and friends can see where the participant is on the track, how far they have travelled, average speed, distance/time to the next checkpoint or service station, ...

----

Firebase video
--------------
To enable these features, you need a Google account. Below is a video explaining how to configure Firebase every step of the way. Usually everything can be configured within 5 minutes.
Below the video you can see exactly which steps are taken and what needs to be filled in.
It starts by going to `https://console.firebase.google.com <https://console.firebase.google.com>`_.


.. raw:: html

   <div style="padding:66.33% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/597044471?title=0&byline=0&portrait=0" style="position:absolute;top:0;left:0;width:100%;height:100%;" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>

----

Video time-index
^^^^^^^^^^^^^^^^

**0:02**
   Enter the name of the project. Any name will do. Press :guilabel:`Continue`.
**0:09**
   Disable ``Enable Google Analytics for this project``. Press :guilabel:`Continue`.
**00:37**
   Press the :guilabel:`Authentication` in the left sidebar. Press :guilabel:`Get started`.
**00:46**
   Press the :guilabel:`Sign-in method` tab and choose the ``Email/Password`` pencil.
**00:49**
   Enable the first switch and choose :guilabel:`Save`.
**0:52**
   Press :guilabel:`Firestore Database` in the left sidebar. Press :guilabel:`Create database`.
**0:58**
   Press :guilabel:`Next` in the popup window
**1:05**
   Choose a ``Cloud Firestore location`` that is closest to you and press :guilabel:`Enable`.
**1:35**
   Choose the :guilabel:`Rules` tab and replace it with the code below and press :guilabel:`Publish`.

   .. sourcecode:: text
      :linenos:

      rules_version = '2';
      service cloud.firestore {
        match /databases/{database}/documents {

          function isValid() {
              return request.auth != null && request.auth.token.ticket;
          }

          function isShareReader() {
              return request.auth != null && request.auth.token.sharing;
          }

          match /news/{message} {
            allow read: if isValid();
            allow write: if false;
          }

          match /tracks/{track} {
              allow read: if isValid() || isShareReader();
            allow list: if false;
            allow write: if false;
          }

          match /tickets/{ticket} {
              allow read: if isValid();
            allow list: if false;
            allow write: if false;
          }

          match /shares/{share} {
              match /locations/{location} {
              allow read: if isShareReader() && request.auth.token.share_id == share;
              allow write: if isValid() && request.auth.token.share_id == share;
            }
          }

        }
      }

**1:52**
   Press the cog-wheel in ``Project Overview`` in the left sidebar and choose :guilabel:`Project settings`.
**1:54**
   Choose the ``IOS`` button at the bottom of the screen. Use **nl.fe-data.tracking** for the ``IOS bundle id``,
   use **FE Tracking (IOS)** for the ``App nickname`` and **1574304676** for the ``App Store ID``. Register the App and download the file.
   Press :guilabel:`Next` for the following steps and finally :guilabel:`Continue to console`.
**2:29**
   Choose the :guilabel:`Add app` button at the bottom of the screen. Choose ``Android`` in the popup window.
**2:34**
   Use **nl.fe_data.tracking** for the ``Android package name`` and  use **FE Tracking (Android)** for the ``App nickname``.
   Register the App and download the file. Press :guilabel:`Next` for the following steps and finally :guilabel:`Continue to console`.
**3:02**
   Choose the :guilabel:`Service accounts` tab at the top of the screen. Now press the :guilabel:`Generate new private key` and
   :guilabel:`Generate key` to download the service-account file.

Firebase event fields
^^^^^^^^^^^^^^^^^^^^^
.. list-table::

    * - .. image:: ../_static/images/usage/Event-tracking-firebase.png
           :target: ../_static/images/usage/Event-tracking-firebase.png
           :alt: Firebase fields

Now upload all 3 files you have downloaded in the video to there corresponding elements.

Remaining fields
^^^^^^^^^^^^^^^^
**Location sharing**
   If switched on the users of the FE Tracking App(> v1.3) can share the track while it is recording, so family and friend stay up to date where they are on the track.
**Maximum shares**
   Is the maximum number of times the share can be used. Mind you: If someone uses the share and immediately discards it and then reinstalls it, this counts as 1 more.
**Minutes trigger**
   If this parameter and the ``Distance trigger`` are both ``0``. Every location update is instantly shared with all share users. This is realtime.
   If this parameter is greater than 0, it means that all location updates are collected until the time expires.
   This only happens at the next location update, so it is not an exact number of minutes. People using the share will then receive a burst of location updates.
**Distance trigger**
   Pretty much the same as the ``Minutes trigger`` only this time updates are collected until the user travelled a distance greater that this parameter.
   Mind you: if this parameter is not zero or the other one is not zero, they must bothe be set to a non-zero value.
   During tracking and when sharing is on, a new burst of location updates is sent to the shares if either the distance has been exceeded or the time has been exceeded.
   When the burst is performed, the distance measurement is restarted from zero and the minute trigger is also restarted from zero.
   When the user stop tracking any leftover location updates are flushed to the shares.

Finally ``Save`` the event.

----

Messages screen
---------------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-tracking-messages.png
           :target: ../_static/images/usage/Event-tracking-messages.png
           :alt: Firebase messages

Once you have defined the ``Basics`` and ``Firebase`` tab for tracking, you can send messages to all users of the *FE Tracking* App who have
scanned a ticket from this event.

Use :guilabel:`List messages` to show the messages that have been sent so far. :guilabel:`New messages` is used to send a new message.
If you have several tracks, you can limit the message to the tracks you select. By default the message goes to all tracks.

----

Costs
-----
Firebase has a very generous free tier where all usage is free. Even better the free quota is per day!
See `https://cloud.google.com/firestore/pricing <https://cloud.google.com/firestore/pricing>`_.

You can do the math by your self with your own event. For every ticket sold a ``write`` and a ``read`` is done if(!) the user uses the *FE Tracking* App for the ticket.
If you use news messages there is a ``read`` for every messages.

Example 1000 tickets
^^^^^^^^^^^^^^^^^^^^
Suppose we have an event which sold 1000 tickets and during the event we send 10 messages. Furthermore we assume everybody is using the *FE Tracking* App.
Total ``writes``: 1000 (tickets) + 10 (news messages) and total ``reads``: 1000 (tickets) + 10.000 (10 news messages per tickets). As you can see this is well below
the daily free quota. Ofcourse it could be a bit more if users delete the track in the App and re-install it, or if you delete an order or tickets(s) from *Fast Events*.
There are a few more writes as wel for managing the tracks, but they are limited.

So in this case the free plan suits your needs.

Example 20.000 tickets
^^^^^^^^^^^^^^^^^^^^^^
We have sold 20.000 tickets and send 20 messages during the day and everybody is using the *FE Tracking* App.

Total ``writes``: 20.000 (tickets) + 20 (news messages) and total ``reads``: 20.000 (tickets) + 400.000 ( 20 news messages per ticket).

As you can see for this case the free plan won't do the trick, you have to upgrade to the ``Blaze plan`` (Pay as you go) and provide your payments details.
But if you do the actual math you will find out that the actual charge is very minimal. In this case you will be charged for 400.000 - 50.000 (daily free quota) = 350.000 ``reads``
and a few extra writes (20.000 free per day). At the end the invoice will be less than 1 Euro.

Location sharing
^^^^^^^^^^^^^^^^
If you enable location sharing it is crucial to understand how this impacts your read and write bundles. Suppose you have an event with 1000 participants and a 10 km walking track.
You have enabled ``Location sharing`` and both ``Minutes trigger`` and ``Distance trigger`` are **0** and you allow a maximum of 2 shares.
This would mean that every location update triggers 1 write and 2 reads. Based on a ``Distance filter`` of 25m it means the number of writes would be 400 and the number of reads 800 ( # shares * 400).
As you know the ``Distance filter`` is elastic. The faster you go the longer the distance becomes. So the numbers are most likely smaller.
For the whole event this boils down to ~400.000 writes and ~800.000 reads. Still a very small amount of money.

.. warning::
   The battery consumption with these settings is obviously more than with a ``Distance trigger`` or an update of, for example, once every 3 minutes.

But you can save on the costs by for instance setting the ``Distance trigger`` to 200m and the ``Minutes trigger`` to 1 minute. Remember it is never exactly 200m.
It means that when the next location update comes in and the new distance is greater than or equal to 200m that the location updates are shared in bulk with the shares.
The math then becomes (worst case): 10.000m/200m = 50 writes en 100 reads.

.. note::
   **No rights can be derived from these examples and amounts.** They are only an indication in a theoretical situation.
   To help avoid unexpected charges on your bill, set monthly budgets and alerts.
   To set a budget, go to the `Billing <https://console.cloud.google.com/billing/>`_ section in the Google Cloud Console and create a budget for your Cloud Billing account.
   You can use the default alert settings or modify the alerts to send notifications at different percentages of your monthly budget.

----

Do's and Don't
--------------
#. Always first define the whole event, including the ``Basics`` tab of the `Tracking tab <../usage/events.html#tracking-tab>`_ and ``Save`` the event before you start with Firebase.
#. Do not download new IOS and Android files from the Firebase Console if you already sold tickets.
   If you do, all users that already downloaded the ticket in the *FE Tracking* App will loose access and have to download the ticket again.
#. If the event is finished and you want to delete everything, you first have to disable ``Tracking`` in the `Basics tab <../usage/events.html#basics-tab>`_.
   Then all tickets, orders and the event can be deleted. In the Firebase Console you need to select ``Project settings`` and at the bottom select :guilabel:`Delete project`.
#. Be extremely careful when moving the location of checkpoints on the track. Although the update takes place immediately,
   it is of course possible that a phone has no coverage and does not receive the update or receives it too late.
   And in that case, the finish qrcode will not be shown, as there is a checkpoint missing.
   It is always better to remove the checkpoint in such cases.
