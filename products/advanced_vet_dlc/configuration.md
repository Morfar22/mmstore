# Advanced Vet DLC — Configuration

Edit the indicated config file and restart the resource after changes. Values are the exact uploaded defaults, not proposed settings. SQL-backed ownership, tax rates, stock and placement may override or outlive config seed values. Comments below are retained as source context and can include legacy notes; the usage/setup pages explain important current behavior.

All Config assignments in the supplied file are included. Vet pharmacy excerpts omit real-world dose/label fields; use the medicine guide for FiveM effects. Do not apply RP values as real treatment instructions.

## Config.Locale

Selects language where supported; most products supply da/en. Smoking/Pause have no generic locale switch.

Source: `config.lua`, line 3.

```lua
Config.Locale = 'da'
```


## Config.LocaleFallback

Controls locale fallback. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 4.

```lua
Config.LocaleFallback = 'en'
```


## Config.Debug

Diagnostic verbosity; keep disabled outside a reproduction.

Source: `config.lua`, line 6.

```lua
Config.Debug = false

-- DeveloperMode exposes diagnostic/test commands only. Keep false in production.
```


## Config.DeveloperMode

Exposes developer/test tools; not normal player permissions.

Source: `config.lua`, line 9.

```lua
Config.DeveloperMode = false
```


## Config.Database

Persistence and automatic schema initialization controls.

Source: `config.lua`, line 11.

```lua
Config.Database = {
    enabled = true,
    autoCreateTables = true,
}
```


## Config.Access

Veterinarian job and ACE access.

Source: `config.lua`, line 16.

```lua
Config.Access = {
    jobs = {
        vet = true,
        veterinarian = true,
        animalcare = true,
        police = true,
    },

    -- Server administrators can optionally grant:
    -- add_ace group.admin advanced_vet.use allow
    ace = 'advanced_vet.use',
}
```


## Config.Commands

Player/staff command names; actual registrations are in the commands guide/reference.

Source: `config.lua`, line 29.

```lua
Config.Commands = {
    open = 'vet',
    records = 'vetrecords',
    diagnostics = 'vetdiag',
}
```


## Config.Keybinds

Default mappings; existing client bindings can survive config changes.

Source: `config.lua`, line 35.

```lua
Config.Keybinds = {
    open = 'F10',
    -- Billing remains available through /vetpay and can be rebound manually,
    -- but does not consume a default gameplay key.
    invoices = '',
}
```


## Config.SetupEditor

Live setup permissions/editor movement; Vet editorOnly requires saved DB positions.

Source: `config.lua`, line 43.

```lua
Config.SetupEditor = {
    enabled = true,

    -- Runtime K9/table/kennel placement is DATABASE/EDITOR ONLY.
    -- Config coordinates are never used as a gameplay fallback.
    editorOnly = true,

    -- Production default: permanent clinic placement is staff/ACE controlled.
    -- Set true only if every veterinarian should be allowed to rebuild clinic positions.
    allowVeterinarian = false,
    acePermission = 'advanced_vet.setup',

    previewSeconds = 12,

    -- Live placement behaves like the K9 cage editor: move/rotate the
    -- patient anchor directly in the world, then confirm with ENTER.
    liveEditor = {
        enabled = true,
        step = 0.05,
        fineStep = 0.01,
        fastStep = 0.20,
        rotationStep = 2.5,
        fineRotationStep = 0.5,
        markerScale = 0.34,

        -- Every K9 patient/release placement is previewed with a real local dog
        -- ped, matching the Advanced K9 cage/kennel editor philosophy. This
        -- makes body clipping, table height and heading visible before saving.
        previewDog = {
            enabled = true,
            alpha = 190,
            model = 'a_c_shepherd',

            -- R cycles these while the live editor is open. Add custom K9 ped
            -- models here if their body size needs to be checked during setup.
            models = {
                'a_c_shepherd',
                'a_c_rottweiler',
                'a_c_husky',
                'a_c_retriever',
            },

            showDirection = true,
            directionLength = 0.95,
            directionColor = { r = 255, g = 20, b = 147, a = 235 },
        },
    },
}
```


## Config.Target

Optional target provider; proximity/native alternatives vary by resource.

Source: `config.lua`, line 92.

```lua
Config.Target = {
    enabled = true,
    provider = 'auto', -- auto / ox_target / markers
}

-- Veterinary clinic points.
-- These include the current custom MLO positions and must be preserved when updating.
```


## Config.Locations

Controls locations. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 99.

