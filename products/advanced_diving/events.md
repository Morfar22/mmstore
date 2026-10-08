# Advanced Diving — Internal registration index

These literal registrations are implementation references, not instructions to bypass the menu or server checks. Configured/dynamic command and event names are not inferred.

| Name | Side | Registration | File |
| --- | --- | --- | --- |
| `divingsonar` | client | `RegisterCommand` | `client/main.lua` |
| `diving` | client | `RegisterCommand` | `client/main.lua` |
| `close` | client | `RegisterNUICallback` | `client/main.lua` |
| `invite` | client | `RegisterNUICallback` | `client/main.lua` |
| `leaveCrew` | client | `RegisterNUICallback` | `client/main.lua` |
| `kickMember` | client | `RegisterNUICallback` | `client/main.lua` |
| `startMission` | client | `RegisterNUICallback` | `client/main.lua` |
| `cancelMission` | client | `RegisterNUICallback` | `client/main.lua` |
| `advanced_diving:refreshDashboard` | client | `RegisterNetEvent` | `client/main.lua` |
| `advanced_diving:crewInvite` | client | `RegisterNetEvent` | `client/main.lua` |
| `advanced_diving:missionStarted` | client | `RegisterNetEvent` | `client/main.lua` |
| `advanced_diving:missionSync` | client | `RegisterNetEvent` | `client/main.lua` |
| `advanced_diving:missionEnded` | client | `RegisterNetEvent` | `client/main.lua` |
| `advanced_diving:hasRequiredGear` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_diving:getDashboard` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_diving:invite` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_diving:acceptInvite` | server | `RegisterNetEvent` | `server/main.lua` |
| `advanced_diving:leaveCrew` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_diving:kickMember` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_diving:startMission` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_diving:claimObjective` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_diving:releaseObjective` | server | `RegisterNetEvent` | `server/main.lua` |
| `advanced_diving:beginLift` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_diving:markSurfaced` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_diving:completeObjective` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_diving:returnBoat` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_diving:cancelMission` | server | `lib.callback.register` | `server/main.lua` |
