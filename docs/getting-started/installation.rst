Installation
============

Requirements
------------
*Fast Events* is integrated with `Mollie <https://my.mollie.com/dashboard/signup/5835294>`_ as payment provider, providing a variety of payment options. If online payments are used, the plugin currently only works for companies, associations, foundations ... located in a `SEPA country <https://wiki.xmldation.com/Support/EPC/List_of_SEPA_countries>`_.
With Mollie there are no fixed recurring costs, you only pay for successful transactions. Press the button below to create your free Mollie account. There is no region restriction for free tickets or RSVP events.

.. image:: ../_static/images/getting-started/Mollie.png
   :target: https://my.mollie.com/dashboard/signup/5835294
   :alt: Mollie

.. note::
   *Fast Events* has been tested on **WordPress 6.0** and above together with **PHP 8.0** and above.
   Older versions of WordPress and PHP are not supported! Make sure the PHP extensions ``gd``, ``imagick`` and ``opcache`` are enabled.
   With most hosting providers this can be done via DirectAdmin or cPanel.

Because the number and variety of plugins is vast and wide, we do not guarantee that the plugin will function with all third-party plugins, themes or browsers of any kind. We do not assume responsibility and will not be held responsible for any conflicts or compatibility issues that may occur due to third-party software. We assume no responsibility for any data loss as a result of installing or using *Fast Events*. Should conflicts occur with third-party software, we may provide support at our discretion.

For performance reasons *Fast Events* is using its own tables and not the WordPress custom post types approach. It requires the presence of the **InnoDB** storage engine in your database engine.

Installation
------------
There are 3 different ways to install *Fast Events*, as with any other registered WordPress plugin.

Using the WordPress Dashboard
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
1. Navigate to the :guilabel:`Add New` in the plugin dashboard
2. Search for ``Fast Events``
3. Click :guilabel:`Install Now`
4. Activate the plugin on the Plugin Dashboard

Uploading in WordPress Dashboard
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
1. Download the latest version of this plugin from https://wordpress.org/plugins/fast-events/
2. Navigate to the :guilabel:`Add New` in the plugins dashboard
3. Navigate to the :guilabel:`Upload` area
4. Select the zip file (from step 1.) from your computer
5. Click :guilabel:`Install Now`
6. Activate the plugin in the Plugin dashboard

Using FTP
^^^^^^^^^
1. Download the latest version of this plugin from https://wordpress.org/plugins/fast-events/
2. Unzip the zip file, which will extract the fast-events directory to your computer
3. Upload the *fast-events* directory to the ``/wp-content/plugins/`` directory in your web server
4. Activate the plugin in the Plugin dashboard

Web based FE Admin
------------------
From *Fast Events* version 1.10 and onwards you can install a Web based version of the FE Admin App. This PWA will be the default admin
interface for *Fast Events* version 2.0, which will be released later in 2023.

Currently there are 3 interfaces to modify the system: the admin interface, the public REST API and the FE Admin App.
These three systems will be merged so that 1 codebase can be maintained.
This means that only the settings menu will remain in the admin interface.
All other functionality will be housed in the FE Admin App.
There will not only be a version for Android and IOS, but also a web version which will only be supported on Chrome,
Safari and Edge. Other browsers may work but are not supported.

The current beta version can be downloaded from https://drive.proton.me/urls/P6JSBFSDK4#Upl2zS1tT7ir
Create a folder ``wp-fe-admin`` in the same directory where ``wp-admin``, ``wp-content``, ... are located.
Unzip the file in this newly created folder. Point you browser at ``http://yourdomain.con/wp-fe-admin``.

You can install the PWA in another directory if you want. Edit the ``index.html`` file of the PWA and change the line
``<base href="/wp-fe-admin/">`` to reflect the new location.

Demo data
---------
The plugin comes pre-loaded with some demo data. Give it a try and play around in the menu and the order contextmenu.
Place dashboard orders and give the :doc:`Scan App <../apps/scan>` a try.
If you want to try the :doc:`Payment App <../apps/payment>`, you first have to create your `free Mollie account <https://my.mollie.com/dashboard/signup/5835294>`_ to receive payments.

Next steps
----------
Read the :doc:`overview <overview>` of the steps required to organize an event. First, make sure you fill in the :doc:`settings <settings>` once.