```lua
Config.Locations = {
    los_santos = {
        label = 'Los Santos Veterinary Clinic',
        blip = {
            enabled = true,
            sprite = 442,
            colour = 2,
            scale = 0.75,
        },
        reception = vector3(1245.62, -367.48, 69.08),
        treatment = vector3(1242.28, -369.13, 69.08),
        pharmacy = vector3(1248.53, -364.40, 69.08),
        records = vector3(1246.88, -362.95, 69.08),
        xray = vector3(1240.90, -371.20, 69.08),
        surgery = vector3(1238.80, -369.20, 69.08),
        kennels = vector3(1238.40, -365.80, 69.08),
        chip = vector3(1243.45, -363.30, 69.08),
        vaccination = vector3(1245.10, -365.30, 69.08),
        billing = vector3(1247.80, -360.90, 69.08),
        appointments = vector3(1244.55, -360.70, 69.08),
        k9training = vector3(1236.65, -367.60, 69.08),
    },

    sandy_shores = {
        label = 'Sandy Shores Animal Care',
        blip = {
            enabled = true,
            sprite = 442,
            colour = 2,
            scale = 0.70,
        },
        reception = vector3(1690.83, 3581.26, 35.62),
        treatment = vector3(1693.10, 3579.10, 35.62),
        pharmacy = vector3(1688.80, 3584.20, 35.62),
        records = vector3(1694.32, 3583.31, 35.62),
        xray = vector3(1695.70, 3578.10, 35.62),
        surgery = vector3(1697.10, 3580.20, 35.62),
        kennels = vector3(1697.60, 3583.30, 35.62),
        chip = vector3(1687.20, 3582.10, 35.62),
        vaccination = vector3(1687.30, 3579.70, 35.62),
        billing = vector3(1691.05, 3585.75, 35.62),
        appointments = vector3(1693.25, 3585.35, 35.62),
        k9training = vector3(1699.45, 3581.65, 35.62),
    },

    paleto_bay = {
        label = 'Paleto Bay Veterinary Clinic',
        blip = {
            enabled = true,
            sprite = 442,
            colour = 2,
            scale = 0.70,
        },
        reception = vector3(561.61, 2752.24, 42.16),
        treatment = vec3(564.50, 2773.54, 42.16),
        pharmacy = vec3(568.19, 2772.85, 42.16),
        records = vec3(562.74, 2776.25, 42.16),
        xray = vec3(563.89, 2775.09, 42.16),
        surgery = vector3(564.7437, 2768.4475, 42.5714),
        kennels = vec3(558.71, 2796.92, 42.16),
        chip = vec3(568.17, 2773.24, 42.16),
        vaccination = vec3(567.96, 2775.74, 42.16),
        billing = vec3(560.45, 2753.03, 42.16),
        appointments = vec3(562.55, 2753.30, 42.16),
        k9training = vec3(568.75, 2799.67, 42.02),
    },
}
```


## Config.DeathIntegration

Sky/native revive and authoritative injury cleanup.

Source: `config.lua`, line 170.

```lua
Config.DeathIntegration = {
    enabled = true,
    provider = 'auto', -- auto / sky_ambulancejob / native
    skyResource = 'sky_ambulancejob',

    -- Sky's command revive context skips the configured death timeout.
    skyReviveContext = {
        reason = 'command',
    },

    -- Treatment definitions still decide whether a treatment is allowed to revive.
    nativeFallback = true,

    -- Sky's public heal event is used only for treatments/procedures marked
    -- clearSkyInjuries. It clears Sky bleeding/wounds/injury effects.
    -- Sky owns the healed injury/HP result; Vet does not lower HP again afterwards.
    clearInjuriesEvent = 'sky_ambulancejob:healPlayer',

    -- Sky's documented server heal event is authoritative.
    -- GetLocalInjuryProfile is diagnostic only and MUST NOT be used as an
    -- acknowledgement contract on Sky 2.x, because its profile contract is
    -- version-dependent and can remain a table after a successful heal.
    profileVerification = 'diagnostic', -- diagnostic / off
    postHealSettleMs = 900,

    -- Log a compact diagnostic if a profile is still returned after heal.
    -- This never makes the Vet treatment fail.
    logResidualProfile = true,
}
```


## Config.K9Training

Controls k9 training. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 200.

