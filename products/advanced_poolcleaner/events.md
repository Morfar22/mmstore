# Advanced Poolcleaner — Internal registration reference

This index locates literal registrations in the uploaded code, including local handlers, network handlers, NUI and callback wrappers. It is a maintainer lookup, **not a stable public API contract**. Event signature parameters exclude the implicit server event source. Registration does not prove an event should be called externally. Preserve original sender, session, permission, proximity, metadata and state checks.

Dynamic commands/exports and config-selected names also exist. See the commands/export pages for resolved names. Entries in comments or unexecuted diagnostic branches can be present; developer-only registration conditions must be checked in source. Parameters are nearest inline handler signatures, not validated documentation of payload schemas.

| Registration | Side | Name | Handler parameters | Source |
| --- | --- | --- | --- | --- |
| RegisterNetEvent | client | `advanced_poolcleaner:client:openCreator` | `` | `client/creator.lua:114` |
| RegisterNetEvent | client | `advanced_poolcleaner:client:toggleDebug` | `` | `client/creator.lua:144` |
| RegisterNUICallback | client | `close` | `_, cb` | `client/main.lua:156` |
| RegisterNUICallback | client | `startMission` | `data, cb` | `client/main.lua:161` |
| RegisterNUICallback | client | `cancelMission` | `_, cb` | `client/main.lua:176` |
| RegisterNUICallback | client | `invite` | `data, cb` | `client/main.lua:182` |
| RegisterNUICallback | client | `leaveGroup` | `_, cb` | `client/main.lua:189` |
| RegisterNUICallback | client | `unlockSkill` | `data, cb` | `client/main.lua:199` |
| RegisterNUICallback | client | `setWaypoint` | `data, cb` | `client/main.lua:212` |
| RegisterNetEvent | client | `advanced_poolcleaner:client:notify` | `message, kind` | `client/main.lua:225` |
| RegisterNetEvent | client | `advanced_poolcleaner:client:syncLocations` | `locations` | `client/main.lua:229` |
| RegisterNetEvent | client | `advanced_poolcleaner:client:groupUpdated` | `group` | `client/main.lua:233` |
| RegisterNetEvent | client | `advanced_poolcleaner:client:missionUpdated` | `mission` | `client/main.lua:240` |
| RegisterNetEvent | client | `advanced_poolcleaner:client:missionFinished` | `payout, xp` | `client/main.lua:248` |
| RegisterNetEvent | client | `advanced_poolcleaner:client:teamInvite` | `_, leaderName` | `client/main.lua:262` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/main.lua:361` |
| lib.callback.register | server | `advanced_poolcleaner:getBootstrap` | `source` | `server/main.lua:539` |
| lib.callback.register | server | `advanced_poolcleaner:getLocations` | `` | `server/main.lua:552` |
| lib.callback.register | server | `advanced_poolcleaner:startMission` | `source, difficulty` | `server/main.lua:556` |
| lib.callback.register | server | `advanced_poolcleaner:cancelMission` | `source` | `server/main.lua:584` |
| lib.callback.register | server | `advanced_poolcleaner:invite` | `source, target` | `server/main.lua:595` |
| lib.callback.register | server | `advanced_poolcleaner:respondInvite` | `source, accept` | `server/main.lua:619` |
| lib.callback.register | server | `advanced_poolcleaner:leaveGroup` | `source` | `server/main.lua:643` |
| lib.callback.register | server | `advanced_poolcleaner:startTask` | `source, taskId` | `server/main.lua:664` |
| lib.callback.register | server | `advanced_poolcleaner:cancelTask` | `source, token` | `server/main.lua:720` |
| lib.callback.register | server | `advanced_poolcleaner:completeTask` | `source, token` | `server/main.lua:735` |
| lib.callback.register | server | `advanced_poolcleaner:unlockSkill` | `source, skillId` | `server/main.lua:804` |
| lib.callback.register | server | `advanced_poolcleaner:adminSavePool` | `source, data` | `server/main.lua:822` |
| lib.callback.register | server | `advanced_poolcleaner:adminDeletePool` | `source, poolId` | `server/main.lua:864` |
| RegisterNetEvent | server | `advanced_poolcleaner:server:reloadLocations` | `` | `server/main.lua:886` |
| AddEventHandler | server | `playerDropped` | `` | `server/main.lua:892` |
| AddEventHandler | server | `onResourceStop` | `resource` | `server/main.lua:919` |
