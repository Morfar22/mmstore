# Internal registration reference

This index locates literal registrations in the uploaded code, including local handlers, network handlers, NUI and callback wrappers. It is a maintainer lookup, **not a stable public API contract**. Event signature parameters exclude the implicit server event source. Registration does not prove an event should be called externally. Preserve original sender, session, permission, proximity, metadata and state checks.

Dynamic commands/exports and config-selected names also exist. See the commands/export pages for resolved names. Entries in comments or unexecuted diagnostic branches can be present; developer-only registration conditions must be checked in source. Parameters are nearest inline handler signatures, not validated documentation of payload schemas.

| Registration          | Side   | Name                                        | Handler parameters         | Source                   |
| --------------------- | ------ | ------------------------------------------- | -------------------------- | ------------------------ |
| AddEventHandler       | client | `onResourceStop`                            | `resource`                 | `client/main.lua:157`    |
| RegisterNetEvent      | client | `advanced_orbital:client:notify`            | `message, kind`            | `client/main.lua:164`    |
| RegisterNetEvent      | client | `advanced_orbital:client:impact`            | `data`                     | `client/orbital.lua:595` |
| RegisterNetEvent      | client | `advanced_orbital:client:applyStrikeDamage` | `data`                     | `client/orbital.lua:640` |
| RegisterNetEvent      | client | `advanced_orbital:client:strikeCancelled`   | `reason`                   | `client/orbital.lua:657` |
| AddEventHandler       | client | `onResourceStop`                            | `resource`                 | `client/orbital.lua:668` |
| lib.callback.register | server | `advanced_orbital:server:getTerminalStatus` | `source, terminalId`       | `server/main.lua:178`    |
| lib.callback.register | server | `advanced_orbital:server:beginSession`      | `source, terminalId, mode` | `server/main.lua:202`    |
| RegisterNetEvent      | server | `advanced_orbital:server:endSession`        | `terminalId`               | `server/main.lua:223`    |
| lib.callback.register | server | `advanced_orbital:server:getIntel`          | `source, terminalId`       | `server/main.lua:230`    |
| lib.callback.register | server | `advanced_orbital:server:requestStrike`     | `source, payload`          | `server/main.lua:257`    |
| AddEventHandler       | server | `playerDropped`                             | \`\`                       | `server/main.lua:443`    |