```lua
Config.K9Training = {
    enabled = true,

    -- Uses Config.AdvancedK9.resource as the single K9 resource-name source.
    -- Proximity is required only to select/start the training session.
    -- Commands inside an active v89+ session are distance-free.
    maxDistance = 12.0,
    stationDistance = 5.0,

    commands = {
        { key = 'search_scent', label = 'Søg person-fært', description = 'Sender en person-fært ordre; K9-spilleren vælger selv om den udføres.' },
        { key = 'search_buried', label = 'Søg nedgravet fært', description = 'Sender nedgravet-fært ordre; K9-spilleren vælger selv om den udføres.' },
        { key = 'sniff', label = 'Færtsøgning', description = 'Sender sniff-ordre; K9-spilleren udfører selv den normale K9-handling.' },
        { key = 'training_stay', label = 'Træn BLIV', description = 'Sender en BLIV-træningsanmodning; K9-spilleren skal acceptere, før øvelsen og XP starter.' },
        { key = 'training_recall', label = 'Træn INDKALD', description = 'Sender en INDKALD-træningsanmodning; K9-spilleren skal acceptere, før øvelsen og XP starter.' },
        { key = 'heel', label = 'PÅ PLADS', description = 'Sender PÅ PLADS-ordre; K9-spilleren styrer selv.' },
        { key = 'stay', label = 'BLIV', description = 'Sender almindelig BLIV-ordre; K9-spilleren vælger selv.' },
        { key = 'recall', label = 'KOM TILBAGE', description = 'Sender en INDKALD-ordre og en visuel træner-markering; K9-spilleren styrer selv.' },
        { key = 'fetch', label = 'Apportering', description = 'Træneren kan starte og kaste apportering; K9-spilleren vælger selv at hente og aflevere.' },
        { key = 'stop_track', label = 'Stop sporing', description = 'Sender en ordre om at stoppe sporingen; K9-spilleren vælger selv at stoppe.' },
    },
}
```


## Config.Inventory

Actual inventory adapter/requirements; string/provider alone does not implement a new adapter.

Source: `config.lua`, line 223.

```lua
Config.Inventory = {
    enabled = true,
    provider = 'auto', -- auto / ox_inventory / tgiann-inventory / framework / none
    prescriptionAmount = 1,

    -- Every issued pharmacy prescription creates TWO inventory items:
    -- 1) the prescribed medicine/product, 2) a metadata-rich prescription document.
    prescriptionDocumentItem = 'vet_prescription',
    prescriptionDocumentEnabled = true,
}



-- Physical animal positioning for examination, X-ray and surgery.
-- The configured coordinates below are the current table alignments.
-- `/vettablepos <clinic> <station>` can be used when intentionally re-aligning
-- a table, but updates should not replace these locations with demo values.
```


## Config.PatientTables

Physical placement/pose/release; supplied legacy coords ignored in editor-only runtime.

Source: `config.lua`, line 240.

