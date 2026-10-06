# Advanced Government — Installation

```cfg
ensure oxmysql
ensure ox_lib
ensure qbx_core
ensure ox_target
ensure nrp_core_systems
ensure advanced_government
```

The loaded `server/nrp_bridge.lua` directly updates `vi_accounts`, logs to `vi_transactions`, reads `nrp_businesses` and emits `nrp:audit:log`. The private-business path also calls the nrp_businesses resource. Neither NRP system is supplied. Changing Banking.resource to Renewed-Banking alone does not replace this bridge.

1. Supply compatible nrp_core_systems banking/schema or develop a replacement adapter.
2. Fresh installs import `install/install.sql`. Compatible v1 upgrades import `install/migrate_v1_to_v2.sql`; that migration does not replace all older base schema.
3. Permanently merge `install/qbx_job.lua` into QBox jobs. Mayor is grade 4.
4. Grant government.admin and map PublicAccounts/BusinessAccounts correctly.
5. Add a single call to WithholdIncomeTax in QBox payroll after successful gross bank pay if you want wage tax. That QBox modification is not in this archive.
6. Restart the server after framework job/wage changes.

The README's older Renewed-Banking example is stale for this build. Existing v1 treasury transactions need the reference column/unique key used by the current adapter.

## Database

Import `install/install.sql` before use.

| Resource-owned table |
| --- |
| `government_audit` |
| `government_budgets` |
| `government_cabinet` |
| `government_campaign_ads` |
| `government_campaign_donations` |
| `government_candidates` |
| `government_contract_bids` |
| `government_contracts` |
| `government_elections` |
| `government_grants` |
| `government_law_votes` |
| `government_laws` |
| `government_office` |
| `government_parties` |
| `government_party_members` |
| `government_referendum_votes` |
| `government_referendums` |
| `government_settings` |
| `government_taxes` |
| `government_treasury` |
| `government_treasury_transactions` |
| `government_votes` |

## Staff ACE

```cfg
add_ace group.admin government.admin allow
```


Source: manifest/config and loaded server database/bridge code.
