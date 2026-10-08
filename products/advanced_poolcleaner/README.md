---
description: "Advanced Poolcleaner 1.2.0: installation, gameplay and integration reference."
---

# Advanced Poolcleaner

Cooperative pool maintenance with task reservations, routes, progression, reputation, skill tree and persistent pool creator. Public job and no required inventory items are the supplied defaults.

| Release | Resource | Config |
| --- | --- | --- |
| **1.2.0** | `advanced_poolcleaner` | `config.lua` |

{% hint style="info" %}
Optional item requirements default to Inventory.mode='none'. Select mode='bridge' for generic bridge inventory reads. Required item mutations and payouts must be confirmed; failed payout completes progression but records zero earnings and needs staff reconciliation.
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
