# Advanced Poolcleaner — Configuration

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

-- public = alle kan tage jobbet. whitelist = kræver Config.RequiredJob.
```


## Config.JobMode

Controls job mode. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 7.

```lua
Config.JobMode = 'public'
```


## Config.RequiredJob

Controls required job. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 8.

```lua
Config.RequiredJob = 'poolcleaner'
```


## Config.RequireOnDuty

Controls require on duty. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 9.

```lua
Config.RequireOnDuty = false
```


## Config.AdminAce

Controls admin ace. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 11.

```lua
Config.AdminAce = 'poolcleaner.admin'
```


## Config.Command

Controls command. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 12.

```lua
Config.Command = 'pooljob'
```


## Config.CreatorCommand

Controls creator command. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 13.

```lua
Config.CreatorCommand = 'poolcreator'
```


## Config.DebugCommand

Controls debug command. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 14.

```lua
Config.DebugCommand = 'pooldebug'
```


## Config.Office

Controls office. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 16.

```lua
Config.Office = {
    coords = vec4(-1150.84, -1521.08, 10.63, 34.0),
    interactionDistance = 2.0,
    drawDistance = 20.0,
    blip = {
        enabled = true,
        sprite = 536,
        colour = 3,
        scale = 0.75,
        label = 'AquaWorks Poolservice'
    },
    ped = {
        enabled = true,
        model = 's_m_m_dockwork_01',
        scenario = 'WORLD_HUMAN_CLIPBOARD'
    }
}
```


## Config.Team

Pool group size, invite range, per-member/split payout and bonus.

Source: `config.lua`, line 34.

```lua
Config.Team = {
    maxMembers = 4,
    inviteDistance = 12.0,
    bonusPerExtraMember = 0.05,
    payoutMode = 'each' -- each eller split
}
```


## Config.Security

Controls security. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 41.

```lua
Config.Security = {
    maxTaskDistance = 8.0,
    minProgressRatio = 0.72,
    missionStartCooldown = 8,
    maxRequestDistanceFromOffice = 12.0
}
```


## Config.Missions

Pool route size, task counts, pay/XP/reputation.

Source: `config.lua`, line 48.

```lua
Config.Missions = {
    short = {
        pools = 1,
        tasksPerPool = 3,
        payout = { min = 2600, max = 3400 },
        xp = 90,
        reputation = 2
    },
    medium = {
        pools = 2,
        tasksPerPool = 4,
        payout = { min = 5200, max = 6800 },
        xp = 190,
        reputation = 4
    },
    long = {
        pools = 3,
        tasksPerPool = 6,
        payout = { min = 8500, max = 11000 },
        xp = 330,
        reputation = 7
    }
}
```


## Config.PaymentAccount

Controls payment account. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 72.

```lua
Config.PaymentAccount = 'bank'

-- Valgfrit item-system. 'none' kræver ingen inventory-items.
-- Sæt mode = 'ox_inventory' eller 'tgiann-inventory' for item-krav.
-- Ved et andet inventory kan server/inventory_bridge.lua tilpasses ét sted.
```


## Config.Inventory

Actual inventory adapter/requirements; string/provider alone does not implement a new adapter.

Source: `config.lua`, line 77.

```lua
Config.Inventory = {
    mode = 'none', -- none | ox_inventory | tgiann-inventory | custom
    consumeOnComplete = true,
    requirements = {
        chemicals = { item = 'pool_chemicals', amount = 1 },
        filter = { item = 'pool_filter', amount = 1 }
    }
}

