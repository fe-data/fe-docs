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

       If the :guilabel:`Personalised` checkbox is unchecked, the field will be displayed on the order form.
       This means that the field has the same value for all tickets and can't be changed once the order has been submitted.

       If the :guilabel:`Personalised` checkbox is checked, the field must be personalised for each ticket.

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

       You can save 4 hits on your server by using the shortcode ``[fe_personalise cdn]``.
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

If you deselect it, tap on the :guilabel:`Layout fields` and select the fields you want to print on the PDF of the eTicket.
The order in which they are selected is also the order in which they are printed.

Use personalisation
-------------------

Interface
^^^^^^^^^
Coming soon ...

Share tickets
^^^^^^^^^^^^^
Coming soon ...

Personalise ticket
^^^^^^^^^^^^^^^^^^
Coming soon ...

Download tickets
^^^^^^^^^^^^^^^^
Coming soon ...

Order information
^^^^^^^^^^^^^^^^^
Coming soon ...

Invoice
^^^^^^^
Coming soon ...

Scan App
^^^^^^^^
Coming soon ...

Tips
----
Coming soon ...