```lua
Config.PatientTables = {
    enabled = true,
    autoPlaceForProcedures = true,
    releaseAfterProcedure = true,

    -- Config.Locations is authoritative. A PatientTables override is only
    -- accepted when it remains close to the matching clinic station.
    maxOverrideDistanceFromStation = 12.0,
    maxPatientDistanceFromTable = 12.0,
    placedPatientInteractionDistance = 15.0,

    -- Legacy values kept for backwards compatibility/documentation only.
    -- Runtime placement NEVER reads these when editor-only placement is enabled.
    fallback = {
        enabled = false,
        zOffset = {
            treatment = 0.78,
            xray = 0.78,
            surgery = 0.78,
            chip = 0.78,
            vaccination = 0.78,
        },
        releaseDistance = 1.15,
        headingMode = 'patient', -- patient / vet
    },

    -- Keeps the patient locked at the configured point while placed.
    enforcePosition = true,
    enforceIntervalMs = 100,
    maxDrift = 0.12,
    playerMaxDrift = 0.75, -- player K9: avoid tiny corrective teleports that cancel Onex emotes

    -- Safety release if the veterinarian leaves the working area.
    autoReleaseDistance = 25.0,
    autoReleaseCheckMs = 5000,

    -- Canine lying pose used BOTH by the setup preview and the real patient.
    -- Runtime placement now mirrors preview order exactly (freeze -> pose ->
    -- re-apply transform), so the K9 lies the same way you positioned it.
    pose = {
        enabled = true,

        -- Exact bdogsleep definition supplied by the server's big-dog emote.
        -- Both preview and the real K9 consume this SAME table.
        emote = 'bdogsleep',
        label = 'Søvn (stor hund)',
        animation = 'sleep_in_kennel',
        dictionary = 'creatures@rottweiler@amb@sleep_in_kennel@',

        -- IMPORTANT: player-controlled K9s use the real Onex emote command.
        -- The direct animation below is only a fallback and is also used by
        -- local non-player preview peds in /vetsetup.
        provider = 'onex',
        externalResource = 'onex-emotes',
        externalCommand = 'e',
        externalStartDelayMs = 650,
        externalVerifyTimeoutMs = 600,
        preEmoteSettleMs = 180,
        postEmoteSettleMs = 160,

        options = {
            flags = {
                loop = true,
            },
            exitemote = 'bdogupk',
        },
        pedtypes = { 'big_dogs' },

        -- Backwards-compatible fallback only. Runtime derives looping from
        -- options.flags.loop first.
        flag = 1,
        lockedFrame = false,
        settleMs = 180,
        loadTimeoutMs = 1500,
    },


    -- LEGACY ONLY: these coordinates are intentionally ignored by runtime.
    -- Use /vetsetup for every K9 patient + release placement.
    locations = {
        los_santos = {
            treatment = {
                coords = vector4(1242.28, -369.13, 69.88, 90.0),
                release = vector4(1243.30, -369.10, 69.08, 270.0),
            },
            xray = {
                coords = vector4(1240.90, -371.20, 69.88, 90.0),
                release = vector4(1241.95, -371.20, 69.08, 270.0),
            },
            surgery = {
                coords = vector4(1238.80, -369.20, 69.88, 90.0),
                release = vector4(1239.85, -369.20, 69.08, 270.0),
            },
            chip = {
                coords = vector4(1243.45, -363.30, 69.88, 180.0),
                release = vector4(1243.45, -364.35, 69.08, 0.0),
            },
            vaccination = {
                coords = vector4(1245.10, -365.30, 69.88, 180.0),
                release = vector4(1245.10, -366.35, 69.08, 0.0),
            },
        },

        sandy_shores = {
            treatment = {
                coords = vector4(1693.10, 3579.10, 36.42, 180.0),
                release = vector4(1693.10, 3577.95, 35.62, 0.0),
            },
            xray = {
                coords = vector4(1695.70, 3578.10, 36.42, 180.0),
                release = vector4(1695.70, 3576.95, 35.62, 0.0),
            },
            surgery = {
                coords = vector4(1697.10, 3580.20, 36.42, 180.0),
                release = vector4(1697.10, 3579.05, 35.62, 0.0),
            },
            chip = {
                coords = vector4(1687.20, 3582.10, 36.42, 90.0),
                release = vector4(1688.20, 3582.10, 35.62, 270.0),
            },
            vaccination = {
                coords = vector4(1687.30, 3579.70, 36.42, 90.0),
                release = vector4(1688.30, 3579.70, 35.62, 270.0),
            },
        },

        paleto_bay = {
            treatment = {
                coords = vec4(564.76, 2768.43, 42.12, 181.20),
                release = vec4(564.30, 2771.37, 42.16, 247.78),
            },
            xray = {
                coords = vec4(564.20, 2774.27, 43.20, 86.52),
                release = vec4(564.30, 2771.37, 42.16, 247.78),
            },
            surgery = {
                coords = vec4(564.76, 2768.43, 42.12, 181.20),
                release = vec4(564.30, 2771.37, 42.16, 247.78),
            },
            chip = {
                coords = vec4(564.76, 2768.43, 42.12, 181.20),
                release = vec4(564.30, 2771.37, 42.16, 247.78),
            },
            vaccination = {
                coords = vec4(564.76, 2768.43, 42.12, 181.20),
                release = vec4(564.30, 2771.37, 42.16, 247.78),
            },
        },
    },
}
```


## Config.Triage

Controls triage. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 392.

```lua
Config.Triage = {
    enabled = true,

    -- RP/gameplay vital signs derived from the current gameplay health state.
    -- These are not real veterinary diagnostic values.
    historyLimit = 20,
    criticalHealthPercent = 25,
    urgentHealthPercent = 50,
    watchHealthPercent = 75,
}
```


## Config.PatientConsent

Which procedures ask player consent and timeout/emergency bypass.

Source: `config.lua`, line 403.

```lua
Config.PatientConsent = {
    enabled = true,
    timeoutMs = 20000,

    -- A dead/critically down player-K9 may receive emergency stabilization
    -- without waiting for a consent UI that the player cannot reasonably use.
    emergencyBypassDead = true,

    treatments = {
        examination = false,
        bandage = true,
        woundCare = true,
        fluids = false,
        nutrition = false,
        stabilize = true,
        fullTreatment = true,
    },

    xray = true,
    surgery = true,
    kennel = true,
    chip = true,
    vaccination = true,
}
```


## Config.XRay

Controls x ray. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 428.

```lua
Config.XRay = {
    enabled = true,
    duration = 4500,
    regions = {
        { id = 'skull', label = 'Kranie' },
        { id = 'chest', label = 'Brystkasse' },
        { id = 'spine', label = 'Rygsøjle' },
        { id = 'hips', label = 'Hofter/bækken' },
        { id = 'front_limbs', label = 'Forben' },
        { id = 'rear_limbs', label = 'Bagben' },
    },
}
```


## Config.Surgery

Controls surgery. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 441.

