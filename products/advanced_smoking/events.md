# Advanced Smoking — Internal registration reference

This index locates literal registrations in the uploaded code, including local handlers, network handlers, NUI and callback wrappers. It is a maintainer lookup, **not a stable public API contract**. Event signature parameters exclude the implicit server event source. Registration does not prove an event should be called externally. Preserve original sender, session, permission, proximity, metadata and state checks.

Dynamic commands/exports and config-selected names also exist. See the commands/export pages for resolved names. Entries in comments or unexecuted diagnostic branches can be present; developer-only registration conditions must be checked in source. Parameters are nearest inline handler signatures, not validated documentation of payload schemas.

| Registration | Side | Name | Handler parameters | Source |
| --- | --- | --- | --- | --- |
| exports | client | `useItem` | `data,slot` | `client/main.lua:15` |
| RegisterNetEvent | client | `advanced_smoking:itemMenu` | `Named function/dynamic handler; inspect source` | `client/main.lua:93` |
| RegisterNetEvent | client | `advanced_smoking:openWheel` | `Named function/dynamic handler; inspect source` | `client/main.lua:94` |
| RegisterNetEvent | client | `advanced_smoking:state` | `state` | `client/main.lua:95` |
| RegisterNetEvent | client | `advanced_smoking:offer` | `data` | `client/main.lua:103` |
| RegisterNetEvent | client | `advanced_smoking:endPuff` | `` | `client/main.lua:116` |
| RegisterCommand | client | `+nrp_smokewheel` | `` | `client/main.lua:117` |
| RegisterCommand | client | `-nrp_smokewheel` | `` | `client/main.lua:118` |
| RegisterKeyMapping | client | `+nrp_smokewheel` | `Named function/dynamic handler; inspect source` | `client/main.lua:119` |
| RegisterCommand | client | `+nrp_smokepuff` | `Named function/dynamic handler; inspect source` | `client/main.lua:120` |
| RegisterCommand | client | `-nrp_smokepuff` | `` | `client/main.lua:121` |
| RegisterKeyMapping | client | `+nrp_smokepuff` | `Named function/dynamic handler; inspect source` | `client/main.lua:122` |
| RegisterCommand | client | `smoking` | `Named function/dynamic handler; inspect source` | `client/main.lua:123` |
| RegisterCommand | client | `smokecollection` | `` | `client/main.lua:124` |
| RegisterNUICallback | client | `close` | `_,cb` | `client/main.lua:127` |
| RegisterNUICallback | client | `action` | `data,cb` | `client/main.lua:128` |
| AddEventHandler | client | `QBCore:Client:OnPlayerUnload` | `` | `client/main.lua:175` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/main.lua:176` |
| RegisterNetEvent | client | `advanced_smoking:smoke` | `src,name,duration,trick` | `client/visuals.lua:105` |
| RegisterNetEvent | client | `advanced_smoking:anim` | `key` | `client/visuals.lua:106` |
| RegisterNetEvent | client | `advanced_smoking:ash` | `src` | `client/visuals.lua:107` |
| RegisterNetEvent | client | `advanced_smoking:pack` | `name` | `client/visuals.lua:110` |
| RegisterNetEvent | client | `advanced_smoking:effect` | `data` | `client/visuals.lua:120` |
| RegisterNetEvent | client | `advanced_smoking:litter` | `id,name,c,bucket,seconds` | `client/world.lua:57` |
| RegisterNetEvent | client | `advanced_smoking:removeLitter` | `id` | `client/world.lua:66` |
| lib.callback.register | server | `advanced_smoking:action` | `src,name,data` | `server/main.lua:264` |
| AddEventHandler | server | `playerDropped` | `` | `server/main.lua:305` |
| AddEventHandler | server | `onResourceStop` | `resource` | `server/main.lua:309` |
| RegisterCommand | server | `smokeshopowner` | `src,args` | `server/shop.lua:86` |
