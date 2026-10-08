# Configuration

Edit the indicated config file and restart the resource after changes. Values are the exact uploaded defaults, not proposed settings. SQL-backed ownership, tax rates, stock and placement may override or outlive config seed values. Comments below are retained as source context and can include legacy notes; the usage/setup pages explain important current behavior.

All Config assignments in the supplied file are included. Vet pharmacy excerpts omit real-world dose/label fields; use the medicine guide for FiveM effects. Do not apply RP values as real treatment instructions.

## Config.Framework

qbox money adapter or standalone without deduction for Cablecar.

Source: `config.lua`, line 3.

```lua
Config.Framework = 'qbox' -- 'qbox' or 'standalone'
```

## Config.Locale

Selects language where supported; most products supply da/en. Smoking/Pause have no generic locale switch.

Source: `config.lua`, line 4.

```lua
Config.Locale = 'da'      -- 'da' or 'en'
```

## Config.Target

Optional target provider; proximity/native alternatives vary by resource.

Source: `config.lua`, line 6.

```lua
Config.Target = {
    enabled = false, -- pure ox_lib by default; enable if you prefer ox_target
    resource = 'ox_target',
    fallbackTextUI = true,
}
```

## Config.Debug

Diagnostic verbosity; keep disabled outside a reproduction.

Source: `config.lua`, line 12.

```lua
Config.Debug = false
```

## Config.ShowStationBlips

Controls show station blips. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 13.

```lua
Config.ShowStationBlips = true


-- ox_lib is the primary UI layer. Scaleforms are not used by this resource.
```

## Config.OxLibUI

Controls ox lib u i. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 17.

```lua
Config.OxLibUI = {
    enabled = true,
    textUIPosition = 'right-center',
    notificationPosition = 'top-right',
    notificationDurationMs = 2500,
    ticketDialog = true,
    ticketDialogSize = 'sm',
    boardingNotifications = true,
    departureNotifications = true,
    arrivalNotifications = true,
}

-- Developer/test controls. The command is registered server-side through ox_lib
-- and restricted to the configured ACE principal (QBox admins use group.admin).
```

## Config.Developer

Controls developer. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 31.

```lua
Config.Developer = {
    enabled = true,
    command = 'cabledev',
    restricted = 'group.admin',
    allowWhenConfigDebug = false, -- keep fare/dev bypass restricted to the command ACE
    bypassTicket = true,         -- authorized testers may board without buying a ticket
    summonWaitSeconds = nil,     -- nil = use Config.StationWait before it departs normally
}
```

## Config.CabinBlips

Controls cabin blips. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 40.

```lua
Config.CabinBlips = {
    enabled = true,
    sprite = 36,
    display = 4,
    scale = 0.80,
    colour = 2,
    shortRange = false,
}

-- Movement tuning. Config.Speed is the maximum line speed. The server eases
-- away from and into stations, while remaining authoritative for all clients.
```

## Config.Speed

Controls speed. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 51.

```lua
Config.Speed = 17.5             -- maximum metres per second along the route
```

## Config.Movement

Controls movement. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 52.

```lua
Config.Movement = {
    accelerationDistance = 50.0, -- metres from either station used for easing
    minimumSpeedFactor = 0.10,   -- prevents asymptotic crawling at the platform
    endpointSnapDistance = 0.20, -- metres; snap cleanly onto the final route point
}
```

## Config.StationWait

Controls station wait. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 57.

```lua
Config.StationWait = 25.0       -- seconds at each end
```

## Config.DoorCloseLead

Controls door close lead. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 58.

```lua
Config.DoorCloseLead = 2.5      -- close doors this many seconds before departure
```

## Config.SyncInterval

Controls sync interval. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 59.

```lua
Config.SyncInterval = 500       -- server -> clients milliseconds
```

## Config.HardSyncThreshold

Controls hard sync threshold. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 60.

```lua
Config.HardSyncThreshold = 0.03 -- snap if progress differs by more than 3%
```

## Config.StreamDistance

Controls stream distance. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 61.

```lua
Config.StreamDistance = 2200.0
```

## Config.Fare

Ticket price/account/lifetime/consumption and free jobs.

