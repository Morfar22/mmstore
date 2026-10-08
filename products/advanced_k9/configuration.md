---
description: "Current configuration excerpts for Advanced K9."
---

# Advanced K9 — Configuration

Select common providers in [mm_bridge](../../bridge/configuration.md). These excerpts come from the delivered **95.1.0** configuration. Edit gameplay settings in the resource, not the shared bridge. SQL records may override initial defaults.

## Config

Source file: `config.lua`.

```lua
Config = {}

-- Resource language: 'da' or 'en'
```

## Config.Locale

Source file: `config.lua`.

```lua
Config.Locale = 'da'
```

## Config.LocaleFallback

Source file: `config.lua`.

```lua
Config.LocaleFallback = 'en'
```

## Config.Debug

Source file: `config.lua`.

```lua
Config.Debug = false

-- DeveloperMode gates test/diagnostic commands and verbose tooling.
-- Keep this false on production servers.
```

## Config.DeveloperMode

Source file: `config.lua`.

```lua
Config.DeveloperMode = false

-- TestMode opens framework/job handler permissions for testing.
-- V32 admin role approval is separate and is NOT bypassed by TestMode.
-- A handler must be handler-approved and the second player must be K9-approved.
```

## Config.TestMode

Source file: `config.lua`.

```lua
Config.TestMode = false
```

## Config.DefaultDogModel

Source file: `config.lua`.

```lua
Config.DefaultDogModel = joaat('a_c_shepherd')
```

## Config.AuthorityJobs

Source file: `config.lua`.

```lua
Config.AuthorityJobs = {
    police = true,
    sheriff = true,
    statepolice = true,
}


-- UI skin access is deliberately separate from TestMode / K9 permissions.
-- Only jobs listed here receive the blue emergency/police tablet skin.
-- Everyone else receives the civilian K9 Companion UI.
```

## Config.UISkins

Source file: `config.lua`.

```lua
Config.UISkins = {
    -- Emergency jobs keep the ORIGINAL blue rugged/police tablet.
    useLegacyEmergencySkin = true,

    -- Everyone not listed under emergencyJobs gets the NEW civilian K9 Companion UI.
    useNewCivilianSkin = true,

    emergencyJobs = {
        police = {
            brand = 'POLITI',
            tagline = 'TRYGHED · FÆLLESSKAB · FOR ALLE',
        },
        sheriff = {
            brand = 'POLITI',
            tagline = 'K9 BEREDSKAB',
        },
        statepolice = {
            brand = 'POLITI',
            tagline = 'K9 BEREDSKAB',
        },

        -- Common emergency-service job names. Change/add these to match your server.
        ambulance = {
            brand = 'BEREDSKAB',
            tagline = 'AKUT K9 ENHED',
        },
        ems = {
            brand = 'BEREDSKAB',
            tagline = 'AKUT K9 ENHED',
        },
        fire = {
            brand = 'BRAND & REDNING',
            tagline = 'K9 BEREDSKAB',
        },
        firefighter = {
            brand = 'BRAND & REDNING',
            tagline = 'K9 BEREDSKAB',
        },
    },

    civilian = {
        brand = 'K9 COMPANION',
        tagline = 'CIVIL HUNDETRÆNING',
    },
}
```

## Config.Commands

Source file: `config.lua`.

```lua
Config.Commands = {
    menu = 'k9',
    status = 'k9role',
}
```

## Config.Database

Source file: `config.lua`.

```lua
Config.Database = {
    enabled = true,
    autoCreateTables = true,
    debug = false,
}
```

## Config.PhoneIntegration

Source file: `config.lua`.

```lua
Config.PhoneIntegration = {
    -- Legacy order/provider fields are retained for configuration compatibility.
    -- Select the active phone in mm_bridge; no local auto probing is performed.
    provider = 'bridge',

    order = {
        'sky_phone',
        'lb-phone',
        'gksphone',
        'yseries',
        'npwd',
        'high-phone',
        'qs-smartphone-pro',
        'v-phone',
        'lsfive-phone',
        'framework',
    },

    -- Keep the last successfully resolved number on the adoption so the
    -- collar still works when the owner is offline.
    cacheLastKnownNumber = true,

    -- V94.3: never scan every database table containing the word "phone".
    -- Sky SQL fallback may inspect only these prefixes plus an optional exact
    -- allow-list. Exports/inventory/framework metadata are still tried first.
    skySqlFallback = true,
    skySchemaTablePrefixes = {
        'sky_phone',
        'skyphone',
    },
    skySchemaTableAllowlist = {
        -- Add exact Sky Phone table names here only if your build uses generic
        -- names that do not start with sky_phone / skyphone.
        -- Example: 'phone_devices'
    },
    skySchemaMaxTables = 48,

    debug = false,
}
```

## Config.Adoption

Source file: `config.lua`.

```lua
Config.Adoption = {
    enabled = true,
    inviteTimeout = 30000,
    autoPairInterval = 5000,

    collarDistance = 2.2,
    targetSystem = 'bridge', -- bridge / none; select target centrally
    targetIcon = 'fa-solid fa-dog',
    targetLabel = 'Tjek K9-halsbånd',

    -- Used until owner/dog chooses another name with the adoption menu.
    defaultDogPrefix = 'K9 ',
}
```

## Config.Pairing

Source file: `config.lua`.

