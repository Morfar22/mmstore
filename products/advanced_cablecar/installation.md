# Advanced Cablecar — Installation

```cfg
ensure ox_lib
ensure qbx_core
ensure advanced_cablecar
```

Start qbx_core before this resource for default qbox fares although it is not a hard dependency. Standalone mode skips money deduction; it does not add ESX/QBCore banking. ox_target is optional/disabled; ox_lib proximity is default. Current ticket prop is prop_park_ticket_01 despite stale README text. Current UI is ox_lib, not the previous Scaleform runtime. Preserve the included GPL v3 LICENSE and NOTICE when redistributing.

## Database

No SQL tables.

| Resource-owned table |
| --- |

## Staff ACE

Normal player use needs no additional product ACE; see restricted developer setup where relevant.

Source: manifest/config and loaded server database/bridge code.
