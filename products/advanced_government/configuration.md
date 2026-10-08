---
description: "Current configuration excerpts for Advanced Government."
---

# Advanced Government — Configuration

Select common providers in [mm_bridge](../../bridge/configuration.md). These excerpts come from the delivered **2.1.0** configuration. Edit gameplay settings in the resource, not the shared bridge. SQL records may override initial defaults.

## Config

Source file: `config.lua`.

```lua
Config = {}
```

## Config.Locale

Source file: `config.lua`.

```lua
Config.Locale = 'da'
```

## Config.Debug

Source file: `config.lua`.

```lua
Config.Debug = false
```

## Config.GovernmentJob

Source file: `config.lua`.

```lua
Config.GovernmentJob = 'government'
```

## Config.AdminAce

Source file: `config.lua`.

```lua
Config.AdminAce = 'government.admin'
```

## Config.OpenCommand

Source file: `config.lua`.

```lua
Config.OpenCommand = 'government'
```

## Config.AdminCommand

Source file: `config.lua`.

```lua
Config.AdminCommand = 'govadmin'
```

## Config.CityHall

Source file: `config.lua`.

```lua
Config.CityHall = {
    enabled = true,
    coords = vec3(-545.13, -204.22, 38.22),
    distance = 2.0,
    drawDistance = 20.0
}
```

## Config.DefaultTreasuryBalance

Source file: `config.lua`.

```lua
Config.DefaultTreasuryBalance = 2500000
```

## Config.CandidateDeposit

Source file: `config.lua`.

```lua
Config.CandidateDeposit = 50000
```

## Config.MinCharacterAgeDays

Source file: `config.lua`.

```lua
Config.MinCharacterAgeDays = 0 -- Set > 0 if your players table exposes a created_at field you want to enforce yourself.
```

## Config.VoteOncePerCharacter

Source file: `config.lua`.

```lua
Config.VoteOncePerCharacter = true
```

## Config.Election

Source file: `config.lua`.

```lua
Config.Election = {
    autoCreate = true,
    termDays = 14,
    registrationHours = 48,
    campaignHours = 72,
    votingHours = 24
}
```

## Config.Taxes

Source file: `config.lua`.

```lua
Config.Taxes = {
    income = { label = 'Indkomstskat', default = 18.0, min = 0.0, max = 35.0 },
    business = { label = 'Virksomhedsskat', default = 12.0, min = 0.0, max = 30.0 },
    vat = { label = 'Moms', default = 8.0, min = 0.0, max = 25.0 },
    vehicle = { label = 'Bilafgift', default = 4.0, min = 0.0, max = 25.0 },
    property = { label = 'Ejendomsskat', default = 2.0, min = 0.0, max = 15.0 },
    capital = { label = 'Kapitalafgift', default = 5.0, min = 0.0, max = 25.0 }
}
```

## Config.PublicJobs

Source file: `config.lua`.

```lua
Config.PublicJobs = {
    police = 'Politi',
    ambulance = 'Ambulance',
    mechanic = 'Mekanik/Infrastruktur',
    lawyer = 'Advokater',
    judge = 'Domstolene',
    prosecutor = 'Anklagemyndigheden',
    doj = 'Justitsministeriet'
}
```

## Config.CabinetRoles

Source file: `config.lua`.

```lua
Config.CabinetRoles = {
    finance = { label = 'Finansminister', permissions = { 'treasury.view', 'treasury.transfer', 'tax.manage', 'budget.manage' } },
    justice = { label = 'Justitsminister', permissions = { 'laws.create', 'laws.vote', 'budget.view' } },
    health = { label = 'Sundhedsminister', permissions = { 'budget.view', 'grants.manage' } },
    business = { label = 'Erhvervsminister', permissions = { 'budget.view', 'grants.manage', 'contracts.manage' } },
    transport = { label = 'Transportminister', permissions = { 'budget.view', 'contracts.manage' } }
}
```

## Config.MayorPermissions

Source file: `config.lua`.

