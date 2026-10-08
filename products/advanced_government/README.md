---
description: "Advanced Government 2.1.0: installation, gameplay and integration reference."
---

# Advanced Government

Mayor and cabinet permissions, treasury, tax rates, elections, campaigns, parties, laws, budgets, grants, tenders and referendums. Society settlement uses the retained NRP SQL integration or an explicitly configured custom adapter.

| Release | Resource | Config |
| --- | --- | --- |
| **2.1.0** | `advanced_government` | `config.lua` |

{% hint style="info" %}
Default native job synchronization is QBox only; QBCore/ESX/standalone use SQL political roles unless custom job sync is configured. Default society settlement still needs NRP resources/schema or an atomic custom society adapter. Payroll tax is an opt-in export, not an automatically installed payroll hook.
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
