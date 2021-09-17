Orders
======
.. list-table::

    * - .. image:: ../_static/images/usage/Orders.png
           :target: ../_static/images/usage/Orders.png
           :alt: Overview orders
    
Choose your event in the drop-down box and it will show you all the orders of the specified event.

.. sidebar:: Order details
    
    Use the ``Quick order search`` input field to get an instant overview of orderdetails. You can type in the order-number and press the enter-key or click the search-button. The search is across all events. If the order belongs to another event which is not displayed, it will automatically lookup the right event, display it and filter on the specified order-number.

.. list-table::

    * - .. image:: ../_static/images/usage/Order-details.png
           :target: ../_static/images/usage/Order-details.png
           :alt: Order details
    
The :guilabel:`Search` input searches through all orders fields of the selected event and only shows the rows that meet the criteria.

.. tip:: If you want to sort on multiple columns. Press the SHIFT-key and click on multiple column headers.

Button bar
^^^^^^^^^^
The top-left button bar has the following functionality:

- Exports all orders of the event to a ‘*csv-file*’, which can be picked up by Excel and do your own data analysis by creating your own pivot-tables and charts.
- Exports all e-tickets to a ‘*csv-file*’, which can be picked up by Excel. If the tickets have been scanned, the timestamp and location is also available in the export.
- Hide/show columns in the table view.
- Summary of the counted ticket-types per ``Payment status`` in a popup-window.
- Summary of the scanned tickets in a popup window.
- Add a new order from the dashboard. Enter the details in the popup window and click :guilabel:`Save new order`. The customer receives an email that is identical to if he would have placed the order himself. The main difference is that there is no payment involved. This function is only available if the ``Dashboard orders`` flag is set in the ‘Basics -tab‘ of the event.

Context menu
^^^^^^^^^^^^
There is a context-menu if you scroll through the orders; **use the right mouse-button** to make it visible and the chosen action is applied on the order where you did the right click.

**Details**
   In a popup window it will show the detailed payment information, the value of every input field and how many tickets of every type where bought.
**Email**
   A popup window gives you the possibility to resend the order confirmation email. The default value is the emailaddress used during ordering, but it can be changed.
**Edit customer**
   Change the name and/or emailaddress of the customer.
**Checkin**
   In a popup window you have the option to put tickets from the order on scanned or vice versa. If level 1 scans (Staged scans) and level 9 scans (Exit scan) are scanned they will be shown as well. If you un-check a level 0 scan all associated level 1 and level 9 scans will be removed as well. If for whatever reason you want to invalidate a ticket, you could use the submenu ‘Delete tickets‘ of the context-menu or simply check the level 0 scan, which means the ticket-holder no longer can pass the entrance. Usually it is best to use the latter option, because the entry remains visible in an export of all tickets. This is obviously not the case when the tickets are removed.
**Custom status**
   This menu-option is only enabled if you filled in the :guilabel:`Optional miscellaneous` settings of the plugin settings. See the example ‘Ship a signed photo book’ on the examples-page.
**Delete order**
   Delete order and all related e-tickets.
**Delete tickets**
   Remove all tickets from the order.
**Create tickets**
   Create tickets for order. This is only possible if there are no tickets yet. If these are new tickets, it is advisable to send the customer an email with the new ticket information, since the qrcodes have been updated.
**Download tickets**
   Download the tickets in a separate window as a pdf-file. This is only possible if there are tickets (customer paid for the order or a dashboard order) and the :guilabel:`tickets` flag in the event definition has been set.
**Download invoice**
   Download the invoice in a separate window as a pdf-file. This is only possible if the :guilabel:`invoice` flag in the event definition has been set.
**Refund order**
   Refund order while deducting the costs as configured in the ``Refund costs`` parameter in the Settings-menu.

   .. warning:: Do not use the Mollie dashboard for refunding.
   

