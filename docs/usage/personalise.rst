Ticket personalisation
======================

The following step‑by‑step guide explains how to configure ticket personalization and shows how the end user can ultimately personalize their tickets.

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

       If the :guilabel:`Personalise` checkbox is unchecked, the field appears on the order form.
       Its value will be the same for all tickets and cannot be changed after the order is submitted.

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

Simply tap :guilabel:`Fields for personalisation` and choose the fields you want to use.
The order in which you select them determines the order in which they will appear during personalisation.

.. note::
   Example: Suppose you have two personalization fields, and you want the second one to appear first in the personalization dialog, with the first field shown last.
   Tap :guilabel:`Fields for personalisation`, select the last field, and click ``Ok``. Then tap :guilabel:`Fields for personalisation` again, choose the first field, and click ``Ok``.

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

       You can reduce server load by up to five requests by using the shortcode ``[fe_personalise cdn]``.
       Instead of pulling the supporting files from your own server, the shortcode loads them from Cloudflare’s global CDN.

       You can also use the **dark** attribute in the shortcode.
       The default theme is light, but if your site has a dark background you can switch to the dark theme.
       You may combine it with the **cdn** attribute, resulting in a shortcode like: ``[fe_personalise cdn dark]``.

4. Use in order email
^^^^^^^^^^^^^^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item::

       Insert the keyword ``{%PERSONALISE%}`` anywhere in the body of the email.

       The customer will see a button in the email that, when clicked, takes them to the page referenced in step 3.

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

Checking the :guilabel:`Default layout` checkbox causes the default QR-code info block to be printed in the eTicket PDF.

If you deselect it, tap :guilabel:`Layout fields` and choose up to 6 fields you want to print on the eticket PDF.
The order in which you select them determines the order in which they appear on the PDF.
Just as with the :guilabel:`Fields for personalisation`, you may need to open and close the dialog multiple times to set the correct order.

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

You can, of course, personalize shared tickets yourself. However, once you’ve done so,
anyone who receives the shared ticket will see the data if they try to personalize it.
Conversely, if another person has already personalized a ticket and you attempt to personalize it,
you’ll receive a warning that the ticket has already been personalized.
The existing data will be displayed, and you won’t be able to edit it.

Once all tickets have been personalized, the QR codes become visible.

Download tickets
^^^^^^^^^^^^^^^^
.. list-table::

    * - .. image:: ../_static/images/usage/Pers-page-download.png
           :target: ../_static/images/usage/Pers-page-download.png
           :alt: Download tickets

Download all tickets by tapping the ``tickets`` icon at the top right,
or download an individual ticket by tapping the ``download`` icon on that ticket's card.

Order information
^^^^^^^^^^^^^^^^^
.. list-table::

    * - .. image:: ../_static/images/usage/Pers-page-order.png
           :target: ../_static/images/usage/Pers-page-order.png
           :alt: Order overview

A simplified order overview that is hidden from share recipients.

Invoice
^^^^^^^
.. list-table::

    * - .. image:: ../_static/images/usage/Pers-page-invoice.png
           :target: ../_static/images/usage/Pers-page-invoice.png
           :alt: Invoice

This tab is visible only when invoices are enabled at the event level. See `Event settings <events.html#event-settings>`_.
Fill in the form, click :guilabel:`Save`, and you will be able to download the invoice.

Scan App
^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  Data in Scan App

       .. figure:: ../_static/images/usage/Pers-scan-app.png
          :target: ../_static/images/usage/Pers-scan-app.png
          :alt: Data in Scan App

   .. grid-item::

       When you scan a personalized ticket, all of the data appears in the green box on the scan screen.

Tips
----
.. note::
   The personalization module can also be useful for events that don’t require personalization.
   It lets customers simply present the QR codes at a scanning point without printing them,
   or download all tickets—or individual tickets—if they wish.