```lua
Config.Pairing = {
    -- Only initial invite/pairing is proximity based.
    maxInviteDistance = 8.0,

    -- Handler commands are intentionally distance-free once paired.
    commandsRequireDistance = false,

    -- Do not silently unpair a normal two-player K9 team just because
    -- handler and dog are far apart. Disconnect/manual unpair still works.
    breakOnDistance = false,
    breakDistance = 150.0,
    inviteTimeout = 30000,
    breakChecks = 3,
    breakCheckInterval = 5000,
}
```

## Config.Scent

Source file: `config.lua`.

```lua
Config.Scent = {
    enabled = true,
    submitInterval = 1000,
    sampleDistance = 2.5,
    lifetime = 180000,
    maxPointsPerPlayer = 220,
    pointTolerance = 3.5,
    refreshInterval = 2500,
    showMarkers = true,
    markerScale = 0.12,
    markerColor = { r = 255, g = 20, b = 147, a = 200 },

    searchRadius = 8.0,
    revealAhead = 3,
    maxGap = 18.0,
    localSearchRadius = 12.0,
    vehicleBreaksTrail = true,
    waterBreaksTrail = true,

    -- V90: trail quality is now based on both age and local contamination.
    -- This never moves the dog or chooses the route for the player.
    quality = {
        strongScore = 0.72,
        normalScore = 0.40,
        contaminationRadius = 4.0,
        contaminationPenalty = 0.12,
        maxContaminationPenalty = 0.48,
        distancePenaltyPerMeter = 0.035,
    },

    -- A target currently in water cannot be acquired as a scent target.
    -- Entering water ends the current scent segment. New scent begins only
    -- after the player is back on land.
    blockTargetsInWater = true,

    -- V26: K9 may track every other player's scent, including its own handler.
    allowHandlerTrail = true,
    handlerSearchRadius = 10.0,

    strengths = {
        strong = 30000,
        normal = 90000,
        weak = 180000
    }
}
```

## Config.ScentArticles

Source file: `config.lua`.

```lua
Config.ScentArticles = {
    enabled = true,
    sampleDistance = 2.5,
    lifetime = 300000,
    trailAcquireRadius = 12.0,

    -- A scent article is a gameplay/RP sample linked to a nearby player.
    -- It is not an inventory exploit and does not remove any item from target.
    propModel = joaat('prop_cs_paper_cup'),
}
```

## Config.ManualAlerts

Source file: `config.lua`.

```lua
Config.ManualAlerts = {
    enabled = true,
    pendingDuration = 30000,

    -- Positive detection results stay private to the K9 player until the K9
    -- deliberately performs an alert. No automatic bark reveals the result.
    handlerSeesPositiveOnlyAfterAlert = true,

    styles = {
        sit = {
            label = 'Sit-markering',
            dictionary = 'creatures@rottweiler@amb@world_dog_sitting@base',
            animation = 'base',
            flag = 1,
            duration = 2200,
        },
        bark = {
            label = 'Bark-markering',
            dictionary = 'creatures@rottweiler@amb@world_dog_barking@idle_a',
            animation = 'idle_a',
            flag = 1,
            duration = 2200,
            sound = 'Bark4',
        },
        down = {
            label = 'Down-markering',
            dictionary = 'creatures@rottweiler@amb@sleep_in_kennel@',
            animation = 'sleep_in_kennel',
            flag = 1,
            duration = 2500,
        },
        stare = {
            label = 'Stille markering',
            duration = 1800,
        },
    },
}
```

## Config.Sniff

Source file: `config.lua`.

```lua
Config.Sniff = {
    radius = 5.0,
    serverTolerance = 6.0,
    cooldown = 5000,
    duration = 1500,
    illegalItems = {
        weed = 'Cannabis',
        coke = 'Cocaine',
        cocaine = 'Cocaine',
        meth = 'Methamphetamine',
        heroin = 'Heroin',
        lockpick = 'Lockpick',
        weapon_pistol = 'Pistol',
    }
}
```

## Config.Tackle

Source file: `config.lua`.

```lua
Config.Tackle = {
    -- J is an instant running tackle. K9 must be moving toward the target.
    dogHitDistance = 3.0,
    serverTolerance = 3.8,
    cooldown = 7000,
    ragdollTime = 2500,
    minRunSpeed = 1.25,
    facingDot = 0.45,
    lungeForce = 1.15,
}
```

## Config.Vehicle

Source file: `config.lua`.

