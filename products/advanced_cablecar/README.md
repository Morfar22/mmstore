---
description: "Advanced Cablecar 1.8.0: installation, gameplay and integration reference."
---

# Advanced Cablecar

Two synchronized cabins on Pala Springs–Mount Chiliad with fares, ticket machines, cabin doors, rider hold/release, local departure cameras, blips and restricted developer summon controls.

| Release | Resource | Config |
| --- | --- | --- |
| **1.8.0** | `advanced_cablecar` | `config.lua` |

{% hint style="info" %}
Optional targets still call ox_target directly. Ticket-machine proximity interactions work without a target provider. Config.Framework='standalone' explicitly skips fares; legacy 'qbox' selects paid bridge behavior. Framework selection in mm_bridge does not override this resource fare setting.
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
