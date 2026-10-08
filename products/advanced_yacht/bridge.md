---
description: "Provider setup and migration boundaries for Advanced Yacht."
---

# Advanced Yacht V5.2 - MM Bridge Edition

FiveM Galaxy Super Yacht system using Rockstar static yacht IPLs.

## UI
All interactive UI now uses **ox_lib**: broker, yacht management, relocation, access, customization, Yacht Services, vehicle upgrades, alerts, input dialogs and notifications.

The old Scaleform management menu has been removed. Native GTA features remain for the world itself: cinematics, yacht horn, defense, static Rockstar props and optional physical yacht name on the hull.

### Config
`Config.OxLibUI` controls context/notification placement and live customization preview.

`Config.HullName` controls the optional Rockstar `YACHT_NAME` hull renderer.

## Jacuzzi water
V5.1 restores the actual Rockstar water surface using `apa_mp_apa_yacht_jacuzzi_ripple1` with collision disabled. The local position is configurable:

```lua
Config.GTAO.jacuzzi.water = {
    enabled = true,
    model = 'apa_mp_apa_yacht_jacuzzi_ripple1',
    offset = vec3(-50.8033, -1.9774, 0.1368),
    zOffset = 0.0,
    headingOffset = 0.0,
}
```

## Main features
- Orion / Pisces / Aquarius
- 36 Rockstar yacht berths
- persistent character ownership through MM Bridge
- secured ox_inventory / TGIANN storage adapters; custom adapter required for other stashes
- wardrobe integration
- GTA-style boarding/departure cinematics
- yacht relocation
- yacht access and crew/guests
- Yacht Services
- yacht defense
- configurable colors, lighting, fittings, flags and name
- expensive permanent helicopter/tender/jetski upgrades via `Config.YachtVehicleShop`
- jacuzzi + GTA swimwear behavior

## Install
```cfg
ensure oxmysql
ensure ox_lib
# Start your chosen framework, target and inventory providers here.
ensure mm_bridge
ensure advanced_yacht
```

Keep the existing database. Tables/migrations are handled by the resource.


## MM Bridge requirements

Requires mm_bridge v0.3.0+, ox_lib, oxmysql and OneSync for the existing networked world/vehicle features. QBox, QBCore and ESX identity/money/admin ACE use the same bridge API. Terminal zones use ox_target, qb-target, qtarget or the bridge standalone target. Restart advanced_yacht after bridge/target restarts.

Citizen IDs and existing stash names advanced_yacht_v3_ID remain unchanged on QBox. ESX uses its actual character identifier. Framework changes do not convert SQL ownership/access entries, money or stored inventory contents. Standalone uses license identity without character separation. With no custom economy it requires all purchase/customization/relocation/vehicle prices to be zero, or use the existing console yachtgive command to grant yachts. Paid actions fail if money is unavailable; nil/false mutations cannot count as successful payments.

## Inventory storage extension

Bridge v0.3.0 does not expose a generic stash API. server/storage_bridge.lua is therefore a resource-local extension following MMBridge.GetStatus().inventory. ox_inventory and TGIANN use their own stash signatures and open/swap hooks. TGIANN contracts follow the supplied original MM Smoking integration and must be checked against the installed inventory version. A version without these hooks fails closed; it is not silently given unrestricted storage.

Config.StorageBridge.enabled=false disables storage while retaining the yacht's other features. Resources can be renamed through Config.StorageBridge.resources. These names must match the selected bridge inventory resource. Existing inventory data is not moved when switching providers.

Storage access is checked for owner/invited character, current distance, registered yacht and package feature. The same check is applied by inventory open/swap hooks, including direct inventory calls. Public yacht/vehicle access does not grant storage access. Unknown yacht stash IDs are denied. An external open dispatch is not a guarantee the player's inventory UI became visible.

qb-inventory, native ESX inventory and standalone storage are unsupported by default, even though those inventories can be used by other bridge methods. They need a secure custom stash adapter; the storage feature remains disabled without one.

Config.StorageBridge.custom can be a trusted SERVER adapter table:

```lua
Config.StorageBridge.custom = {
    resource = 'your_secure_inventory', -- optional; require started state when provided
    install = function(authorize)
        -- Install native open AND item-transfer checks for yacht stash IDs.
        -- authorize(source, inventoryId) returns true/false for yacht stashes,
        -- nil for unrelated inventories. Store/enforce this callback in the provider.
        -- Return true only once checks are actually installed.
        return false -- replace with a real implementation before enabling
    end,
    register = function(data)
        -- data: id, yachtId, label, slots, weight in grams
        return false
    end,
    open = function(source, data)
        -- Call the installed provider's SERVER stash API after authorization.
        return false
    end,
}
```

Defining these hooks alone does not make an unsafe provider secure: its native client paths and item transfers must enforce the same authorization. Provider restarts invalidate registrations; restart this resource if a custom adapter has no separate resource lifecycle. Do not enable storage by merely returning true from install.

## Money and SQL limitations

Framework charges/credits and SQL writes are separate operations, not an atomic transaction. Existing per-operation refund paths remain; an unconfirmed credit now logs its source, amount and reason and tells the player to contact staff. No automatic retry is made after an ambiguous provider failure. Reconcile such operations against framework/SQL records before replaying them. This migration does not solve all concurrent purchase/race cases in the original yacht code.

## Validation

27 offline bridge/server/storage tests pass, including failed/nil money mutation, free standalone purchase, ownership/distance checks, direct stash/swap access, hook failures, provider stops and custom adapters. Tests use mocked FiveM, bridge, inventory and SQL APIs. Lua syntax checks also pass. No live GTA/provider validation was performed; yacht IPL placement, jacuzzi, cinematics, vehicle physics and inventory persistence require live testing.

Run texlua tests/bridge_spec.lua from the resource directory. The deliberate SQL/refund and missing-hook logs are expected test cases.
