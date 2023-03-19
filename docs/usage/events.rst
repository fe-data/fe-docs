Events
======

Events overview
---------------
.. list-table::

    * - .. image:: ../_static/images/usage/Events-overview.png
           :target: ../_static/images/usage/Events-overview.png
           :alt: Overview events

The top-left button bar has the following functionality:

- Hide/show columns in the table view.
- Export selected events. Select 1 or more events by using SHIFT or CTRL-keys and a mouse-click. In the popup-screen you can also select the associated media and pages. In this way you can prepare an event on 1 system, export it, and import it on another system.
- Import events. Selected the zip-file and choose if you wish to overwrite media and/or pages if present. Any URL's present in the zip-file from the exporting site will be replaced by the url relative to the importing site.
  Be careful with other people's zip files. Always check whether the URL's in the different parts of the event definition (emails, redirects, REST calls, ..) are valid.
- Add a new event. Most of the time it’s more convenient to use the ``Duplicate event`` in the context menu, rather than starting with an empty event.

There is a context-menu if you scroll through the orders; **use the right mouse-button** to make it visible and the chosen action is applied on the event where you did the right click.

**Edit event**
   In a popup window you can edit the event. It’s also possible to double-click on the event to edit it.
**Delete event**
   Deletion of the event. Keep in mind if you delete an event, also all associated orders, tickets and scan data will be deleted.
**Duplicate event**
   Duplicate an existing event. This can be quit handy for grouped events. You may already have created an event for day one and you need an event for day two. Just duplicate the “*day one*” event and change for instance the name and date of the duplicated event.
**Set sold to 0**
   Set the sold tickets to zero.
**Delete all orders an tickets**
   All related orders, tickets and scan data will be deleted.
**Bulk copy**
   If you need to change multiple events, first change a single event and edit the fields. Now select the target events. Left mouse-click the first one. If you want to select a whole range, press SHIFT and left mouse click or use CTRL and left mouse click to select individual targets. Once you have completed the selection, position the mouse above the event you have changed and right click to show the contextmenu and chose :guilabel:`Bulk copy`. A screen pops up and you can chose which fields you want to copy to the targets.
**Tickets sold**
   Show the stock and the number of tickets sold per ticket type. The menu selection is especially interesting if you have multiple ticket types.
**Map**
   Show track(s) on a map including checkin numbers for all checkpoints.

----

Basics tab
----------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-basics.png
           :target: ../_static/images/usage/Event-basics.png
           :alt: Event basics

The basics definition of the event.

**Event name**
   The name of the event (max. 50 characters). This description is used as the first line in the qrcode block.
**Available start/end date**
   The ticket sale takes place between these 2 dates. Click on the grayed date and click on the first date and next on the last date and click on :guilabel:`Close`.
**Stock**
   The number of tickets available for the event. If all tickets are sold, customers will see a sold out message. If you leave this blank or set to zero, there is no limit on the number of tickets to be sold.
**Connect stock event-id**
   Instead of counting the tickets sold for this event, the numbers are also deducted from the stock of another event. Take for example our boat trip example. There are 500 tickets available and they cost € 10,–. But senior citizens only pay € 4,– and you want to reserve 100 tickets for them. Define a separate event for senior citizens with stock set to 100 and let it point to the id of the main event. First it checks it’s own stock, if it’s not blank or ‘*0*’ and then it checks the linked stock.
   If you use linked events, the following stock checks are performed:

   #. The stock of the ticket type is checked, if you have defined stock.
   #. The stock at the event level is checked, if you have defined stock.
   #. The stock of the **linked event** is checked, if you have defined stock.
   #. The stock of the **ticket type of the linked event** is checked, if the ticket type matches one of the tickets of the linked event and if you have defined stock. Matching the tickets types is case sensitive.
**Send email**
   Send an email or not. Only makes sense to turn this off at a basic RSVP event or if you have added the shortcode for the download link in the “*Thank you*” page.
**Tickets**
   Use or not use tickets. Keep in mind that tickets are never sent, but always have to be downloaded with a link sent by email.
**Invoice**
   Use or not use invoices. Keep in mind that invoices are never sent, but always have to be downloaded with a link sent by email.
**Unique users**
   Users can only place 1 order per event. This can also be used across multiple events. See `Groups tab`_. The user is identified by the emailaddress.
**User groups**
   Only users who belong to a certain group can place orders. Works together with `Groups tab`_.
**ReCaptcha**
   Protect your order page against spam with `Google ReCaptcha <https://developers.google.com/recaptcha/>`_. Make sure you have set the keys in the `Settings <../getting-started/settings.html#recaptcha-settings>`_. *Fast Events* only supports ReCaptcha v2.
