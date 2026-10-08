---
description: "Provider setup and migration boundaries for Advanced Poolcleaner."
---

# Advanced Poolcleaner v1.2.0 — MM Bridge

This resource now uses your existing `mm_bridge` for character IDs, player lookup, job/duty checks,
staff ACE checks, money, inventory requirements and notifications.
Requires mm_bridge 0.1.0 or newer with the API supplied in this conversation, your selected framework, ox_lib and oxmysql.
The bridge is not included in this ZIP. Keep its folder named `mm_bridge`.

## Install / upgrade

1. Back up your old resource and pool database tables.
2. Replace `advanced_poolcleaner` with this folder, preserving its name.
3. Merge your existing configuration and custom pool coordinates into the supplied `config.lua`.
4. Start dependencies, then `mm_bridge`, then this resource. See `server.cfg.example`.

```cfg
ensure oxmysql
ensure ox_lib
# Start the selected framework here.
# Start the inventory selected in mm_bridge before the bridge, if item requirements are enabled.
ensure mm_bridge
ensure advanced_poolcleaner
```

The default remains `Config.Inventory.mode = 'none'`: no items are required.
To enable item requirements, set `mode = 'bridge'` and select your actual inventory in `mm_bridge/config.lua`.
For TGIANN, set the bridge's `Inventory = 'tgiann'` and correct `TgiannResource` name.
Install the optional item definitions in your inventory when enabling requirements.

Legacy modes `ox_inventory` and `tgiann-inventory` still work when the bridge selects the matching provider.
A mismatch, unavailable provider, unknown mode or unimplemented custom mode refuses required-item operations.
Item counts now include all matching stacks rather than just the first TGIANN stack.
Items are consumed only if `consumeOnComplete` is enabled, as before.

## Preserved gameplay and data

- Public/whitelist access, optional duty requirement and `poolcleaner.admin` ACE.
- Multiplayer groups, task locks, timing/proximity checks, creator, skill tree and progression.
- Each/split payment modes, team bonuses and skill multipliers.
- Existing citizenid keys and SQL tables; no schema migration.
- NUI layout and DA/EN locales; notification rendering uses the bridge's ox_lib wrapper.

## Payment failures

Mission completion now checks the bridge's AddMoney result. On failure, the mission still completes and
awards its normal completion/XP/reputation, but records zero earned money for that member and sends an error notification.
The server logs the mission ID, character ID, expected amount, account and error so staff can reconcile it.
There is no automatic retry queue or atomic transaction across QBox money and pool SQL data.
The new settlement guard prevents duplicate payouts during reentrant mission completion.

## Verification

21 offline integration tests passed with simulated providers, FiveM events and database responses.
All included Lua files compile and the UI JavaScript passes Node syntax checks.
No live FiveM, database or installed inventory tests have been performed.

Run the included mocks from the resource directory:

```sh
texlua tests/bridge_spec.lua
```

On your development server, test one solo mission, a co-op mission in each/split mode, item consumption,
full/empty inventory, duty access, creator permissions and bank payout. Repeat with the inventory you actually use.
Confirm existing progression and saved pools load, and test a provider outage before public release.

## Rollback

Restore your previous Poolcleaner folder and configuration. No new database columns or tables were introduced.

## Changelog

- v1.2.0: shared MM Bridge integration, validated payment result, settlement guard, inventory adapter consolidation.
- v1.1.0: original supplied multiplayer build.
