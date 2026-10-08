---
description: "Current configuration excerpts for Advanced Orbital."
---

# Advanced Orbital — Configuration

Select common providers in [mm_bridge](../../bridge/configuration.md). These excerpts come from the delivered **1.3.0** configuration. Edit gameplay settings in the resource, not the shared bridge. SQL records may override initial defaults.

## Config

Source file: `shared/config.lua`.

```lua
Config = {}
```

## Config.Locale

Source file: `shared/config.lua`.

```lua
Config.Locale = 'da'
```

## Config.Debug

Source file: `shared/config.lua`.

```lua
Config.Debug = false

-- Framework and target providers are selected in mm_bridge/config.lua.
-- Standalone: use ACE/public access and set EVERY terminal price to 0.
```

## Config.MoneyAccount

Source file: `shared/config.lua`.

```lua
Config.MoneyAccount = 'bank'
```

## Config.RequireDuty

Source file: `shared/config.lua`.

```lua
Config.RequireDuty = false
```

## Config.DefaultPrice

Source file: `shared/config.lua`.

```lua
Config.DefaultPrice = 250000
```

## Config.DailyPlayerLimit

Source file: `shared/config.lua`.

```lua
Config.DailyPlayerLimit = 3
```

## Config.DailyServerLimit

Source file: `shared/config.lua`.

```lua
Config.DailyServerLimit = 15
```

## Config.CooldownSeconds

Source file: `shared/config.lua`.

```lua
Config.CooldownSeconds = 180
```

## Config.CountdownSeconds

Source file: `shared/config.lua`.

```lua
Config.CountdownSeconds = 3
```

## Config.InstantStrike

Source file: `shared/config.lua`.

```lua
Config.InstantStrike = false
```

## Config.Camera

Source file: `shared/config.lua`.

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

Source file: `shared/config.lua`.

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

Source file: `shared/config.lua`.

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

Source file: `shared/config.lua`.

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

Source file: `shared/config.lua`.

```lua
Config.Discord = {
    enabled = false,
    webhook = '',
    username = 'Orbital Control',
}

-- ACE is checked server-side through MMBridge.HasAce.
-- Example: add_ace group.admin advanced_orbital.admin allow
```

## Config.AdminAce

Source file: `shared/config.lua`.

```lua
Config.AdminAce = 'advanced_orbital.admin'
```

## Config.Terminals

Source file: `shared/config.lua`.

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
            jobs = { police = 5 }, -- active job = minimum grade
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

Source file: `shared/config.lua`.

```lua
Config.SafeZones = {
    { label = 'Pillbox', coords = vec3(307.2, -595.3, 43.3), radius = 120.0 },
}

-- Optional blacklist for automatic vehicle lock.
```

## Config.BlacklistedVehicleModels

Source file: `shared/config.lua`.

```lua
Config.BlacklistedVehicleModels = {
    [joaat('polmav')] = true,
}
```

## Config.Intel

Source file: `shared/config.lua`.

```lua
Config.Intel = {
    enabled = true,
    showJob = true,
    showCoords = true,
    showServerId = true,
}
```
