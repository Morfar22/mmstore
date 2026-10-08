# Internal registration reference

This index locates literal registrations in the uploaded code, including local handlers, network handlers, NUI and callback wrappers. It is a maintainer lookup, **not a stable public API contract**. Event signature parameters exclude the implicit server event source. Registration does not prove an event should be called externally. Preserve original sender, session, permission, proximity, metadata and state checks.

Dynamic commands/exports and config-selected names also exist. See the commands/export pages for resolved names. Entries in comments or unexecuted diagnostic branches can be present; developer-only registration conditions must be checked in source. Parameters are nearest inline handler signatures, not validated documentation of payload schemas.

| Registration          | Side   | Name                                       | Handler parameters | Source                 |
| --------------------- | ------ | ------------------------------------------ | ------------------ | ---------------------- |
| RegisterNetEvent      | client | `advanced_cablecar:client:state`           | `data`             | `client/main.lua:987`  |
| RegisterCommand       | client | `cabledebug`                               | \`\`               | `client/main.lua:1059` |
| RegisterNetEvent      | client | `advanced_cablecar:client:developerResult` | `ok, reason`       | `client/main.lua:1064` |
| AddEventHandler       | client | `onResourceStop`                           | `resource`         | `client/main.lua:1243` |
| lib.callback.register | server | `advanced_cablecar:server:buyTicket`       | `source`           | `server/main.lua:95`   |
| lib.callback.register | server | `advanced_cablecar:server:canBoard`        | `source`           | `server/main.lua:119`  |
| AddEventHandler       | server | `playerDropped`                            | \`\`               | `server/main.lua:137`  |
| RegisterNetEvent      | server | `advanced_cablecar:server:requestState`    | \`\`               | `server/main.lua:159`  |
| exports               | server | `HasCableCarTicket`                        | `source`           | `server/main.lua:287`  |