**Confirmation emails**
   Use this only with RSVP events or events with free tickets. The user must confirm via a link in an email whether he is present.
   The process flow is:
   
   #. User makes a booking on booking page
   #. User is redirected to the page you entered in the ``Redirect after booking`` input field
   #. User gets the email defined in the `Email tab`_.
   #. User clicks on the :guilabel:`Confirm` button in the email
   #. User is redirected to the page you entered in the :guilabel:`Redirect` input field in the `Confirmation email tab`_ and he receives the confirmation email.
   
   In the orders overview the order will show up as ``booked - confirmed`` or ``dashboard - confirmed`` if they are booked through the admin interface of the :doc:`Orders menu <orders>`.
**Confirmation timeout**
   This setting works together with :guilabel:`Confirmation emails`. This field is in minutes. The user must press the confirm link within x minutes otherwise the reservation will be deleted. If you enter ``0`` for this field, the order stays in the system until its confirmed; it wont be deleted automatically.
**Dashboard orders**
   Whether or not the option to place order in the :doc:`order menu </usage/orders>` is active. These orders follow all defined logic, but no payments are made.
**Test payments**
   Use this flag to test your event before the event goes into production.
**Seats**
   Use a seating plan. Works together with `Seats tab`_.
**Webhooks**
   Whether or not webhooks are enabled for this event. See also :doc:`Webhooks </advanced/webhooks>`
**Reload on exit**
   If an exit scan is done, stock is increased by 1 if this flag is set.
   You can compare it with a car park that is full. As soon as a car leaves the car park, there is space for a new car.
**Tracking**
   Use the `FE Tracking App <https://fe-tracking.fast-events.eu/>`_ for sporting events in particular to enable participants to signal checkpoints
   on the route in the App and possibly upload them to the server when they are passed.
   Works together with `Tracking tab`_.
**SaaS fee**
   If not empty it overrides the saas fee specified in the `Payment provider settings <../getting-started/settings.html#client-fee>`_. Leave empty if you want to use the value in the settings.
**SaaS user**
   Select the user this event is assigned to. If you don't select a user and select **'---'** instead, the system will use the default Mollie keys as defined in the settings and will not operate in Saas-mode for this event. If the system is not running in ``SaaS mode`` this entry can be ignored.
   The :guilabel:`Revoke authorization` button is only visible if the assigned user has authorized *Fast Events* to process payment information on its behalf.
   If access is revoked, the sub-merchant has to authorize again. The sub-merchant **must** authorize *Fast Events* before tickets can be sold.
**Terms html**
   If this field is not empty, then this is shown at the bottom of the order page as a checkbox. The user must check this in order to place the order. If you work with links (see screenshot above), always target a new window. Only the following html-tags are allowed: ``<a>``, ``<b>``, ``<i>`` and ``<u>``.
**Redirect after booking**
   The page (‘*Thank you*‘ page) to which the user will be redirected if the payment/booking has been successfully completed.

----

Type tab
--------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-type.png
           :target: ../_static/images/usage/Event-type.png
           :alt: Event type

This tab defines what kind of event we are dealing with.

**Event type**
   The :guilabel:`No date` option is only applicable for an event that is used by the :doc:`Payment app </apps/payment>`.
   Click on the grayed date and select your date and time and choose :guilabel:`Close` in the popup-window.
   The :guilabel:`Date format` will show up on the third line of the qrcode block on the e-ticket and it’s placeholders can be found `here <https://www.php.net/manual/en/datetime.format.php#refsect1-datetime.format-parameters>`_.
**Group type**
   Make a selection:
   
   - :guilabel:`No group`: you just have a single event at a particular date and time.
   - :guilabel:`Single select group`: the same event is running at multiple different dates. For example: you are organizing a boat trip on Thursday and Friday; the trip follows the same route on both dates and prices are the same as wel. You need to define 2 events where the date in the ``Event type`` differs (one on Thursday and the other on Friday). People can choose which tour they want to make during the ordering process. Make sure you fill in ``Event group``; this ties both events together. Any name will do, f.i. “*Boat*“.
   - :guilabel:`Multiple select group`: a variation on the previous choice. We still have a boat trip on Thursday and Friday and prices for both are still the same, but the route on Thursday differs from the one Friday. During ordering people can either choose to make 1 trip or book both trips on Thursday and Friday. Again: make sure you fill in ``Event group``; this ties both events together. Any name will do, f.i. “*Boat*“.
   - :guilabel:`Passe-partout`: works in conjunction with ``Multiple select group`` events. In our previous boat trip example, you could select either to take 1 or 2 boat trips, all for the same price per day. With this option you present the customer a separate page to buy the 2 boat trips for a separate price (usually lower). Buying 1 passe-partout gets you 2 e-tickets in this example. One for every day. Stock control is applied on the targeted events; stock of the Thursday trip and Friday trip is decreased by one if you buy 1 passe-partout. The passe-partout event itself can also have stock control.

**Event group**
   Must be filled in if you did choose :guilabel:`Single select group`, :guilabel:`Multiple select group` or :guilabel:`Passe-partout`.

----

