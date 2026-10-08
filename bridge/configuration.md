# Bridge configuration

Edit mm_bridge/config.lua. Select exact providers when multiple are started. Custom adapter names must be selected explicitly; auto only scans built-in candidates.

```lua
MMBridgeConfig = {
    Framework = 'auto', -- auto | qbox | qbcore | esx | standalone | custom adapter name
    FrameworkResource = nil, -- optional override for the selected framework
    FrameworkResources = { qbox = 'qbx_core', qbcore = 'qb-core', esx = 'es_extended' },
    Inventory = 'auto', -- auto | tgiann | ox_inventory | qb-inventory | esx | standalone | none | custom
    OxResource = 'ox_inventory',
    TgiannResource = 'tgiann-inventory',
    QbInventoryResource = 'qb-inventory',
    Target = 'auto', -- auto | ox_target | qb-target | qtarget | standalone | none | custom
    TargetResources = { ox_target = 'ox_target', ['qb-target'] = 'qb-target', qtarget = 'qtarget' },
    Phone = 'none', -- auto | lb-phone | qb-phone | framework | export | none | custom
    PhoneResources = { ['lb-phone'] = 'lb-phone', ['qb-phone'] = 'qb-phone' },
    PhoneExport = {
        Resource = 'your-phone',
        ServerNumberExport = nil, -- exact server export name from your phone documentation
        ServerNumberArgument = 'source', -- source | character
        ServerNotifyExport = nil, -- signature (source, notificationTable)
        ClientNumberExport = nil, -- signature ()
        ClientOpenExport = nil, -- signature ()
        ClientNotifyExport = nil -- signature (notificationTable)
    },
    Billing = 'framework', -- framework | esx_billing | nrp | none | custom
    BillingResources = { esx_billing = 'esx_billing', nrp = 'nrp_core_systems' },
    EsxBillingTable = 'billing',
    StandaloneTargetKey = 38, -- E
    StaffAce = 'mmstore.staff',
    MaxMoneyAmount = 1000000000,
    MaxItemCount = 10000,
    EsxAccounts = { cash = 'money', bank = 'bank', crypto = false },
    EsxAssumeDuty = false, -- explicit fallback only when job has no duty field
    EsxBossGrades = { boss = true },
    BillingJournal = 'billing-journal.json', -- generated on first use; preserve on upgrades
    CustomAdapterOwners = { -- external resource names permitted to register adapters
        -- ['my_mm_adapters'] = true
    }
}

```

The bridge has no generic stash, inventory UI/weight, needs setter or offline job administration API. Product-local hooks implement these where documented.
