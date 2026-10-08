# Advanced Pausemenu — Internal registration index

These literal registrations are implementation references, not instructions to bypass the menu or server checks. Configured/dynamic command and event names are not inferred.

| Name | Side | Registration | File |
| --- | --- | --- | --- |
| `close` | client | `RegisterNUICallback` | `client/main.lua` |
| `map` | client | `RegisterNUICallback` | `client/main.lua` |
| `settings` | client | `RegisterNUICallback` | `client/main.lua` |
| `inventory` | client | `RegisterNUICallback` | `client/main.lua` |
| `runCommand` | client | `RegisterNUICallback` | `client/main.lua` |
| `waypoint` | client | `RegisterNUICallback` | `client/main.lua` |
| `disconnect` | client | `RegisterNUICallback` | `client/main.lua` |
| `refresh` | client | `RegisterNUICallback` | `client/main.lua` |
| `escmenu` | client | `RegisterCommand` | `client/main.lua` |
| `map` | client | `RegisterCommand` | `client/main.lua` |
| `advanced_pausemenu:server:getStatus` | server | `lib.callback.register` | `server/main.lua` |
| `advanced_pausemenu:server:disconnect` | server | `RegisterNetEvent` | `server/main.lua` |
