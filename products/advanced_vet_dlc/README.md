---
description: "Advanced Vet DLC 15.11.0: installation, gameplay and integration reference."
---

# Advanced Vet DLC

Veterinary gameplay for player animals and supported networked world animals: records, treatment, RP triage, X-ray, phased surgery, pharmacy, chips, vaccination, kennel admission, appointments and invoices. Optional K9 integration adds passports, care sync and temporary trainer sessions.

| Release | Resource | Config |
| --- | --- | --- |
| **15.11.0** | `advanced_vet_dlc` | `config.lua` |

{% hint style="info" %}
Prescription items need slot/metadata support. Plain ESX inventory cannot preserve prescription metadata. Bridge billing supports own invoices; NRP retains clinic SQL lists, other clinic-wide lists need a hook. Needs and inventory item-definition/tooltip introspection remain local extensions. Patient IDs default to legacy licenses.
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