```lua
Config.Vehicle = {
    enterDistance = 8.0,
    handlerVehicleDistance = 12.0,
    doorTolerance = 3.0,

    -- V90: configured vehicles can use a physical K9 cage/cargo anchor.
    -- Unconfigured vehicles keep the existing seat-based flow.
    cage = {
        enabled = true,
        preferAnchor = true,
        maxAttachDistance = 14.0,

        -- Per-model local offsets. Add/tune your server's actual K9 vehicles.
        -- /k9cagetune toggles live tuning while attached.
        -- /k9cageprint prints the current model override to F8.
        models = {
            -- ['police3'] = {
            --     offset = { x = 0.0, y = -1.15, z = 0.25 },
            --     rotation = { x = 0.0, y = 0.0, z = 0.0 },
            --     exitOffset = { x = -1.0, y = -1.8, z = 0.0 },
            --     postureKey = 'sleep', -- 'sit' or 'sleep'
            -- },
        },

        tuning = {
            moveStep = 0.01,
            rotateStep = 2.0,
        },
    },

    camera = {
        enabled = true,

        -- Saved per vehicle model in the database. No config coordinates are
        -- required for normal use.
        autoUseSaved = true,
        freeLook = true,
        toggleKey = 'V',

        defaultFov = 62.0,
        minFov = 35.0,
        maxFov = 90.0,

        mouseSensitivity = 3.4,
        maxPitch = 78.0,

        editorMoveSpeed = 0.06,
        editorFastMultiplier = 3.0,
        editorFineMultiplier = 0.25,
        editorMaxDistance = 8.0,

        -- V94.6.2: if no saved camera exists, never leave the dog on GTA's
        -- normal follow-ped camera inside the vehicle geometry.
        safeFallback = true,
        fallbackBack = 3.4,
        fallbackUp = 1.35,
        fallbackFov = 64.0,
        nearClip = 0.18,
    },

    -- Normal passenger-seat animation and fallback.
    carSitAnimation = {
        dictionary = 'creatures@rottweiler@incar@',
        animation = 'sit',
        flag = 1 -- loop
    },

    -- V93: the player-controlled dog chooses its posture while attached to a
    -- configured K9 cage. Sleep uses the exact bdogsleep animation supplied.
    cagePostures = {
        default = 'sit',

        sit = {
            label = 'Sit',
            dictionary = 'creatures@rottweiler@incar@',
            animation = 'sit',
            flag = 1,
        },

        sleep = {
            label = 'Sleep (big dog)',
            dictionary = 'creatures@rottweiler@amb@sleep_in_kennel@',
            animation = 'sleep_in_kennel',
            flag = 1,
        },
    },

    rearLeftDoorIndex = 2, -- rear-left door, matching seat 1 behind driver
    autoCloseDoorDelay = 3000,
    handlerDeathResponse = true,
    handlerTrackDuration = 20000
}
```

## Config.Swimming

Source file: `config.lua`.

```lua
Config.Swimming = {
    enabled = true,
    surfaceOffset = 0.32,

    -- K9 swimming is deliberately a little slower than before.
    -- 1.00 = old speed, 0.78 = roughly 22% less propulsion.
    speedMultiplier = 0.78,

    walkForce = 0.85,
    sprintForce = 1.35,
}
```

## Config.K9Armour

Source file: `config.lua`.

```lua
Config.K9Armour = {
    enabled = true,

    -- Armour automatically applied to the player-controlled K9 whenever
    -- a K9 team is created/recreated.
    amount = 100,
}
```

## Config.FallProtection

Source file: `config.lua`.

```lua
Config.FallProtection = {
    enabled = true,

    -- Collision proof is only active while the player-controlled K9 is airborne
    -- and for a very short landing window.
    landingGrace = 450,
    minAirTime = 120,

    -- Extra fallback: if GTA still subtracts health on landing, restore the
    -- pre-fall health only when no weapon damage was registered during the fall.
    restoreLandingHealth = true,
}
```

## Config.Parkour

Source file: `config.lua`.

```lua
Config.Parkour = {
    enabled = true,
    keybind = 'SPACE',

    cooldown = 950,

    -- Normal free jump.
    jumpHorizontalVelocity = 4.8,
    jumpVerticalVelocity = 6.2,

    -- V40 phased vault:
    -- phase 1 gets the dog above the obstacle before forward clearance starts.
    vaultLiftVelocity = 7.8,
    vaultLiftDuration = 220,

    -- phase 2 clears the wall after enough vertical height has been gained.
    vaultForwardVelocity = 8.6,
    vaultMinForwardVertical = 3.0,
    forwardPulseDelay = 90,
    forwardPulseCount = 3,

    -- Existing run speed adds a little more forward travel.
    speedBoostMultiplier = 0.30,
    maxSpeedBoost = 2.0,

    obstacleDistance = 1.75,
    obstacleRadius = 0.32,

    lowProbeHeight = 0.18,
    probeStep = 0.18,
    maxVaultHeight = 1.72,

    -- We want the body clearly above the measured collision before committing
    -- to the big horizontal push.
    clearanceExtra = 0.30,

    landingProbeDistance = 2.35,
    landingProbeHeight = 1.10,

    disableRagdollDuringVault = true,
    vaultSafetyDuration = 900,

    showTooHighMessage = true,
}
```

## Config.Training

Source file: `config.lua`.

