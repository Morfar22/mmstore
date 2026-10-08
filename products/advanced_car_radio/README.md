---
description: "Advanced Car Radio 1.2.0: installation, gameplay and integration reference."
---

# Advanced Car Radio

Persistent vehicle radio with personal playlists, plate-based libraries, playback queues, xSound positional audio, per-character listening volume and door/window/roof-dependent cabin leakage.

| Release | Resource | Config |
| --- | --- | --- |
| **1.2.0** | `advanced_car_radio` | `shared/config.lua` |

{% hint style="info" %}
Requires xSound for audio, oxmysql for persistence and ox_lib. No target/inventory/phone adapter is required. Provider changes do not move saved radio ownership automatically.
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