Email tab
---------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-email.png
           :target: ../_static/images/usage/Event-email.png
           :alt: Event email

This tab defines the email that the user will receive once the order has been placed and paid for. This email is also used for dashboard orders (See :doc:`orders menu </usage/orders>`).

**Sender name and sender email**
   Optional fields. Use it if you want to override the ``Sender name`` and ``Sender email`` in the `Email settings <../getting-started/settings.html#email-settings>`_.
**Sender email**
   Optional field. Don't leave it blank.
**Email subject**
   The subject of the email. Don't leave it blank.
**Email BCC**
   There is an option to add only 1 BCC email address
**Email body**
   A smart editor where you can create your own fancy style emails. A word of advice: keep it simple and small and don't include large images.
   If you must use images, use links from your own site or a CDN.
   Remember that the email doesn't contain the e-tickets, but a link to download them.

   You can use a couple of keywords and *Fast Events* will replace them with the info available in the order:
   
   - :guilabel:`{%NAME%}` is the name of the person who placed the order.
   - :guilabel:`{%EMAIL%}` is the email address of the person who placed the order.
   - :guilabel:`{%YEAR%}` substitute the current year (YYYY).
   - :guilabel:`{%TICKETS%}` the unique link for downloading the e-tickets.
   - :guilabel:`{%DOWNLOAD-TICKETS%}` insert the following block with the appropriate links to download the tickets.

     .. list-table::

         * - .. image:: ../_static/images/usage/Download-tickets.png
                :target: ../_static/images/usage/Download-tickets.png
                :alt: Download tickets block

   - :guilabel:`{%INVOICE%}` the unique link for downloading the invoice.
   - :guilabel:`{%FIELDS%}` the input fields from the input-tab in table format.
   - :guilabel:`{%CONFIRM%}` only applicable for RSVP events and if the :guilabel:`Confirmation emails` flag in the `Basics tab`_ has bee set. The link to confirm that you will be present/participate.

.. warning:: Make sure to URL-escape a keyword if it is included in a hyperlink. E.g. ``<a href="%7B%25TICKETS%25%7D">Download tickets</a>``.

Don’t forget to test your email if it is ‘**spam-proof**‘. There are many tools available on the Internet, but we recommend using https://www.mail-tester.com/
Click the :guilabel:`Send test email` button and use the email address on the mail-tester site and within a minute you have detailed report.
You should take this very seriously, because if your email gets a high spam rating from receiving domains, your emails may end up in the '*Spam*' folder, or they won't be delivered at all.
Or worse, your domain may be blacklisted.

Deep dive
^^^^^^^^^
For the experts: the email itself is embedded in a container that is no wider than 600px. Always test on your mobile first to make sure the email formats well.
Don't include images directly from your camera, which can be several Mb in size.
If you must include images, keep the resolution at an acceptable level and use tools such as https://kraken.io to reduce the size.

*Fast Events* will ‘purify’ the email to prevent XSS-attacks, e.g. scripts are not allowed.

----

Confirmation email tab
----------------------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-confirmation-email.png
           :target: ../_static/images/usage/Event-confirmation-email.png
           :alt: Event confirmation email

This tab is only used if the :guilabel:`Confirmation emails` flag is set in the `Basics tab`_ and works in combination with the :guilabel:`Confirmation timeout` field. See `Email tab`_ for explanation of the keywords.

You usually use this if you have an event with free tickets. In other to prevent that pranksters reserve tickets with bogus emailaddresses they dont own, they will get a confirmation email that needs to be confirmed. If not the order is deleted after a defined timeout.

The process flow is:
   
   #. User makes a booking on booking page
   #. User is redirected to the page you entered in the :guilabel:`Redirect after booking` input field in the `Basics tab`_
   #. User gets the email defined in the ‘*Email – tab*‘. Make sure you include the ``{%CONFIRM%}`` keyword in the email.
      The email should contain something like *' ... thank you for your booking. Please click the confirmation link below to confirm your presence. This link is valid for 60 minutes ...'*.
      This is where the :guilabel:`Confirmation timeout` field kicks in. Enter a value of 60 (or whatever you prefer); the field is in minutes. If the user doesn't click the link within 60 minutes, the order/reservation wil be deleted.
      If you enter ``0`` for this field, the order stays in the system until its confirmed; it wont be deleted automatically. You can do 't yourself in the :doc:`Orders menu <orders>` by sorting on date and delete orders manually.
   #. User clicks on the :guilabel:`Confirm` button in the email
   #.  User is redirected to the page you entered in the :guilabel:`Redirect` input field in the ‘*Confirmation email – tab*‘ and receives the email defined in this tab as well..

In the orders overview the order will show up as ``booked - confirmed`` or ``dashboard - confirmed`` if you book it yourself via the :doc:`Orders menu <orders>`.

.. note:: The :doc:`fast_events_new_order hook <../hooks/new_order>` will be triggered **after** the user confirms the order.

