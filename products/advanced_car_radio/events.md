# Advanced Car Radio — Internal registration index

These literal registrations are implementation references, not instructions to bypass the menu or server checks. Configured/dynamic command and event names are not inferred.

| Name | Side | Registration | File |
| --- | --- | --- | --- |
| `advanced_car_radio:client:state` | client | `RegisterNetEvent` | `client/main.lua` |
| `close` | client | `RegisterNUICallback` | `client/main.lua` |
| `refresh` | client | `RegisterNUICallback` | `client/main.lua` |
| `resolveTrack` | client | `RegisterNUICallback` | `client/main.lua` |
| `control` | client | `RegisterNUICallback` | `client/main.lua` |
| `saveSettings` | client | `RegisterNUICallback` | `client/main.lua` |
| `createPlaylist` | client | `RegisterNUICallback` | `client/main.lua` |
| `renamePlaylist` | client | `RegisterNUICallback` | `client/main.lua` |
| `deletePlaylist` | client | `RegisterNUICallback` | `client/main.lua` |
| `addPlaylistTrack` | client | `RegisterNUICallback` | `client/main.lua` |
| `removePlaylistTrack` | client | `RegisterNUICallback` | `client/main.lua` |
| `addVehicleTrack` | client | `RegisterNUICallback` | `client/main.lua` |
| `removeVehicleTrack` | client | `RegisterNUICallback` | `client/main.lua` |
| `advanced_car_radio:server:settings` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:activeStates` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:bootstrap` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:resolveMetadata` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:saveSettings` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:createPlaylist` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:renamePlaylist` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:deletePlaylist` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:addPlaylistTrack` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:removePlaylistTrack` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:addVehicleTrack` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:removeVehicleTrack` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:control` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_car_radio:server:ended` | server | `RegisterNetEvent` | `server/main.lua` |
