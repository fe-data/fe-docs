Changelog
=========

v2.1.0 (16 feb 2024)
------------------------
* Added personalisation for tickets. Input fields can now be defined at the order level or ticket level and
  attach input fields to ticket types. Ticket personalisation can be embedded into the **Redirect after booking** page using a shortcode
  or as a link in the order confirmation email.
* New input field types for date and time and, minimum and maximum values.
* The layout of the QR code info block on the PDF eTicket can now be customised with personalisation fields or order information.
* New email filters: fast_events_mail_from, fast_events_mail_from_name and fast_events_mail_charset.
* Replaced languages directory by i18n.

v2.0.1 (04 Jan 2024)
--------------------
* Corrected authorisation permissions for reading/deleting order logs.
* Set default template-id for tickets

v2.0.0 (30 Dec 2023)
--------------------
* Major refactor of the administration interface. The :doc:`FE Admin App <../apps/admin>` is now available for Android, IOS **and Web**.
  They all share the same codebase which is a huge saving in maintenance.
* The administration interface can be installed separately as Web maintenance interface for the plugin or the :doc:`FE Admin App <../apps/admin>`
  can be used on a phone or tablet on Android or IOS.
* Both the browser version and the version for a phone or tablet have a fully responsive layout.
* From now on, the management web interface can be updated separately without the need for a new version of the plugin.
  Updates can be performed manually or fully automatically.
* Redesign of the authentication system. There is no migration from the old system to the new one.
* New :doc:`public REST API's <../advanced/api>` are available.
* This release requires :doc:`FE Admin <../apps/admin>` v4.0.0 or higher.