```lua
Config.Training = {
    enabled = true,
    interactionDistance = 3.0,

    petDuration = 4500,
    petHandlerAnimation = {
        dictionary = 'creatures@rottweiler@tricks@',
        animation = 'petting_franklin',
        flag = 1
    },
    petDogAnimation = {
        dictionary = 'creatures@rottweiler@amb@world_dog_sitting@base',
        animation = 'base',
        flag = 1
    },

    stayDuration = 6000,
    stayMoveTolerance = 0.75,

    recallTimeout = 15000,
    recallDistance = 2.2,

    fetchModel = joaat('prop_tennis_ball'),
    fetchPickupDistance = 1.35,
    fetchReturnDistance = 2.5,
    fetchTimeout = 60000,

    -- V86: configurable tennis-ball attachment.
    -- Dog mouth values can be tuned live with /k9balltune while the dog
    -- is actually carrying the fetch ball. /k9ballprint prints a ready
    -- config snippet for the current dog model to F8.
    fetchAttachment = {
        handlerHand = {
            bone = 57005,
            offset = { x = 0.10, y = 0.02, z = -0.02 },
            rotation = { x = -90.0, y = 0.0, z = 0.0 },
        },

        dogMouth = {
            bone = 31086,
            offset = { x = 0.02, y = 0.22, z = -0.02 },
            rotation = { x = 0.0, y = 0.0, z = 0.0 },

            -- Optional per-model overrides. Values only need to be added
            -- when a breed needs a different mouth alignment.
            models = {
                -- ['a_c_shepherd'] = {
                --     bone = 31086,
                --     offset = { x = 0.02, y = 0.22, z = -0.02 },
                --     rotation = { x = 0.0, y = 0.0, z = 0.0 },
                -- },
            },
        },

        tuning = {
            enabled = true,
            moveStep = 0.005,
            rotateStep = 2.0,
        },
    },

    -- V36: Handler controls fetch throw strength by holding E.
    fetchThrow = {
        chargeTime = 1800,
        minForce = 7.0,
        maxForce = 20.0,
        minUpForce = 2.4,
        maxUpForce = 5.2,
    },

    rewards = {
        pet = { xp = 1, bond = 2 },
        treat = { xp = 2, bond = 4 },
        stay = { xp = 5, bond = 2 },
        recall = { xp = 5, bond = 2 },
        fetch = { xp = 8, bond = 4 },
        sniff = { xp = 3, bond = 1 },
        track = { xp = 6, bond = 2 },
        tackle = { xp = 4, bond = 1 },
    },

    recallOutline = {
        enabled = true,
        duration = 15000,
        stopDistance = 2.2,

        -- FiveM entity outline is attempted first, but it is not reliable
        -- enough to be the only visual cue on every client/build.
        outlineEnabled = true,
        color = { r = 70, g = 180, b = 255, a = 220 },
        shader = 0,

        -- Reliable dog-client-only fallback shown above the handler/trainer.
        markerEnabled = true,
        markerType = 2,
        markerHeight = 1.25,
        markerScale = 0.26,
        markerBob = true,
        markerFaceCamera = true,

        -- Optional short label under the marker.
        labelEnabled = true,
        label = 'HANDLER',
    }
}


-- V12 keybinds. FiveM key mappings can be rebound by players in Settings > Key Bindings > FiveM.
```

## Config.Keybinds

Source file: `config.lua`.

```lua
Config.Keybinds = {
    menu = 'F7',

    -- Shared contextual gameplay mappings. Each physical key is registered
    -- only once; the active role decides whether it is a handler order or
    -- a direct K9 action. This keeps FiveM's key-binding list clean.
    shared = {
        searchScent = 'G',
        trackHandler = 'Y',
        buriedSearch = 'B',
        sniff = 'H',
        tackle = 'J',
        vehicleToggle = 'I',
        stopTrack = 'BACK',
    },

    handler = {
        heel = 'K',
        stay = 'L',
        recall = 'U',
        -- I is now the normal enter/exit toggle. Legacy forced exit is
        -- intentionally unbound by default but remains rebindable.
        vehicleExit = '',
    },
    dog = {
        -- I is now the normal enter/exit toggle. Legacy forced exit is
        -- intentionally unbound by default but remains rebindable.
        vehicleExit = '',
    }
}
```

## Config.Stamina

Source file: `config.lua`.

```lua
Config.Stamina = {
    -- Any player using an animal/dog ped always has infinite stamina, paired or free.
    -- This is intentionally not configurable per Civil/Service mode and
    -- does not require an active handler or partner.
    alwaysInfiniteForDogPlayers = true
}
```

## Config.Attack

Source file: `config.lua`.

```lua
Config.Attack = {
    enabled = true,
    useLeftClick = true,
    range = 2.25,
    facingDot = 0.15,
    cooldown = 900,
    playerDamage = 18,
    npcDamage = 28,
    ragdollChance = 35,
    ragdollTime = 900,
    lungeForce = 0.85
}
```

## Config.Notifications

Source file: `config.lua`.

```lua
Config.Notifications = {
    defaultDuration = 6000,
    commandDuration = 9000,
    urgentDuration = 12000,

    userDefaults = {
        position = 'top-right',
        commandDuration = 9000,
        soundEnabled = true,
        commandSound = true,
        successSound = true,
        urgentSound = true
    },

    sound = {
        enabled = true,
        commandName = 'SELECT',
        commandSet = 'HUD_FRONTEND_DEFAULT_SOUNDSET',
        urgentName = 'ERROR',
        urgentSet = 'HUD_FRONTEND_DEFAULT_SOUNDSET',
        successName = 'CHECKPOINT_PERFECT',
        successSet = 'HUD_MINI_GAME_SOUNDSET'
    }
}
```

## Config.BuriedTraining

Source file: `config.lua`.

