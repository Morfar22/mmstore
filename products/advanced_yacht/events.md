# Advanced Yacht — Internal registration reference

This index locates literal registrations in the uploaded code, including local handlers, network handlers, NUI and callback wrappers. It is a maintainer lookup, **not a stable public API contract**. Event signature parameters exclude the implicit server event source. Registration does not prove an event should be called externally. Preserve original sender, session, permission, proximity, metadata and state checks.

Dynamic commands/exports and config-selected names also exist. See the commands/export pages for resolved names. Entries in comments or unexecuted diagnostic branches can be present; developer-only registration conditions must be checked in source. Parameters are nearest inline handler signatures, not validated documentation of payload schemas.

| Registration | Side | Name | Handler parameters | Source |
| --- | --- | --- | --- | --- |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/hull_name.lua:73` |
| RegisterNetEvent | client | `advanced_yacht:client:notify` | `Named function/dynamic handler; inspect source` | `client/main.lua:26` |
| RegisterNetEvent | client | `advanced_yacht:client:syncWorld` | `list` | `client/main.lua:494` |
| RegisterNetEvent | client | `advanced_yacht:client:refreshPurchasedFleet` | `yachtId` | `client/main.lua:663` |
| RegisterNetEvent | client | `advanced_yacht:client:horn` | `coords` | `client/main.lua:1676` |
| RegisterNetEvent | client | `advanced_yacht:client:refreshMenu` | `yachtId` | `client/main.lua:1681` |
| RegisterCommand | client | `yachtmenu` | `` | `client/main.lua:1692` |
| RegisterKeyMapping | client | `yachtmenu` | `Named function/dynamic handler; inspect source` | `client/main.lua:1695` |
| RegisterCommand | client | `yachtdebug` | `` | `client/main.lua:1697` |
| RegisterCommand | client | `yachtdebugparts` | `` | `client/main.lua:1713` |
| RegisterNetEvent | client | `advanced_yacht:client:defenseStrike` | `netId, coords` | `client/main.lua:1821` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/main.lua:1897` |
| AddEventHandler | server | `onResourceStart` | `resource` | `server/main.lua:415` |
| RegisterNetEvent | server | `advanced_yacht:server:requestSync` | `` | `server/main.lua:421` |
| lib.callback.register | server | `advanced_yacht:server:getDashboard` | `src` | `server/main.lua:425` |
| lib.callback.register | server | `advanced_yacht:server:isDefenseExcluded` | `src, yachtId` | `server/main.lua:480` |
| lib.callback.register | server | `advanced_yacht:server:canUse` | `src, yachtId, feature` | `server/main.lua:484` |
| lib.callback.register | server | `advanced_yacht:server:canUseVehicle` | `src, yachtId` | `server/main.lua:503` |
| RegisterNetEvent | server | `advanced_yacht:server:buy` | `packageKey, yachtName, groupId` | `server/main.lua:511` |
| RegisterNetEvent | server | `advanced_yacht:server:relocate` | `yachtId, targetGroup` | `server/main.lua:552` |
| RegisterNetEvent | server | `advanced_yacht:server:rename` | `yachtId, newName` | `server/main.lua:589` |
| RegisterNetEvent | server | `advanced_yacht:server:addGuest` | `yachtId, targetSrc, role` | `server/main.lua:611` |
| RegisterNetEvent | server | `advanced_yacht:server:removeGuest` | `yachtId, guestCid` | `server/main.lua:636` |
| RegisterNetEvent | server | `advanced_yacht:server:setCustomization` | `yachtId, category, value` | `server/main.lua:718` |
| RegisterNetEvent | server | `advanced_yacht:server:setTexture` | `yachtId, textureId` | `server/main.lua:723` |
| RegisterNetEvent | server | `advanced_yacht:server:setPackage` | `yachtId, targetKey` | `server/main.lua:727` |
| RegisterNetEvent | server | `advanced_yacht:server:setDefenseExclusions` | `yachtId, mode` | `server/main.lua:761` |
| RegisterNetEvent | server | `advanced_yacht:server:setServiceOption` | `yachtId, category, value` | `server/main.lua:783` |
| RegisterNetEvent | server | `advanced_yacht:server:buyVehicleUpgrade` | `yachtId, upgradeKey` | `server/main.lua:810` |
| RegisterNetEvent | server | `advanced_yacht:server:sellVehicleUpgrade` | `yachtId, upgradeKey` | `server/main.lua:866` |
| RegisterNetEvent | server | `advanced_yacht:server:ensureFleet` | `yachtId, placements` | `server/main.lua:936` |
| RegisterNetEvent | server | `advanced_yacht:server:soundHorn` | `yachtId` | `server/main.lua:994` |
| RegisterNetEvent | server | `advanced_yacht:server:defenseStrike` | `yachtId` | `server/main.lua:1008` |
| RegisterNetEvent | server | `advanced_yacht:server:toggleDefense` | `yachtId` | `server/main.lua:1030` |
| RegisterNetEvent | server | `advanced_yacht:server:openStorage` | `yachtId` | `server/main.lua:1045` |
| RegisterCommand | server | `yachtgive` | `src, args` | `server/main.lua:1057` |
| RegisterCommand | server | `yachtdelete` | `src, args` | `server/main.lua:1086` |
| RegisterCommand | server | `yachtsync` | `src` | `server/main.lua:1099` |
| AddEventHandler | server | `onResourceStop` | `resource` | `server/main.lua:1105` |
| exports | server | `HasYachtAccess` | `src, yachtId` | `server/main.lua:1110` |
| exports | server | `GetYacht` | `yachtId` | `server/main.lua:1114` |