Source: `config.lua`, line 63.

```lua
Config.Fare = {
    enabled = true,
    price = 250,
    moneyType = 'cash',
    ticketLifetimeMinutes = 20,
    consumeOnBoard = true,
    freeJobs = {
        -- police = true,
        -- ambulance = true,
    }
}
```

## Config.Models

Controls models. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 75.

```lua
Config.Models = {
    cabin = 'p_cablecar_s',
    doorLeft = 'p_cablecar_s_door_l',
    doorRight = 'p_cablecar_s_door_r',
}

-- Visible ticket machines at both stations.
-- prop_ticket_machine_01 is a base-game GTA V prop, so no streamed asset is required.
```

## Config.TicketMachine

Controls ticket machine. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 83.

```lua
Config.TicketMachine = {
    enabled = true,
    model = 'prop_park_ticket_01',
    freeze = true,
    invincible = true,
    collision = true,
    placeOnGround = true,
    targetDistance = 2.5,
}



-- GTA-style scripted departure cinematics. These are not Rockstar mission
-- cutscene assets; they are native scripted cameras that follow the moving
-- p_cablecar_s entity, so they stay aligned with our synchronized tram.
```

## Config.Cinematic

Controls cinematic. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 98.

```lua
Config.Cinematic = {
    enabled = true,
    autoPlayOnDeparture = true,
    allowSkip = true,
    skipCommand = 'cablecamskip',
    skipKey = 'BACK', -- Backspace
    startDelayMs = 350,
    returnBlendMs = 850,
    hideHud = true,
    letterbox = true,
    letterboxSize = 0.075,
    audioScene = true,
    audioSceneUp = 'CABLE_CAR_RIDE_UP_SCENE',
    audioSceneDown = 'CABLE_CAR_RIDE_DOWN_SCENE',
    lookAtOffset = { x = 0.0, y = 0.0, z = -3.65 },

    -- Camera positions are cabin-local offsets. Each shot smoothly travels
    -- from `from` to `to` while looking back at the cabin.
    up = {
        { duration = 2200, from = { x = 7.5,  y = -7.0, z = -1.7 }, to = { x = 5.5,  y = -10.0, z = -0.6 }, fovFrom = 47.0, fovTo = 42.0 },
        { duration = 2400, from = { x = -8.0, y = -2.0, z = -2.0 }, to = { x = -9.5, y = 4.5,   z = -1.0 }, fovFrom = 44.0, fovTo = 40.0 },
        { duration = 2200, from = { x = 0.0,  y = 8.5,  z = 1.5 },  to = { x = 0.0,  y = 11.5,  z = 3.2 },  fovFrom = 46.0, fovTo = 38.0 },
    },
    down = {
        { duration = 2200, from = { x = -7.5, y = 7.0,  z = -1.5 }, to = { x = -5.0, y = 10.5, z = 0.0 },  fovFrom = 47.0, fovTo = 42.0 },
        { duration = 2400, from = { x = 8.5,  y = 1.5,  z = -2.2 }, to = { x = 9.5,  y = -5.0, z = -1.0 }, fovFrom = 44.0, fovTo = 40.0 },
        { duration = 2200, from = { x = 0.0,  y = -8.5, z = 1.8 },  to = { x = 0.0,  y = -11.5, z = 3.4 },  fovFrom = 46.0, fovTo = 38.0 },
    },
}
```

## Config.Audio

Controls audio. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 128.

```lua
Config.Audio = {
    enabled = true,
    bank1 = 'CABLE_CAR',
    bank2 = 'CABLE_CAR_SOUNDS',
    soundSet = 'CABLE_CAR_SOUNDS',
    running = 'Running',
    arrive = 'Arrive_Station',
    depart = 'Leave_Station',
    doorOpen = 'DOOR_OPEN',
    doorClose = 'DOOR_CLOSE',
}
```

## Config.Doors

Controls doors. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 140.

```lua
Config.Doors = {
    closedOffset = 0.95,
    openDistance = 0.90,
    animationTime = 1.0,
}

-- GTA V contains native suspension/hook animations for p_cablecar_s.
-- These are switched as each cabin reaches the matching cable gradient.
```

## Config.GradientAnimations

