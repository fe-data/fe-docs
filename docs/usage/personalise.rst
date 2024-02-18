Ticket personalisation
======================

The following is a step-by-step guide on how to configure ticket personalisation and how the end user will ultimately be able to personalise tickets.

Configure personalisation
-------------------------

1. Define input fields
^^^^^^^^^^^^^^^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  Edit input field

       .. figure:: ../_static/images/usage/Pers-input.png
          :target: ../_static/images/usage/Pers-input.png
          :alt: Define input fields

   .. grid-item::

       The first step is to define 1 or more `input fields <events.html#input-fields>`_.

       If the :guilabel:`Personalise` checkbox is unchecked, the field will be displayed on the order form.
       This means that the field has the same value for all tickets and can't be changed once the order has been submitted.

       If the :guilabel:`Personalise` checkbox is checked, the field must be personalised for each ticket.

2. Use in ticket types
^^^^^^^^^^^^^^^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  Edit ticket type

       .. figure:: ../_static/images/usage/Pers-ticket-edit.png
          :target: ../_static/images/usage/Pers-ticket-edit.png
          :alt: Edit ticket type

   .. grid-item-card::  Select personalisation fields

       .. figure:: ../_static/images/usage/Pers-ticket-select.png
          :target: ../_static/images/usage/Pers-ticket-select.png
          :alt: Select personalisation fields

Connecting input fields to `ticket types <events.html#ticket-types>`_ is the next step.

It is possible to associate different input fields with different tickets.
And not all tickets need to have personalisation fields.

Simply tap on the :guilabel:`Fields for personalisation` and select the fields you want to use.
The order in which they are selected is also the order in which they will be displayed during personalisation.

3. Use in thank-you-page
^^^^^^^^^^^^^^^^^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  Redirect after booking

       .. figure:: ../_static/images/usage/Pers-basic.png
          :target: ../_static/images/usage/Pers-basic.png
          :alt: Redirect after booking

   .. grid-item::

       The next step is to edit the WordPress page referenced in the :guilabel:`Redirect after booking` field.

       Insert the shortcode ``[fe_personalise]`` anywhere on the page.

       You can save 5 hits on your server by using the shortcode ``[fe_personalise cdn]``.
       Instead of fetching the supporting files from your server, it fetches them from Cloudflare's global CDN.

       Another option is to use the **dark** attribute in the shortcode.
       The default theme is light, but if your site has a dark background you can use this keyword.
       Combine it optionally with the **cdn** attribute and the resulting shortcode should be ``[fe_personalise cdn dark]``.

4. Use in order email
^^^^^^^^^^^^^^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item::

       Insert the keyword ``{%PERSONALISE%}`` anywhere in the body of the email.

       The customer will see a button in the email which, when clicked, will take them to the page used in step 3.

   .. grid-item-card::  Define email

       .. figure:: ../_static/images/usage/Pers-email.png
          :target: ../_static/images/usage/Pers-email.png
          :alt: Define email

5. Use in eticket PDF
^^^^^^^^^^^^^^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  PDF eticket fields

       .. figure:: ../_static/images/usage/Pers-eticket.png
          :target: ../_static/images/usage/Pers-eticket.png
          :alt: PDF eticket fields

   .. grid-item-card::  PDF eticket layout

       .. figure:: ../_static/images/usage/Event-tickets-layout.png
          :target: ../_static/images/usage/Event-tickets-layout.png
          :alt: PDF eticket layout

Checking the :guilabel:`Default layout` checkbox will cause the default QR code info block to be printed in the eTicket PDF.

If you deselect it, tap on the :guilabel:`Layout fields` and select up to 6 fields you want to print on the PDF of the eTicket.
The order in which they are selected is also the order in which they are printed.

Use personalisation
-------------------
Below, we use the Openair event that is part of the demo data. You can add your own sample order by going to FE Admin
and pressing the ``+`` button in the :guilabel:`Orders` tab to add a new order. Next, click on the **triple dot** icon of the new
order and select :guilabel:`Share PDF tickets`.

The App will respond with: ``Personalisation needed``. Click :guilabel:`Personalise` and and you will be taken directly to the personalisation page.

