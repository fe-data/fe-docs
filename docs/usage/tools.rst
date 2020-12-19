Tools
=====

Send order emails
-----------------
.. list-table::

    * - .. image:: ../_static/images/usage/Tools-order.png
           :target: ../_static/images/usage/Tools-order.png
           :alt: Send order emails

During normal operations there should not be a need to send order emails as they are emailed automatically after the customer has paid for the order. But maybe the email that automatically got send did contain a serious fault or omission, or if your email-system or email-provider wasn't available for a period of time.
Well than this tool might be handy. Make sure you make the necessary adjustments and off you go.

All conditions in the fields below are included in the selection.

After you click :guilabel:`Send order emails`, the system will show a popup dialog, where you need to confirm the action. A progress bar will keep you informed on the progress. Don’t close the window until the bar has reached 100%.

**Selected events**
   You can selected multiple events by using the CTRL-key together with the mouse.
**Order between dates**
   Click on the grayed out date and click on the first date and click on the last date. The orders between these date-times are processed.
**# Tickets between**
   Only orders with the number of tickets between these values are processed.
**Amount between**
   Only order amounts between these values are processed.
   
----

Mail Manager
------------
.. list-table::

    * - .. image:: ../_static/images/usage/Tools-mail.png
           :target: ../_static/images/usage/Tools-mail.png
           :alt: Send emails

The ‘*Mail Manager*‘ gives you the option to send e-mails to customers who have placed orders and all the conditions in the fields below have been met.

After you click :guilabel:`Send emails`, the system will show a popup dialog, where you need to confirm the action. A progress bar will keep you informed on the progress. Don’t close the window until the bar has reached 100%.

**Selected events**
   You can selected multiple events by using the CTRL-key together with the mouse.
**Order between dates**
   Click on the grayed out date and click on the first date and click on the last date. The orders between these date-times are processed.
**# Tickets between**
   Only orders with the number of tickets between these values are processed.
**Amount between**
   Only order amounts between these values are processed.
**Tickets scanned**
   Only orders with 1 or more tickets that have been scanned are processed.
**Email subject**
   Don't leave the amil subject empty
**Email body**
   A smart editor where you can create your own fancy styled email. A word of advice: keep it simple and small and don’t pull in large images. If you still have the desire to use images, use links from your own site or a CDN.

   You can use a couple of keywords and *Fast Events* will replace them with the info available in the order:
   
   - :guilabel:`{%NAME%}` is the name of the person who placed the order.
   - :guilabel:`{%EMAIL%}` is the email address of the person who placed the order.
   - :guilabel:`{%TICKETS%}` the unique link for downloading the e-tickets.
   - :guilabel:`{%INVOICE%}` the unique link for downloading the invoice.
   - :guilabel:`{%FIELDS%}` the input fields from the input-tab in table format.
   - :guilabel:`{%CONFIRM%}` only applicable for RSVP events (no e-tickets). The link to confirm that you will be present.
   
Don’t forget to test your email if it is ‘**spam-proof**‘. There are many tools available on the Internet, but we recommend using https://www.mail-tester.com/ Click the :guilabel:`Send test email` button and use the email address on the mail-tester site and within a minute you have detailed report. Be pretty serious about this, because if your email gets a high spam rating from receiving domains, your mails may end up in ‘*Spam*‘ folders or won’t be delivered at all.
Or worse, your domain can be blacklisted.

Deep dive
^^^^^^^^^
For the experts: the email itself is embedded in a container of maximum 600px wide. Always test on your mobile first if the email formats well.
Don’t include images straight from your camera, which can be several Mb’s. If you want to include images, keep the resolution at an acceptable level and pull the image through tools like https://kraken.io to squeeze the size.

*Fast Events* will ‘purify’ the email to prevent XSS-attacks, e.g. scripts are not allowed.

----

Refund orders
-------------
.. list-table::

    * - .. image:: ../_static/images/usage/Tools-refund.png
           :target: ../_static/images/usage/Tools-refund.png
           :alt: Refund orders

If you want to refund a single order, use the ‘Orders‘ menu. This tool is of use if for instance you have to cancel your event and you want to refund the costs. There is an option to withhold a fixed amount per order or ticket.

After you click :guilabel:`Refund orders`, the system will show a popup dialog, where you need to confirm the action. A progress bar will keep you informed on the progress. Don’t close the window until the bar has reached 100%.

**Selected events**
   You can selected multiple events by using the CTRL-key together with the mouse.
**Order between dates**
   Click on the grayed out date and click on the first date and click on the last date. The orders between these date-times are processed.
**# Tickets between**
   Only orders with the number of tickets between these values are processed.
**Amount between**
   Only order amounts between these values are processed.
**Costs per**
   Calculate the fixed deduction per *order* or per *ticket*.
**Cost**
   The deduction costs per order or per ticket.


