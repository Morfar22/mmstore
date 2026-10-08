# Installation

```cfg
ensure oxmysql
ensure ox_lib
ensure qbx_core
ensure tgiann-inventory
ensure ox_target
ensure advanced_smoking
```

This is a TGIANN-style adapter, not a generic inventory switch. Config.Inventory is the resource name. It requires native TGIANN exports/hooks.

**Missing distribution files:** the archive has the 41-product catalog but no Smoking inventory item definition file or 41 item icons mentioned in README. Define every smk\_\* catalog item, including four loose cigarettes and the roach. Attach client export advanced\_smoking.useItem for usable items and preserve unique metadata/nonstacking behavior. Use the catalog page for exact keys/weights.

Verify GetItemBySlot, GetPlayerItems, UpdateItemMetadata, CanCarryItem, AddItem, RemoveItem, registerHook, RegisterStash and OpenInventory. Missing hooks leave containers locked with a console error. Install items before opening shop sales. Give initial owner via `smokeshopowner <server-id>` in console or with admin ACE. Ownership is a separate persistent record, not a QBox job.

## Database

Automatic creation exists. Four schemas are in startup code.

| Resource-owned table     |
| ------------------------ |
| `nrp_smoking_deliveries` |
| `nrp_smoking_profiles`   |
| `nrp_smoking_props`      |
| `nrp_smoking_shops`      |

## Staff ACE

```cfg
add_ace group.admin advanced_smoking.admin allow
```

Source: manifest/config and loaded server database/bridge code.
