---
description: "Dependencies and upgrade steps for Advanced Diving 1.1.0."
---

# Advanced Diving — Installation

{% hint style="info" %}
Use the bridge release **1.1.0** with **mm_bridge 0.3.0+**. External providers are not included.
{% endhint %}

## 1. Prepare the resource

Back up the current resource and database. Keep the folder named `advanced_diving`. Merge your existing settings into the new config instead of replacing your custom settings blindly.

## 2. Start dependencies

Start your selected framework, inventory, phone and target providers before mm_bridge. The manifest dependencies for this release are:

```cfg
ensure mm_bridge
ensure ox_lib
ensure ox_target
ensure oxmysql
ensure advanced_diving
```

This lists required resources, not all optional integrations. Install OneSync and external gameplay integrations where the product's networked features require them. See [bridge integration](bridge.md).

## 3. Prepare data and items

No separate SQL file is included; see the resource database initialization where applicable.

Use the [SQL/install reference](install-reference.md) for included schemas and item templates. Import initial schema only where needed; preserve existing records. Review ALTER migrations before applying them. Add required item definitions when you enable inventory requirements.

## 4. Configure and verify

This release still directly requires ox_target for its job NPC. Choosing qb-target/qtarget in mm_bridge does not replace that integration. Optional gear checks use the bridge; gear is not consumed. Failed crew payout completes progression with zero credited earnings and requires reconciliation.

Read [configuration](configuration.md), [bridge integration](bridge.md) and [troubleshooting](troubleshooting.md). Test one complete workflow, a missing-provider case and persistence after reconnect before production. Live provider combinations have not been validated here.