-- Færdigheder er bevidst simple og originale. Serveren beregner alle bonusser.
```


## Config.Skills

Pool unlock prerequisites/costs; actual effects in server/client implementation.

Source: `config.lua`, line 87.

```lua
Config.Skills = {
    efficiency = {
        label = 'Hurtige hænder',
        description = '7% kortere arbejdstid.',
        cost = 1,
        prerequisite = nil
    },
    steady = {
        label = 'Rutineret tekniker',
        description = 'Gør skill checks en smule nemmere.',
        cost = 1,
        prerequisite = 'efficiency'
    },
    chemistry = {
        label = 'Vandkemi',
        description = '5% ekstra betaling pr. tur.',
        cost = 1,
        prerequisite = 'steady'
    },
    route = {
        label = 'Ruteplanlægger',
        description = '10% ekstra XP.',
        cost = 1,
        prerequisite = 'chemistry'
    },
    master = {
        label = 'Poolmester',
        description = 'Yderligere 8% betaling.',
        cost = 2,
        prerequisite = 'route'
    }
}
```


## Config.TaskOrder

Controls task order. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 120.

```lua
Config.TaskOrder = { 'vacuum', 'skim', 'sweep', 'backwash', 'chemicals', 'filter' }
```


## Config.Tasks

Pool action durations, animations, props and checks.

Source: `config.lua`, line 122.

```lua
Config.Tasks = {
    vacuum = {
        duration = 10500,
        icon = 'water',
        progressKey = 'progress_vacuum',
        anim = { dict = 'amb@world_human_janitor@male@base', clip = 'base', flag = 49 },
        prop = { model = 'prop_tool_broom', bone = 28422, pos = vec3(-0.01, 0.0, -0.02), rot = vec3(0.0, 0.0, 0.0) },
        skill = { 'easy', 'easy' }
    },
    skim = {
        duration = 9000,
        icon = 'leaf',
        progressKey = 'progress_skim',
        anim = { dict = 'amb@world_human_janitor@male@base', clip = 'base', flag = 49 },
        prop = { model = 'prop_poolskimmer', bone = 28422, pos = vec3(0.0, 0.0, 0.0), rot = vec3(0.0, 0.0, 0.0) },
        skill = { 'easy', 'medium' }
    },
    sweep = {
        duration = 8500,
        icon = 'broom',
        progressKey = 'progress_sweep',
        anim = { dict = 'amb@world_human_janitor@male@base', clip = 'base', flag = 49 },
        prop = { model = 'prop_tool_broom', bone = 28422, pos = vec3(-0.01, 0.0, -0.02), rot = vec3(0.0, 0.0, 0.0) },
        skill = { 'easy' }
    },
    backwash = {
        duration = 9500,
        icon = 'rotate',
        progressKey = 'progress_backwash',
        anim = { dict = 'mini@repair', clip = 'fixing_a_ped', flag = 49 },
        skill = { 'easy', 'medium' }
    },
    chemicals = {
        duration = 8000,
        icon = 'flask',
        progressKey = 'progress_chemicals',
        anim = { dict = 'anim@heists@box_carry@', clip = 'idle', flag = 49 },
        prop = { model = 'prop_bucket_02a', bone = 28422, pos = vec3(0.02, 0.0, -0.08), rot = vec3(0.0, 0.0, 0.0) },
        skill = { 'easy', 'medium' }
    },
    filter = {
        duration = 11000,
        icon = 'filter',
        progressKey = 'progress_filter',
        anim = { dict = 'mini@repair', clip = 'fixing_a_ped', flag = 49 },
        skill = { 'medium', 'medium' }
    }
}

-- Disse er start-eksempler. Brug /poolcreator til at lave præcise punkter direkte in-game.
-- Hver task kan have sit eget punkt. Anchor bruges til mission-sortering/debug.
```


## Config.DefaultPools

Example pool coordinates; add precise DB locations with creator.

Source: `config.lua`, line 173.

```lua
Config.DefaultPools = {
    {
        id = 'richman_01',
        name = 'Richman Residence',
        anchor = vec3(-1122.55, 374.18, 70.97),
        tasks = {
            vacuum = vec3(-1124.06, 376.14, 70.05),
            skim = vec3(-1119.86, 374.75, 70.05),
            sweep = vec3(-1117.74, 369.86, 70.92),
            backwash = vec3(-1129.04, 369.98, 70.87),
            chemicals = vec3(-1128.35, 372.41, 70.87),
            filter = vec3(-1129.10, 368.70, 70.87)
        }
    },
    {
        id = 'vinewood_01',
        name = 'Vinewood Hills Pool',
        anchor = vec3(-754.35, 620.86, 142.80),
        tasks = {
            vacuum = vec3(-756.06, 622.13, 142.20),
            skim = vec3(-751.99, 620.17, 142.20),
            sweep = vec3(-748.89, 616.74, 142.84),
            backwash = vec3(-760.06, 616.70, 142.78),
            chemicals = vec3(-758.80, 618.72, 142.78),
            filter = vec3(-760.58, 615.42, 142.78)
        }
    },
    {
        id = 'vinewood_02',
        name = 'North Conker Pool',
        anchor = vec3(332.75, 425.30, 148.95),
        tasks = {
            vacuum = vec3(331.86, 426.58, 148.30),
            skim = vec3(335.17, 424.31, 148.30),
            sweep = vec3(338.55, 421.62, 148.92),
            backwash = vec3(327.66, 421.62, 148.92),
            chemicals = vec3(329.05, 423.45, 148.92),
            filter = vec3(326.82, 420.44, 148.92)
        }
    },
    {
        id = 'vespucci_01',
        name = 'Vespucci Rooftop Pool',
        anchor = vec3(-1192.37, -1574.70, 4.61),
        tasks = {
            vacuum = vec3(-1193.68, -1573.25, 4.10),
            skim = vec3(-1190.64, -1575.84, 4.10),
            sweep = vec3(-1187.45, -1579.08, 4.61),
            backwash = vec3(-1197.49, -1578.88, 4.61),
            chemicals = vec3(-1196.13, -1576.78, 4.61),
            filter = vec3(-1198.04, -1579.85, 4.61)
        }
    }
}
```
