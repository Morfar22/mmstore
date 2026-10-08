# Exports and integrations

Server export HasCableCarTicket(source) clears expired ticket data and reports valid access. Tickets are temporary; free job/fare-disabled handling is part of the internal check.

```lua
-- SERVER
local canUseTicket = exports.advanced_cablecar:HasCableCarTicket(playerServerId)
```

Optional ox\_target is Config.Target-controlled. The server syncs timetable/movement snapshots; clients interpolate cabins and run local cinematics. Do not replace sync snapshots with per-client independent timers. No QB/ESX money adapters are provided by the standalone option.

Source: export declarations and loaded framework/inventory/billing bridges in the supplied product.
