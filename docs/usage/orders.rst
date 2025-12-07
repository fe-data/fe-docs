Orders
======
.. list-table::

    * - .. image:: ../_static/images/usage/Orders.png
           :target: ../_static/images/usage/Orders.png
           :alt: Overview orders
    
Choose your event in the drop-down box and it will show you all the orders of the specified event.
Sort orders by clicking on the header descriptions. On smaller screens select the filter-icon and choose on which field to sort.

Double clicking/tapping on a card or line brings you straight to the order `details`_.

Pulling down the list triggers a refresh of the orders.

Adding a new order can be done by clicking/tapping the ``+``-icon. The order will have the order status ``Dashboard``.

Searching
---------
Searching is done on ``Id``, ``Name``, ``Email``, ``Order created``, ``Payment status`` and ``Custom status``.

Searching starts after every typed character.

Customer support
----------------
Circumstances may cause customers not to receive an order e-mail and thus request help from the event organisation.
Every order that has been paid has an order number in the description of the payment statement in the credit card or banking environment.

So when a customer reports, the first question should be: "What is your order number?".
The second question should be: "What are the last 4 digits of your credit card or bank number?", so you can verify the claim.
This information is visible in the ``Details`` choice of the popupmenu. On smaller screen press the information-icon in the header.

If the order id is not listed in you current event, it may be part of another event if you are working with multiple events.
You can search for an order id in all events by searching for '@{ORDER-ID}' and ENTER. So for example, :guilabel:`@123`.

.. list-table::

    * - .. image:: ../_static/images/usage/Order-details.png
           :target: ../_static/images/usage/Order-details.png
           :alt: Order details
    

Orders popupmenu
----------------

Details
^^^^^^^
Show the detailed payment information, the value of every input field and how many tickets of every type where bought.
By default the ``Payment information`` is not visible. Just click/tap the dropdown icon to show the info, if you are allowed.

.. note:: All detailed payment information is stored at Mollie; the Fast Events plugin does not keep copies of this information.

----

Email
^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  Email overview

       .. figure:: ../_static/images/usage/Order-email-main.png
          :target: ../_static/images/usage/Order-email-main.png
          :alt: Email overview

   .. grid-item-card::  Event details

       .. figure:: ../_static/images/usage/Order-email-detail.png
          :target: ../_static/images/usage/Order-email-detail.png
          :alt: Event details

An overview of the order‑confirmation emails sent is displayed, and if `email webhooks <email-webhooks.html>`_ are configured,
it will also show the various events reported by the email provider — provided, of course,
that you configured them during the setup of your email provider.

Tapping the card shows the raw email‑webhook information sent by the email provider.

Sliding the card left or right lets you remove this email log.

The email icon opens a pop‑up window that lets you resend the order‑confirmation email.
The default address is the one used during ordering, but it can be changed.

----

Share
^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  Share tickets/invoice

       .. figure:: ../_static/images/usage/Order-share.png
          :target: ../_static/images/usage/Order-share.png
          :alt: Share tickets/invoice

   .. grid-item::

       Share the link or the PDF of all tickets or invoice.

       You can only share tickets if the :guilabel:`tickets` flag in the event definition has been set. Likewise for :guilabel:`invoices`.

----

Edit customer
^^^^^^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item::

       Change the name, emailaddress and customer status of the customer.

   .. grid-item-card::  Edit customer

       .. figure:: ../_static/images/usage/Order-edit-customer.png
          :target: ../_static/images/usage/Order-edit-customer.png
          :alt: Edit customer

----

Refund
^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  Refund order

       .. figure:: ../_static/images/usage/Order-refund.png
          :target: ../_static/images/usage/Order-refund.png
          :alt: Refund order

   .. grid-item::

       Refund order while deducting the costs as configured in the `Refund costs <../getting-started/settings.html#refund-costs>`_ parameter in the Settings-menu.

       .. warning:: Do not use the Mollie dashboard for refunding.

----

Delete order
^^^^^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item::

       Delete order and all related e-tickets.

   .. grid-item-card::  Delete order

       .. figure:: ../_static/images/usage/Order-delete.png
          :target: ../_static/images/usage/Order-delete.png
          :alt: Delete order

----

Delete tickets
^^^^^^^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  Delete tickets

       .. figure:: ../_static/images/usage/Order-delete-tickets.png
          :target: ../_static/images/usage/Order-delete-tickets.png
          :alt: Delete tickets

   .. grid-item::

       Remove all tickets from the order. Download is no longer possible.

----

Create tickets
^^^^^^^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item::

       Create tickets for an order. This is only possible if the order has no tickets yet.
       If these are new tickets, it’s advisable to email the customer the updated ticket information, since the QR codes have changed.

   .. grid-item-card::  Create tickets

       .. figure:: ../_static/images/usage/Order-create-tickets.png
          :target: ../_static/images/usage/Order-create-tickets.png
          :alt: Create tickets

----

Checkin
^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  Checkin

       .. figure:: ../_static/images/usage/Order-checkin.png
          :target: ../_static/images/usage/Order-checkin.png
          :alt: Checkin

   .. grid-item::

       You have the option to put tickets from the order on scanned or vice versa.
       If a ``Level scan`` and ``Exit scan`` have been scanned, they will be shown as well.

       If you un-check a ``Start scan`` all associated ``Level scans`` and ``Exit scans`` will be removed as well.

       If for whatever reason you want to invalidate a ticket, you could use the submenu :guilabel:`Delete tickets`
       of the popupmenu or simply check the ``Start scan``, which means the ticket-holder no longer can pass the entrance.
       Usually it is best to use the latter option, because the entry remains visible in an export of all tickets.
       This is obviously not the case when the tickets are removed.

----

Error log
^^^^^^^^^
.. grid:: 2
   :gutter: 2

   .. grid-item-card::  Error overview

       .. figure:: ../_static/images/usage/Order-error-main.png
          :target: ../_static/images/usage/Order-error-main.png
          :alt: Error overview

   .. grid-item-card::  Error details

       .. figure:: ../_static/images/usage/Order-error-detail.png
          :target: ../_static/images/usage/Order-error-detail.png
          :alt: Error details

Any errors related to this order.
In most cases, it is an incorrect email address that caused a bounce, or the recipient marked the message as spam.

If you tap on the card, detailed raw information - if available - is shown.

.. note:: Bounce, spam reports, or any other events related to an order‑confirmation email are visible in the logging
          system only if `email webhooks <email-webhooks.html>`_ are enabled.
