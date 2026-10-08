---
description: "Dependencies and upgrade steps for Advanced Orbital 1.3.0."
---

# Advanced Orbital — Installation

{% hint style="info" %}
Use the bridge release **1.3.0** with **mm_bridge 0.3.0+**. External providers are not included.
{% endhint %}

## 1. Prepare the resource

Back up the current resource and database. Keep the folder named `advanced_orbital`. Merge your existing settings into the new config instead of replacing your custom settings blindly.

## 2. Start dependencies

Start your selected framework, inventory, phone and target providers before mm_bridge. The manifest dependencies for this release are:

```cfg
ensure mm_bridge
ensure ox_lib
ensure oxmysql
ensure advanced_orbital
```

This lists required resources, not all optional integrations. Install OneSync and external gameplay integrations where the product's networked features require them. See [bridge integration](bridge.md).

## 3. Prepare data and items

- `sql/advanced_orbital.sql`

Use the [SQL/install reference](install-reference.md) for included schemas and item templates. Import initial schema only where needed; preserve existing records. Review ALTER migrations before applying them. Add required item definitions when you enable inventory requirements.

## 4. Configure and verify

Active job/grade/duty, ACE or public terminal access is checked server-side. Standalone without a custom economy requires DefaultPrice and every terminal's price to be zero. oxmysql and the supplied SQL are still required.

Read [configuration](configuration.md), [bridge integration](bridge.md) and [troubleshooting](troubleshooting.md). Test one complete workflow, a missing-provider case and persistence after reconnect before production. Live provider combinations have not been validated here.