```lua
Config.BuriedTraining = {
    enabled = true,

    -- Any player may prepare a training hide during testing.
    allowAnyoneToBury = false,

    recordInterval = 1000,
    sampleDistance = 2.0,
    maxRecordedPoints = 80,
    lifetime = 600000,          -- 10 minutes
    acquireRadius = 7.0,
    pointTolerance = 3.5,
    revealAhead = 3,
    maxGap = 20.0,

    buryDuration = 5000,
    findRadius = 2.2,
    finalRevealRadius = 5.0,
    finalMarkerScale = 1.50,

    markerScale = 0.12,
    markerColor = { r = 255, g = 20, b = 147, a = 200 },

    -- Hidden training article. It is placed slightly below the actual
    -- terrain, not at the player's ped Z.
    objectModel = joaat('prop_tennis_ball'),
    buriedDepth = 0.18,

    groundPlacement = {
        probeHeight = 3.0,
        revealOffset = 0.025,

        -- Visual shown while /k9bury is running. The ball is moved
        -- straight down to the ground with physics disabled.
        buryVisual = true,
        startHeight = 0.65,
        forwardOffset = 0.45,
        updateMs = 20,
    },

    keybind = 'B'
}
```

## Config.K9Sounds

Source file: `config.lua`.

```lua
Config.K9Sounds = {
    -- Custom sound names. With InteractSound, place matching .ogg files in
    -- InteractSound's sounds folder using these names.
    Whine1 = 'germanshepherd_whine',
    Whine2 = 'germanshepherd_whine_2',
    Bark4 = 'germanshepherd_4bark',

    backend = 'auto', -- auto / interact-sound / none
    distance = 18.0,
    volume = 0.55
}


-- While the player is the K9 ped, human emotes/utilities are locked.
-- This is independent from handler command-emotes.
```

## Config.DogEmoteLock

Source file: `config.lua`.

```lua
Config.DogEmoteLock = {
    enabled = true,

    -- Prevent GTA ambient / gesture animation layers on the dog ped.
    disableGestureAnims = true,
    disableAmbientAnims = true,

    -- Common controls used by emote menus / point / hands-up utilities.
    -- Add your server's custom emote-menu key here if it differs.
    blockedControls = {
        -- B/control 29 is intentionally NOT blocked because Advanced K9
        -- uses B for buried-scent gameplay while the player is the dog.
        73,  -- X: commonly used for hands-up / cancel
        170, -- F3
        166, -- F5
        167, -- F6
        168, -- F7
        244, -- M
        303, -- U
    },

    -- Human-only animations that should be forcibly stopped if another
    -- resource manages to start them on the K9 ped.
    blockedAnimations = {
        { dictionary = 'anim@mp_point', animation = 'task_mp_pointing' },
        { dictionary = 'random@mugging3', animation = 'handsup_standing_base' },
        { dictionary = 'missminuteman_1ig_2', animation = 'handsup_base' },
        { dictionary = 'mp_am_hold_up', animation = 'handsup_base' },
    },

    -- Human scenario emotes are not valid for the K9 ped.
    stopHumanScenarios = true,

    -- Expose a state bag so external resources such as emote menus can
    -- also check the K9 lock without depending on this resource internally.
    stateBagKey = 'advancedK9EmotesLocked',

    debug = false,
}



-- External trainer API used by Advanced Vet DLC.
-- This never grants the trainer police job permissions. It only gives a
-- temporary training-control channel to an already active Service K9 player.


-- The dog is a human-controlled player. Handler/vet commands are instructions,
-- never remote-control actions on the dog client.
```

## Config.DogAgency

Source file: `config.lua`.

```lua
Config.DogAgency = {
    enabled = true,
    handlerCommandsAreAdvisory = true,
    formalTrainingRequiresDogAcceptance = true,
    trainingRequestTimeout = 20000,
}
```

## Config.ExternalTraining

Source file: `config.lua`.

```lua
Config.ExternalTraining = {
    enabled = true,
    serviceDogsOnly = true,
    maxDistance = 12.0,

    allowedCommands = {
        search_scent = true,
        track_trainer = false,
        search_buried = true,
        sniff = true,
        heel = true,
        stay = true,
        recall = true,
        training_stay = true,
        training_recall = true,
        fetch = true,
        stop_track = true,
    },
}
```

## Config.CommandEmotes

Source file: `config.lua`.

```lua
Config.CommandEmotes = {
    enabled = true,

    -- Only the handler plays command gesture/emotes.
    -- The K9 player never receives command-emotes.
    dogEnabled = false,

    -- Every handler order uses the same emote whether it is triggered from
    -- the /k9 UI or a keybind, because both routes go through K9SendCommand.
    handler = {
        search_scent = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_point',
            duration = 1500,
            flag = 48,
        },
        track_handler = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_me_hard',
            duration = 1500,
            flag = 48,
        },
        search_buried = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_point',
            duration = 1500,
            flag = 48,
        },
        sniff = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_point',
            duration = 1400,
            flag = 48,
        },
        tackle_order = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_bring_it_on',
            duration = 1500,
            flag = 48,
        },
        -- PÅ PLADS
        heel = {
            label = 'Whistle',
            animation = 'hail_taxi',
            dictionary = 'taxi_hail',
            options = {
                duration = 1300,
                flags = {
                    move = true
                }
            }
        },
        stay = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_easy_now',
            duration = 1600,
            flag = 48,
        },
        recall = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_come_here_soft',
            duration = 1700,
            flag = 48,
        },
        vehicle_enter = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_point',
            duration = 1400,
            flag = 48,
        },
        vehicle_exit = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_come_here_soft',
            duration = 1500,
            flag = 48,
        },
        stop_track = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_easy_now',
            duration = 1500,
            flag = 48,
        },

        -- Training commands from the UI use matching handler gestures too.
        civil_sit = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_point',
            duration = 1400,
            flag = 48,
        },
        civil_down = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_point',
            duration = 1400,
            flag = 48,
        },
        civil_focus = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_me_hard',
            duration = 1500,
            flag = 48,
        },
        civil_place = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_point',
            duration = 1500,
            flag = 48,
        },
        civil_heel = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_come_here_soft',
            duration = 1600,
            flag = 48,
        },
        civil_settle = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_easy_now',
            duration = 1600,
            flag = 48,
        },
        civil_impulse = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_easy_now',
            duration = 1600,
            flag = 48,
        },
        training_stay = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_easy_now',
            duration = 1600,
            flag = 48,
        },
        training_recall = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_come_here_soft',
            duration = 1700,
            flag = 48,
        },
        fetch = {
            dictionary = 'gestures@m@standing@casual',
            animation = 'gesture_point',
            duration = 1300,
            flag = 48,
        },
    },
}
```

