# Advanced Vet DLC — Exports and integrations

{% hint style="info" %}
Server exports are for trusted resources. Enforce caller authorization and source/amount checks. Client menu actions are not proof of payment or permission. Internal events are not a public adapter API.
{% endhint %}

Prescription items need slot/metadata support. Plain ESX inventory cannot preserve prescription metadata. Bridge billing supports own invoices; NRP retains clinic SQL lists, other clinic-wide lists need a hook. Needs and inventory item-definition/tooltip introspection remain local extensions. Patient IDs default to legacy licenses.

| Export | Side | Arguments | Implementation |
| --- | --- | --- | --- |
| `IsVeterinarian` | server | `src` | `server/main.lua` |
| `IsAdvancedK9Patient` | server | `src` | `server/main.lua` |
| `useVetMedicine` | server | `event, item, inventory, slot, data` | `server/medicine.lua` |

Dynamic exports are described in their specialized integration guides; this literal index is not an exhaustive list of dynamically generated names. Consult [bridge integration](bridge.md) for return contracts and provider limitations, and [internal registrations](events.md) for module routing.