----

Input tab
---------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-input.png
           :target: ../_static/images/usage/Event-input.png
           :alt: Event input

You can add more input fields on the order form beyond the :guilabel:`Name` and :guilabel:`Email` fields. The fields are displayed top to bottom in the order screen. With the ‘**+**‘ sign you can add more rows. The value field is optional, except if the type-field is ``Select``, then you enter the choices separated by a ‘**,**‘.

Example: the :guilabel:`Field description` is ``Color`` and :guilabel:`Value` could be something like ``Black,White,Green,Red``.

If the Type field is set to :guilabel:`Password`, the value the user has entered will **not** be stored in the database. The value is preserved till the filter ‘:doc:`fast_events_input_fields </hooks/input_fields>` is executed. Immediate after the filter it’s value is removed.

**Submit label**
   The label of the button to submit the order.

----

Tickets tab
-----------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-tickets.png
           :target: ../_static/images/usage/Event-tickets.png
           :alt: Event tickets

Add the tickets you want to sell. The ‘**+**‘ and ‘**–**‘ buttons are used to add rows or remove them. Duplicate ticket types are not allowed.
If the :guilabel:`Count` field is set to ``Yes`` then the purchased quantity is deducted from the stock at the event level as defined in the `Basics tab`_.
The :guilabel:`Price` field includes VAT.

If you leave the stock field empty, you can keep selling tickets until you reach the maximum you have defined at the event level.
In the above configuration only 100 ``Gold (Backstage)`` tickets can be sold and there is no limit for the ``Silver`` tickets until it reaches the maximum defined at the event level.
It can happen that all tickets are sold out, but only 50 ``Gold (Backstage)`` tickets are sold.
If you want 100 ``Gold (Backstage)`` tickets to be guaranteed, you will also have to limit the number of ``Silver`` tickets.
Together, they must add up to the number defined at the event level.

If a ticket is sold out, it will still show up in the orderpage, but you can’t select it and it is flagged as sold out.

.. warning::
   **Never** add or remove ticket-types if orders already have been accepted.

.. note::
   If you want to give free parking tickets to all participants and want to check them at the entrance of the parking lot, you can for example define the following ticket.
   Define a new tickets: set :guilabel:`Ticket description` to ``Parking ticket``, :guilabel:`Price` is ``0``, :guilabel:`Min` is ``1``, :guilabel:`Max` is ``1`` and :guilabel:`Count` is ``No``.

----

PDF templates tab
-----------------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-pdf.png
           :target: ../_static/images/usage/Event-pdf.png
           :alt: Event PDF templates

Preparation
^^^^^^^^^^^
Make sure you have uploaded the PDF-templates for the etickets and if needed for the invoices. Upload the PDF’s in the Media-library of your WordPress installation.

**How to create a template?**
   Use for example Word, LibreOffice, … and design a single-page A4 e-ticket. Leave a 120 mm x 40 mm block somewhere on the page. You can position it either vertical or horizontal or even in any angle you want. This is the block where *Fast Events* will print the qrcode block and some other information. Save the design as PDF and upload it to your WordPress Media library.
**Recommendations**
   Keep the PDF as small as possible, preferable below 200kb for a single eticket. Don’t use full blown images. Bring them back to an acceptable resolution. And pull them first through sites like https://kraken.io to squeeze the size. An image resolution of 150 DPI for etickets is enough.
   Make use of use the `pdf system fonts <https://kbpdfstudio.qoppa.com/standard-14-pdf-fonts/>`_. For example use for your text the ``Helvetica`` font. Try to prevent the use of special fonts, because these are embedded in the PDF and then the PDF becomes larger. You can analyse your `PDF here <http://pdf-analyser.edpsciences.org/>`_.

Ticket
^^^^^^
The size of the eticket is always A4 (210mm x 297mm) and so the :guilabel:`Qrcode x-position` and :guilabel:`Qrcode y-position` values must stay within these limits.
The values of these fields are in millimetres.
Pick a template from the dropdown box and start playing with the :guilabel:`Qrcode x-position` and :guilabel:`Qrcode y-position` to position the qrcode block.
Click on the :guilabel:`Example ticket` button to see the result. Repeat this step until you are satisfied with the positioning.
With the :guilabel:`Qrcode rotate` field you can rotate the qrcode block. Rotation is done from the top left corner and must be between **0** and **360**.
:guilabel:`Qrcode scale` is a percentage that can be used to scale the qrcode block. The default value is ``100``.
Look at the `example template <../_static/pdf/Vinyl-template.pdf>`_ and the `ticket example <../_static/images/usage/Ticket-example.jpg>`_ if the settings of the screenshot above have been applied.

