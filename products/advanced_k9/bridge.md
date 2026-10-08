---
description: "Provider setup and migration boundaries for Advanced K9."
---

# Advanced K9 95.1.0 — mm_bridge

Requires mm_bridge 0.3.0+, ox_lib and oxmysql. This ZIP contains only advanced_k9; install the bridge separately. The source was Advanced K9 95.0.1.

## Install and upgrade

Back up your configuration and database, replace the resource, and transfer your own gameplay/location/vehicle/approval settings into the new configuration. Keep the resource named advanced_k9 so Vet exports and owned phone adapters retain their names. For a new installation use sql/advanced_k9.sql; the existing database initialization/migrations remain. Do not drop existing tables.

```cfg
ensure oxmysql
ensure ox_lib
# Start the selected framework, inventory, phone and target resources here.
ensure mm_bridge
ensure advanced_k9
ensure advanced_vet_dlc
```

Choose Framework, Inventory, Target and Phone in mm_bridge/config.lua. Adoption.targetSystem now selects bridge or none; its old provider values no longer choose a provider locally. PhoneIntegration.provider/order are retained for config compatibility but do not control selection.

## Compatibility and boundaries

| Integration | Behavior |
| --- | --- |
| Framework | QBox, QBCore, ESX, standalone or custom adapters. Jobs, character name/ID and ACE checks use mm_bridge. |
| Sniff inventory | Uses bridge GetItemCount with ox_inventory, TGIANN, qb-inventory, plain ESX or custom inventory adapters. Unsupported/unavailable inventory reports an error, not a clean sniff. Standalone needs an inventory adapter for item sniffing. |
| Collar target | ox_target, qb-target, qtarget or custom bridge entity targets. Owned handles are removed on ped changes, provider changes and resource stop. Existing /k9collar fallback remains. |
| Phone | Reads only mm_bridge's selected server phone adapter. Built-in lb-phone, qb-phone, framework or configured export adapters work through their documented bridge contracts. |
| Needs | Bridge player metadata provides hunger/thirst. QBox/QB native SetMetaData is an isolated local extension with readback; ESX keeps its existing esx_status events. Custom needs use Config.Bridge.getNeeds/setNeeds. |
| Vet | Existing care, passport and dog state exports are retained. Vet does not become a paired handler; existing consent/player-controlled treatment flows remain. |
| UI | Existing tablet, sound-aware notifications, prompts and progress cards remain resource-local. ox_lib supplies callback infrastructure; its UI functions are deliberately overridden by the established K9 UI facade. |
| Billing | K9 has no invoice feature to migrate. Billing is handled by Vet and the central bridge. |

Framework.GetClientSnapshot obtains only the requesting player's job, permission result, needs and provider status through a server callback. The short client cache is for rendering; server actions continue to check authoritative jobs and existing approvals.

Service authority in standalone requires advanced_k9.authority ACE, or explicit Config.Bridge.allowStandaloneAuthority=true. Civil gameplay remains available. Handler/dog administrator approvals remain separate and mandatory where configured. TestMode is still an explicit development permission override; keep it false in production.

## Phone adapter pack

The pre-existing phone implementations are retained as optional server adapters, disabled by default. They provide number lookup only; they do not claim phone notifications/open-menu support. They preserve the source integration contracts and need validation against your installed phone version.

To use the supplied Sky integration:

1. Set Config.PhoneIntegration.registerLegacyAdapters=true in advanced_k9/config.lua.
2. Allow its adapter registration in mm_bridge/config.lua:

```lua
CustomAdapterOwners = { advanced_k9 = true },
Phone = 'k9_sky_phone',
```

Merge this owner into the existing CustomAdapterOwners table rather than replacing other owners. Start mm_bridge before advanced_k9. Adapter names are k9_sky_phone, k9_gksphone, k9_yseries, k9_npwd, k9_high-phone, k9_qs-smartphone-pro, k9_v-phone and k9_lsfive-phone. Select names containing hyphens as quoted strings. Existing Sky SQL fallback settings remain in PhoneIntegration; review the table prefix/allow-list and disable skySqlFallback if exports alone are sufficient.

Alternatively configure the bridge's export phone adapter to the exact server export and argument expected by your phone, or register your own phone adapter. No local auto selection or fallback to another phone provider occurs. Previously cached owner phone numbers remain available for offline collars as before; a provider outage does not invent a replacement number.

## Custom needs and data identity

Config.Bridge.getNeeds is an optional server function(src) returning hunger, thirst percentages. Config.Bridge.setNeeds is an optional server function(src,hunger,thirst) returning true only after applying the values. The central bridge does not offer a generic needs setter. K9 continues to keep its internal care stats when an external needs integration is unavailable; this does not confirm an external HUD update. ESX writes are client event dispatches, not server-confirmed metadata writes.

Config.Bridge.databaseIdentity defaults to legacy_license. It preserves existing K9 approvals, adoption records, progression, preferences and passport/kennel relationships. Framework character IDs used for phone lookup continue through mm_bridge. Switching databaseIdentity to character requires manually migrating every related K9 identity key and coordinating the Vet integration. No automatic license-to-character migration is included; changing frameworks also requires an identity review.

Existing tracking, scent, dog movement, vehicle cages, cameras, stationary kennels, adoption, training, active-handler gates, role approval, emotes, care and Vet integration are retained. This conversion does not redesign gameplay or database ownership.

## Validation

49 mocked checks cover server authority, standalone permissions, character identity, native/custom needs, client snapshot caching, phone facade/adapter registration, inventory failures, legacy database identities, target registration, ped/provider changes and stop cleanup. All 67 Lua files compile; node --check passes for html/app.js.

Run from the advanced_k9 resource directory:

```bash
texlua tests/bridge_spec.lua
texlua tests/target_spec.lua
```

A live FiveM test has not been performed. On staging verify approved handler/dog pairing, active dog selection, service/civil restrictions, tablet, inventory sniff, collar phone lookup, food/water/HUD sync, vehicles/kennels, and Vet consent/care/passports. Validate your installed phone/inventory versions and retained database records before production.
