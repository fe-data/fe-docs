Changelog
=========

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

We will release the 2.1 version at the end of Q1 2024. This version is all about personalising etickets with input data to be entered after the order is placed.
Personalisation can be done by the order taker or by individuals who receive a link to one of the order taker's tickets.
The existing input fields will be used. However, the 2.1 upgrade should **not be done on an active event** because the internal structure of the orders will be different.
There will be **no conversion of the old orders** during the upgrade.


