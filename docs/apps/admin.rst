FE Admin App
============
With the FE Admin App, you can manage the entire *Fast Events* plugin.
Far-reaching possibilities to create and manage accounts and, for example,
limit their functionality and only grant access to selected events.

The App has a responsive design. On phones it will use cards to display the information and bottom-navigation
to navigate between ``Tools``, ``Events`` and ``Orders``. On larger screens, typically on phones in landscape mode
and tablets in portrait mode, it will show multiple cards side by side and navigation will be in a sidebar.

On large screens, desktop browsers and tablets in landscape mode, the information is displayed in table format.

Download
--------
The App is available for Android 9.0 and above and IOS 13 and above.

.. list-table::

    * - .. image:: ../_static/images/apps/Admin-Android.png
           :target: https://play.google.com/store/apps/details?id=nl.fe_data.admin
           :alt: FE Admin App
           :scale: 50%
      - .. image:: ../_static/images/apps/Admin-IOS.png
           :scale: 50%
           :target: https://apps.apple.com/app/fe-admin/id6448051190

Full list of capabilities
-------------------------
Depending on the permissions configuration, users will only see the components they are allowed to see.
The full list of components is shown below.
Permissions can be configured in the ``Permissions`` popupmenu choice in the :guilabel:`Accounts` tool.


Events
^^^^^^
#. Detailed overview.
#. Synchronise parts of an event with another event.
#. Detailed information about tickets sold.
#. Detailed information on scanning tickets in progress.
#. Basic settings.
#. Show and modify email templates.
#. Show, add, modify and delete input fields.
#. Show and modify PDF templates.
#. Show, add, modify and delete ticket types.
#. Show, add, modify and delete scan keys.
#. Show and modify seating plans.
#. Show and modify tracking information.
#. Show and modify Saas information.
#. Add event.
#. Duplicate event.
#. Delete all orders.
#. Delete event.

Orders
^^^^^^
#. Detailed overview of the order: it also requires displaying input fields permission.
#. Email the order.
#. Share tickets link.
#. Share tickets PDF.
#. Change the name, email address and custom status of the order.
#. Refund and order.
#. Delete an order.
#. Delete tickets.
#. Create tickets.
#. Checkin tickets.
#. Error log.
#. Add new orders).

Tools
^^^^^
#. Sales dashboard.
#. Scan a ticket to see its details. This is an informational scan only. It also requires order details permission
#. Show and delete logging entries.
#. Maintain email lists / closed user groups.
#. Show, add, modify and delete webhooks.
#. Show, add, modify and delete coupons.
#. Export orders to Excel format.
#. Export tickets to Excel format.
#. Export scans to Excel format.
#. Export events.
#. Import events.
#. Send bulk order emails.
#. Send bulk free format emails.
#. Bulk refund orders.
#. (Sub)account management.

Server accounts
---------------
The first time the App is launched, it will show the ``Server Account`` page where a new server can be configured.
Press the ``+`` button to add a new server.

Administrator accounts
^^^^^^^^^^^^^^^^^^^^^^
If the `Web management interface <../getting-started/settings.html#management-interface>`_ is installed
there is no reel need to use this type of account configuration. But of course, if you want to manage your events on the go,
you can do that too. But bear in mind that 'administrator' accounts always have full access to all functionality.
If full access is not needed, just configure a new regular account in the ``Accounts`` tool and limit its functionality.

To configure the 'administrator' account, enter any name, scan the qrcode on the
`Rest API settings <../getting-started/settings.html#rest-api-settings>`_ page of the plugin and enter the
login-name of the 'administrator' user in the 'Username' field.

For the application password, an application password needs to be created once in WordPress for the 'administrator' user.
Make sure you are logged into WordPress as an 'administrator' user and choose :guilabel:`Users` -> :guilabel:`Profile`.
Scroll down to the 'Application Passwords' section. Enter any name in ``New Application Password Name``
and press :guilabel:`Add New Application Password`.
The popup window now displays the generated application password. Copy and save it and use it in this server configuration of the App.

Now that all fields are filled in, press save (disk icon at top right). To login click/tap the card shown.

Regular accounts
^^^^^^^^^^^^^^^^
Create/maintain accounts in the `Accounts <../usage/tools.html#admin-accounts>`_ tool of the :guilabel:`Tools` section.
With the popupmenu choices you can configure all settings of the account.

**Add/change account**
   * **Basic settings - tab**
      #. **Login:**
         The login name of the account. This is only shown when creating an account.
         When the account is saved, a popup will show the application password. Be sure to save this in a safe location.
         You will not be able to retrieve it.
      #. **Name:**
         The descriptive name of the account.
      #. **Emailadress:**
         Use any emailaddress you want, even a non-existing one is ok. WordPress needs one, but Fast Events never uses it.
         Use a valid one if you want to use regular logins to WordPress for this account
      #. **Disable WordPress login:**
         The default is switched on. You can't use the account to login to WordPress and a password reset wil not work either.
      #. **Temporary blocking:**
         If enabled, the account is temporary blocked. The user cannot use the App.
      #. **Allowed endpoints:**
         A comma separated list of allowed endpoints. The default value is ``fast-events/v1``.
         But more can be added if there are other plugins using REST and if this user needs to be able to access those as well.
      #. **Maximum number of sub-accounts:**
         If this account is allowed - later in the ``Permissions`` settings - maintenance permission on its own account,
         specify here how many sub-accounts it can create. The sub-accounts all have the same set of permissions and
         events visibility as the account itself. But while defining it, you can narrow down the permissions even further.
         You can **never** extend them. If you want that, the 'administrator' first has to enable the extra permission on the account level.
   * **Authorised events - tab**
      Select the events the user has access to.
   * **Saas - tab**
      Only visible to 'administrator` accounts and if `Saas mode <../getting-started/settings.html#saas-mode>`_ has
      been in enabled in the settings.
      It wil show if the user has already authorised the plugin to manage payment transactions on its behalve.
      If authorisation has been given the 'administrator' can revoke it.
