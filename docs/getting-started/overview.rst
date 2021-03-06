Overview
************
Make sure you have your free Mollie account configured. Without it you can only use RSVP events or sell free etickets (0.00 amount).

.. image:: ../_static/images/getting-started/Mollie.png
   :target: https://www.mollie.com/dashboard/signup/5835294
   :alt: Mollie

To use *Fast Events*, a one-time configuration is required. To do this, go to the :doc:`settings <settings>` of the plugin. The settings can only be changed by an account with admin rights.

This plugin allows you to sell tickets for different types of events. Per event there are all kinds of possibilities to impose restrictions such as, time of sale, maximum number of tickets that can be purchased, group membership, purchase once, limit ticket type stock and much more. A few examples

- online sale of etickets for a single event
- sell etickets for a group of events. The user can only choose a single event
- sell etickets for a group of events. The user can select multiple events
- sell a passe-partout. Customers may attend all events in the group
- use it for a bicycle tour with multiple checkpoints for scanning
- sell tickets for a theater and use a seating plan

Have look at the detailed :doc:`examples <../usage/examples>` to get an idea what type of event you can create.

----

Checklist for creating an event
-------------------------------
Before you start creating an event, it is advisable to go through all the questions in the following checklist and collect the answers before you create the event.

- The name of the event.
- The exact date and perhaps the starting time
- When will the ticket sale start and when will it end?
- How many tickets are available (stock on event level)?
- Do you need multiple ticket types? Eg. a tickets for adults and a ticket for children, each with a different price and stock. Do they need to be counted (Deducted from the stock)?
- How many tickets can be ordered in a single order?
- Are user allowed to place multiple orders?
- Do you need a seating plan?
- Is it a single event or are there multiple events eg. 1 event per day for a series of days?
- Do you need an passe-partout (access to all events for a reduced price)?
- Are there different access-rights for some tickets. Eg. all tickets are scanned at the main-entrance but some ticket types (fi. Backstage) have ‘Backstage’ access and can be scanned at the Backstage-entrance.
- Design the email the user receives after a successful order (see `example <../usage/events.html#email-tab>`_)?
- Create a “*Thank you for your purchase*” page (See `thank you example <#thank-you-page>`_ below).
- Do you need more information from the user during ordering. Normally only the name and emailaddress are needed. Be very careful adding too many fields, as users tend to bailout if they see a huge list of mandatory fields.
- Design your eticket. Do you need different designs per ticket type?
- Scanning of the etickets: are multiple entries used and do you want to measure how many pass a specific entry?
- Do you want to give free tickets to, for example, sponsors?

----

PDF etickets
------------
Customers will receive an email with an unique link to download the etickets as a pdf-file. You have to create a PDF-template which the plugin can use to create the eticket.
This is an `example of a template <../_static/pdf/Vinyl-template.pdf>`_.

How to create a template?
^^^^^^^^^^^^^^^^^^^^^^^^^
Use for example Word, LibreOffice, … and design a single-page A4 e-ticket. Leave a 120 mm x 40 mm block somewhere on the page. You can position it either vertical or horizontal or even in any angle you want. This is the block where *Fast Events* will print the qrcode block and some other information. Save the design as PDF and upload it to your WordPress Media library.

Recommendations
^^^^^^^^^^^^^^^
Keep the PDF as small as possible, preferable below 200kb for a single eticket. Don’t use full blown images. Bring them back to an acceptable resolution. And pull them first through sites like https://kraken.io to squeeze the size. An image resolution of 150 DPI for etickets is enough.
Make use of use the `PDF system fonts <https://kbpdfstudio.qoppa.com/standard-14-pdf-fonts/>`_. For example use for your text the ``Helvetica`` font. Try to prevent the use of special fonts, because these are embedded in the PDF and then the PDF becomes larger. You can analyse your `PDF here <http://pdf-analyser.edpsciences.org/>`_.

----

Thank you page
--------------

