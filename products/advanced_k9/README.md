---
description: "Advanced K9 95.1.0: installation, gameplay and integration reference."
---

# Advanced K9

A two-player handler and player-controlled dog system with service/civilian profiles, adoption, progression, scent work, training, care, vehicle cages and stationary kennels. Handler and veterinary orders are instructions; the dog player controls movement and accepts formal drills.

| Release | Resource | Config |
| --- | --- | --- |
| **95.1.0** | `advanced_k9` | `config.lua` |

{% hint style="info" %}
Standalone service authority needs ACE or explicit opt-in; civil play remains available. Needs and optional legacy phone adapters remain local extensions. The existing K9 UI and Vet exports are retained. Database keys default to legacy licenses; character mode requires a manual migration.
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
