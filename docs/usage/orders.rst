Orders
======
.. list-table::

    * - .. image:: ../_static/images/usage/Orders.png
           :target: ../_static/images/usage/Orders.png
           :alt: Overview orders
    
Choose your event in the drop-down box and it will show you all the orders of the specified event.
Sort orders by clicking on the header descriptions. On smaller screens select the filter-icon and choose on which field to sort.

Double clicking/tapping on a card or line brings you straight to the order `details`_.

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

Email
^^^^^
A popup window gives you the possibility to resend the order confirmation email.
The default value is the emailaddress used during ordering, but it can be changed.

Share
^^^^^
Share the link or the PDF of all tickets or invoice.
You can only share tickets if the :guilabel:`tickets` flag in the event definition has been set. Likewise for :guilabel:`invoices`.

Edit customer
^^^^^^^^^^^^^
Change the name, emailaddress and customer status of the customer.

Refund
^^^^^^
Refund order while deducting the costs as configured in the `Refund costs <../getting-started/settings.html#refund-costs>`_ parameter in the Settings-menu.

.. warning:: Do not use the Mollie dashboard for refunding.

Delete order
^^^^^^^^^^^^
Delete order and all related e-tickets.

Delete tickets
^^^^^^^^^^^^^^
Remove all tickets from the order. Download is no longer possible.

Create tickets
^^^^^^^^^^^^^^
Create tickets for order. This is only possible if there are no tickets yet.
If these are new tickets, it is advisable to send the customer an email with the new ticket information, since the qrcodes have been updated.

Checkin
^^^^^^^
You have the option to put tickets from the order on scanned or vice versa.
If a ``Level scan`` and ``Exit scan`` have been scanned, they will be shown as well.
If you un-check a ``Start scan`` all associated ``Level scans`` and ``Exit scans`` will be removed as well.
If for whatever reason you want to invalidate a ticket, you could use the submenu :guilabel:`Delete tickets`
of the popupmenu or simply check the ``Start scan``, which means the ticket-holder no longer can pass the entrance.
Usually it is best to use the latter option, because the entry remains visible in an export of all tickets.
This is obviously not the case when the tickets are removed.

Error log
^^^^^^^^^
Any errors related to this order.