## Config.K9QuickActions

Source file: `config.lua`.

```lua
Config.K9QuickActions = {
    commands = {
        Sit = 'k9sit',
        Down = 'k9down',
        Jump = 'k9jump',
        Bark = 'k9bark',
        Bark4 = 'k9bark4',
        Whine1 = 'k9whine1',
        Whine2 = 'k9whine2',
    },

    keybinds = {
        -- Defaults deliberately avoid existing G/H/J/K/L/U/I/O bindings.
        Sit = 'NUMPAD1',
        Down = 'NUMPAD2',
        Bark = 'NUMPAD3',
        Bark4 = 'NUMPAD4',
        Whine1 = 'NUMPAD5',
        Whine2 = 'NUMPAD6',
        Jump = 'SPACE',
    },

    sit = {
        dictionary = 'creatures@rottweiler@amb@world_dog_sitting@base',
        animation = 'base',
        flag = 1
    },

    down = {
        dictionary = 'creatures@rottweiler@amb@sleep_in_kennel@',
        animation = 'sleep_in_kennel',
        flag = 1
    },

    bark = {
        dictionary = 'creatures@rottweiler@amb@world_dog_barking@idle_a',
        animation = 'idle_a',
        flag = 1,
        duration = 1800
    },

    bark4Duration = 3600,

    whine = {
        dictionary = 'creatures@rottweiler@amb@world_dog_sitting@idle_a',
        animation = 'idle_a',
        flag = 1,
        duration = 1700
    }
}
```

## Config.FoundBark

Source file: `config.lua`.

```lua
Config.FoundBark = {
    enabled = true,
    duration = 2800,

    -- User-provided big dog bark emote.
    dictionary = 'creatures@rottweiler@amb@world_dog_barking@idle_a',
    animation = 'idle_a',
    flag = 1,

    barkOnScentAcquired = false,
    barkOnPositiveSniff = false,
    barkOnBuriedFind = false
}
```

## Config.CivilK9

Source file: `config.lua`.

```lua
Config.CivilK9 = {
    enabled = true,
    defaultType = 'service', -- service / civil

    -- Ordinary citizens may create/use Civil K9 teams.
    -- Service K9 and Civil/Service switching remain police/authority-only.
    -- The dog player never controls the active K9 type.
    allowNonAuthorityHandlers = true,

    -- Public Civil K9 access:
    -- true = ordinary citizens can create/adopt Civil K9 teams without
    -- police job or K9 role approval.
    publicAccess = true,

    labels = {
        service = 'Service K9',
        civil = 'Civil K9',
    },

    -- Civilian companion-dog progression. This is separate from police K9 XP.
    ranks = {
        { rank = 1, name = 'Family Foundation', xp = 0 },
        { rank = 2, name = 'Home Manners', xp = 20 },
        { rank = 3, name = 'Reliable Companion', xp = 50 },
        { rank = 4, name = 'Social Companion', xp = 90 },
        { rank = 5, name = 'Advanced Obedience', xp = 140 },
        { rank = 6, name = 'Elite Companion', xp = 210 },
    },

    activityLabels = {
        sit = 'Sit',
        down = 'Down',
        focus = 'Focus',
        stay = 'Stay',
        place = 'Place',
        recall = 'Recall',
        heel = 'Heel',
        fetch = 'Fetch',
        settle = 'Settle',
        impulse = 'Impulse Control',
    },

    unlocks = {
        sit = 1,
        down = 1,
        focus = 1,

        stay = 2,
        place = 2,
        recall = 2,

        heel = 3,
        fetch = 3,

        settle = 4,

        impulse = 5,
    },

    rewards = {
        pet = { xp = 2, bond = 2 },
        treat = { xp = 2, bond = 4 },
        sit = { xp = 3, obedience = 1, focus = 1 },
        down = { xp = 3, obedience = 1, focus = 1 },
        focus = { xp = 4, obedience = 1, focus = 1 },
        stay = { xp = 6, obedience = 2 },
        place = { xp = 7, obedience = 2, place = 1 },
        recall = { xp = 8, obedience = 2, recall = 1 },
        heel = { xp = 8, obedience = 2, heel = 1 },
        fetch = { xp = 6, bond = 2 },
        settle = { xp = 8, social = 2 },
        impulse = { xp = 10, obedience = 2, impulse = 1 },
    },

    drills = {
        sitDuration = 3000,
        downDuration = 3000,
        focusDuration = 5000,
        focusDistance = 3.0,

        placeDuration = 8000,
        placeRadius = 1.15,

        heelDuration = 10000,
        heelDistance = 3.0,

        settleDuration = 8000,
        settleRadius = 1.0,

        impulseDuration = 10000,
        impulseRadius = 0.85,
    },

    -- Every Service K9 progression feature can be enabled/disabled for
    -- Civil K9 individually. `rank` is the Civil Rank required when enabled.
    --
    -- This table mirrors Config.Progression.unlocks so the same client/server
    -- security gates are used for both Service and Civil profiles.
    features = {
        heel = {
            enabled = true,
            rank = 3,
        },
        stay = {
            enabled = true,
            rank = 2,
        },
        recall = {
            enabled = true,
            rank = 2,
        },
        vehicle_enter = {
            enabled = true,
            rank = 1,
        },
        vehicle_exit = {
            enabled = true,
            rank = 1,
        },
        stop_track = {
            enabled = false,
            rank = 1,
        },
        pet = {
            enabled = true,
            rank = 1,
        },
        treat = {
            enabled = true,
            rank = 1,
        },
        sniff = {
            enabled = false,
            rank = 4,
        },
        fetch = {
            enabled = true,
            rank = 3,
        },
        search_scent = {
            enabled = false,
            rank = 4,
        },
        track_handler = {
            enabled = false,
            rank = 4,
        },
        search_buried = {
            enabled = false,
            rank = 5,
        },
        tackle_order = {
            enabled = false,
            rank = 6,
        },
        tackle = {
            enabled = false,
            rank = 6,
        },

        -- Civil bite training:
        -- true  = Civil K9 can unlock Bite / Attack at the configured rank.
        -- false = Bite stays unavailable to Civil K9.
        bite = {
            enabled = true,
            rank = 5,
        },
    },
}
```