.. list-table::

    * - .. figure:: ../_static/images/getting-started/Thank-you.png
           :target: ../_static/images/getting-started/Thank-you.png
           :alt: Example thank you page
           
           An example “Thank you for the purchase” page

It is possible to include a download link for the etickets in the “*Thank you*” page. It’s up to you yo do this in combination with an email or just omit the email (See `Events (Basic tab) <../usage/events.html#basics-tab>`_, :guilabel:`Emails` checkbox) and use the download link. You can put that download link anywhere in the “Thank you” page with a shortcode. Use the following shortcode:

.. code-block:: text

   [fe_download showimage="yes" downloadtext="Download eticket(s)"]

You can customize the text of the hyperlink by changing the ``downloadtext`` parameter. The ``showimage`` parameter is only applicable if there is a single (1) eticket.
If you set it to “**yes**” , the qrcode wil be included in the page. This can be useful, for example, for the sale of consumption coins.
You buy the coins on your mobile and show the qrcode on the “*Thank you*” page at the counter and the qrcode can be scanned directly and you receive your coins. So no queuing at the counter or time consuming payment actions. If there is more than 1 eticket this parameter will be ignored.
Don't use this shortcode together with the ``Group type`` :guilabel:`Multiple select group`.

.. image:: ../_static/images/getting-started/Qrcode-example.png
   :align: left
   :alt: Qrcode example
       
This is an example qrcode. At the bottom the ticket-id and after the dash the order-id. On the right the date and time the order was created and on the left the date (and time the page was created.

.. raw:: html

   <div style="clear:both"></div>

----

Order pages
-----------

.. image:: ../_static/images/getting-started/Order-example-1.png
   :align: right
   :scale: 50%
   :alt: Order example with event id
       
Once you have defined your event(s), you should create one or more order pages, depending on your requirements. If you just have a single event, use the shortcode-format as shown in the example. The id is the number of the event.

.. raw:: html

   <div style="clear:both"></div>


.. image:: ../_static/images/getting-started/Order-example-2.png
   :align: left
   :scale: 50%
   :alt: Order example with grouping
       
Or use this shortcode-format. Your OpenAir festivals is running for 2 days and visitors can attend 1 or more days. You need to create an event for every day, which are linked together by the group name.

See `Type tab <../usage/events.html#type-tab>`_ for more explanation.

.. raw:: html

   <div style="clear:both"></div>

Next steps
----------
#. Goto the :doc:`orders menu <../usage/orders>` and add via de the dashboard a new order.
#. Check if the email arrives and if the content is ok.
#. Download the eticket and check it.
#. Use the :doc:`Scan App <../apps/scan>` to scan the eticket.
#. Check in the contextmenu the order details if the ticket is scanned. You can remove the scan with the ``Checkin`` contextmenu.
#. Now test the orderpage. Make sure you have :guilabel:`Test payments` switched on in the `Basics tab <../usage/events.html#basics-tab>`_ of the event.
#. Check again the email, eticket and scan the eticket.
#. Do a refund of the last order.
#. Check the stock value.
#. If you are happy with the results, you should remove all orders and tickets via the contextmenu in the :doc:`events menu <../usage/events>` and uncheck :guilabel:`Test payments`.
#. Your event is now live

Don't
-----
Once your event(s) has orders you, never change the following fields:

- don't add, remove or change ticket names in the `Tickets tab <../usage/events.html#tickets-tab>`_. You can change the price and stock.
- don't change the :guilabel:`Connect stock event-id` field in the `Basics tab <../usage/events.html#basics-tab>`_.
- don't change :guilabel:`Event type`, :guilabel:`Group type` or :guilabel:`Event group` in the `Type tab <../usage/events.html#type-tab>`_. You may change ``Date`` and/or ``Date format``.
- don't add, remove or change extra input fields in the `Input tab <../usage/events.html#input-tab>`_
- don't change :guilabel:`User groups` in the `Groups tab <../usage/events.html#groups-tab>`_
- don't change the :guilabel:`Seats configuration` in the `Seats tab <../usage/events.html#seats-tab>`_. You can add at the end new seats, but you should never remove seats.