Interface
^^^^^^^^^
.. list-table::

    * - .. image:: ../_static/images/usage/Pers-page-1.png
           :target: ../_static/images/usage/Pers-page-1.png
           :alt: Personalisation page

The personalisation section is fully responsive. Depending on the width of the screen, it can display 1, 2 or 3 ticket cards side by side.
Once all the tickets have been personalised, you will be able to download them if you wish.
In most cases, however, it is not necessary to download the tickets, as the QR code will appear on the screen and can be scanned at the entrance to an event.

Share tickets
^^^^^^^^^^^^^
.. list-table::

    * - .. image:: ../_static/images/usage/Pers-page-share-1.png
           :target: ../_static/images/usage/Pers-page-share-1.png
           :alt: Share tickets

If you have purchased a number of tickets, it is possible to share 1 or more with other people so that they can personalise their own tickets.
Once you start selecting tickets, a red button will appear on the right hand side of the screen.

.. list-table::

    * - .. image:: ../_static/images/usage/Pers-page-share-2.png
           :target: ../_static/images/usage/Pers-page-share-2.png
           :alt: Share tickets link

Tap, in this example, the :guilabel:`Share 1 ticket` and a popup dialog will show the link to share.
Copy it and share it with another attendee so they can personalise their own tickets.
After sharing, each shared ticket will have a small red badge attached to it to remind you that it has been shared.

The person receiving the share will see a similar screen, but there are some differences:

1. It is not possible to select and share tickets.
2. The :guilabel:`Order` and :guilabel:`Invoice` are not available.

Personalise ticket
^^^^^^^^^^^^^^^^^^
.. list-table::

    * - .. image:: ../_static/images/usage/Pers-page-edit-1.png
           :target: ../_static/images/usage/Pers-page-edit-1.png
           :alt: Personalise ticket

Tap the ``pencil`` icon to personalise the ticket and the :guilabel:`Save` button to save it.
Once the ticket has been saved, it will no longer be possible to edit it.
The ``pencil`` icon is no longer available.

.. list-table::

    * - .. image:: ../_static/images/usage/Pers-page-edit-2.png
           :target: ../_static/images/usage/Pers-page-edit-2.png
           :alt: Personalised ticket saved

You can of course personalise shared tickets yourself, but once you have done so, the recipient of the shared ticket will see the data if they try to personalise it.
Conversely, if the other person has personalised one or more tickets and you try to personalise it, it will also
warn that the ticket has already been personalised. The data will be displayed and you will not be able to edit it.

Once all tickets have been personalised the QR codes become visible.

Download tickets
^^^^^^^^^^^^^^^^
.. list-table::

    * - .. image:: ../_static/images/usage/Pers-page-download.png
           :target: ../_static/images/usage/Pers-page-download.png
           :alt: Download tickets

Download all tickets by tapping the ``tickets`` icon at the top right,
or download an individual ticket by tapping the ``download`` icon in a ticket card.

Order information
^^^^^^^^^^^^^^^^^
.. list-table::

    * - .. image:: ../_static/images/usage/Pers-page-order.png
           :target: ../_static/images/usage/Pers-page-order.png
           :alt: Order overview

A simplified order overview that is not visible to share recipients.

Invoice
^^^^^^^
.. list-table::

    * - .. image:: ../_static/images/usage/Pers-page-order.png
           :target: ../_static/images/usage/Pers-page-order.png
           :alt: Order overview

This tab is only visible if invoices are enabled at the event level. See `Event settings <events.html#event-settings>`_.
Fill in the form, :guilabel:`Save` it and you will be able to download the invoice.

Scan App
^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  Data in Scan App

       .. figure:: ../_static/images/usage/Pers-scan-app.png
          :target: ../_static/images/usage/Pers-scan-app.png
          :alt: Data in Scan App

   .. grid-item::

       When you scan a personalised ticket, all the data is displayed in the green box on the scan screen.

Tips
----
.. note::
   It can also be useful to use the personalisation module for events that don't use personalisation.
   It will allow customers to simply present the QR codes at a scanning point without printing them,
   or to download all or individual tickets.
