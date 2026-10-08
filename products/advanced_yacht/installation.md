# Installation

```cfg
ensure oxmysql
ensure ox_lib
ensure qbx_core
ensure ox_inventory
ensure ox_target
ensure advanced_yacht
```

All five manifest dependencies, including ox\_inventory, are required. No TGIANN stash bridge is supplied. Configure broker/economy and appearance (defaults to illenium-appearance; qb-clothing/custom/none alternatives). Supply the appearance resource. Yacht uses Rockstar static IPLs/props and scripted cameras, not a custom drivable yacht or story cutscene asset. Vehicle add-ons are bought separately.

## Database

Automatic creation exists. Optional manual schema: `install.sql`.

| Resource-owned table              |
| --------------------------------- |
| `advanced_yacht_properties`       |
| `advanced_yacht_property_access`  |
| `advanced_yacht_vehicle_upgrades` |

## Staff ACE

```cfg
add_ace group.admin advanced_yacht.admin allow
```

Source: manifest/config and loaded server database/bridge code.
