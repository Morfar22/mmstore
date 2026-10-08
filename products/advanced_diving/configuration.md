---
description: "Current configuration excerpts for Advanced Diving."
---

# Advanced Diving — Configuration

Select common providers in [mm_bridge](../../bridge/configuration.md). These excerpts come from the delivered **1.1.0** configuration. Edit gameplay settings in the resource, not the shared bridge. SQL records may override initial defaults.

## Config

Source file: `shared/config.lua`.

```lua
Config = {}
```

## Config.Locale

Source file: `shared/config.lua`.

```lua
Config.Locale = 'da' -- da / en
```

## Config.Debug

Source file: `shared/config.lua`.

```lua
Config.Debug = false
```

## Config.MaxCrewSize

Source file: `shared/config.lua`.

```lua
Config.MaxCrewSize = 4
```

## Config.InviteDistance

Source file: `shared/config.lua`.

```lua
Config.InviteDistance = 35.0
```

## Config.CrewBonusPerExtraMember

Source file: `shared/config.lua`.

```lua
Config.CrewBonusPerExtraMember = 0.05
```

## Config.MaxCrewBonus

Source file: `shared/config.lua`.

```lua
Config.MaxCrewBonus = 0.15
```

## Config.PaymentAccount

Source file: `shared/config.lua`.

```lua
Config.PaymentAccount = 'bank'
```

## Config.RequireGearItem

Source file: `shared/config.lua`.

```lua
Config.RequireGearItem = false
```

## Config.GearItem

Source file: `shared/config.lua`.

```lua
Config.GearItem = 'diving_gear'
```

## Config.SonarKey

Source file: `shared/config.lua`.

```lua
Config.SonarKey = 'G'
```

## Config.SonarCooldown

Source file: `shared/config.lua`.

```lua
Config.SonarCooldown = 15000
```

## Config.ObjectInteractDistance

Source file: `shared/config.lua`.

```lua
Config.ObjectInteractDistance = 2.8
```

## Config.ServerInteractDistance

Source file: `shared/config.lua`.

```lua
Config.ServerInteractDistance = 20.0 -- generous server-side tolerance; client interaction remains limited to 2.8m
```

## Config.ObjectiveActionGraceMs

Source file: `shared/config.lua`.

```lua
Config.ObjectiveActionGraceMs = 750 -- latency grace; server still validates action duration
```

## Config.ReturnDistance

Source file: `shared/config.lua`.

```lua
Config.ReturnDistance = 16.0
```

## Config.BoatModel

Source file: `shared/config.lua`.

```lua
Config.BoatModel = 'dinghy'
```

## Config.BoatPlatePrefix

Source file: `shared/config.lua`.

```lua
Config.BoatPlatePrefix = 'DIVE'
```

## Config.LiftBagModel

Source file: `shared/config.lua`.

```lua
Config.LiftBagModel = 'prop_beachball_02' -- replace with a custom lift-bag prop if desired
```

## Config.JobPed

Source file: `shared/config.lua`.

```lua
Config.JobPed = {
    model = 's_m_m_dockwork_01',
    coords = vec4(-797.33, -1492.77, 1.60, 106.82),
    scenario = 'WORLD_HUMAN_CLIPBOARD'
}
```

## Config.BoatSpawn

Source file: `shared/config.lua`.

```lua
Config.BoatSpawn = vec4(-812.73, -1502.66, 0.08, 109.0)
```

## Config.BoatReturn

Source file: `shared/config.lua`.

```lua
Config.BoatReturn = vec3(-811.35, -1505.30, 0.0)
```

## Config.Levels

Source file: `shared/config.lua`.

```lua
Config.Levels = {
    { level = 1, xp = 0 },
    { level = 2, xp = 250 },
    { level = 3, xp = 600 },
    { level = 4, xp = 1050 },
    { level = 5, xp = 1600 },
    { level = 6, xp = 2300 },
    { level = 7, xp = 3150 },
    { level = 8, xp = 4150 },
    { level = 9, xp = 5300 },
    { level = 10, xp = 6600 },
    { level = 11, xp = 8050 },
    { level = 12, xp = 9650 },
    { level = 13, xp = 11400 },
    { level = 14, xp = 13300 },
    { level = 15, xp = 15400 }
}
```

## Config.Contracts

Source file: `shared/config.lua`.

