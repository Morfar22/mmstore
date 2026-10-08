---
description: "Provider setup and migration boundaries for Advanced Pausemenu."
---

# advanced_pausemenu v5.2.0 — MM Bridge

Modern responsive ESC menu with native GTA map/settings. Framework data is read through mm_bridge v0.3.0+: QBox, QBCore, ESX or standalone identity. No direct framework exports remain in the resource.

## Dependencies and installation

- ox_lib
- mm_bridge v0.3.0 or newer
- Your selected framework/inventory resources, when applicable

Replace the resource folder and merge the new config rather than keeping the old Inventory.resource/fallbackCommand settings. Configure providers in mm_bridge/config.lua.

```cfg
ensure ox_lib
# Start selected framework and inventory providers here.
ensure mm_bridge
ensure advanced_pausemenu
```

## Player information

The server returns only the requesting player's character ID/name, active job/grade and money through MMBridge methods. Clients cannot choose another player's source for this snapshot. The online list still shows connected players' display names and ping, as before.

Service counts enumerate connected players' active jobs and count only on-duty players. ESX without a duty field is off-duty by default; explicitly set EsxAssumeDuty in the bridge if that is the policy for your server. Standalone/missing framework service data is unavailable. The current interface does not render the services array; it is retained in the status response for extensions.

Standalone supports the ESC menu, native map/settings, online list, configured commands and license-based identity. Unsupported money displays a dash, not a fabricated zero. No SQL, target, billing or phone adapter is required by this resource; the configurable phone command remains a local shortcut.

## Inventory card and UI opening

The server uses MMBridge.GetItems for real item totals. ox_inventory, TGIANN, qb-inventory and basic ESX inventory are therefore read through the selected bridge adapter. Without a readable inventory, the card is disabled by default.

Bridge v0.3.0 has no inventory UI-open/weight export. The menu therefore provides explicit local configuration for that handoff, rather than assuming every provider has ox_inventory's UI signature:

```lua
Config.Inventory = {
    enabled = true,
    command = 'inventory', -- replace with the exact registered command in YOUR inventory
    open = nil, -- optional client function() with provider-specific UI call; must return true on confirmed opening
    getWeight = nil, -- optional client function() returning current,max weight in GRAMS
    allowWithoutInventory = false,
}
```

Verify the installed inventory's command; the default is a configurable shortcut, not a claim that every inventory registers that command. A command handoff cannot confirm the inventory actually opened. For an inventory without a command, supply a client open function matching its documented installed-version API. It takes priority over command, and errors/false/nil report opening failure. Do not return true merely because an event was dispatched.

No automatic TGIANN/QB UI export or weight signature is guessed. Weight is shown only when getWeight returns valid finite numbers; otherwise the card shows the bridge item count. You can disable the card with enabled=false. allowWithoutInventory=true is an explicit override for a custom UI without a bridge-readable inventory; it does not invent inventory data.

## Controls and native frontend

- /escmenu opens/closes the custom menu.
- /map opens GTA's native pause map.
- Config.ReplaceDefaultPause controls ESC replacement.

Native GTA map/settings behavior and the existing responsive layout are preserved. Native frontend loops need live GTA testing; this migration does not claim to fix provider-specific UI or GTA settings loading issues.

## Validation

22 migration behavior tests pass with mocked FiveM/bridge calls. Run texlua tests/bridge_spec.lua from this resource directory. Lua compilation and JavaScript syntax checks also passed. Tests cover source-bound snapshots, duty, unsupported standalone balances, inventory availability/commands/custom UI/weight and configured command validation. No live FiveM test was performed.

## Changes in 5.2.0

- Remove qbx_core dependency and client framework data reads; add mm_bridge.
- Read identity, jobs/duty, money and inventory summaries through the bridge.
- Use bridge notifications; show unavailable balances honestly.
- Replace hardcoded ox_inventory UI/weight assumptions with configured local hooks/command.
- Disable unavailable inventory cards and reject their NUI opening requests.
