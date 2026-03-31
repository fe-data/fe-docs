Payment Providers
=================

*Fast Events* supports Mollie, PayPal, and Stripe as payment providers.
The focus of Mollie is the Eurozone, whereas PayPal and Stripe operate worldwide.

Before configuring the `payment‑provider settings <../getting-started/settings.html#payment-provider-account>`_, you need a fully functional environment in Mollie, PayPal, or Stripe.
That means both the test environment (sandbox) and the live environment of the provider must be working.

You can create one of the accounts below by clicking the respective logo. None of the providers charge periodic fees for using a standard environment.
Fees are only incurred when transactions (ticket sales) are processed through *Fast Events*.

.. image:: ../_static/images/getting-started/Mollie.png
   :target: https://my.mollie.com/dashboard/signup/5835294
   :alt: Mollie

.. image:: ../_static/images/getting-started/Paypal.jpg
   :target: https://www.paypal.com/us/webapps/mpp/account-selection
   :alt: Paypal

.. image:: ../_static/images/getting-started/Stripe.png
   :target: https://dashboard.stripe.com/register
   :alt: Stripe

Points of attention
-------------------

Order expiration
^^^^^^^^^^^^^^^^
In the payment settings, it is possible to specify when an order expires.
If this setting is set to ``0``, the payment provider determines when the order expires for each payment method.
This can sometimes be hours or even days. The latter is the case, for example, when payment methods that accept bank transfers have been selected.
Therefore, it is advisable to select only card transactions as the payment method.
Often, those have a shorter expiration time.

While an order has the status ``open``, the tickets are locked by *Fast Events* and they are only released when the order expires.
Therefore, it is advisable to choose a timer of 10 or 15 minutes anyway.

Let end‑users know on the order page that the tickets are reserved for a duration of 10 minutes (or another value).
If payment is not made within 10 minutes, the transaction expires and the tickets are released again.

Because Fast Events works with a so‑called “authorization” and “capture” flow, once the customer has given authorization for the payment,
the payment will be released again by *Fast Events* if the expiry timer did fire before the authorisation.

Refunds
^^^^^^^
Refunding paid orders is, of course, possible, with the optional ability to retain a fixed amount as incurred fees.

Always perform a refund using the Management interface or the FE Admin App.

Use preferably not the refund options that the payment provider offers in its dashboard.
In the case of, for example, multi‑select events, where there is one payment for all events, the Fast Events plugin will set all orders to ``refunded``.
With the FE Admin App an individual order can be refunded.

----

Basic configuration
-------------------

Mollie
^^^^^^
Below is the JSON snippet you need to fill in for the ``Payment configuration`` in the settings.
Copy the keys from the Mollie :guilabel:`Dashboard` -> :guilabel:`Developers` into the ``live_key`` and ``test_key`` fields.
Be sure to enter valid JSON, and you can verify it with online tools such as https://jsonbeautifier.org
The Mollie API key values start with ``live_…`` and ``test_…``.

.. code-block:: json

   {
        "type": "payment",
        "provider": {
            "class": "FeData\\FastEvents\\Payment\\Provider\\MollieProvider",
            "live_key": "your_live_key",
            "test_key": "your_test_key"
        }
    }

.. warning::
   Mollie does not support the "authorization" and "capture" flow for all payment methods.
   iDEAL does not support this, but its successor Wero, which will be rolled out in 2026, does support it.
   If iDEAL is used or any other payment method that does not support an “authorization” and “capture” flow,
   then it is best to set the “expire timer” to 15 minutes. This is the standard expiry that Mollie itself applies for iDEAL.

   See also: https://docs.mollie.com/docs/handling-payment-status#expiry-times-per-payment-method

   Still you can use a shorter timer. If after the order had expired, the user still paid, the amount will immediately be refunded in full
   and the payment status will be set to ``refunded``. But remember: this is only valid for payment methods that dont support
   the "authorization" and "capture" flow.

----

PayPal
^^^^^^
Below is the JSON snippet you need to fill in for the ``Payment configuration`` in the settings.
Copy the keys from the PayPal :guilabel:`Developer Dashboard` -> :guilabel:`Apps & Credentials` into the ``live_client_id`` and ``live_secret`` fields.
Switch to the sandbox environment and do the same for the ``test_client_id`` and ``test_secret`` fields.
Be sure to enter valid JSON, and you can verify it with online tools such as https://jsonbeautifier.org

.. code-block:: json

   {
        "type": "payment",
        "provider": {
            "class": "FeData\\FastEvents\\Payment\\Provider\\PaypalProvider",
            "test_client_id": "your_test_client_id",
            "test_secret": "your_test_secret",
            "live_client_id": "your_live_client_id",
            "live_secret": "your_live_secret"
        }
    }

Wait mode
~~~~~~~~~
Turn off the :guilabel:`Wait mode`!
PayPal webhook events do not arrive instantly as they do with Stripe and Mollie.
Therefore you cannot send the customer back to a page where, for example, tickets need to be personalized.
Because Fast events waits only up to 5 seconds for the order to be marked as paid, the customer will end up on the error page.
Send the customer to a generic page that, for example, states that an email will soon be sent with further instructions on how to personalize the tickets.
This way, the user experience is optimal.

----