```lua
Config.Surgery = {
    enabled = true,

    phases = {
        { key = 'prepare', label = 'Forberedelse', ratio = 0.15 },
        { key = 'anesthesia', label = 'Bedøvelse / overvågning', ratio = 0.20 },
        { key = 'operation', label = 'Kirurgisk indgreb', ratio = 0.42 },
        { key = 'closure', label = 'Lukning / bandagering', ratio = 0.13 },
        { key = 'recovery', label = 'Restitution / observation', ratio = 0.10 },
    },

    procedures = {
        wound_repair = {
            label = 'Kirurgisk sårbehandling',
            description = 'RP-operation til større sårskader.',
            duration = 12000,
            minimumHealthPercent = 65,
            clearBlood = true,
            invoiceAmount = 1800,
        },
        fracture_stabilization = {
            label = 'Frakturstabilisering',
            description = 'RP-kirurgi til stabilisering efter røntgenfund.',
            duration = 15000,
            minimumHealthPercent = 55,
            clearBlood = true,
            invoiceAmount = 2400,
        },
        emergency_surgery = {
            label = 'Akut operation',
            description = 'Akut RP-indgreb til kritisk skadet patient.',
            duration = 18000,
            minimumHealthPercent = 75,
            clearBlood = true,
            invoiceAmount = 3500,
        },
    },
}
```


## Config.Kennels

Controls kennels. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 480.

```lua
Config.Kennels = {
    enabled = true,
    slots = {
        'A-01', 'A-02', 'A-03', 'A-04',
        'B-01', 'B-02', 'B-03', 'B-04',
    },

    physical = {
        enabled = true,

        -- Optional physical kennel/doghouse object. Each slot can place its own
        -- prop in /vetsetup independently from the dog's patient anchor.
        object = {
            enabled = true,
            model = 'prop_doghouse_01',
            freeze = true,
            collision = true,
            invincible = true,
        },

        -- LEGACY ONLY: runtime kennel placement ignores these offsets.
        -- Use /vetsetup for kennel prop, K9 position and release position.
        slotOffsets = {
            ['A-01'] = { x = -1.20, y = -0.80, z = 0.00, heading = 0.0 },
            ['A-02'] = { x = -0.40, y = -0.80, z = 0.00, heading = 0.0 },
            ['A-03'] = { x =  0.40, y = -0.80, z = 0.00, heading = 180.0 },
            ['A-04'] = { x =  1.20, y = -0.80, z = 0.00, heading = 180.0 },
            ['B-01'] = { x = -1.20, y =  0.80, z = 0.00, heading = 0.0 },
            ['B-02'] = { x = -0.40, y =  0.80, z = 0.00, heading = 0.0 },
            ['B-03'] = { x =  0.40, y =  0.80, z = 0.00, heading = 180.0 },
            ['B-04'] = { x =  1.20, y =  0.80, z = 0.00, heading = 180.0 },
        },

        maxPatientDistance = 8.0,
        releaseOffset = { x = 0.0, y = -2.0, z = 0.0, heading = 180.0 },

        -- Kennel patients use the exact same proven big-dog sleep pose as
        -- treatment tables. Player-controlled K9s therefore use the real
        -- Onex `bdogsleep` command, while preview/NPC peds use the same native
        -- dictionary/clip. One pose definition prevents visual drift.
        pose = Config.PatientTables.pose,
    },
}
```


## Config.ChipScanner

Controls chip scanner. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 524.

```lua
Config.ChipScanner = {
    enabled = true,
    chipPrefix = 'AVET',
}
```


## Config.Vaccinations

Controls vaccinations. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 529.

```lua
Config.Vaccinations = {
    enabled = true,

    -- These are gameplay/RP schedules, not veterinary dosing instructions.
    products = {
        core = {
            label = 'Kernevaccination',
            rpValidDays = 365,
        },
        kennel_cough = {
            label = 'Kennelhostevaccination',
            rpValidDays = 365,
        },
        rabies = {
            label = 'Rabiesvaccination',
            rpValidDays = 365,
        },
    },
}
```


## Config.Billing

Invoice provider/account/limit. Shipped Vet provider is NRP.

Source: `config.lua`, line 549.

```lua
Config.Billing = {
    provider = 'nrp',
    nrpAccount = 'vet', -- Account for ACE-authorized staff without a veterinary job.
    enabled = true,
    account = 'bank',
    maxInvoice = 100000,
    allowStandaloneFree = false,
}
```


## Config.Appointments

Controls appointments. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 558.

```lua
Config.Appointments = {
    enabled = true,
    maxNoteLength = 500,
}
```


## Config.MedicineUse

Controls medicine use. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 563.