**Template per ticket-type**
   *Fast Events* offers you the possibility to use different pdf-templates per ticket-type. For example: your event contains the ticket-types ``Silver`` and ``Backstage``.
   Create a default template with the name :guilabel:`Vinyl-template.pdf` (any name will do).
   This default template will be the template for the ``Silver`` ticket. For the ``Backstage`` ticket you should create a pdf with the name :guilabel:`Vinyl-template-Backstage.pdf`.
   Select in the drop-down box the ‘*Vinyl-template.pdf*‘. That’s it; if *Fast Events* can’t find the template, it will use the default selected template.
   Mind you: the template-names are case sensitive and make sure the ``.pdf`` suffix is lowercase and the ticket name should not contain spaces.
   The qrcode block will be printed on the same location for all templates.

   .. note:: If you upload a new ticket template, always open the event for editing and save it again. Do this for every event that is using this template.

**No border**
   If checked, no border is printed around the qrcode block.

Invoice
^^^^^^^
The preparations for the invoice template are the same as the one for the tickets template. Look at the `invoice template <../_static/pdf/OpenAir-Invoice.pdf>`_ and the `invoice example <../_static/images/usage/Invoice-example.png>`_ if the settings of the screenshot above have been applied.

This is certainly not an official invoice, but more a proof of purchase. For official invoices, it is better to link *Fast Events* with an accounting package. You can do that, for example, by using the :doc:`fast_events_new_order <../hooks/new_order>` webhook. Look here for an `example <../hooks/new_order.html#examples>`_.

----

Scan tab
-----------------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-scan.png
           :target: ../_static/images/usage/Event-scan.png
           :alt: Event scan keys

Preparation
^^^^^^^^^^^
Scanning tickets can be easily defined in this screen. Varying from a single scan for all types (level 0) of tickets to a stepped scan (level 1) for selected ticket types.
For example, visitors must first be scanned at the main entrance before they can be scanned at the backstage entrance and only if they have a ``Gold (Backstage)`` ticket.
You can add multiple tickets in the :guilabel:`Scan tickets` field. Just separate them with a comma.

You can also include an exit scan (level 9). Once a user passes this scan, no other scans are possible anymore.

Scanning is done with the :doc:`mobile scan app<../apps/scan>`, so no need for expensive scan equipment.
Configure the scan app by pressing the right button in the :guilabel:`Scan key` field and scan it in the app settings and you are ready to scan.

Add more rows by pressing ‘**+**‘ and remove rows by pressing ‘**–**‘ .
Use the first button on the :guilabel:`Scan key` field to regenerate the scankey and pressing the other button shows a
popup window with the configuration qrcode you can scan with the mobile app to configure it, or copy the configuration qrcode and for example mail
it to the people who do the actual scanning

The :guilabel:`Date format` is used in the :doc:`mobile scan app<../apps/scan>`. You can find the specification `here <https://www.php.net/manual/en/datetime.format.php#refsect1-datetime.format-parameters>`_.

.. note::
   Scan keys and locations must be unique per event, but you can use the same scan keys and/or locations across events.

Examples
^^^^^^^^
**1. One event with a single entrance**
   Just define a single scankey. Leave :guilabel:`Scan tickets` empty and give :guilabel:`Scan location` a name.
**2. One event with multiple entrances**
   You would like to know how many visitors arrive at each entrance. Define different scan keys for each entry. Leave :guilabel:`Scan tickets` empty and set :guilabel:`Scan location` to the name of the entries. In the :doc:`orders-menu <orders>` you can download a csv-file of the scanned tickets and subsequently do some data-analysis. Another option is to use the :doc:`fast_event_scan_ticket event <../hooks/scan_ticket>` and monitor in realtime how many people did pass the different entrances.
**3. Multiple events grouped together**
   It’s basically 1 single event, but you are selling tickets per boarding place for a boat trip. Per event (boarding place) you define an unique scankey. Leave the :guilabel:`Scan tickets` empty and give the :guilabel:`Scan location` a name.
**4. A single event with regular tickets and tickets with backstage rights**
   See the screenshot above. There is a scankey for all tickets for the main entrance and a separate scankey for the ``Gold (Backstage)`` ticket with the level set to ‘**1**’. This means that before you can scan a backstage ticket it must have been scanned at the main entrance. If you have multiple ticket types that are allowed to go backstage, just add them to :guilabel:`Scan tickets` separated by a comma. Mind you: make sure the name of the ticket matches one (or more) ticket types you have defined in the `Tickets tab`_. The fields are case sensitive.
**5. Addition on 4. Backstage visitors can also pickup a free cocktail**
   The same definition as example 4, but just add 1 unique scankey for the ``Gold (Backstage)`` ticket, the level should be set to 1 and give it a name (“*Free cocktail*”).
**6. Cycling tour with several checkpoints**
   Make a start scan (level 0) at the beginning of the tour and a scan key (level 1) for each checkpoint. Optionally, you can do a level 9 (Exit scan) at the end of the tour and, for example,
   give the participants a reminder medal when they have completed all the checkpoints. The latter is easy to check in the :doc:`Scan App<../apps/scan>`.