```lua
Config.MayorPermissions = {
    ['treasury.view'] = true,
    ['treasury.transfer'] = true,
    ['tax.manage'] = true,
    ['budget.view'] = true,
    ['budget.manage'] = true,
    ['cabinet.manage'] = true,
    ['laws.create'] = true,
    ['laws.vote'] = true,
    ['laws.enact'] = true,
    ['grants.manage'] = true,
    ['contracts.manage'] = true,
    ['audit.view'] = true
}

-- Nordisk integration. Other tax types remain available to server exports;
-- only normal QBox wages are automatically taxed by this installation.
```

## Config.IncomeTaxEnabled

Source file: `config.lua`.

```lua
Config.IncomeTaxEnabled = true
```

## Config.MaxTransactionAmount

Source file: `config.lua`.

```lua
Config.MaxTransactionAmount = 1000000000
```

## Config.PublicAccounts

Source file: `config.lua`.

```lua
Config.PublicAccounts = {
    police = 'police', ambulance = 'ambulance', mechanic = 'mechanic',
    lawyer = 'lawyer', judge = 'judge', prosecutor = 'prosecutor', doj = 'doj',
}


-- v2 modules
```

## Config.Banking

Source file: `config.lua`.

```lua
Config.Banking = {
    enabled = true,
    resource = 'nrp_core_systems',
    accountPrefix = '', -- NRP routes private concessions through BusinessAccounts below.
    requireRunningResource = true
}
```

## Config.Business

Source file: `config.lua`.

```lua
Config.Business = {
    requireBossForApplications = true,
    blockedJobs = { unemployed = true, government = true },
    maxGrantRequest = 2000000,
    maxContractBid = 10000000
}
```

## Config.Parties

Source file: `config.lua`.

```lua
Config.Parties = {
    creationFee = 25000,
    maxNameLength = 64,
    maxShortNameLength = 12
}
```

## Config.Referendums

Source file: `config.lua`.

```lua
Config.Referendums = {
    defaultHours = 24,
    minHours = 1,
    maxHours = 168
}
```

## Config.CampaignAds

Source file: `config.lua`.

```lua
Config.CampaignAds = {
    defaultHours = 24,
    drawDistance = 35.0,
    zones = {
        cityhall = { label = 'Rådhuset', coords = vec3(-545.33, -207.41, 38.22), price = 15000 },
        legion = { label = 'Legion Square', coords = vec3(215.31, -810.22, 30.73), price = 25000 },
        missionrow = { label = 'Mission Row', coords = vec3(428.09, -981.77, 30.71), price = 20000 },
        pillbox = { label = 'Pillbox', coords = vec3(306.36, -588.82, 43.28), price = 18000 }
    }
}

Config.MayorPermissions['parties.manage'] = true
Config.MayorPermissions['referendums.manage'] = true
Config.MayorPermissions['campaign.manage'] = true

-- Private accounts match nrp_economy and the central NRP business bank.
```

## Config.BusinessAccounts

Source file: `config.lua`.

```lua
Config.BusinessAccounts = {
    restaurant = 'vespucci_kitchen', logistics = 'atlas_response_logistics',
    realestate = 'nordisk_boligservice', security = 'apex_security',
    shopkeeper = 'downtown_247', fueler = 'ltd_little_seoul', casino = 'diamond_casino',
    themepark = 'del_perro_tivoli', taxi = 'metro_cab',
}


-- Framework/target providers are selected in mm_bridge/config.lua.
-- auto: native QBox job sync; on other frameworks SQL government roles only.
```

## Config.JobBridge

Source file: `config.lua`.

```lua
Config.JobBridge = { mode = 'auto', qboxResource = 'qbx_core', custom = nil }
-- Society settlement outside NRP needs an explicit atomic transfer adapter.
```

## Config.SocietyBridge

Source file: `config.lua`.

```lua
Config.SocietyBridge = { mode = 'nrp_sql', custom = nil }
```

## Config.IncomeTaxOwners

Source file: `config.lua`.

```lua
Config.IncomeTaxOwners = { ['qbx_core'] = true, ['qb-core'] = true, ['es_extended'] = true }
```