```lua
Config.MedicineUse = {
    enabled = true,
    maxTargetDistance = 3.0,
    requirePrescriptionPatientMatch = true,

    -- Only these jobs count as an actual veterinarian being available for the
    -- GoldenPaws emergency-heal rule. Police access to the Vet UI does not count.
    vetOnlineJobs = {
        vet = true,
        veterinarian = true,
        animalcare = true,
    },

    -- Pure gameplay values. These are not real veterinary doses or medical guidance.
    -- A human uses the product on the nearest player-controlled K9. A K9 using the
    -- item itself applies it to itself.
}
```


## Config.Pharmacy

Catalog/stock/prescription workflow; documented gameplay effects are separate from source RP label text.

Source: `config.lua`, line 581.

```lua
Config.Pharmacy = {
    enabled = true,
    defaultStock = 20,
    maxStock = 100,
    requirePatientForPrescription = true,

    -- Gameplay profiles based on the supplied canine prescription reference.
    -- Real-world dose guidance is NOT used as FiveM gameplay logic.
    -- Strong prescription products can alter the K9 player's screen/movement,
    -- while food/water products primarily affect hunger/thirst.
    products = {
        quietpaws = {
            itemName = 'vet_quietpaws',
            category = 'Sedative',
            productName = 'QuietPaws™',
            gameplayInfo = 'Heavy sedation for 3 min: slower movement, no sprint/jump/attack, strong sedated screen effect.',
            kind = 'medicine',
            effects = {
                status = 'sedated',
                duration = 180,
                moveRate = 0.62,
                disableSprint = true,
                disableJump = true,
                disableAttack = true,
                visual = {
                    label = 'Tung sedation',
                    priority = 100,
                    timecycle = 'spectator5',
                    strength = 0.62,
                    pulse = 0.05,
                    cameraShake = 0.12,
                    motionBlur = true,
                },
            },
        },

        gentleease = {
            itemName = 'vet_gentleease',
            category = 'Strong Painkiller',
            productName = 'GentleEase™',
            gameplayInfo = 'Strong pain-relief status for 4 min with mild drowsy visual and movement effect; does not heal wounds.',
            kind = 'medicine',
            effects = {
                status = 'pain_relief',
                duration = 240,
                -- Pain relief is deliberately not treated as wound healing.
                moveRate = 0.90,
                visual = {
                    label = 'Stærk smertelindring / døsighed',
                    priority = 70,
                    timecycle = 'spectator5',
                    strength = 0.28,
                    pulse = 0.025,
                    cameraShake = 0.035,
                    motionBlur = true,
                },
            },
        },

        happyjoints = {
            itemName = 'vet_happyjoints',
            category = 'Mild Painkiller (NSAID)',
            productName = 'HappyJoints™',
            gameplayInfo = 'Joint-support status for 10 min; no narcotic screen effect.',
            kind = 'medicine',
            effects = {
                status = 'joint_support',
                duration = 600,
            },
        },

        bellybloom = {
            itemName = 'vet_bellybloom',
            category = 'Stomach / GI Support',
            productName = 'BellyBloom™',
            gameplayInfo = 'GI/stomach-support status for 10 min; does not add hunger.',
            kind = 'medicine',
            effects = {
                status = 'gi_support',
                duration = 600,
            },
        },

        peacefulpet = {
            itemName = 'vet_peacefulpet',
            category = 'Anxiety / Calming',
            productName = 'PeacefulPet™',
            gameplayInfo = 'Calming for 4 min: mild drowsy screen/movement effect and K9 attack actions are blocked.',
            kind = 'medicine',
            effects = {
                status = 'calmed',
                duration = 240,
                moveRate = 0.88,
                disableAttack = true,
                visual = {
                    label = 'Beroligende / døsig',
                    priority = 45,
                    timecycle = 'spectator5',
                    strength = 0.16,
                    pulse = 0.015,
                    cameraShake = 0.0,
                    motionBlur = false,
                },
            },
        },

        goldenpaws_daily = {
            itemName = 'vet_goldenpaws_daily',
            category = 'Multivitamin',
            productName = 'GoldenPaws Daily™',
            gameplayInfo = '15 min vitality buff: +25% max HP; if no on-duty Vet is online, also restores 25 percentage points of HP.',
            kind = 'medicine',
            effects = {
                status = 'wellness',
                duration = 900,

                -- GoldenPaws vitality gameplay buff. This is intentionally a
                -- FiveM/RP mechanic, not real-world veterinary guidance.
                maxHealthMultiplier = 1.25,

                -- Applied only when the server cannot find an on-duty Vet.
                emergencyHealPercent = 0.25,
            },
        },

        meadowbowl = {
            itemName = 'vet_meadowbowl',
            category = 'Daily Food',
            productName = 'MeadowBowl™',
            gameplayInfo = 'Full daily meal: restores 45 hunger.',
            kind = 'nutrition',
            effects = {
                hunger = 45,
            },
        },

        softharvest = {
            itemName = 'vet_softharvest',
            category = 'Sensitive / Recovery Food',
            productName = 'SoftHarvest™',
            gameplayInfo = 'Recovery meal: restores 35 hunger and grants recovery-nutrition status for 5 min.',
            kind = 'nutrition',
            effects = {
                status = 'recovery_nutrition',
                duration = 300,
                hunger = 35,
            },
        },

        sprinkle_of_sunshine = {
            itemName = 'vet_sprinkle_of_sunshine',
            category = 'Food Topper',
            productName = 'Sprinkle of Sunshine™',
            gameplayInfo = 'Food topper: restores 5 hunger and grants appetite-support status for 5 min.',
            kind = 'nutrition',
            effects = {
                status = 'appetite_support',
                duration = 300,
                hunger = 5,
            },
        },

        clearspring = {
            itemName = 'vet_clearspring',
            category = 'Hydration / Water Additive',
            productName = 'ClearSpring™',
            gameplayInfo = 'Hydration support: restores 25 thirst.',
            kind = 'hydration',
            effects = {
                thirst = 25,
            },
        },

        pawpure = {
            itemName = 'vet_pawpure',
            category = 'Electrolyte Water Boost',
            productName = 'PawPure™',
            gameplayInfo = 'Electrolyte hydration: restores 40 thirst and grants electrolyte-support status for 5 min.',
            kind = 'hydration',
            effects = {
                status = 'electrolyte_support',
                duration = 300,
                thirst = 40,
            },
        },

        stillbrook = {
            itemName = 'vet_stillbrook',
            category = 'Daily Water',
            productName = 'StillBrook™',
            gameplayInfo = 'Daily water: restores 30 thirst.',
            kind = 'hydration',
            effects = {
                thirst = 30,
            },
        },
    },
}
```