```lua
Config.Contracts = {
    [1] = {
        id = 1,
        title = { da = 'Havnerensning', en = 'Harbour Cleanup' },
        description = { da = 'Ryd affald og tabt gods tæt ved marinaen. Perfekt til nye dykkere.', en = 'Clear debris and lost cargo near the marina. Ideal for new divers.' },
        minLevel = 1,
        pay = 3200,
        xp = 180,
        center = vec3(-896.54, -1538.74, -8.0),
        radius = 65.0,
        objectives = {
            { coords = vec3(-877.51, -1548.35, -7.17), model = 'prop_box_wood02a_pu', type = 'pickup' },
            { coords = vec3(-860.88, -1544.17, -9.35), model = 'prop_barrel_02a', type = 'pickup' },
            { coords = vec3(-860.13, -1563.38, -8.30), model = 'prop_box_wood05a', type = 'pickup' },
            { coords = vec3(-880.73, -1569.67, -9.69), model = 'prop_barrel_01a', type = 'pickup' },
            { coords = vec3(-908.19, -1580.86, -7.02), model = 'prop_boxpile_06b', type = 'pickup' }
        }
    },
    [2] = {
        id = 2,
        title = { da = 'Tabt fragt', en = 'Lost Cargo' },
        description = { da = 'Fastgør løfteballoner på sunkne kasser og få dem op til båden.', en = 'Attach lift bags to sunken crates and recover them to the boat.' },
        minLevel = 3,
        pay = 5200,
        xp = 310,
        center = vec3(-2180.0, -564.0, -18.0),
        radius = 95.0,
        objectives = {
            { coords = vec3(-2157.5, -551.6, -17.8), model = 'prop_box_wood02a_pu', type = 'lift' },
            { coords = vec3(-2171.1, -578.4, -20.4), model = 'prop_box_wood02a_pu', type = 'lift' },
            { coords = vec3(-2190.3, -548.2, -19.2), model = 'prop_box_wood02a_pu', type = 'lift' },
            { coords = vec3(-2205.8, -571.5, -21.0), model = 'prop_box_wood02a_pu', type = 'lift' },
            { coords = vec3(-2178.6, -593.0, -18.7), model = 'prop_box_wood02a_pu', type = 'lift' },
            { coords = vec3(-2219.2, -545.5, -22.1), model = 'prop_box_wood02a_pu', type = 'lift' }
        }
    },
    [3] = {
        id = 3,
        title = { da = 'Vrag-ekspedition', en = 'Wreck Expedition' },
        description = { da = 'Skær værdifulde dele fri fra et gammelt vrag. Kræver mere erfaring.', en = 'Cut valuable parts loose from an old wreck. Requires more experience.' },
        minLevel = 7,
        pay = 7600,
        xp = 470,
        center = vec3(-3150.0, 1115.0, -26.0),
        radius = 115.0,
        objectives = {
            { coords = vec3(-3128.0, 1096.5, -25.0), model = 'prop_rub_carwreck_2', type = 'cut' },
            { coords = vec3(-3142.6, 1130.2, -27.4), model = 'prop_rub_carwreck_3', type = 'cut' },
            { coords = vec3(-3168.4, 1117.8, -29.0), model = 'prop_rub_carwreck_5', type = 'cut' },
            { coords = vec3(-3176.1, 1088.6, -26.3), model = 'prop_box_wood02a_pu', type = 'lift' },
            { coords = vec3(-3136.3, 1151.7, -23.7), model = 'prop_box_wood02a_pu', type = 'lift' },
            { coords = vec3(-3190.5, 1137.4, -30.5), model = 'prop_box_wood05a', type = 'recover' }
        }
    },
    [4] = {
        id = 4,
        title = { da = 'Dybvandsbjærgning', en = 'Deep Water Salvage' },
        description = { da = 'Et stort holdjob langt fra land med tungt gods og tekniske bjærgninger.', en = 'A large offshore crew contract with heavy cargo and technical salvage.' },
        minLevel = 12,
        pay = 11500,
        xp = 700,
        center = vec3(-1940.0, -3390.0, -34.0),
        radius = 140.0,
        objectives = {
            { coords = vec3(-1908.0, -3375.0, -31.0), model = 'prop_box_wood02a_pu', type = 'lift' },
            { coords = vec3(-1926.5, -3410.0, -36.0), model = 'prop_box_wood02a_pu', type = 'lift' },
            { coords = vec3(-1960.0, -3368.5, -38.0), model = 'prop_box_wood02a_pu', type = 'lift' },
            { coords = vec3(-1980.0, -3402.5, -35.0), model = 'prop_box_wood02a_pu', type = 'lift' },
            { coords = vec3(-1914.2, -3432.7, -33.5), model = 'prop_rub_carwreck_2', type = 'cut' },
            { coords = vec3(-1951.8, -3438.0, -40.0), model = 'prop_rub_carwreck_3', type = 'cut' },
            { coords = vec3(-1994.0, -3374.0, -37.2), model = 'prop_box_wood05a', type = 'recover' },
            { coords = vec3(-1889.0, -3404.0, -32.0), model = 'prop_box_wood05a', type = 'recover' }
        }
    }
}

function DivingGetLevelFromXP(xp)
    xp = tonumber(xp) or 0
    local level = 1
    for i = 1, #Config.Levels do
        if xp >= Config.Levels[i].xp then level = Config.Levels[i].level end
    end
    return level
end

function DivingNextLevelXP(xp)
    local current = DivingGetLevelFromXP(xp)
    for i = 1, #Config.Levels do
        if Config.Levels[i].level == current + 1 then
            return Config.Levels[i].xp
        end
    end
    return Config.Levels[#Config.Levels].xp
end
```
