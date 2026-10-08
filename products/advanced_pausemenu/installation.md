# Installation

```cfg
ensure ox_lib
ensure qbx_core
ensure advanced_pausemenu
```

Replace NORDISK RP branding, FAQ, updates, commands and waypoints in config. Inventory bridge calls `openInventory('player')`, GetPlayerWeight and GetPlayerMaxWeight. Changing its resource string to TGIANN does not ensure those exports exist. Implement a compatible adapter or working fallbackCommand; command fallback does not supply weights. Run one ESC replacement. No SQL/items are required.

## Database

No SQL tables.

| Resource-owned table |
| -------------------- |

## Staff ACE

Normal player use needs no additional product ACE; see restricted developer setup where relevant.

Source: manifest/config and loaded server database/bridge code.