## Config.Interaction

Controls interaction. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 832.

```lua
Config.Interaction = {
    maxDistance = 4.0,
    refreshDistance = 6.0,
    requireLineOfSight = true,
}
```


## Config.AdvancedK9

Optional resource name/state/passport/care integration.

Source: `config.lua`, line 838.

```lua
Config.AdvancedK9 = {
    enabled = true,
    resource = 'advanced_k9',
    dogStateBag = 'advancedK9Dog',
    passportIntegration = true,

    -- After a treatment that restores food/water, the DLC will sync the
    -- framework needs and ask Advanced K9 to refresh its internal care values.
    syncCareNeeds = true,
}
```


## Config.AnimalModels

Controls animal models. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 849.

```lua
Config.AnimalModels = {
    'a_c_shepherd',
    'a_c_rottweiler',
    'a_c_husky',
    'a_c_retriever',
    'a_c_westy',
    'a_c_poodle',
    'a_c_pug',
    'a_c_chop',
    'a_c_cat_01',
    'a_c_coyote',
    'a_c_mtlion',
    'a_c_boar',
    'a_c_deer',
    'a_c_cow',
    'a_c_pig',
    'a_c_rabbit_01',
}

-- Purely gameplay values. These are not real-world veterinary protocols.
```


## Config.ProcedurePresentation

Internal/optional ox_lib progress and staff animation settings.

Source: `config.lua`, line 869.

