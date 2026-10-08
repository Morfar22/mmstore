# Getting started

1. Back up replaced resources and database.
2. Extract product folders under resources; keep folder names.
3. Read product dependencies and install only required providers.
4. Merge item/job snippets into existing definitions, preserving other entries.
5. Import mandatory SQL or enable documented automatic creation. Fresh schemas are not universal upgrade migrations.
6. Configure real map points, access, economy and integrations.
7. Start dependencies first, then product; inspect console/F8.
8. Run the product acceptance checklist with two players for shared workflows.

## Startup ordering example

Choose only supported/adapted inventory integrations for your server; do not blindly enable two inventories.

```cfg
ensure oxmysql
ensure ox_lib
ensure qbx_core
ensure ox_target
# Start selected inventory, phone, audio, appearance and optional bridges first.
# Start nrp_core_systems before Government/default Vet billing.
ensure advanced_k9
ensure advanced_vet_dlc
# Add other products after their dependencies.
```

No external dependency resources are included. Government requires NRP banking adaptation/supply; Smoking needs missing item/icon distribution files. These prerequisites must be resolved before customer installation.