----

Groups tab
-----------------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-groups.png
           :target: ../_static/images/usage/Event-groups.png
           :alt: Event groups

In this tab you can configure that orders can only be made if customers are member of a group. Configuring this tab only makes sense if you have checked ``User groups`` in the `Basics tab`_.

WordPress roles
^^^^^^^^^^^^^^^
Select from the dropdown list the roles you allow to place orders. You can select multiple roles by pressing SHIFT and click on the different roles. *Fast Events* will check if the emailaddress entered during the order-process belongs to an existing user in the WordPress database and if the role of the user matches the ones you have enabled. If you have defined a :guilabel:`Password` field in the `Input tab`_, *Fast Events* will also verify if the password matches with the one stored in de WordPress Database. If you don’t select any role, *Fast Events* assumes any role is valid.

Upload a csv file
^^^^^^^^^^^^^^^^^
Suppose you want to have a boat trip and only the members of your football club are allowed to participate.
Create a spreadsheet with the name in the first column, the email address in the second column and the maximum number of tickets the person can buy in the third column,
and save it as a csv-file. Use a comma (,) as field separator. Emailaddresses in the file need to be unique!
Press the :guilabel:`Upload csv file` button and upload the file. Ready!
Now only customers with the email addresses you uploaded can place orders and they can only buy as many tickets as specified.

You can upload the same file or an updated version multiple times. Rows will be overwritten or added. No rows are deleted. If you want the latter, you will first have to delete everything by clicking the :guilabel:`Delete group` button. This button only deletes entries of the current event.

The search button shows a popup window with the number of entries per event.

You can also reference a group of another event by setting the event-id.

REST API
^^^^^^^^
This is an option to check via a configurable REST URL if an order can be placed and how many tickets can be ordered. In realtime *Fast Events* checks via a POST request, content-type ``application/json`` and a security key (HTTP Header) .
These are the parameters are included in the body of the HTTP request as a JSON string:

**$attr['name']**
    (*string*) The name of the person placing the order.
**$attr['email']**
    (*string*) The emailaddress of the person placing the order. This value is *read-only*.
**$attr['order_amount']**
    (*string*) The total order value. For example ``6.50``. This value is *read-only*.
**$attr['order_vat']**
    (*string*) The total order VAT value. For example ``2.50``. This value is *read-only*.
**$attr['fields']**
    *array* of input fields.
       
    1. **'name'** (*string, case sensitive*) The name of the input field.
    2. **'value'** (*string*) The value of the input field.
**$attr['tickets']**
    *array* of ticket-types ordered.
       
    1. **'name'** (*string, case sensitive*) The name of the ticket-type.
    2. **'price'** (*string*) The ticket price. Example ``6.25``.
    3. **'vat'** (*string*) VAT.
    4. **'count'** (*int*) The number of tickets ordered.
    
The server should respond with ``{"count":0}`` if you are not allowed to place an order. It is possible to include an error as well. For example: ``{"count":0,"error":"This user is unknown"}``. This JSON string should be returned in the body of the response. This error-string will be shown to the user.

If the server decides the input is valid it should return the maximum number of tickets this person can buy, eg. ``{"count":5}``

REST API example
^^^^^^^^^^^^^^^^
.. code-block:: bash
   :linenos:
   
   curl https://api.exampledomain.com/search \
      -X POST \
      -H 'Accept: application/json' \
      -H 'Content-Type: application/json' \
      -H 'X_API_KEY: Hgbsda$ZKKa!4Ix' \
      -d '{"name":"John Doe","email":"JohnDoe@yourdomain.com","fields":null,"tickets":[{"name":"Silver","price":"7.00","vat":"21.00","count":1}],"order_amount":"7.00","order_vat":"1.21"}'

``https://api.exampledomain.com/search`` is the REST API URL.
The ``X_API_KEY: Hgbsda$ZKKa!4Ix`` is the part you have to copy into the HTTP Header field. It’s the secure key between the client and the server.

.. warning:: If you have defined input-fields, they will be included as well. So password-fields **will be visible to the external server**. Only use the REST API in this case if you trust this server and/or it is under your control.

Unique bookings/orders
^^^^^^^^^^^^^^^^^^^^^^
Use this input field if you have checked the :guilabel:`Unique users` checkbox in the `Basics tab`_. For a single event there is no need to enter event-id of the current event, as the default is the current event-id. But suppose you have a boat trip on Thursday and another one on Friday. You define 2 separate events and users are only allowed to book on either Thursday or Friday, but not on both dates. Enter here both event-ids separated by a comma, e.g. “**2,4**”. Mind you, you have to this for both events!

----

Seats tab
---------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-seats.png
           :target: ../_static/images/usage/Event-seats.png
           :alt: Event seats

In this tab you can configure the seating for the event. Configuring this tab only makes sense if you have checked :guilabel:`Seats` in the `Basics tab`_.