Controls gradient animations. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 148.

```lua
Config.GradientAnimations = {
    enabled = true,
    dict = 'p_cablecar_s',
    blend = 8.0,
}

-- The base-game p_cablecar_s origin sits high above the passenger compartment.
-- The original Skyway Tram logic uses cablecar.position + vector3(0, 0, -5.3)
-- as the passenger/interior reference point. Keep all rider logic around that origin.
```

## Config.Rider

Controls rider. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 157.

```lua
Config.Rider = {
    interiorZ = -5.30,
    freeBoardOffset = { x = 0.0, y = 0.0, z = -5.30 },

    -- Original script ejects the player 3.5 metres along the cabin's right vector.
    exitSideDistance = 3.50,

    -- Safety volume around the real passenger compartment. This is only used
    -- to recover a rider if client interpolation/collision pushes them outside.
    cabinBounds = { x = 3.0, y = 3.0, zMin = -6.25, zMax = -3.80 },

    -- Free-standing rider carrier. The player's cabin-local position is captured
    -- before each cabin move and restored after it, preserving walking/animations.
    freeStand = {
        preserveTasks = true,
        preserveIK = true,
        safetyMargin = 0.65,
        rescueDelayMs = 450,
        minCarryDistance = 0.001,
    },
}
```

## Config.Stations

Controls stations. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 179.

```lua
Config.Stations = {
    bottom = {
        label = 'Pala Springs',
        ticket = { x = -750.10, y = 5594.80, z = 41.95, heading = 90.0 },
        exit = { x = -746.30, y = 5595.00, z = 41.95, heading = 270.0 },
        blip = { x = -745.0, y = 5595.0, z = 47.0 },
    },
    top = {
        label = 'Mount Chiliad',
        ticket = { x = 450.10, y = 5572.00, z = 781.45, heading = 270.0 },
        exit = { x = 442.80, y = 5572.00, z = 781.45, heading = 90.0 },
        blip = { x = 446.0, y = 5572.0, z = 786.0 },
    }
}

-- Route A runs bottom -> top.
```

## Config.Tracks

Controls tracks. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 195.

```lua
Config.Tracks = {
    {
        heading = 270.0,
        points = {
            { x = -740.911, y = 5599.341, z = 47.250 },
            { x = -739.557, y = 5599.346, z = 46.997 },
            { x = -581.009, y = 5596.517, z = 77.379 },
            { x = -575.717, y = 5596.388, z = 79.220 },
            { x = -273.805, y = 5590.844, z = 240.795 },
            { x = -268.707, y = 5590.744, z = 243.395 },
            { x = 6.896, y = 5585.668, z = 423.614 },
            { x = 11.774, y = 5585.591, z = 426.711 },
            { x = 236.820, y = 5581.445, z = 599.642 },
            { x = 241.365, y = 5581.369, z = 603.183 },
            { x = 412.855, y = 5578.216, z = 774.401 },
            { x = 417.541, y = 5578.124, z = 777.688 },
            { x = 444.930, y = 5577.589, z = 786.535 },
            { x = 446.288, y = 5577.590, z = 786.750 },
        }
    },
    -- Route B runs top -> bottom, mirroring route A.
    {
        heading = 90.0,
        points = {
            { x = 446.291, y = 5566.377, z = 786.750 },
            { x = 444.937, y = 5566.383, z = 786.551 },
            { x = 417.371, y = 5567.001, z = 777.708 },
            { x = 412.661, y = 5567.085, z = 774.439 },
            { x = 241.310, y = 5570.594, z = 603.137 },
            { x = 236.821, y = 5570.663, z = 599.561 },
            { x = 11.350, y = 5575.298, z = 426.629 },
            { x = 6.575, y = 5575.391, z = 423.570 },
            { x = -268.965, y = 5580.996, z = 243.386 },
            { x = -273.993, y = 5581.124, z = 240.808 },
            { x = -575.898, y = 5587.286, z = 79.251 },
            { x = -581.321, y = 5587.400, z = 77.348 },
            { x = -739.646, y = 5590.614, z = 47.006 },
            { x = -740.970, y = 5590.617, z = 47.306 },
        }
    }
}
```
