# Vet — Billing and integrations

# Advanced Vet DLC 15.11.0 — mm_bridge

Requires mm_bridge 0.3.0+, ox_lib and oxmysql. This archive contains only advanced_vet_dlc; install the previously supplied bridge separately.

## Installation

Back up the resource configuration and database. Replace the resource, transfer your clinic, medicine and K9 settings, and keep the resource name advanced_vet_dlc. Import sql/advanced_vet.sql for a new installation; use the existing supplied migrations when upgrading older schemas. Do not drop existing tables.

Start dependencies first:

```cfg
ensure oxmysql
ensure ox_lib
# Start your framework, inventory, target and billing resources here.
ensure mm_bridge
ensure advanced_vet_dlc
```

Select framework, inventory, target and billing providers in mm_bridge/config.lua. Vet's inventory and target provider settings are now bridge; none disables dispensing and markers selects keyboard interactions. Existing auto/provider names do not override the central bridge selection.

## Compatibility

| Area | Behavior |
| --- | --- |
| Framework | QBox, QBCore, ESX, standalone or a registered custom bridge adapter; jobs and personal money use bridge APIs. |
| Target | ox_target, qb-target, qtarget or custom bridge targets; markers when targets are disabled/unavailable. |
| Prescriptions | ox_inventory, TGIANN, QB inventory or custom metadata/slot-capable adapters. Plain ESX inventory cannot preserve prescription metadata and dispensing fails explicitly. |
| Medicine | Native ox/TGIANN item exports retained; framework usable registration uses mm_bridge. Authoritative slots are required. Unknown TGIANN callback phases are rejected. Test the installed TGIANN version's one-shot consume contract before launch. |
| Billing | Central bridge billing. NRP keeps the existing clinic-wide SQL ledger and ownership checks. Framework billing pays the online issuing player, not a clinic society. |
| Custom billing | Return veterinary metadata (ui=veterinary, clinicId) from get-invoices for the customer menu. Config.Billing.bridgeRows can supply clinic-wide rows. Payment ownership must be enforced by the billing adapter. |
| ESX billing | Set bridgeSociety to society_vet if needed. Standard esx_billing does not retain Vet clinic metadata or expose bridge payment; use its original billing menu. Vet's clinic/customer lists cannot reconstruct that association. |
| Needs | Existing K9 exports take priority. QBox/QB native SetMetaData is an isolated extension with readback. ESX dispatches to existing esx_status client handling. Other frameworks need Config.BridgeNeeds. |
| Phones | No new phone feature was added; existing Vet UI/K9 flows remain. |

Register custom framework, inventory, target or billing adapters in mm_bridge as described in its custom-adapters documentation. Resource-specific needs are configured as a server function Config.BridgeNeeds(src,hunger,thirst) returning true only after applying the values. Generic bridge adapters do not provide a needs or item-definition catalog API; native inventory tooltip/item-export introspection remains isolated locally. For a renamed TGIANN resource set Config.Inventory.tgiannResource to match the central bridge configuration.

## Existing data and behavior

Config.BridgeIdentity defaults to legacy_license to retain current patient records, consents, prescriptions and passport keys. Character billing identity comes from mm_bridge. Only switch BridgeIdentity to character after manually migrating every related Vet key and coordinating K9 identities; changing frameworks also needs billing identity review. The unstable session-ID fallback was removed.

Legacy Vet invoice rows remain payable through the original SQL claim flow, with money removed through the bridge. New invoices use the selected bridge ledger. Framework invoice string IDs survive the HTML/client/server path. Billing must be available; standalone never silently bypasses positive charges. Free zero-cost treatments remain free. Config.Billing.allowStandaloneFree no longer bypasses payment.

Medicine and prescription documents are separate inventory writes. A partially delivered bundle is reported; it is not automatically retried or compensated. Review the stored prescription and recipient inventory before dispensing again. ESX on-duty behavior is controlled centrally by mm_bridge's EsxAssumeDuty setting.

K9, ambulance, consent, placement editor, kennel, pharmacy, treatments and patient gameplay remain in the resource. K9 care fallback no longer invents hunger/thirst when metadata is unavailable.

## Validation

36 isolated mocked checks cover identity compatibility, strict money results, prescription metadata, invoice filtering/string IDs, custom needs, authoritative medicine slots and replay rejection. 35 Lua files compile; node --check passes for html/app.js. Run texlua tests/bridge_spec.lua from the resource directory.

No live FiveM server test was performed. Verify access/duty, clinic targets, prescribing and using medicine, K9 consent/care, legacy and new invoice payment, database continuity, and the installed inventory's consume behavior on a staging server before production.
