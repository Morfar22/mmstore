# Source review and release prerequisites

Reviewed archive: archive-2026-10-06T185320+0200.tar.gz, eleven product folders, 221 files. The automated source pass read text files for registrations/config/schema/resources and inventoried all binary assets; manifests, configuration and relevant gameplay/framework/inventory/financial/placement handlers were examined to author these guides. This is documentation review, not a full security certification or a live gameplay test.

## Verified here

* All 11 resource manifests point to existing included files/patterns.
* All 10 included JavaScript files pass node --check.
* JSON locale files are parsed during documentation validation.
* Documentation navigation/relative links, section coverage and source inventory are checked after generation.

Lua runtime/syntax, actual MySQL migrations, NRP banking exports/schema, inventory APIs, native visuals/sounds and multiplayer gameplay were not executed. Historical README test counts are not re-run or endorsed here. No source resource was patched.

## Confirmed distribution/integration differences

| Product    | Finding                                                                                                 | Installation/release action                                                                     |
| ---------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Government | Hard NRP banking dependency and direct ledger/schema integration; QBox wage caller absent.              | Provide compatible NRP or complete adapter; install permanent jobs and one actual payroll hook. |
| Vet        | Default billing NRP/QBox; editorOnly requires saved DB anchors; Onex pose configuration.                | Configure billing/providers, create all used placements and verify patient pose/consent.        |
| Smoking    | 41 catalog entries; no inventory item definitions/icons; TGIANN-only bridge; CameraEffects actual true. | Supply item assets/definitions and version-compatible hooks; adjust effects deliberately.       |
| K9         | Public civilian access; service approvals; sniff lacks direct TGIANN export adapter.                    | Use intended role policy and check fallback item data or adapt contraband sniff.                |
| Pausemenu  | Generic ox-style inventory exports; native settings page 6; no generic locale selector.                 | Implement actual inventory compatibility and translate hardcoded strings; live-test settings.   |
| All        | Several F7/G/H defaults overlap; manifest versions differ from historical README headings.              | Rebind per server/player; deploy/document exact uploaded versions.                              |
| Orbital    | Impact safe-zone cancellation occurs after payment/log/count without refund path.                       | Publish accurate behavior or implement reconciled refund as a separate code change.             |

The [source inventory](source-inventory.md) includes every supplied file and hashes, while per-product registration pages expose source lookup locations. Review notes do not state that every internal event is a supported API.
