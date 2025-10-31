Performance
===========

PHP version
-----------
Make sure you run the latest version of PHP. Right now that is **8.4**
Most hosting providers give you the option to set the version via DirectAdmin or cPanel.

.. warning:: Make sure the PHP extensions ``gd``, ``imagick`` and ``opcache`` are enabled.
             With most hosting providers this can be done via DirectAdmin or cPanel.

WP Super Cache
--------------
The `WP Super Cache plugin <https://wordpress.org/plugins/wp-super-cache/>`_ turns your website files into static files,
so your pages are not delivered from time consuming WordPress scripts, but simply from these static files.
This ensures a speed gain since the PHP scripts do not have to be run every time.

Don’t cache dynamic pages! For *Fast Events* you have to make an exception for every **order-page**, **thank-you-page** and the **error-page**.
Add them in the ``Advanced`` tab of the WP Super Cache settings.

Autoptimize
-----------
The `Autoptimize plugin <https://wordpress.org/plugins/autoptimize/>`_ aggregates, minifies and caches scripts and styles,
injects CSS in the page head by default but can also inline critical CSS and defer the aggregated full CSS,
moves and defers scripts to the footer and minifies HTML. It may boost performance of your site, but make sure you test it.
Certainly if you use it in combination with a caching plugin and a CDN.

There is a kind of hidden feature in this plugin that lets you pre-compress the aggregated js and css-files.
A real time-saver, instead of compressing these files for every request, it serves the pre-compressed files straight from the cache.
Include the following snippet in the Snippets-plugin to enable this feature.

.. code-block:: php

   <?php
   add_filter('autoptimize_filter_cache_create_static_gzip','__return_true');

Translations
------------
*Fast Events* uses the WordPress translation API. This API is not very efficient and the WordPress Performance Team has come up
with the `Performant Translations <https://wordpress.org/plugins/performant-translations/>`_ plugin to speed up the API.
Tests have shown that this plugin can improve elapse time of the API by more than 20%.

**Important**: this new functionality has been merged into WordPress 6.5! However, this plugin is still useful!

On WordPress 6.5+, this plugin automatically converts existing .mo files to .php and afterwards only loads the translations from the .php file.
This is useful for cases where language packs are not downloaded from WordPress.org but somewhere else.

CDN
---
Consider using a CDN. There are many available, but `Cloudflare <https://www.cloudflare.com/cdn/>`_ has a free plan.
This can give your site really a boost.
It requires a fair amount of knowledge to configure this, but it can save a lot of hits on the server.

Redis
-----
Not every hosting provider is offering Redis. But some do and if you have a VPS you can configure it yourself.
Install the `Redis Object Cache plugin <https://wordpress.org/plugins/redis-cache/>`_ and it will cache objects in memory rather then getting information from the database every time.

Cloudflare
----------
Even with the free plan your site will hugely benefit from Cloudflare. You can just go for a simple caching approach by using the
free `Cloudflare plugin <https://wordpress.org/plugins/cloudflare/>`_;
here is an `example guide <https://themeisle.com/blog/cloudflare-for-wordpress-tutorial/>`_ how to do this.

Paid plans do offer extensive WAF (WordPress Application Firewall) rules, and a lot more, that can protect your site.


Use a Theme optimized for speed
-------------------------------
Consider using the `GeneratePress theme <https://wordpress.org/themes/generatepress/>`_.
At the moment it’s the fastest theme you can get in terms of size and speed.
The premium version offers you a ton of features and good support, and is definitely worth the money.

Database size
-------------
Keep your database as small as possible. If you have finished an event, remove it’s content before you start a new one.
Before you do, you can of course export all the orders, tickets and scans for archiving purposes or data analysis.

REST API server
---------------
Another option is to run WordPress only as a REST‑API server, without using it for any front‑end rendering.
For example, you can use `Cloudflare Pages <https://pages.cloudflare.com/>`_ as the front-end web server and call the `ordering API <api-ordering.html>`_ on the back-end to order etickets.
Enable :guilabel:`Use ordering API` in the `Miscellaneous-settings <../getting-started/settings.html#miscellaneous-settings>`_ for this scenario.
Then fill in the :guilabel:`Cache time orderscreen` and :guilabel:`Ordering shortcodes` fields.
