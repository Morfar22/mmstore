---
description: "Dependencies and upgrade steps for Advanced Vet DLC 15.11.0."
---

# Advanced Vet DLC — Installation

{% hint style="info" %}
Use the bridge release **15.11.0** with **mm_bridge 0.3.0+**. External providers are not included.
{% endhint %}

## 1. Prepare the resource

Back up the current resource and database. Keep the folder named `advanced_vet_dlc`. Merge your existing settings into the new config instead of replacing your custom settings blindly.

## 2. Start dependencies

Start your selected framework, inventory, phone and target providers before mm_bridge. The manifest dependencies for this release are:

```cfg
ensure oxmysql
ensure ox_lib
ensure mm_bridge
ensure advanced_vet_dlc
```

This lists required resources, not all optional integrations. Install OneSync and external gameplay integrations where the product's networked features require them. See [bridge integration](bridge.md).

## 3. Prepare data and items

- `sql/advanced_vet.sql`
- `sql/v15_6_1_migration.sql`

Use the [SQL/install reference](install-reference.md) for included schemas and item templates. Import initial schema only where needed; preserve existing records. Review ALTER migrations before applying them. Add required item definitions when you enable inventory requirements.

## 4. Configure and verify

Prescription items need slot/metadata support. Plain ESX inventory cannot preserve prescription metadata. Bridge billing supports own invoices; NRP retains clinic SQL lists, other clinic-wide lists need a hook. Needs and inventory item-definition/tooltip introspection remain local extensions. Patient IDs default to legacy licenses.

Read [configuration](configuration.md), [bridge integration](bridge.md) and [troubleshooting](troubleshooting.md). Test one complete workflow, a missing-provider case and persistence after reconnect before production. Live provider combinations have not been validated here.
