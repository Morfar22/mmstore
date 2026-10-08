# Update and roll back

1. Back up the resource config, SQL tables, inventory storage and mm_bridge/billing-journal.json.
2. Read the release integration boundary and local hooks before replacing files.
3. Merge config changes, start providers/bridge/adapters/consumers in order and test on staging.
4. Confirm old ownership/progression/patient/adoption data still loads.
5. Keep the previous release until your live workflow passes.

Do not switch framework/inventory and upgrade gameplay in one untracked step. There is no automatic cross-framework data or stash migration.

For rollback, stop consumers, restore the old code/config and compatible dependencies, and restore data only after reconciling any completed payments or SQL writes. Replacing files alone does not undo financial operations.