In this example we are working with 60 seats and the seats are filled in the order A1, B1, A2, B2, ... C10, D10, C9, D9, ... E1, F1, E2, F2,...

.. list-table::

    * - .. figure:: ../_static/images/usage/Seats-example.png
           :target: ../_static/images/usage/Seats-example.png
           :alt: Example seating plan
           
           Example seating plan
      
      - .. figure:: ../_static/images/usage/Seats-ticket.png
           :target: ../_static/images/usage/Seats-ticket.png
           :alt: Example seating plan
           
           Position seat information
           
**Number of seats**
   The total number of seats.
**Print format**
   The seating module of *Fast Events* works with 2 variables, the row, which can be any string, but in this example we use "**A, B, C, D, E and F**" as row identifiers. The second parameter is a number. The numbers dont have to be sequential. They also do not have to start with 1. The seating info is printed in the qrcode-block just after the ticket-type.
   Suppose you want the string to look like "**Gold (Backstage), row A table 09**". The print format must then be ``, row %s table %'02d``. The format comes from the `printf-function <https://www.php.net/manual/en/function.sprintf.php#refsect1-function.sprintf-parameters>`_.
**Seats configuration**
  The format is ``row:seatFrom-seatTo,row:seatFrom-seatTo,...``. So in our example is must be :guilabel:`A:1-1,B:1-1,A:2-2,B:2-2`. The total number of seats must match the configuration you specify here. It can of course be a lot of work to enter such a seating order, especially if you have hundreds or more. For these cases we suggest you goto https://sandbox.onlinephpfunctions.com/ and use the following code:
  
  .. code-block:: php
   :linenos:
   
   <?php
   for ($i=1; $i<=10;$i++) {
     echo "A:$i-$i,B:$i-$i,";
   }
   for ($i=10; $i>0;$i--) {
     echo "C:$i-$i,D:$i-$i,";
   }
   for ($i=1; $i<=10;$i++) {
     echo "E:$i-$i,F:$i-$i,";
   }

Grab the output and paste it here. Done!
   
But of course there can be seat configurations that are a lot simpler. Suppose you fill the seats sequential per row. The configuration is then ``A:1-10,B:1-10,C:1-10,D:1-10,E:1-10,F:1-10``.

**Linked event**
   Use the event with this id for the seatingplan.

----

Tracking tab
------------
.. list-table::

    * - .. image:: ../_static/images/usage/Event-tracking.png
           :target: ../_static/images/usage/Event-tracking.png
           :alt: Event tracking

The essence of Tracking is simple. Suppose you have a sports event in which the participants have to follow a mapped out
route and scattered along the route are a number of checkpoints where you have to show your eticket and have it scanned.
At the end of the route your eticket is scanned again and when you have passed all checkpoints you will receive a medal or other proof of participation.

To make this possible, event organisers would normally have people at each checkpoint who scan the participants' tickets and possibly at the start to gain access to the event.
This in itself is perfectly possible. Define a level 0 scan (=entrance), per checkpoint a level 1 scan and at the end a level 9 scan.

There are, of course, quite sophisticated solutions available on the market, but they all require an investment in hardware and/or software,
or participants must purchase Apps or a combination of these.

The *Fast Events* WordPress plugin offers a standard solution with a `tracking App  <https://fe-tracking.fast-events.eu/>`_ that participants can download for free for Android and IOS.
The App allows participants to track their progress along the route, and checkpoints are automatically flagged by
the App and will be uploaded to the organisation's server, where they are handled as if they were a scan of the ticket.
This means that checkpoints do not need to be manned, in fact they can be completely virtual. That is, they are only known to the App by their geographical coordinates.

In addition, it is also possible to use real-time track updates and send real-time news messages to all users of the *FE Tracking* App for this event.

Step-by-step implementation
^^^^^^^^^^^^^^^^^^^^^^^^^^^
#. Enable the :guilabel:`Tracking` flag in the `Basics tab`_.
#. Define KML-files to describe the track, including the checkpoints and any other points of interest you want to show in the App.
   Ech KML-file can only contain a single track, if for instance you have an event with multiple distances.
#. Upload **ALL** KML-files by pressing the :guilabel:`Upload KML file(s)` button in this tab. You can't upload them one-by-one or delete one.
#. Fill in the remaining fields in this tab.
#. Inform participants how to use the *FE Tracking* App. This could be in the email that participants receive when they have ordered
   a ticket or on a webpage that is prominently displayed on the website.

KML files
^^^^^^^^^
*Fast Events* uses KML-files created by `Google My Maps <https://support.google.com/mymaps/?topic=3188329>`_. You will need a free Google account for this.
If your event has only a single distance, you need to create ofcourse 1 KML file. If you have multiple distances you need to create a KML file for every distance.
Every KML files contains the track, the checkpoints and other points of interest grouped by layer for every type of point of interest.
Draw the route in the direction it will be walked, cycled, driven, etc. Always start at the beginning! Zoom in as much as possible to make the track as accurate as possible.

