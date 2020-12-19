Security
========
This is by no means an exhaustive list of security measurements you should take to protect your website and data. Its already a good start if you take security seriously and that you orientate your self what can be done and how to keep security up to date.

A couple of suggestions which are quite important as a starting point.

* Make sure you run the latest version of WordPress and all the plugins you use.
* Check your PHP version. Right now the latest version is 7.4.
* Use two-factor (2FA) or multi-factor authentication (MFA) for your hosting-account and WordPress admin account. Consider the usage of a password manager, e.g. Lastpass, 1Password, Dashlane, …
* Don’t use the username ‘*admin*’ as you WordPress admin account. Use a random string as username.
* Does you hosting-provider offer automatic backups? If not, consider a plugin like `UpdraftPlus – Backup/Restore <https://wordpress.org/plugins/updraftplus/>`_.
* Always use HTTPS. Most hostingprovider nowadays support Let’s Encrypt free certificates.
* …

The next ones require in-depth knowledge of your hosting environment. Only use them if you know what you are doing!

HTTPS
-----
Most hosting providers offer free ‘*Let’s Encrypt*’ certificates for HTTPS. Use them! Often you can configure them in your Directadmin or cPanel environment of your webserver.

But this is not enough. You have to make sure your webserver only serves HTTPS requests. In general you can include the following snippet in your :file:`.htaccess` file.

.. code-block:: apache
   :linenos:

   RewriteEngine On
   RewriteCond %{HTTPS} off
   RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

Add you domain to the Strict-Transport-Security preload list. Goto `https://hstspreload.org/ <https://hstspreload.org/>`_ Only do this if you are absolutely sure. Adding your domain to the list is a simple step. Taking it off the list is painful and slow. Before you add your domain to the list, add the next snippet to your ``.htaccess`` file.

.. code-block:: apache

   Header set Strict-Transport-Security "max-age=63072000; includeSubdomains; preload"

Security headers
----------------
A few security headers you should consider adding to your :file:`.htaccess` file. Only do so if you know what you are doing.

.. code-block:: apache
   :linenos:

   Header append X-FRAME-OPTIONS "SAMEORIGIN"
   Header set X-XSS-Protection "1; mode=block"
   Header set X-Content-Type-Options "nosniff"
   Header set X-Permitted-Cross-Domain-Policies "master-only"
   Header set Referrer-Policy "same-origin"

Two Factor Authentication
-------------------------
Protect you WordPress admin login (and other logins as well) with the `Two Factor <https://wordpress.org/plugins/two-factor/>`_ plugin.

Disable File Editing
--------------------
WordPress comes with a set of easy-to-reach theme and plugin editors. You can find them under :guilabel:`Appearance` > :guilabel:`Theme Editor` and :guilabel:`Plugins` > :guilabel:`Plugin Editor`. These allow direct access to your site’s code.

While these tools are useful to some, many WordPress users aren’t programmers and will never need to touch anything here.
WordPress has a constant to disable editing from Dashboard. Placing this line in :file:`wp-config.php`.

.. code-block:: text

   define('DISALLOW_FILE_EDIT', true);
  
Online security check
---------------------
There are a few sites that offer online security checks.
`https://www.ssllabs.com/ssltest/ <https://www.ssllabs.com/ssltest/>`_ offers you a deep analysis of the configuration of your SSL web server. If everything is ok, your grade should be ``A+``.
`https://securityheaders.com/ <https://securityheaders.com/>`_ checks your HTTPS security headers you have configured in the :file:`.htaccess` file. Grades A and A+ are a good score.

There are many more. Google is your friend.

Realtime security plugins
-------------------------
WordPress is the most popular and widely used CMS platform on the Internet. Almost 1/3 of all websites globally use WordPress. As a result of this popularity, hackers and spammers have taken keen interest in breaking the security of WP-operated sites.
Here is a list of some free and paid security plugins that can be used to keep your WordPress site secured:

* `Wordfence <https://wordpress.org/plugins/wordfence/>`_
* `iThemes security <https://wordpress.org/plugins/better-wp-security/>`_
* `Sucuri security <https://wordpress.org/plugins/sucuri-scanner/>`_
* `All In One WP Security & Firewall <https://wordpress.org/plugins/all-in-one-wp-security-and-firewall/>`_
* `MalCare Security and Firewall <https://wordpress.org/plugins/malcare-security/>`_
* `Bulletproof security <https://wordpress.org/plugins/bulletproof-security/>`_
* ...

Further reading
---------------
Have a look at `https://premium.wpmudev.org/blog/ultimate-guide-wordpress-security/ <https://premium.wpmudev.org/blog/ultimate-guide-wordpress-security/>`_.
