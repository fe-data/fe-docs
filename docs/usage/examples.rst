Examples
========
Some examples of how fast events can be used. You may use them as an example for your own music event, festival, sports event, bicycle tour, …

We will be using our Vinyl Open Air festival and a boattrip on a lake as examples. We wont be setting dates in our examples.
And of course we assume you create your own pdf etickets, emails, ..
You could also add a seatingplan to the '*Boattrip*' examples.

Single ticket
^^^^^^^^^^^^^
The most basic event. A single day for for our boattrip and we have a fairly large boat that can accommodate 500 passengers.
Create a single event and define a single ticket with a price, a single scan-code and set stock to 500 at the event-level in the `Basics tab <events.html#basics-tab>`_.

Multiple tickets
^^^^^^^^^^^^^^^^
Pretty much the same as the first one, except you define 2 different ticket types.
One for adults and one for children with a different price.
You can use the same single scan code for both tickets and scan the tickets once the participants board the vessel.
If you want to limit the number of children to for instance 100, enter 100 in the :guilabel:`stock` field of the children-ticket in the `ticket tab <events.html#tickets-tab>`_.

Multiple days (same route)
^^^^^^^^^^^^^^^^^^^^^^^^^^
The boat trip is done on 2 consecutive days with the exact same route.
Define 2 events and group them together. Make sure you set the group-type to :guilabel:`Single select group`.
The fastest method is to create first a single event and define all fields, including the event group.
Then duplicate the event and the only thing you need to change is a few dates: obviously the event-date and the dates when you sell tickets.

Make sure you use the :guilabel:`group` attribute in the shortcode on the ordering page.
And use for the shortcode on the order-page something like ``[fast_events group="boat"]``.

Multiple days (different routes)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A small variation on the previous example.
You still need to define two events a pull them together in a group, but this time the group type is :guilabel:`Multiple select group`.
Which means customers can either book 1 day or both days.

Multiple days (Passe-partout)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Exactly the same as the previous one.
You just add a third event to the group and change the group-type for this event to :guilabel:`Passe-partout` and of course change the price.
You have to define a separate ordering page for the pass-partout though. If someone buys a pass-partout he gets 2 tickets, one for every day.

Mind you the shortcode for the order-page is ``[fast_events id=22]``, where *22* is the event id and don' forget to set the :guilabel:`group` attribute.

Single day (football club)
^^^^^^^^^^^^^^^^^^^^^^^^^^
Everybody can order, but you have an agreement with the local football club who can buy 100 tickets against a reduced rate.
There are 200 members. Create a new separate event and make sure you set the :guilabel:`User groups` flag.
Create an Excel sheet with 3 columns (Name, Emailadress, Number of tickets ) for the 200 members and export it as
csv-file and use it in the `Groups - tab <events.html#groups-tab>`_ under :guilabel:`Upload csv file`.
You set the number of tickets in the excel sheet to the maximum number of tickets allowed in a single order.
Set the stock for this event to 100 and the connected event-id to the general event-id of the event where everybody can buy tickets.
It may be smart to also set the :guilabel:`Unique users` flag, so football club members can only place a single order.
Create a separate order page for the football club.

Movie night at the community center
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Access to the movie night is free, but people need to reserve a seat before they can attend.
Define an event with a single free (0.00 amount) ticket and count this ticket.
Create a seating configuration that matches the number of available tickets.
As prankster may flood your event with bogus reservations you should work with confirmation emails and to make it even
more strict you can combine this with selling to a closed user group (=members of the community center).
Define an email on the `Email tab <events.html#email-tab>`_ and use the ``{%CONFIRM%}`` tag.
If the purchaser presses the confirm link, they will receive the email defined in the `Confirmation email tab <events.html#confirmation-email-tab>`_.
Only then is the reservation final. Make sure you set the :guilabel:`Confirmation emails` and :guilabel:`Confirmation timeout` in the `Basics tab <events.html#basics-tab>`_.
The timeout is in minutes, which means if the orderer does not press the confirm link for x minutes, the reservation will be deleted.
If you work with closed user groups to allow only community center members to place orders, you should set the :guilabel:`Groups` check box on the `Basics tab <events.html#basics-tab>`_
and use, for example a `csv upload <events.html#upload-a-csv-file>`_ to limit the access. And ofcourse you should scan the etickets at the entrance.

DJ Festival with backstage tickets
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Create a single event and two tickets types: ``Silver`` tickets for general admission and ``Gold (Backstage)`` tickets.
Make sure you have different scan-keys and specify which tickets can be scanned for backstage access. See `Scan tab <events.html#scan-tab>`_ for an example.

Mountainbike tour (Multiple locations and multiple timeslots)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Depending on the number of locations and the number of timeslots you have different options:

#. Use a single event and name your tickets **Location-id__Timeslot** Eg. "*Start-A_09:00*", "*Start-A_10.00*", "Start-B_09:00*", ...
   This is the most simple solution, but if the numbers increase the order form becomes very huge and hence not very customer friendly.
   Another disadvantage of this approach is that the content of the email the user receives is the same for all locations.
