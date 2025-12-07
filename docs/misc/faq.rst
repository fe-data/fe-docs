FAQ
===

Downloading tickets fails
-------------------------
Take a look in the `errorlog <../usage/tools.html#error-log>`_. The PDF template used may not be present.
For example, you will see the following message in the errorlog.

.. code-block:: text
   :linenos:

    2025-03-13 17:26:53
    REST API
    Cannot find PDF template id 60. Change the ticket types by selecting an existing PDF template.

I get "Invalid address (setFrom)"
---------------------------------
First of all check your :doc:`settings <../getting-started/settings>` if your emailaddress is valid.
If it is valid and you are still getting this error, most likely your PHP version is the culprit.
You can check this by executing the following piece of code on your hosting platform

.. code-block:: php
   :linenos:
   
    <?php
    echo "PHP version: " . phpversion() . "\n";
    echo "PCRE version: " . PCRE_VERSION . "\n";

If the PCRE version is lower than **10.32 2018-09-10 1**, you have to go back to your hosting provider and ask for an updated version of PHP which includes PCRE 10.32 or higher.

How do I remove the order-id in the qrcode block?
-------------------------------------------------
Use the :doc:`fast_events_ticket_text <../hooks/ticket_text>` filter which can change/remove any line in the info-block.
Here is an :doc:`example <../hooks/ticket_text>`.

Is there a premium version of the plugin?
-----------------------------------------
Noop, this is it and it’s all for free. If you like this plugin, or it is useful to you in some way,
please consider a :doc:`donation <../misc/donate>` and give it a review on WordPress.org.

Is *Fast Events* integrated with an accounting package?
-------------------------------------------------------
No. But it’s quite easy to implement with the :doc:`fast_events_new_order <../hooks/new_order>` action.
Here is an :doc:`example <../hooks/new_order>`.