```lua
Config.ProcedurePresentation = {
    enabled = true,

    -- internal = Advanced Vet's own progressbar, no extra dependency.
    -- ox_lib = use lib.progressCircle when ox_lib is running.
    -- auto = prefer ox_lib, otherwise use the internal progressbar.
    progressProvider = 'internal',

    lockMovement = true,
    lockCombat = true,

    default = {
        animation = {
            dictionary = 'amb@medic@standing@tendtodead@base',
            name = 'base',
            flag = 1,
            loadTimeoutMs = 1800,
        },
        fallbackScenario = 'CODE_HUMAN_MEDIC_TEND_TO_DEAD',
    },

    -- Procedure-family defaults. Treatment-specific overrides live below.
    procedures = {
        treatment = {
            eyebrow = 'BEHANDLING',
            animation = {
                dictionary = 'amb@medic@standing@tendtodead@base',
                name = 'base',
                flag = 1,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'CODE_HUMAN_MEDIC_TEND_TO_DEAD',
        },

        surgery = {
            eyebrow = 'OPERATION',
            animation = {
                dictionary = 'mini@repair',
                name = 'fixing_a_ped',
                flag = 1,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'CODE_HUMAN_MEDIC_TEND_TO_DEAD',
        },

        xray = {
            eyebrow = 'RØNTGEN',
            animation = {
                dictionary = 'amb@world_human_clipboard@male@base',
                name = 'base',
                flag = 49,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'WORLD_HUMAN_CLIPBOARD',
        },

        chip = {
            eyebrow = 'MICROCHIP',
            duration = 4500,
            animation = {
                dictionary = 'mini@repair',
                name = 'fixing_a_ped',
                flag = 1,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'CODE_HUMAN_MEDIC_TEND_TO_DEAD',
        },

        vaccination = {
            eyebrow = 'VACCINATION',
            duration = 3500,
            animation = {
                dictionary = 'amb@medic@standing@tendtodead@base',
                name = 'base',
                flag = 1,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'CODE_HUMAN_MEDIC_TEND_TO_DEAD',
        },
    },

    -- Treatment-specific presentation. These all use known GTA V animation
    -- dictionaries already used by the resource, with reliable scenarios as
    -- fallback. This keeps examination/diagnostics visually distinct from
    -- hands-on treatment without inventing fragile animation clips.
    treatments = {
        examination = {
            eyebrow = 'UNDERSØGELSE',
            animation = {
                dictionary = 'amb@world_human_clipboard@male@base',
                name = 'base',
                flag = 49,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'WORLD_HUMAN_CLIPBOARD',
        },
        bandage = {
            eyebrow = 'FORBINDING',
            animation = {
                dictionary = 'mini@repair',
                name = 'fixing_a_ped',
                flag = 1,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'CODE_HUMAN_MEDIC_TEND_TO_DEAD',
        },
        woundCare = {
            eyebrow = 'SÅRBEHANDLING',
            animation = {
                dictionary = 'mini@repair',
                name = 'fixing_a_ped',
                flag = 1,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'CODE_HUMAN_MEDIC_TEND_TO_DEAD',
        },
        fluids = {
            eyebrow = 'VÆSKEBEHANDLING',
            animation = {
                dictionary = 'amb@medic@standing@tendtodead@base',
                name = 'base',
                flag = 1,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'CODE_HUMAN_MEDIC_TEND_TO_DEAD',
        },
        nutrition = {
            eyebrow = 'ERNÆRINGSSTØTTE',
            animation = {
                dictionary = 'amb@medic@standing@tendtodead@base',
                name = 'base',
                flag = 1,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'CODE_HUMAN_MEDIC_TEND_TO_DEAD',
        },
        stabilize = {
            eyebrow = 'STABILISERING',
            animation = {
                dictionary = 'mini@repair',
                name = 'fixing_a_ped',
                flag = 1,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'CODE_HUMAN_MEDIC_TEND_TO_DEAD',
        },
        fullTreatment = {
            eyebrow = 'FULD BEHANDLING',
            animation = {
                dictionary = 'mini@repair',
                name = 'fixing_a_ped',
                flag = 1,
                loadTimeoutMs = 1800,
            },
            fallbackScenario = 'CODE_HUMAN_MEDIC_TEND_TO_DEAD',
        },
    },
}
```


## Config.Treatments

Controls treatments. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 1028.

```lua
Config.Treatments = {
    examination = {
        label = 'Undersøgelse',
        description = 'Kontrollerer dyrets aktuelle spilstatus og journalfører besøget.',
        duration = 2500,
        category = 'diagnostic',
    },

    bandage = {
        label = 'Forbinding',
        description = 'Rens og forbind mindre skader.',
        duration = 3500,
        category = 'treatment',
        healPercent = 15,
        clearBlood = true,
    },

    woundCare = {
        label = 'Sårbehandling',
        description = 'Grundigere behandling af skader og blod.',
        duration = 5000,
        category = 'treatment',
        healPercent = 30,
        clearBlood = true,
        clearSkyInjuries = true,
    },

    fluids = {
        label = 'Væskebehandling',
        description = 'Støttende behandling og fuld hydrering i spilsystemet.',
        duration = 4500,
        category = 'support',
        healPercent = 5,
        thirst = 100,
    },

    nutrition = {
        label = 'Ernæringsstøtte',
        description = 'Gendanner dyrets madstatus i spilsystemet.',
        duration = 3500,
        category = 'support',
        hunger = 100,
    },

    stabilize = {
        label = 'Stabilisering',
        description = 'Stabiliserer et hårdt skadet dyr til minimum 45% helbred.',
        duration = 6000,
        category = 'emergency',
        minimumHealthPercent = 45,
        clearBlood = true,
        clearSkyInjuries = true,
        revive = true,
    },

    fullTreatment = {
        label = 'Fuld behandling',
        description = 'Fuld behandling i spilsystemet: helbred, blod, mad og vand.',
        duration = 8000,
        category = 'emergency',
        healthPercent = 100,
        hunger = 100,
        thirst = 100,
        clearBlood = true,
        clearSkyInjuries = true,
        revive = true,
    },
}
```
