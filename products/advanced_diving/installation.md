# Installation

```cfg
ensure oxmysql
ensure ox_lib
ensure qbx_core
ensure ox_target
ensure advanced_diving
```

Enable OneSync. Configure dock, boat spawn/return and objectives for your map. Gear items are disabled by default. With RequireGearItem true, install ox\_inventory and the named diving\_gear item; no TGIANN gear bridge is supplied. Lift bag uses prop\_beachball\_02 as a placeholder; a custom streamed model is optional and absent. No diving MLO is supplied.

## Database

Automatic creation exists. Optional manual schema: `install.sql`.

| Resource-owned table      |
| ------------------------- |
| `advanced_diving_players` |

## Staff ACE

Normal player use needs no additional product ACE; see restricted developer setup where relevant.

Source: manifest/config and loaded server database/bridge code.
