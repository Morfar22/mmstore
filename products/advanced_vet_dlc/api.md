# Advanced Vet DLC — Exports and integrations

## Exports

| Side | Export | Contract |
| --- | --- | --- |
| Server | IsVeterinarian(src) | Boolean based on job/use ACE |
| Server | IsAdvancedK9Patient(src) | Player animal/K9 classification through Vet bridge |
| Client | OpenNearestPatient() | Starts the existing nearby-patient UI request |
| Server inventory | useVetMedicine(event, item, inventory, slot, data) | Generic inventory callback, not a direct heal API |
| Server inventory | Dedicated medicine exports | Per-product callback identities used by TGIANN |

```lua
-- SERVER
local permitted = exports.advanced_vet_dlc:IsVeterinarian(playerServerId)
-- CLIENT
exports.advanced_vet_dlc:OpenNearestPatient()
```

For item definitions, use the exact bundled install tables, including server.export identities. Do not manually call medicine callback exports as gameplay RPCs: phase/source/slot/patient/metadata contracts come from inventory. The medicine page lists dedicated names.

NRP billing calls CreateInvoice and PayInvoice on nrp_core_systems and reads nrp_invoices. It is not automatically portable to another framework/billing ledger. Sky integration uses its server heal event and revive flow, keeping returned injury profiles diagnostic. K9 integration uses passport/care exports and temporary trainer sessions, not handler pairing.

If selecting ox_lib presentation, note the supplied Vet manifest does not load @ox_lib/init.lua. The runtime checks availability of the lib global, and includes internal/native fallbacks. Merely having another resource named ox_lib running does not by itself load its global API into this resource; adapt the manifest if intentionally relying on lib calls.

Source: export declarations and loaded framework/inventory/billing bridges in the supplied product.
