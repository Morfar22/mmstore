# Installation

```cfg
ensure oxmysql
ensure ox_lib
ensure qbx_core
ensure advanced_poolcleaner
```

For whitelist use, set JobMode = whitelist, RequiredJob and optional RequireOnDuty, then merge qbx\_job\_snippet.lua. Public is default. Inventory.mode none needs no items; ox\_inventory/tgiann-inventory modes need matching supplied snippets. Custom mode deliberately fails until server/inventory\_bridge.lua is adapted. Grant poolcleaner.admin and create exact task points through /poolcreator. Default locations are examples, not supplied interiors.

## Database

Automatic creation exists. Optional manual schema: `sql/install.sql`.

| Resource-owned table      |
| ------------------------- |
| `advanced_pool_locations` |
| `advanced_pool_profiles`  |

## Staff ACE

```cfg
add_ace group.admin poolcleaner.admin allow
```

Source: manifest/config and loaded server database/bridge code.
