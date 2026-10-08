# Government — Society banking



Config.SocietyBridge.mode='nrp_sql' retains the supplied NRP integration. It requires nrp_core_systems plus its vi_accounts/vi_transactions schema. Private concessions additionally use nrp_businesses and its ownership data. NRP was removed as a hard manifest dependency; choosing this adapter still requires those resources/schema. Config.Banking.enabled=false disables society settlement.

The NRP SQL path preserves treasury debit, account credit, receipt and grant/contract status updates on a single oxmysql transaction connection. Standalone treasury credits/debits without a society account still use government SQL. Grants/contracts or society payouts are disabled without a supported society adapter. A framework choice does not convert NRP banking itself.

Custom banking is configured through Config.SocietyBridge.custom:

- resolveAccount(job): return an actual mapped account string or nil. Blocked jobs remain blocked.
- isConcessionBoss(source,job): confirm real private-business control, returning true only when authorized.
- transfer(amount,direction,reason,metadata,actorId,actorName,account,settlement): return true and optional resulting treasury balance only after confirmed atomic settlement. settlement may contain kind=grant/contract, IDs and review details.
- credit(account,amount): confirmed standalone society credit used by the existing job-credit export; it is not a substitute for atomic transfer.

The transfer adapter must validate/recheck available treasury funds and settlement eligibility, update the government grant/contract status exactly once, credit the real society account and persist receipt/audit data atomically or provide an equally durable settlement protocol. Calling an external AddMoney export and returning true is not a complete settlement adapter. This package does not guess ESX addonaccount, QB banking or other providers' schema. Configure PublicAccounts/BusinessAccounts to real account mappings.
