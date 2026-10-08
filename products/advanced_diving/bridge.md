---
description: "Provider setup and migration boundaries for Advanced Diving."
---

# Advanced Diving v1.1.0 — MM Bridge update

Requires your existing `mm_bridge` (0.1.0+ API), your selected framework, ox_lib, oxmysql, ox_target and OneSync.
The bridge is not included in this ZIP. Replace only this resource and merge your existing configuration.

```cfg
ensure oxmysql
ensure ox_lib
# Start the selected framework here.
# Start the inventory configured in mm_bridge if RequireGearItem is enabled.
ensure ox_target
ensure mm_bridge
ensure advanced_diving
```

## Changes

- Character IDs, player lookup, money and client/server notifications use mm_bridge.
- Optional gear-item checks use a source-bound server callback and bridge inventory counts.
  Configure the inventory once in mm_bridge; both its TGIANN and ox_inventory basic adapters can be used.
- Boat-return settlement is guarded against duplicate concurrent hand-ins.
- Each crew member's payment result is checked. Failed payment is logged with run ID, character ID,
  expected amount, account and error. The member receives an error notification and zero earnings are recorded.
  Completion and XP are still awarded. There is no automatic payment retry or atomic money/SQL transaction.
- The return callback's pay field reports the initiating player's actual credited amount.

## Preserved

The supplied v1.0.3 salvage changes, multiplayer crew flow, contracts, full per-member pay,
crew bonus, XP, sonar, objects, boat handling and UI are preserved. SQL schema and citizenid values are unchanged.
`RequireGearItem` stays false by default; gear is not consumed. If enabled, define `GearItem` in your inventory.
Checking gear on activation is not a continuous inventory enforcement or anti-cheat mechanism.

## Validation

18 offline integration tests passed using the actual migrated server callbacks with simulated providers,
FiveM entities and database responses. Lua and UI JavaScript syntax checks passed.
No live FiveM, actual salvage, installed inventory or database tests were performed.

Run the included mocks from this resource directory: `texlua tests/bridge_spec.lua`.
On your development server, verify gear activation, missing gear, a solo salvage contract,
a multiplayer contract, lifting/loading objectives, boat return, bonus pay, XP and reconnect persistence.
Verify failed payout handling and repeated hand-in cannot pay twice. Keep mm_bridge started before this script.

To roll back, restore your previous resource and configuration; no schema migration is needed.

---

