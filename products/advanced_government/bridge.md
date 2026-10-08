---
description: "Provider setup and migration boundaries for Advanced Government."
---

# advanced_government v2.1.0 — MM Bridge

Government treasury, taxes, elections, cabinet roles, parties, campaign ads, grants, contracts, laws and referendums. Core identity, personal money, ACE, notifications and City Hall targets now use mm_bridge v0.3.0+.

## Installation

Required: mm_bridge v0.3.0+, ox_lib and oxmysql. Start your selected framework/target and any configured bank adapters before this resource.

```cfg
ensure ox_lib
ensure oxmysql
# Start selected framework, target and society banking resources here.
ensure mm_bridge
ensure advanced_government
add_ace group.admin government.admin allow
```

Fresh install: import install/install.sql. Preserve existing government_* tables when upgrading. If upgrading the original v1 database, import install/migrate_v1_to_v2.sql as directed for that schema. The bridge release adds no new SQL migration. Merge the new config; old configs lack JobBridge, SocietyBridge and IncomeTaxOwners.

QBox ownership/citizenids remain unchanged. ESX uses the real character identifier, including colon/multicharacter prefixes. Standalone license identity has no character separation. Changing frameworks does not convert existing citizen/office/party/SQL identifiers.

## Framework and target scope

QBox, QBCore and ESX player identity/personal money come from MMBridge. Standalone supports SQL government roles and read-only/community features, but paid candidate registration, party creation and donations require an economy adapter. Configure zero registration/party fees only where supported; donations inherently require money.

City Hall supports ox_target, qb-target, qtarget or bridge standalone interactions. /government remains available without a target. Restart this resource after bridge/target-provider restarts. Inventory, phone and billing adapters are not used here.

SQL government_office and government_cabinet are authoritative for political permissions. A framework job alone does not confer government access. The configured AdminAce remains server-side. Existing mutation authorization, SQL settlement checks and callback throttling remain in place.

## Framework jobs and offline characters

Bridge 0.3.0 does not implement offline job administration. server/job_bridge.lua provides a resource-local extension:

- JobBridge.mode='auto': native QBox job sync when framework=qbox; SQL political roles only on QBCore/ESX/standalone.
- mode='roles': explicitly disable native framework job changes on every framework. SQL mayor/cabinet permissions still work. A successful political role assignment in this mode does not assert a native job changed.
- mode='qbox': require QBox; fail if another framework/resource is selected.

qboxResource must match a renamed selected QBox core. install/qbx_job.lua is the permanent QBox job definition; install it for native sync. QBox preserves native multijob add/remove/primary semantics and offline lookups.

Roles-only mode resolves manually appointed characters from connected players through the bridge. Manual cabinet/admin mayor appointments therefore require the target online. Existing SQL election winners may be offline; their political role is still authoritative when they return. No offline QBCore/ESX player table format is guessed.

For native QB/ESX/custom job sync, provide Config.JobBridge.custom as a trusted SERVER table:

```lua
Config.JobBridge.custom = {
    -- resource='your_job_adapter', -- optional started-state requirement
    getCharacter=function(characterId) return nil end, -- normalized {PlayerData=...}, or nil
    ensure=function() return false end, -- verify/create real job definition
    add=function(characterId,job,grade) return false end,
    remove=function(characterId,job) return false end,
    primary=function(characterId,job) return false end,
}
```

These are placeholders. Mutations must return true only when confirmed and explicitly handle offline characters and single-job versus multijob behavior. Provider failures do not become confirmed job changes. SQL office updates and native job changes are not one atomic transaction; reconcile sync failures printed in the console.

## Society banking and atomic settlement

Config.SocietyBridge.mode='nrp_sql' retains the supplied NRP integration. It requires nrp_core_systems plus its vi_accounts/vi_transactions schema. Private concessions additionally use nrp_businesses and its ownership data. NRP was removed as a hard manifest dependency; choosing this adapter still requires those resources/schema. Config.Banking.enabled=false disables society settlement.

The NRP SQL path preserves treasury debit, account credit, receipt and grant/contract status updates on a single oxmysql transaction connection. Standalone treasury credits/debits without a society account still use government SQL. Grants/contracts or society payouts are disabled without a supported society adapter. A framework choice does not convert NRP banking itself.

Custom banking is configured through Config.SocietyBridge.custom:

- resolveAccount(job): return an actual mapped account string or nil. Blocked jobs remain blocked.
- isConcessionBoss(source,job): confirm real private-business control, returning true only when authorized.
- transfer(amount,direction,reason,metadata,actorId,actorName,account,settlement): return true and optional resulting treasury balance only after confirmed atomic settlement. settlement may contain kind=grant/contract, IDs and review details.
- credit(account,amount): confirmed standalone society credit used by the existing job-credit export; it is not a substitute for atomic transfer.

The transfer adapter must validate/recheck available treasury funds and settlement eligibility, update the government grant/contract status exactly once, credit the real society account and persist receipt/audit data atomically or provide an equally durable settlement protocol. Calling an external AddMoney export and returning true is not a complete settlement adapter. This package does not guess ESX addonaccount, QB banking or other providers' schema. Configure PublicAccounts/BusinessAccounts to real account mappings.

## Income tax integration

WithholdIncomeTax(source,grossWage) now uses numeric source through the bridge, not a citizenid passed to a source-only money API. It is a SERVER export for a trusted payroll resource after successful gross wage payment. Only exact resource names in Config.IncomeTaxOwners are accepted.

```lua
-- In the authorized payroll resource AFTER confirmed gross payout:
local withheld = exports.advanced_government:WithholdIncomeTax(source, grossWage)
```

The export does not install payroll hooks automatically. Preserve an existing QBox wage hook if already installed. Add an explicit hook in QB/ESX payroll if desired and authorize its exact resource name. Other tax exports remain opt-in integrations; displaying a rate does not tax unrelated scripts automatically.

A treasury failure attempts an online refund to the same character. Replacement/disconnected characters are not credited accidentally; unconfirmed credits are logged for manual reconciliation. No offline money API is invented.

## Money and failure limits

Personal money operations and government SQL writes are separate operations, not an atomic framework/SQL transaction. Existing refund paths are retained through a confirmation-checking credit helper. SQL job changes and native framework job changes are similarly separate. Interrupted operations or an ambiguous provider result require staff reconciliation; do not retry credits blindly. Society custom adapters must preserve the settlement guarantees described above.

## Validation

28 offline migration tests pass with mocked FiveM, framework, banking and SQL APIs. Tests cover native QBox job handling, roles-only behavior, ESX identifiers, authorization, numeric-source donations, rejected/nil mutations, bank availability, atomic-adapter delegation, trusted payroll callers, replacement-character refunds and target cleanup. Lua and JavaScript syntax checks pass.

Run texlua tests/bridge_spec.lua from this resource directory. Negative job/credit/target error logs are expected test cases. No live FiveM, payroll, bank/schema or actual SQL transaction validation was performed. The existing government NUI layout is retained.
