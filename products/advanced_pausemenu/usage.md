# Pausemenu — Using the menu

ESC or /escmenu opens the configured menu. The map/settings cards open the native GTA frontend; /map opens the native map. Waypoints and shortcuts use your configured commands.

The server provides the requesting player's identity, active job and money through the bridge. Unsupported balances show a dash. The online list keeps display names and ping. Service duty counts exist in the response but are not rendered in the current UI.

Configure Inventory.command to the command actually registered by your inventory, or supply Inventory.open. Inventory.getWeight is an optional local client hook. Bridge v0.3.0 does not open inventories or read weights. See [bridge integration](bridge.md).

Translate configured/hardcoded labels where needed. Native frontend and inventory UI behavior require live validation against the installed server resources.