Stripe
^^^^^^
Below is the JSON snippet you need to fill in for the ``Payment configuration`` in the settings.
Copy the keys from the Stripe :guilabel:`Dashboard` into the ``live_key`` and ``test_key`` fields.
The Stripe API key values start with ``sk_live_…`` and ``sk_test_…``.

.. code-block:: json

   {
        "type": "payment",
        "provider": {
            "class": "FeData\\FastEvents\\Payment\\Provider\\StripeProvider",
            "live_key": "your_live_key",
            "test_key": "your_test_key"
        }
    }

You'll notice that once you save the settings, several additions are made to the JSON configuration.
There are actually two webhooks added by *Fast Events* —one in the test environment and one in the live environment—that
keep *Fast Events* asynchronously informed about the settlement of a payment transaction.


.. code-block:: json

   {
        "type": "payment",
        "provider": {
            "class": "FeData\\FastEvents\\Payment\\Provider\\StripeProvider",
            "live_key": "your_live_key",
            "test_key": "your_test_key",
            "webhook_live_key": "whsec_live_generated",
            "webhook_test_key": "whsec_test_generated"
        }
    }

The contents of these fields are required to verify the webhook signature.
You can modify the webhook signature yourself in the Stripe Dashboard,
but make sure that the corresponding field—like the one shown—receives the updated signature.

----

SaaS configuration
------------------
With SaaS mode, it is possible to use *Fast Events* as a ticketing platform to which multiple organizations. associations, ... can be connected.
Each organization then has its own event(s) and its own *Fast Events* account on the platform.
You can then charge an application fee to the sellers on your platform. The fee can be calculated per order or per ticket.
The application fee can be set system‑wide, meaning the same for everyone, or you can configure it per individual account.

In the following paragraphs, it is explained how to configure this for each payment provider.

Steps required to connect a new organization to the platform:

1. Create a *Fast Events* account for the new organization in the `Admin accounts <../usage/tools.html#admin-accounts>`_ tool in the ``Tools``-section.
   Do **not** create the account in the WordPress dashboard.
2. Select the events the new organization can use.
3. Select the username created under step 1 in the `Saas menu <../usage/events.html#saas>`_ of each event owned by the seller.
4. If necessary, change the sender in the `Email tab <../usage/events.html#address-subject>`_.
   Verify that the email provider being used can work with this new sender.
5. Set ``Permissions`` in the `Admin accounts <../usage/tools.html#admin-accounts>`_ menu for the user created in step 1.
6. The customer can now use the `FE Admin App <../apps/admin.html#regular-accounts>`__ to authorize the platform to process payment information on behalf of the customer.
   Use the account created in step 1 to log in.
   The first time, you’ll be prompted to log in to the payment provider to grant *Fast Events* permission to perform transactions on behalf of the seller.
   Make sure the seller has both a test and a live environment set up with the payment provider; otherwise, you’ll need to fill in those details at this step.

If you first use the test environment (sandbox) and then want to switch to the live environment.
Then first revoke the authorization for access before making the switch.
You can do this in the Admin Interface under accounts.
Double‑click the account and revoke the authorization in the SaaS tab.

After the FE Admin App is started again, the app will once more ask the sub-merchant to grant permission to the platform owner to make payments and refunds on behalf of the sub‑merchant.
But this time in live mode.


Mollie
^^^^^^
You have to register an Application (= *Fast Events* ) once in the
`Mollie Dashboard <https://my.mollie.com/dashboard/signup/5835294>`_ via the menu ``Developers`` -> ``Apps``.
When entering the data, the ``Redirect URL`` should look like this ``https://example.com/wp-json/fast-events/v1/saas/authorize``.
If the registration is successful, the fields :guilabel:`Client-ID` and :guilabel:`Client-secret` can be filled in.

.. warning::
   Mollie does not support the ``authorization`` and ``capture`` flow in SaaS mode together with application fees.
   Therefore, take that into account when setting a possible expiration timer.

----

Paypal
^^^^^^
At the moment, the PayPal driver does not provide SaaS support.

----

Stripe
^^^^^^
Enable Connect in the Stripe Dashboard settings. Then go to ``Settings`` → ``Connect`` → ``Onboarding options``.
In the :guilabel:`OAuth` tab, enable ``Enable OAuth`` and enter the URI as ``https://example.com/wp-json/fast-events/v1/saas/authorize``,
replacing **example.com** with your own domain name.

After it is saved, you can enter the Client ID—starting with ``ca_``—into the :guilabel:`Client ID` field in the payment‑provider settings.
The ``client‑secret`` field is not used by Stripe.

Enable SaaS mode in the *Fast Events* settings and save the configuration.
After doing so, you’ll see that the Payment configuration has been expanded with two additional entries, as shown below.
These are the webhooks for the connected account in the live and test environments.

.. code-block:: json

   {
        "type": "payment",
        "provider": {
            "class": "FeData\\FastEvents\\Payment\\Provider\\StripeProvider",
            "live_key": "your_live_key",
            "test_key": "your_test_key",
            "webhook_live_key": "whsec_live_generated",
            "webhook_test_key": "whsec_test_generated",
            "saas_webhook_test_key": "whsec_test_generated",
            "saas_webhook_live_key": "whsec_live_generated"
        }
    }