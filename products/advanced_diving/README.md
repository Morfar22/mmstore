---
description: "Advanced Diving 1.1.0: installation, gameplay and integration reference."
---

# Advanced Diving

Cooperative diving with shared networked boats and salvage objects, XP contracts, sonar, scuba toggling and server-owned objective reservations. Crews share the normal world; no mission routing buckets are created.

| Release | Resource | Config |
| --- | --- | --- |
| **1.1.0** | `advanced_diving` | `shared/config.lua` |

{% hint style="info" %}
This release still directly requires ox_target for its job NPC. Choosing qb-target/qtarget in mm_bridge does not replace that integration. Optional gear checks use the bridge; gear is not consumed. Failed crew payout completes progression with zero credited earnings and requires reconciliation.
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
