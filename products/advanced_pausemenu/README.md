---
description: "Advanced Pausemenu 5.2.0: installation, gameplay and integration reference."
---

# Advanced Pausemenu

A framework-connected pause menu with character/money information, service counts, player list, inventory weight where supported, FAQ, updates, shortcuts and waypoints. Native map/settings bridges return to the custom menu.

| Release | Resource | Config |
| --- | --- | --- |
| **5.2.0** | `advanced_pausemenu` | `config.lua` |

{% hint style="info" %}
The bridge reads inventory items but has no UI-open or weight API. Configure Inventory.command or a confirmed client Inventory.open hook; getWeight is a local hook. Unsupported balances show as unavailable. Service counts use duty but are not currently rendered by the UI.
{% endhint %}

## Set up your server

1. Read [installation](installation.md) and [bridge integration](bridge.md).
2. Merge the [configuration](configuration.md) into your server settings.
3. Follow [gameplay](usage.md), then test the real providers on staging.

## Keep these references nearby

- [Commands and controls](commands.md)
- [Troubleshooting](troubleshooting.md)
- [Exports and integration contracts](api.md)
- [SQL and installation files](install-reference.md)