## Config.Progression

Source file: `config.lua`.

```lua
Config.Progression = {
    enabled = true,
    persist = true,

    levels = {
        { level = 1, name = 'Recruit', xp = 0 },
        { level = 2, name = 'Nosework I', xp = 15 },
        { level = 3, name = 'Tracker', xp = 35 },
        { level = 4, name = 'Search Specialist', xp = 60 },
        { level = 5, name = 'Patrol K9', xp = 90 },
        { level = 6, name = 'Elite K9', xp = 140 },
    },

    -- Server enforced. Direct K9 actions use the same keys.
    labels = {
        heel = 'På plads',
        stay = 'Bliv',
        recall = 'Kom tilbage',
        vehicle_enter = 'Ind i bil',
        vehicle_exit = 'Ud af bil',
        stop_track = 'Stop tracking',
        pet = 'Klap K9',
        treat = 'Godbid',
        sniff = 'Sniff',
        fetch = 'Fetch',
        search_scent = 'Person-fært',
        track_handler = 'Handler-fært',
        search_buried = 'K9bury search',
        tackle_order = 'Tackle ordre',
        tackle = 'Tackle',
        bite = 'Bite / attack',
    },

    unlocks = {
        heel = 1,
        stay = 1,
        recall = 1,
        vehicle_enter = 1,
        vehicle_exit = 1,
        stop_track = 1,
        pet = 1,
        treat = 1,

        sniff = 2,
        fetch = 2,

        search_scent = 3,
        track_handler = 3,

        search_buried = 4,

        tackle_order = 5,
        tackle = 5,
        bite = 5,
    }
}
```

## Config.Passport

Source file: `config.lua`.

```lua
Config.Passport = {
    enabled = true,

    specializations = {
        general = 'General K9',
        patrol = 'Patrol',
        narcotics = 'Narcotics',
        tracking = 'Tracking',
        search_rescue = 'Search & Rescue',
    },

    -- Certifications are derived from progression. They are display records,
    -- not automatic actions or permission bypasses.
    certificationLevels = {
        basic_obedience = 1,
        nosework = 2,
        tracking = 3,
        search = 4,
        patrol = 5,
        elite = 6,
    },
}
```

## Config.Admin

Source file: `config.lua`.

```lua
Config.Admin = {
    approvalRequired = true,
    command = 'k9admin',
    acePermission = 'advancedk9.admin',

    -- Optional identifier allowlist in addition to ACE.
    -- Example: 'license:1234567890abcdef'
    identifiers = {}
}
```

## Config.SetupEditor

Source file: `config.lua`.

```lua
Config.SetupEditor = {
    enabled = true,

    -- Handler/dog team members may configure K9 vehicle anchors in-game.
    -- Administrators with the existing Advanced K9 admin ACE are also allowed.
    allowTeamMembers = true,
    acePermission = 'advancedk9.admin',

    cageMoveStep = 0.01,
    cageRotateStep = 2.0,
}
```

## Config.VehicleCrashSafe

Source file: `config.lua`.

