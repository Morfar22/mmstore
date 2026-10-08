# Phone adapters

LB Phone implements number lookup, client opening and client/server notifications through its documented exports.
qb-phone and framework read `PlayerData.charinfo.phone`; neither invents missing ESX/standalone phone metadata.
Those adapters do not provide phone opening, app integration or notification APIs.

For another phone, use `Phone = 'export'` with PhoneExport settings:

- Resource: installed resource name.
- ServerNumberExport: exact export name, called with source or character identifier.
- ServerNumberArgument: 'source' or 'character'.
- ServerNotifyExport: called with source and notification table.
- ClientNumberExport: called with no arguments; omit it to query your own server number callback.
- ClientOpenExport: called with no arguments.
- ClientNotifyExport: called with the notification table.

Only use matching documented signatures. An unset method returns an explicit configuration error.
For Quasar, Sky, NPWD or other providers with different argument order, payloads or SQL storage, add a custom phone adapter
instead of assuming their APIs match. Templates in custom-adapters.md show where to map these functions.

`dispatched` means the external call was made, not that a notification was delivered, stored or read.
Client LB notifications are transient; server behavior follows LB's own source-versus-phone-number rules.
The bridge does not implement SMS, mail, calls or custom phone apps; these can be added as explicit adapter capabilities.
