Changelog
=========
v1.4.0 (5 Dec 2022)
--------------------
* New: PHP 8.0 or higher is needed.
* New: Optional event_ids as emailaddress suffix in the authorisation settings limiting the access to the specified event_ids.
* New: The plugin is now SaaS enabled and can be used as a ticketing service for multiple companies, associations, ...
* New: Ability to set a sender and email address per event.
* New: Optional cache order forms if the Ordering API is used.
* New: Option of no border around the qrcode block in PDF tickets.
* New: FE Admin 1.6 will only work with Fast Events 1.4.0 or higher.
* Change: Ordering status lines are now optional in the `Miscellaneous settings <../getting-started/settings.html#miscellaneous-settings>`_
* Fix: Order paging length state saved in frontend.
* Fix: PDF template selection is now sorted.
* Fix: Order submit button is now disabled after submitting a new order.

v1.3.0 (24 Feb 2022)
--------------------
* New: Ordering API added for generating order forms so that the client frontend can be integrated with other, non-WordPress, development environments.

v1.2.2 (24 Jan 2022)
--------------------
* New: Use '{%YEAR%}' in email templates

v1.2.1 (17 Nov 2021)
--------------------
* Fixed: Authorization bug

v1.2 (26 Okt 2021)
------------------
* New: For sport events -> It is possible to give users the option of sharing their track in real time with family and friends as they travel it.
  This feature requires `FE Tracking <https://fe-tracking.fast-events.eu/>`_ (v1.3 or higher)

v1.1 (29 Sep 2021)
------------------
* New: ``{%DEEPLINK%}`` parameter in emails or ``[fe-ticket downloadtext"Download in App"]`` shortcode in orderpage ->
  Adds a link so a ticket can be directly imported into the `FE Tracking App <https://fe-tracking.fast-events.eu/>`_ (v1.2 or higher)
  without having to download or scan it first.

v1.0 (1 Sep 2021)
-----------------
* First release