#. Create an event per location and the ticket types are the various timeslots.
   Tie them together in a single select group and give the group a name.
   You will need a single order page, where the customer first selects the location in a dropdown menu and then orders the tickets for a timeslot or multiple timeslots.
   Or ofcourse the other way around is also possible: an event per timeslot and the tickets per location. Now the customer first selects the timeslot and then the location.
#. A static page with 2 buttons. On the buttons you show the timeslots and once pressed,
   you will be directed to the orderpage of that particular timeslot, which is a single event with the tickets per location.
   And also here you can do it the other way around. Show the locations on the static buttons and use the timeslots for the ticket types.

Sell drink coins
^^^^^^^^^^^^^^^^
You sell them in numbers of 5, 10 or 20 (or whatever you prefer).
Create 3 different events and a ‘*ticket*’ where the minimum to order = 1 and maximum = 1.
Create a single page on your website with the 3 references to the separate order pages.
Use for the “*Thank you*” page the ``[fe_download showimages="yes" downloadtext="Download eticket for drinkcoins"]`` shortcode somewhere on the page.
After payment he customer will be redirected to the thank you page which includes the qrcode which he can show at the counter to receive the coins.

An alternative is to make 1 event and three ticket types (5 coins, 10 coins and 20 coins)

Collect contributions at home from members
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
If you install Fast Event it comes pre-configured with settings for instant payments.
See :doc:`Settings-page <../getting-started/settings>`. Install the :doc:`Payment App <../apps/payment>` on your phone and configure it.
You can now show your members a qrcode which can be scanned to make the payment. Dutch and Belgium bank apps can scan the qrcode directly from the bank app.

Bicycle tour with checkpoints and detailed “Thank you” email
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
This is a bicycle tour of 60km. At the start (*entry scan, level 0*) participants get the detailed route.
There are 5 checkpoints spread across the route (*staged scan, level 1*).
Another scan is made at the end (exit scan, level 9) of the route.
When the participants have passed all checkpoints they will receive a nice medal and they will also receive an email with all the details of what time they have passed the checkpoints.

Defining this event is pretty straightforward. A single event with an entry scan, 5 level-1 scans and an exit scan.
To get the “*Thank you*” email with the detailed info, you have to create a snippet on the :doc:`fast_events_scan_ticket <../hooks/scan_ticket>` filter.
Have a look at the `detailed example <../hooks/scan_ticket.html#send-thank-you-email-with-detailed-scan-info>`_.

You can easily check whether the participant has passed all checkpoints with the :guilabel:`info` button in the :doc:`scan app <../apps/scan>`.

You can take your cycling to the next level by optionally using the `FE Tracking App <https://fe-tracking.fast-events.eu/>`_ for users who want it.
Or even configure the use of :doc:`Firebase <../advanced/firebase>` to use realtime track updates and realtime messages from the event organization.

Ship a signed photo book
^^^^^^^^^^^^^^^^^^^^^^^^
All visitors of the Open Air DJ Festival can buy a signed photo.
Although *Fast Event* is not a full-blown webshop, you can easily ship a single item (photo book) to customers if it’s occasionally.
No need to install complex webshop-plugins, just use ‘Fast Events’.

One of our Dutch beta customers has used this feature. See the :doc:`fast_event_custom_status <../hooks/custom_status>` function for examples.

As only visitors of the DJ Festival can order the photo book, you first need to export the order list and remove all the fields in the Excel sheet, except the name and emailaddress.
Add a third column with the number of photo books a customer can buy in a single order.
Create a new event and upload the CSV-file in the `Groups tab <events.html#groups-tab>`_ and make sure you set
the :guilabel:`Groups` flag and :guilabel:`Unique users` flag in the `Basics tab <events.html#basics-tab>`_.
For shipping you will need extra address fields (Street, zipcode, city, …), add them in the `Input tab <events.html#input-tab>`_.
You define the photo album as ticket in the ‘Tickets – tab‘. Set the min. and max. to 1, or whatever is allowed.

Make sure you have set the :guilabel:`Custom statuses` setting in the plugin settings. Fi you could use ``processing,shipped``.
Use the :doc:`fast_events-custom_status <../hooks/custom_status>` filter to create a snippet.

If you study the example you will see that the customer gets an email as soon as we start processing the order.
You can do that by accessing the order and choose :guilabel:`Custom status` in the contextmenu.
For shipping, the beta customer was using `MyParcel <https://www.myparcel.nl/>`_ to create shipping-labels and installed
the `Chrome-extension <https://www.myparcel.nl/koppelingen/google-chrome-extensie/>`_ they offer.
By carefully crafting the message in the filter for the ``shipped`` custom status, you can generate output that can be
easily linked to the extension to print a shipment label with just a few clicks. MyParcel will email the customer automatically the trackingcode.
