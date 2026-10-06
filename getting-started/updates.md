# Updates and rollback

Back up code and all relevant tables. Merge config fields while preserving map/job/account customizations. Fresh-install SQL is not an arbitrary fork migration. Government v2 migration assumes a compatible v1 schema; automatic Vet/K9/Yacht changes also need review for forks.

Restart full server for framework jobs/items/wage-hook changes when hot reload is unsupported. Preserve metadata, invoices, loans, stashes and placed objects. Test multiplayer after integration changes.

Rollback by stopping affected resource and restoring a compatible code/config/database set. Reconcile in-flight invoices/returns/payments before deleting tables or stashes; reverting code against upgraded schema may be incompatible.
