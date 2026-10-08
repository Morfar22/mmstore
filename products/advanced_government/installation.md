---
description: "Dependencies and upgrade steps for Advanced Government 2.1.0."
---

# Advanced Government — Installation

{% hint style="info" %}
Use the bridge release **2.1.0** with **mm_bridge 0.3.0+**. External providers are not included.
{% endhint %}

## 1. Prepare the resource

Back up the current resource and database. Keep the folder named `advanced_government`. Merge your existing settings into the new config instead of replacing your custom settings blindly.

## 2. Start dependencies

Start your selected framework, inventory, phone and target providers before mm_bridge. The manifest dependencies for this release are:

```cfg
ensure mm_bridge
ensure ox_lib
ensure oxmysql
ensure advanced_government
```

This lists required resources, not all optional integrations. Install OneSync and external gameplay integrations where the product's networked features require them. See [bridge integration](bridge.md).

## 3. Prepare data and items

No separate SQL file is included; see the resource database initialization where applicable.

Use the [SQL/install reference](install-reference.md) for included schemas and item templates. Import initial schema only where needed; preserve existing records. Review ALTER migrations before applying them. Add required item definitions when you enable inventory requirements.

## 4. Configure and verify

Default native job synchronization is QBox only; QBCore/ESX/standalone use SQL political roles unless custom job sync is configured. Default society settlement still needs NRP resources/schema or an atomic custom society adapter. Payroll tax is an opt-in export, not an automatically installed payroll hook.

Read [configuration](configuration.md), [bridge integration](bridge.md) and [troubleshooting](troubleshooting.md). Test one complete workflow, a missing-provider case and persistence after reconnect before production. Live provider combinations have not been validated here.