```lua
Config.VehicleCrashSafe = {
    enabled = true,
    mode = 'soft_cage',

    -- V94.5: restored on soft-cage, but started in separate delayed stages
    -- after cage entry has completed.
    autoPosture = true,
    autoCamera = true,

    -- The real player-controlled K9 follows the cage offset without being
    -- attached to the vehicle or forced into a GTA passenger seat.
    disableMovementWhileCaged = true,
    noCollisionWithVehicle = true,
    stateLogIntervalMs = 5000,

    -- Cage 1-4 are capabilities, not requirements. A vehicle model can have
    -- any subset active. Disabled cages keep their geometry for later.
    optionalSlots = true,
    legacyAnchorAsSlot1 = true,

    -- Avoid stacking animation/camera natives into the same frame as entry.
    autoPostureDelayMs = 300,
    autoCameraDelayMs = 650,

    -- V94.6.4: I toggles vehicle entry/exit for the dog.
    -- Exit is pushed safely behind the vehicle while keeping the saved X side.
    vehicleToggleKey = 'I',
    toggleExitBehind = true,
    toggleExitMinBehindY = -2.80,
    toggleExitExtraZ = 0.08,

    -- Handler quick-setup keeps the full editor available but removes several
    -- menu hops for the normal cage setup workflow.
    quickSetup = true,
}
```

## Config.VehicleStaff

Source file: `config.lua`.

```lua
Config.VehicleStaff = {
    command = 'k9cagestaff',
    deleteAllConfirmation = 'DELETE ALL',
}
```

## Config.VehicleDiagnostics

Source file: `config.lua`.

```lua
Config.VehicleDiagnostics = {
    -- Production default: diagnostics are opt-in through DeveloperMode/config.
    -- Enable temporarily while investigating vehicle/cage issues.
    enabled = false,
    mirrorClientToServer = false,
    clientHistory = 160,
    serverHistoryPerPlayer = 300,

    -- Handler-created LOCAL ped template. It is never networked and never
    -- replaces/moves the real player-controlled K9.
    templateDefaultModel = 'a_c_shepherd',
    templateModels = {
        'a_c_shepherd',
        'a_c_rottweiler',
        'a_c_husky',
        'a_c_retriever',
    },

    maxVehicleSlots = 4,
    reservationTimeoutMs = 20000,
    heartbeatMs = 5000,

    -- Editing is discrete (one movement step per key press), specifically so
    -- diagnostic output remains readable and every attach call has a before/
    -- after checkpoint.
    editor = {
        moveStep = 0.025,
        fineMoveStep = 0.005,
        rotateStep = 2.0,
        fineRotateStep = 0.5,
    },
}
```

## Config.Care

Source file: `config.lua`.

```lua
Config.Care = {
    enabled = true,

    -- Requested bowl props.
    Food = 'prop_cs_bowl_01',
    Water = 'v_res_mbowl',

    placementDistance = 1.25,
    maxBowlsPerHandler = 4,
    servingsPerBowl = 4,

    interactionDistance = 1.55,
    serverTolerance = 2.6,

    eatDuration = 4200,
    drinkDuration = 3500,

    foodRestore = 35,
    waterRestore = 45,
    snackRestore = 8,

    -- ENVI-HUD reads the active framework needs. Keep our K9 stats synced
    -- with the same hunger/thirst source rather than running a second HUD.
    syncFrameworkNeeds = true,
    hudSyncInterval = 15000,

    -- Standalone fallback only. QB/Qbox/ESX needs already decay in their
    -- normal framework/status systems, so we do not double-decay them.
    decayInterval = 60000,
    hungerDecay = 1,
    thirstDecay = 2,

    lowWarning = 25,

    overfeed = {
        enabled = true,
        threshold = 100,
        foodPoints = 45,
        snackPoints = 30,
        decayPerMinute = 12,
        cooldown = 120000,

        dumpDuration = 4500,
        propLifetime = 45000,
        dictionary = 'creatures@rottweiler@move',
        animation = 'dump_loop',
        flag = 1,

        prop = {
            model = 'prop_big_shit_02',
            bone = 51826,
            offset = { x = 0.0, y = 0.2, z = -0.46 },
            rotation = { x = 0.0, y = -20.0, z = 0.0 }
        }
    },

    dogInteractionAnimation = {
        dictionary = 'creatures@rottweiler@amb@world_dog_sitting@base',
        animation = 'base',
        flag = 1
    }
}
```

## Config.StationaryKennels

Source file: `config.lua`.

```lua
Config.StationaryKennels = {
    enabled = true,
    command = 'k9kennel',
    acePermission = 'advancedk9.admin',
    allowAuthoritySetup = true,
    defaultModel = 'prop_doghouse_01',
    -- Local ghost ped used while staff positions the K9 inside a stationary kennel.
    -- Change this to any valid dog ped model if you use a custom service-dog model.
    previewDogModel = 'a_c_shepherd',
    serverInteractionDistance = 10.0,
    editorMoveStep = 0.03,
    editorRotateStep = 2.0,
    deleteAllConfirmation = 'DELETE ALL',
}

-- Framework/inventory/target/phone providers are selected in mm_bridge/config.lua.
```

## Config.Bridge

Source file: `config.lua`.

```lua
Config.Bridge = {
    authorityAce = 'advanced_k9.authority',
    allowStandaloneAuthority = false, -- explicit opt-in; civil play remains available
    databaseIdentity = 'legacy_license', -- do not change without migrating all K9 tables
    getNeeds = nil, -- server function(src) -> hunger, thirst percentages
    setNeeds = nil, -- server function(src, hunger, thirst) -> confirmed true
}
-- Enable only when using one of the supplied k9_* phone adapters.
-- mm_bridge must allow advanced_k9 as a CustomAdapterOwners entry.
```

## Config.PhoneIntegration.registerLegacyAdapters

Source file: `config.lua`.

```lua
Config.PhoneIntegration.registerLegacyAdapters = false
```
