# Advanced Vet DLC — Installation

```cfg
ensure oxmysql
ensure advanced_vet_dlc
```

Only oxmysql is a hard dependency, but shipped `Billing.provider = 'nrp'` calls qbx_core/nrp_core_systems and requires their invoice schema. Those resources are absent. To use local legacy invoices, select a non-NRP value such as `legacy`; this selects the existing local route, not a new third-party adapter. Test its framework payment behavior.

1. Define your veterinary framework jobs. No Vet job snippet is supplied.
2. Review Access.jobs: police currently has Vet UI access.
3. Grant use and setup ACEs separately.
4. Merge the matching `install/` inventory table entries; do not replace your full item file.
5. Save patient AND release positions for every used table/kennel in `/vetsetup`. `editorOnly = true` means config coordinates are not runtime fallbacks.
6. Start/configure Onex emotes for the shipped `bdogsleep`/`bdogupk` pose flow, or configure and test another provider.
7. Start advanced_k9 before Vet when using its optional integration.

Clinic MLOs and item icons are not included. Check workstation points against your map.

## Database

Automatic creation exists. Optional manual schema: `sql/advanced_vet.sql`.

| Resource-owned table |
| --- |
| `advanced_vet_admissions` |
| `advanced_vet_appointments` |
| `advanced_vet_chips` |
| `advanced_vet_invoices` |
| `advanced_vet_patients` |
| `advanced_vet_placement_overrides` |
| `advanced_vet_prescriptions` |
| `advanced_vet_stock` |
| `advanced_vet_surgeries` |
| `advanced_vet_triage` |
| `advanced_vet_vaccinations` |
| `advanced_vet_visits` |
| `advanced_vet_xrays` |

## Staff ACE

```cfg
add_ace group.admin advanced_vet.use allow
add_ace group.admin advanced_vet.setup allow
```


Source: manifest/config and loaded server database/bridge code.
