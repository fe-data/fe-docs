Performance
===========

PHP version
-----------
Make sure you run the latest version of PHP. Right now that is **7.4**
Most hosting providers give you the option to set the version via DirectAdmin or cPanel.

.. warning:: Make sure the PHP extensions ``gd``, ``imagick`` and ``opcache`` are enabled. With most hosting providers this can be done via DirectAdmin or cPanel.

WP Super Cache
--------------
The `WP Super Cache plugin <https://wordpress.org/plugins/wp-super-cache/>`_ turns your website files into static files, so your pages are not delivered from time consuming WordPress scripts, but simply from these static files. This ensures a speed gain since the PHP scripts do not have to be run every time.

Don’t cache dynamic pages! For *Fast Events* you have to make an exception for every order-page, thank-you-page and the error-page. Add them in the ``Advanced`` tab of the WP Super Cache settings.

Autoptimize
-----------
The `Autoptimize plugin <https://wordpress.org/plugins/autoptimize/>`_ aggregates, minifies and caches scripts and styles, injects CSS in the page head by default but can also inline critical CSS and defer the aggregated full CSS, moves and defers scripts to the footer and minifies HTML. It may boost performance of your site, but make sure you test it. Certainly if you use it in combination with a caching plugin and a CDN.

There is a kind of hidden feature in this plugin that lets you pre-compress the aggregated js and css-files. A real time-saver, instead of compressing these files for every request, it serves the pre-compressed files straight from the cache.
Include the following snippet in the Snippets-plugin to enable this feature.

.. code-block:: php

   <?php
   add_filter('autoptimize_filter_cache_create_static_gzip','__return_true');
   
CDN
---
Consider using a CDN. There are many available, but `Cloudflare <https://www.cloudflare.com/cdn/>`_ has a free plan. This can give your site really a boost.
It requires a fair amount of knowledge to configure this, but there are also hosting providers such as `Vimexx <https://www.vimexx.nl>`_ that offer this as a standard option in some packages.

Redis
-----
Not every hosting provider is offering Redis. But some do and if you have a VPS you can configure it yourself. Install the `Redis Object Cache plugin <https://wordpress.org/plugins/redis-cache/>`_ and it will cache objects in memory rather then getting information from the database every time.

Use a Theme optimized for speed
-------------------------------
Consider using the `GeneratePress theme <https://wordpress.org/themes/generatepress/>`_. At the moment it’s the fastest theme you can get in terms of size and speed. The premium version offers you a ton of features and good support, and is definitely worth the money.

Database size
-------------
Keep your database as small as possible. If you have finished an event, remove it’s content before you start a new one. Before you do, you can of course export all the orders and tickets for archiving purposes or data analysis.
