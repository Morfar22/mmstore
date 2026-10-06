# Advanced Diving — Internal registration reference

This index locates literal registrations in the uploaded code, including local handlers, network handlers, NUI and callback wrappers. It is a maintainer lookup, **not a stable public API contract**. Event signature parameters exclude the implicit server event source. Registration does not prove an event should be called externally. Preserve original sender, session, permission, proximity, metadata and state checks.

Dynamic commands/exports and config-selected names also exist. See the commands/export pages for resolved names. Entries in comments or unexecuted diagnostic branches can be present; developer-only registration conditions must be checked in source. Parameters are nearest inline handler signatures, not validated documentation of payload schemas.

| Registration | Side | Name | Handler parameters | Source |
| --- | --- | --- | --- | --- |
| RegisterCommand | client | `divingsonar` | `Named function/dynamic handler; inspect source` | `client/main.lua:386` |
| RegisterKeyMapping | client | `divingsonar` | `Named function/dynamic handler; inspect source` | `client/main.lua:387` |
| RegisterCommand | client | `diving` | `Named function/dynamic handler; inspect source` | `client/main.lua:388` |
| RegisterNUICallback | client | `close` | `_, cb` | `client/main.lua:390` |
| RegisterNUICallback | client | `invite` | `data, cb` | `client/main.lua:395` |
| RegisterNUICallback | client | `leaveCrew` | `_, cb` | `client/main.lua:402` |
| RegisterNUICallback | client | `kickMember` | `data, cb` | `client/main.lua:409` |
| RegisterNUICallback | client | `startMission` | `data, cb` | `client/main.lua:416` |
| RegisterNUICallback | client | `cancelMission` | `_, cb` | `client/main.lua:423` |
| RegisterNetEvent | client | `advanced_diving:refreshDashboard` | `` | `client/main.lua:430` |
| RegisterNetEvent | client | `advanced_diving:crewInvite` | `crewId, leaderName` | `client/main.lua:434` |
| RegisterNetEvent | client | `advanced_diving:missionStarted` | `run` | `client/main.lua:450` |
| RegisterNetEvent | client | `advanced_diving:missionSync` | `run` | `client/main.lua:457` |
| RegisterNetEvent | client | `advanced_diving:missionEnded` | `reason` | `client/main.lua:465` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/main.lua:562` |
| lib.callback.register | server | `advanced_diving:getDashboard` | `source` | `server/main.lua:391` |
| lib.callback.register | server | `advanced_diving:invite` | `source, target` | `server/main.lua:395` |
| RegisterNetEvent | server | `advanced_diving:acceptInvite` | `crewId` | `server/main.lua:428` |
| lib.callback.register | server | `advanced_diving:leaveCrew` | `source` | `server/main.lua:460` |
| lib.callback.register | server | `advanced_diving:kickMember` | `source, target` | `server/main.lua:471` |
| lib.callback.register | server | `advanced_diving:startMission` | `source, contractId` | `server/main.lua:487` |
| lib.callback.register | server | `advanced_diving:claimObjective` | `source, runId, objectiveId, mode` | `server/main.lua:514` |
| RegisterNetEvent | server | `advanced_diving:releaseObjective` | `runId, objectiveId` | `server/main.lua:553` |
| lib.callback.register | server | `advanced_diving:beginLift` | `source, runId, objectiveId` | `server/main.lua:566` |
| lib.callback.register | server | `advanced_diving:markSurfaced` | `source, runId, objectiveId` | `server/main.lua:580` |
| lib.callback.register | server | `advanced_diving:completeObjective` | `source, runId, objectiveId` | `server/main.lua:602` |
| lib.callback.register | server | `advanced_diving:returnBoat` | `source, runId` | `server/main.lua:663` |
| lib.callback.register | server | `advanced_diving:cancelMission` | `source` | `server/main.lua:697` |
| AddEventHandler | server | `playerDropped` | `` | `server/main.lua:719` |
| AddEventHandler | server | `onResourceStop` | `resource` | `server/main.lua:725` |
