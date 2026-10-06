# Advanced Government — Configuration

Edit the indicated config file and restart the resource after changes. Values are the exact uploaded defaults, not proposed settings. SQL-backed ownership, tax rates, stock and placement may override or outlive config seed values. Comments below are retained as source context and can include legacy notes; the usage/setup pages explain important current behavior.

All Config assignments in the supplied file are included. Vet pharmacy excerpts omit real-world dose/label fields; use the medicine guide for FiveM effects. Do not apply RP values as real treatment instructions.

## Config.Locale

Selects language where supported; most products supply da/en. Smoking/Pause have no generic locale switch.

Source: `config.lua`, line 3.

```lua
Config.Locale = 'da'
```


## Config.Debug

Diagnostic verbosity; keep disabled outside a reproduction.

Source: `config.lua`, line 4.

```lua
Config.Debug = false
```


## Config.GovernmentJob

Controls government job. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 5.

```lua
Config.GovernmentJob = 'government'
```


## Config.AdminAce

Controls admin ace. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 6.

```lua
Config.AdminAce = 'government.admin'
```


## Config.OpenCommand

Controls open command. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 7.

```lua
Config.OpenCommand = 'government'
```


## Config.AdminCommand

Controls admin command. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 8.

```lua
Config.AdminCommand = 'govadmin'
```


## Config.CityHall

Controls city hall. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 10.

```lua
Config.CityHall = {
    enabled = true,
    coords = vec3(-545.13, -204.22, 38.22),
    distance = 2.0,
    drawDistance = 20.0
}
```


## Config.DefaultTreasuryBalance

Controls default treasury balance. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 17.

```lua
Config.DefaultTreasuryBalance = 2500000
```


## Config.CandidateDeposit

Controls candidate deposit. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 18.

```lua
Config.CandidateDeposit = 50000
```


## Config.MinCharacterAgeDays

Controls min character age days. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 19.

```lua
Config.MinCharacterAgeDays = 0 -- Set > 0 if your players table exposes a created_at field you want to enforce yourself.
```


## Config.VoteOncePerCharacter

Controls vote once per character. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 20.

```lua
Config.VoteOncePerCharacter = true
```


## Config.Election

Registration/campaign/voting duration and mayor term.

Source: `config.lua`, line 22.

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

Government default/min/max percent values; persisted rates can outlive config changes.

Source: `config.lua`, line 30.

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

Controls public jobs. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 39.

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

Government permission sets.

Source: `config.lua`, line 49.

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

Controls mayor permissions. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 57.

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

Controls income tax enabled. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 74.

```lua
Config.IncomeTaxEnabled = true
```


## Config.MaxTransactionAmount

Controls max transaction amount. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 75.

```lua
Config.MaxTransactionAmount = 1000000000
```


## Config.PublicAccounts

Government public-job NRP ledger mapping.

Source: `config.lua`, line 76.

```lua
Config.PublicAccounts = {
    police = 'police', ambulance = 'ambulance', mechanic = 'mechanic',
    lawyer = 'lawyer', judge = 'judge', prosecutor = 'prosecutor', doj = 'doj',
}


-- v2 modules
```


## Config.Banking

NRP adapter settings; loaded bridge still requires its schema.

Source: `config.lua`, line 83.

```lua
Config.Banking = {
    enabled = true,
    resource = 'nrp_core_systems',
    accountPrefix = '', -- NRP routes private concessions through BusinessAccounts below.
    requireRunningResource = true
}
```


## Config.Business

Controls business. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 90.

```lua
Config.Business = {
    requireBossForApplications = true,
    blockedJobs = { unemployed = true, government = true },
    maxGrantRequest = 2000000,
    maxContractBid = 10000000
}
```


## Config.Parties

Controls parties. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 97.

```lua
Config.Parties = {
    creationFee = 25000,
    maxNameLength = 64,
    maxShortNameLength = 12
}
```


## Config.Referendums

Controls referendums. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 103.

```lua
Config.Referendums = {
    defaultHours = 24,
    minHours = 1,
    maxHours = 168
}
```


## Config.CampaignAds

Campaign-fund-priced advertising locations.

Source: `config.lua`, line 109.

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

Government private-concession NRP account mapping.

Source: `config.lua`, line 125.

```lua
Config.BusinessAccounts = {
    restaurant = 'vespucci_kitchen', logistics = 'atlas_response_logistics',
    realestate = 'nordisk_boligservice', security = 'apex_security',
    shopkeeper = 'downtown_247', fueler = 'ltd_little_seoul', casino = 'diamond_casino',
    themepark = 'del_perro_tivoli', taxi = 'metro_cab',
}
```
