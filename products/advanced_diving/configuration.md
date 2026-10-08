# Configuration

Edit the indicated config file and restart the resource after changes. Values are the exact uploaded defaults, not proposed settings. SQL-backed ownership, tax rates, stock and placement may override or outlive config seed values. Comments below are retained as source context and can include legacy notes; the usage/setup pages explain important current behavior.

All Config assignments in the supplied file are included. Vet pharmacy excerpts omit real-world dose/label fields; use the medicine guide for FiveM effects. Do not apply RP values as real treatment instructions.

## Config.Locale

Selects language where supported; most products supply da/en. Smoking/Pause have no generic locale switch.

Source: `shared/config.lua`, line 3.

```lua
Config.Locale = 'da' -- da / en
```

## Config.Debug

Diagnostic verbosity; keep disabled outside a reproduction.

Source: `shared/config.lua`, line 4.

```lua
Config.Debug = false
```

## Config.MaxCrewSize

Controls max crew size. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 5.

```lua
Config.MaxCrewSize = 4
```

## Config.InviteDistance

Controls invite distance. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 6.

```lua
Config.InviteDistance = 35.0
```

## Config.CrewBonusPerExtraMember

Controls crew bonus per extra member. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 7.

```lua
Config.CrewBonusPerExtraMember = 0.05
```

## Config.MaxCrewBonus

Controls max crew bonus. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 8.

```lua
Config.MaxCrewBonus = 0.15
```

## Config.PaymentAccount

Controls payment account. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 9.

```lua
Config.PaymentAccount = 'bank'
```

## Config.RequireGearItem

Controls require gear item. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 10.

```lua
Config.RequireGearItem = false
```

## Config.GearItem

Controls gear item. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 11.

```lua
Config.GearItem = 'diving_gear'
```

## Config.SonarKey

Controls sonar key. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 12.

```lua
Config.SonarKey = 'G'
```

## Config.SonarCooldown

Controls sonar cooldown. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 13.

```lua
Config.SonarCooldown = 15000
```

## Config.ObjectInteractDistance

Controls object interact distance. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 14.

```lua
Config.ObjectInteractDistance = 2.8
```

## Config.ServerInteractDistance

Controls server interact distance. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 15.

```lua
Config.ServerInteractDistance = 20.0 -- generous server-side tolerance; client interaction remains limited to 2.8m
```

## Config.ObjectiveActionGraceMs

Controls objective action grace ms. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 16.

```lua
Config.ObjectiveActionGraceMs = 750 -- latency grace; server still validates action duration
```

## Config.ReturnDistance

Controls return distance. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 17.

```lua
Config.ReturnDistance = 16.0
```

## Config.BoatModel

Controls boat model. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 18.

```lua
Config.BoatModel = 'dinghy'
```

## Config.BoatPlatePrefix

Controls boat plate prefix. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 19.

```lua
Config.BoatPlatePrefix = 'DIVE'
```

## Config.LiftBagModel

Controls lift bag model. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 20.

```lua
Config.LiftBagModel = 'prop_beachball_02' -- replace with a custom lift-bag prop if desired
```

## Config.JobPed

Diving dock worker model/position.

Source: `shared/config.lua`, line 22.

```lua
Config.JobPed = {
    model = 's_m_m_dockwork_01',
    coords = vec4(-797.33, -1492.77, 1.60, 106.82),
    scenario = 'WORLD_HUMAN_CLIPBOARD'
}
```

## Config.BoatSpawn

Controls boat spawn. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 28.

```lua
Config.BoatSpawn = vec4(-812.73, -1502.66, 0.08, 109.0)
```

## Config.BoatReturn

Controls boat return. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 29.

```lua
Config.BoatReturn = vec3(-811.35, -1505.30, 0.0)
```

## Config.Levels

Diving total XP thresholds.

Source: `shared/config.lua`, line 31.

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

Diving contract unlock/pay/XP/objective model/type/coords.

Source: `shared/config.lua`, line 49.

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
```