**Permissions**
   Select the permissions the account is allowed to use.
**Copy/paste permissions**
   This copies or pasts all permissions.
**Settings**
   It shows the configuration qrcode the user can scan to configure the account in the FE Admin App. Still the user has to manually enter
   the username and application password.
**Reset API**
   If the API key is reset, then all users of this account and its sub-accounts must re-enter the API key.
**Reset password**
   If the application password is reset, then all users of this account must re-enter the application password to continue using the App.
**Sub-accounts**
   Maintaining sub-accounts more-or-less follows the same rules as maintaining an account. Except it uses the API key that is defined
   at the account level and it uses the same ``Basic settings`` as defined at the account level.
**Delete account**
   Delete all information (including all sub-accounts!). Access to the App and the REST API is instantly disabled.

Once you have entered the server details, save them and click/tap the server card to log in.
To switch between accounts, simply press the top-left 'hamburger' menu and select a different account.

Desktop users
^^^^^^^^^^^^^
If the `Web interface <../getting-started/settings.html#management-interface>`_ has been installed it is also
possible to use it apart from WordPress in any webbrowser.
The URL is:

.. code-block:: html

   https://exampledomain.com/wp-content/uploads/fast-events/admin/

Just configure a regular account and you are good to go.

While it is possible to switch between different accounts on the same server in the browser version of the app,
it is **not possible** to switch between accounts on different servers.
The WordPress REST API has a strict CORS setting by default for security reasons.
By default, it is not allowed to use the REST API from a browser with pages loaded from another server.
The easiest way is then to define multiple bookmarks that point to the correct server. For example,
if you have the *Fast Events* plugin running on 2 servers, configure the URLs as follows:

.. code-block:: html

   https://exampleserver-1.com/wp-content/uploads/fast-events/admin/
   https://exampleserver-2.com/wp-content/uploads/fast-events/admin/

Nevertheless, for specialists versed in http header configurations and CORS, it is possible to access multiple servers from one location.
However, we strongly advise against this.

Usage
-----
The first time the App is launched and if *Fast Events* is running in ``SaaS mode`` and the sub-merchant has not yet
authorized access to its payment information, a ``Connect with Mollie`` screen will be displayed to authorise access.

The way the App works is pretty straightforward. You can use the buttons at the bottom or sidebar to switch
between ``Orders``, ``Events`` and ``Tools``.
As the App is responsive it either displays 1 or 2 cards side by side or information is shown in table format.

Pretty much every where you can double-tap on the content (card or line) to jump immediately to editing the content,
provided you the permission to do so. For other choices you have to tap/click the three vertical dots and either
a popupmenu or bottom-sheet will be shown.

How to use the different sections. Al examples are taken from the Web based version of the App. On other devices like
phones or tablets it may look differently, but the same functionality is offered.

* **Events administration**:
  :doc:`Events <../usage/events>`
* **Order administration**:
  :doc:`Orders <../usage/orders>`
* **Tools**:
  :doc:`Tools <../usage/tools>`
* **Example usage**
  :doc:`Tools <../usage/tools>`

Settings
--------
The App and Admin Web interface have some general settings. You can find them by clicking on the hamburger menu and selecting :guilabel:`Settings`.
Most settings are related to sharing information within the application. For example, when sharing information with an email application,
you can enter a subject and by default the text in the setting will be used.

Events
^^^^^^
**Details**
   Share subject of a short overview of the event details.
**Total sales**
   Share subject of an overview of the number of tickets sold.
**Total scans**
   Share subject of an overview of the number of scans per location and ticket type.

Orders
^^^^^^
**Details**
   Share subject of a short overview of the order details, including the tickets.
**Cache**
   If you switch between the order lists of different events, the order list is cached for this amount of minutes.
   You can always force to reload a fresh copy by pulling down the order list in the App or Web interface.

Tools
^^^^^
**Error log**
   Share subject of an overview of a specific error.
**Sales dashboard**
   Share subject of an overview of the number of tickets sold for the selected events.
**Coupon email subject**
   The default subject used when sending an email with coupon information.
**Coupon email body**
   Press the :guilabel:`Set email body` button to define the email body when sending an email with coupon information.
   This is the default body used when sending bulk coupon emails, but you can override the default by using the menu option to send the emails.
   The body can contain a number of keywords, that will be replaced with the information in the coupon.

   - :guilabel:`{%EMAIL%}` the email address in the coupon.
   - :guilabel:`{%CODE%}` the coupon code.
   - :guilabel:`{%AMOUNT%}` the discount percentage or amount.
   - :guilabel:`{%START-DATE%}` the coupon is valid from this date.
   - :guilabel:`{%END-DATE%}` the coupon is valid until this date.
   - :guilabel:`{%MIN-TICKETS%}` the minimum number of tickets required.
   - :guilabel:`{%MAX-TICKETS%}` the maximum number of tickets allowed.
   - :guilabel:`{%MIN-AMOUNT%}` the minimum amount required.
   - :guilabel:`{%MAX-AMOUNT%}` the maximum amount allowed.