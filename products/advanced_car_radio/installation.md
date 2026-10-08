---
description: "Dependencies and upgrade steps for Advanced Car Radio 1.2.0."
---

# Advanced Car Radio — Installation

{% hint style="info" %}
Use the bridge release **1.2.0** with **mm_bridge 0.3.0+**. External providers are not included.
{% endhint %}

## 1. Prepare the resource

Back up the current resource and database. Keep the folder named `advanced_car_radio`. Merge your existing settings into the new config instead of replacing your custom settings blindly.

## 2. Start dependencies

Start your selected framework, inventory, phone and target providers before mm_bridge. The manifest dependencies for this release are:

```cfg
ensure mm_bridge
ensure ox_lib
ensure oxmysql
ensure xsound
ensure advanced_car_radio
```

This lists required resources, not all optional integrations. Install OneSync and external gameplay integrations where the product's networked features require them. See [bridge integration](bridge.md).

## 3. Prepare data and items

- `sql/install.sql`

Use the [SQL/install reference](install-reference.md) for included schemas and item templates. Import initial schema only where needed; preserve existing records. Review ALTER migrations before applying them. Add required item definitions when you enable inventory requirements.

## 4. Configure and verify

Requires xSound for audio, oxmysql for persistence and ox_lib. No target/inventory/phone adapter is required. Provider changes do not move saved radio ownership automatically.

Read [configuration](configuration.md), [bridge integration](bridge.md) and [troubleshooting](troubleshooting.md). Test one complete workflow, a missing-provider case and persistence after reconnect before production. Live provider combinations have not been validated here.