In case of multiple distances, the user can choose the distance in the App. However, if the name of the track in the KML file is the same as the name of the
ticket that the user has purchased, then this KML file is automatically selected by the App without the user having a choice.

In the App the user can scan the eticket if it has been printed or search the PDF for a valid qrcode if it is stored on the phone. In case of multiple etickets in the PDF
the user will be asked which page needs to be search for the qrcode.

Here is an example:

.. list-table::

    * - .. image:: ../_static/images/usage/Track-demo.png
           :target: ../_static/images/usage/Track-demo.png
           :alt: Demo track

You can only define a single path! And as show in the example every layer with similar points of interests are grouped together and all need to have **the same icon and color**.

.. list-table::

    * - .. image:: ../_static/images/usage/Track-details.png
           :target: ../_static/images/usage/Track-details.png
           :alt: Track details

For every point of interest in the layers you have to use a short descriptive name. The description can contain as much text as you like.
**You can't use your own icons**; always use one of the embedded Google My Maps icons.

.. warning::

   Each checkpoint must be linked to a scan entry in the `Scan tab`_. The link is via the location field.
   So make sure the name of the checkpoint is exactly the same as a location field.

   The ``Checkpoints``-layer needs to be the first layer after the track.

.. list-table::

    * - .. image:: ../_static/images/usage/Phone-details.png
           :target: ../_static/images/usage/Phone-details.png
           :alt: Phone details

This is how the dialogues will look like on the phone.

Export the KML file
^^^^^^^^^^^^^^^^^^^
.. sidebar:: Save KML file

    Use the ``Export to KML/KMZ`` in the main menu and make sure you tick the last checkbox.

.. list-table::

    * - .. image:: ../_static/images/usage/Save-kml.png
           :target: ../_static/images/usage/Save-kml.png
           :alt: Save KML file

.. tip::

   If you need to create multiple Maps which include mostly the same points of interest, create the first Map and export it as KML file.
   Create a new Map and import the previous exported KML file and make the changes you need.

Remaining fields
^^^^^^^^^^^^^^^^
**Tracking window**
   Between these 2 times the participant can enable recording in de *FE Tracking* App and it will register when checkpoints are passed.
   Outside these windows all information (POI's and record track) is still visible, but recording is not possible.
**Geofence radius**
   The radius of the circle around a checkpoint. Once the mobile enters a checkpoint-circle, the checkpoint is flagged as passed.
   The minimum radius is 200 meters. Make sure you position the checkpoint very accurately on the Map by zooming in as much as possible.
**Distance filter**
   The *FE Tracking* App is optimized for battery-efficiency. It samples the accelerometer periodically while tracking in order to power-down
   the GPS as soon as the device is determined to be stationary. It uses the distance filter to query for the GPS location.
   But the filter itself is elastic; the faster you go, the larger the distance filter becomes. And ofcourse the other way around.
   The default value is 10 meters. But keep in mind that for walking 10 meters would be a good start, for cycling you would be better of to the start with 25 meters.
**No entry scan**
   Suppose you have a cycle tour with several starting points on the route and you do not want to do an access scan so that the participants can start immediately.
   Then tick this checkbox. If a checkpoint upload is done from the *FE Tracking* App, an entry scan is done automatically if it has not already been done.
   Under the hood *Fast Events* does a level 0 scan with the same location name (=Checkpoint name) prepended with an asterix (*).
**Force Tracking App**
   Level 0 and level 1 checkpoints (= scan location!) can only be uploaded by the Tracking App, you can't scan them with the Scan App.
   The level 9 scan can be scanned by the Scan App, but please note that it has to be the 'Finish/end qrcode' found in the main screen of the overview of all routes.
**Information URL**
   This is where you should put your dynamic information. The user can click this URL from within the *FE Tracking* App. If you expect a lot of traffic,
   consider a CDN in front of your site or use something like `Amazon Amplify <https://aws.amazon.com/amplify/>`_, which is free the first year.
**Emergency number**
   The phone number users should call in case of emergencies. This phone number is visible in the *FE Tracking* App.
**Emergency information**
   Put here the static information what the rules are to call the number.

Warnings
^^^^^^^^
#. Never change the tracking field in the `Basics tab`_ while the event is running.
#. Never change the scan fields in the `Scan tab`_ while the event is running.
#. Participants can download tickets in the *FE Tracking* App until the end of the tracking window. Except, of course, if the ticket, the order or the event has been deleted earlier.
#. Participants should keep their qrcodes on the eticket for themselves. Each time the ticket is downloaded into the
   *FE Tracking* App a new unique signature will be generated. This means that the last person is the ``owner`` of the ticket.
   Previous downloads (by others or on a different phone) cannot upload checkpoints any more from the *FE Tracking* App and the final scan will also fail.
   **So keep the eticket qrcode secret!**