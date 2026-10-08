# Configuration

Edit the indicated config file and restart the resource after changes. Values are the exact uploaded defaults, not proposed settings. SQL-backed ownership, tax rates, stock and placement may override or outlive config seed values. Comments below are retained as source context and can include legacy notes; the usage/setup pages explain important current behavior.

All Config assignments in the supplied file are included. Vet pharmacy excerpts omit real-world dose/label fields; use the medicine guide for FiveM effects. Do not apply RP values as real treatment instructions.

## Config.Locale

Selects language where supported; most products supply da/en. Smoking/Pause have no generic locale switch.

Source: `shared/config.lua`, line 3.

```lua
Config.Locale = 'da'
```

## Config.Debug

Diagnostic verbosity; keep disabled outside a reproduction.

Source: `shared/config.lua`, line 4.

```lua
Config.Debug = false
```

## Config.MoneyAccount

Controls money account. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 6.

```lua
Config.MoneyAccount = 'bank'
```

## Config.RequireDuty

Controls require duty. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 7.

```lua
Config.RequireDuty = false
```

## Config.DefaultPrice

Controls default price. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 8.

```lua
Config.DefaultPrice = 250000
```

## Config.DailyPlayerLimit

Controls daily player limit. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 9.

```lua
Config.DailyPlayerLimit = 3
```

## Config.DailyServerLimit

Controls daily server limit. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 10.

```lua
Config.DailyServerLimit = 15
```

## Config.CooldownSeconds

Controls cooldown seconds. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 11.

```lua
Config.CooldownSeconds = 180
```

## Config.CountdownSeconds

Controls countdown seconds. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 12.

```lua
Config.CountdownSeconds = 3
```

## Config.InstantStrike

Controls instant strike. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 13.

```lua
Config.InstantStrike = false
```

## Config.Camera

Orbital movement/FOV/lock/search distances.

Source: `shared/config.lua`, line 15.

```lua
Config.Camera = {
    startHeight = 650.0,
    minHeight = 180.0,
    maxHeight = 1200.0,
    moveSpeed = 145.0,
    fastMultiplier = 3.0,
    zoomMin = 15.0,
    zoomMax = 75.0,
    zoomStep = 5.0,
    defaultFov = 55.0,
    lockHoldMs = 700,
    maxTargetDistance = 4500.0,
    rayDistance = 5000.0,
}
```

## Config.Strike

Blast/player/vehicle/render radii; actual GTA explosion code uses tag 59.

Source: `shared/config.lua`, line 30.

```lua
Config.Strike = {
    explosionType = 59, -- EXP_TAG_ORBITAL_CANNON (kept for reference; impact code is hard-locked to 59)
    damageScale = 8.0,
    cameraShake = 1.5,
    radius = 35.0,
    lethalRadius = 32.0, -- players inside this radius are killed server-authoritatively
    vehicleDestroyRadius = 42.0,
    vehicleForce = 24.0,
    renderDistance = 2500.0,
    followTargetUntilImpact = true,
}
```

## Config.Audio

Controls audio. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 42.

```lua
Config.Audio = {
    enabled = true,
    audioBank = 'DLC_CHRISTMAS2017/XM_ION_CANNON',
    operatorSoundSet = 'dlc_xm_orbital_cannon_sounds',
    remoteSoundSet = 'dlc_xm_orbital_cannon_remote_sounds',
    impactSound = 'DLC_XM_Explosions_Orbital_Cannon',
    impactSoundSet = nil,
    useBackgroundLoop = true,
}
```

## Config.Controls

Native GTA input IDs for Orbital, not arbitrary keyboard strings.

Source: `shared/config.lua`, line 52.

```lua
Config.Controls = {
    exit = 177,        -- BACKSPACE
    fire = 22,         -- SPACE
    cycleVision = 0,   -- V
    lock = 44,         -- Q
    fast = 21,         -- SHIFT
    up = 32,           -- W
    down = 33,         -- S
    left = 34,         -- A
    right = 35,        -- D
    zoomIn = 241,
    zoomOut = 242,
}
```

## Config.Discord

Optional webhook settings; keep private, disabled by default.

Source: `shared/config.lua`, line 66.

```lua
Config.Discord = {
    enabled = false,
    webhook = '',
    username = 'Orbital Control',
}

-- ACE is checked with IsPlayerAceAllowed(source, ace).
-- Example: add_ace group.admin advanced_orbital.admin allow
```

## Config.AdminAce

Controls admin ace. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 74.

```lua
Config.AdminAce = 'advanced_orbital.admin'
```

## Config.Terminals

Orbital IDs, actual points, job grade/ACE/public access, prices and modes.

Source: `shared/config.lua`, line 76.

```lua
Config.Terminals = {
    {
        id = 'iaa_orbital',
        label = 'Orbital kontrolterminal',
        coords = vec3(-1044.70, -2749.83, 21.36),
        radius = 1.6,
        price = 250000,
        marker = true,
        access = {
            jobs = { police = 5 }, -- job = minimum grade
            aces = { 'advanced_orbital.use' },
            public = false,
        },
        modes = {
            surveillance = true,
            manual = true,
            automatic = true,
        }
    },
}

-- Areas where strikes are blocked. Surveillance remains available.
```

## Config.SafeZones

Orbital impact blocked zones; verify real server map points.

Source: `shared/config.lua`, line 98.

```lua
Config.SafeZones = {
    { label = 'Pillbox', coords = vec3(307.2, -595.3, 43.3), radius = 120.0 },
}

-- Optional blacklist for automatic vehicle lock.
```

## Config.BlacklistedVehicleModels

Controls blacklisted vehicle models. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 103.

```lua
Config.BlacklistedVehicleModels = {
    [`polmav`] = true,
}
```

## Config.Intel

Controls intel. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 107.

```lua
Config.Intel = {
    enabled = true,
    showJob = true,
    showCoords = true,
    showServerId = true,
}
```
