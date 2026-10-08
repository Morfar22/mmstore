# Internal registration reference

This index locates literal registrations in the uploaded code, including local handlers, network handlers, NUI and callback wrappers. It is a maintainer lookup, **not a stable public API contract**. Event signature parameters exclude the implicit server event source. Registration does not prove an event should be called externally. Preserve original sender, session, permission, proximity, metadata and state checks.

Dynamic commands/exports and config-selected names also exist. See the commands/export pages for resolved names. Entries in comments or unexecuted diagnostic branches can be present; developer-only registration conditions must be checked in source. Parameters are nearest inline handler signatures, not validated documentation of payload schemas.

| Registration          | Side   | Name                                            | Handler parameters                   | Source                |
| --------------------- | ------ | ----------------------------------------------- | ------------------------------------ | --------------------- |
| RegisterNetEvent      | client | `advanced_car_radio:client:state`               | `state`                              | `client/main.lua:303` |
| RegisterNUICallback   | client | `close`                                         | `_, cb`                              | `client/main.lua:356` |
| RegisterNUICallback   | client | `refresh`                                       | `_, cb`                              | `client/main.lua:361` |
| RegisterNUICallback   | client | `resolveTrack`                                  | `data, cb`                           | `client/main.lua:367` |
| RegisterNUICallback   | client | `control`                                       | `data, cb`                           | `client/main.lua:373` |
| RegisterNUICallback   | client | `saveSettings`                                  | `data, cb`                           | `client/main.lua:390` |
| RegisterNUICallback   | client | `createPlaylist`                                | `data, cb`                           | `client/main.lua:402` |
| RegisterNUICallback   | client | `renamePlaylist`                                | `data, cb`                           | `client/main.lua:413` |
| RegisterNUICallback   | client | `deletePlaylist`                                | `data, cb`                           | `client/main.lua:424` |
| RegisterNUICallback   | client | `addPlaylistTrack`                              | `data, cb`                           | `client/main.lua:435` |
| RegisterNUICallback   | client | `removePlaylistTrack`                           | `data, cb`                           | `client/main.lua:447` |
| RegisterNUICallback   | client | `addVehicleTrack`                               | `data, cb`                           | `client/main.lua:459` |
| RegisterNUICallback   | client | `removeVehicleTrack`                            | `data, cb`                           | `client/main.lua:471` |
| AddEventHandler       | client | `onResourceStop`                                | `resourceName`                       | `client/main.lua:608` |
| lib.callback.register | server | `advanced_car_radio:server:settings`            | `source`                             | `server/main.lua:495` |
| lib.callback.register | server | `advanced_car_radio:server:activeStates`        | \`\`                                 | `server/main.lua:501` |
| lib.callback.register | server | `advanced_car_radio:server:bootstrap`           | `source, claimedPlate`               | `server/main.lua:511` |
| lib.callback.register | server | `advanced_car_radio:server:resolveMetadata`     | `_, url`                             | `server/main.lua:537` |
| lib.callback.register | server | `advanced_car_radio:server:saveSettings`        | `source, data`                       | `server/main.lua:543` |
| lib.callback.register | server | `advanced_car_radio:server:createPlaylist`      | `source, name`                       | `server/main.lua:575` |
| lib.callback.register | server | `advanced_car_radio:server:renamePlaylist`      | `source, playlistId, name`           | `server/main.lua:588` |
| lib.callback.register | server | `advanced_car_radio:server:deletePlaylist`      | `source, playlistId`                 | `server/main.lua:600` |
| lib.callback.register | server | `advanced_car_radio:server:addPlaylistTrack`    | `source, playlistId, rawTrack`       | `server/main.lua:611` |
| lib.callback.register | server | `advanced_car_radio:server:removePlaylistTrack` | `source, playlistId, trackId`        | `server/main.lua:632` |
| lib.callback.register | server | `advanced_car_radio:server:addVehicleTrack`     | `source, claimedPlate, rawTrack`     | `server/main.lua:642` |
| lib.callback.register | server | `advanced_car_radio:server:removeVehicleTrack`  | `source, claimedPlate, trackId`      | `server/main.lua:665` |
| lib.callback.register | server | `advanced_car_radio:server:control`             | `source, claimedPlate, action, data` | `server/main.lua:675` |
| RegisterNetEvent      | server | `advanced_car_radio:server:ended`               | `claimedPlate, generation`           | `server/main.lua:756` |
| AddEventHandler       | server | `playerDropped`                                 | \`\`                                 | `server/main.lua:771` |
| AddEventHandler       | server | `onResourceStop`                                | `resourceName`                       | `server/main.lua:784` |
