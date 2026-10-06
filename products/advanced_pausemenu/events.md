# Advanced Pausemenu — Internal registration reference

This index locates literal registrations in the uploaded code, including local handlers, network handlers, NUI and callback wrappers. It is a maintainer lookup, **not a stable public API contract**. Event signature parameters exclude the implicit server event source. Registration does not prove an event should be called externally. Preserve original sender, session, permission, proximity, metadata and state checks.

Dynamic commands/exports and config-selected names also exist. See the commands/export pages for resolved names. Entries in comments or unexecuted diagnostic branches can be present; developer-only registration conditions must be checked in source. Parameters are nearest inline handler signatures, not validated documentation of payload schemas.

| Registration | Side | Name | Handler parameters | Source |
| --- | --- | --- | --- | --- |
| RegisterNUICallback | client | `close` | `_, cb` | `client/main.lua:221` |
| RegisterNUICallback | client | `map` | `_, cb` | `client/main.lua:226` |
| RegisterNUICallback | client | `settings` | `_, cb` | `client/main.lua:231` |
| RegisterNUICallback | client | `inventory` | `_, cb` | `client/main.lua:236` |
| RegisterNUICallback | client | `runCommand` | `data, cb` | `client/main.lua:263` |
| RegisterNUICallback | client | `waypoint` | `data, cb` | `client/main.lua:278` |
| RegisterNUICallback | client | `disconnect` | `_, cb` | `client/main.lua:291` |
| RegisterNUICallback | client | `refresh` | `_, cb` | `client/main.lua:297` |
| RegisterCommand | client | `escmenu` | `` | `client/main.lua:304` |
| RegisterCommand | client | `map` | `` | `client/main.lua:308` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/main.lua:344` |
| lib.callback.register | server | `advanced_pausemenu:server:getStatus` | `source` | `server/main.lua:29` |
| RegisterNetEvent | server | `advanced_pausemenu:server:disconnect` | `` | `server/main.lua:51` |
