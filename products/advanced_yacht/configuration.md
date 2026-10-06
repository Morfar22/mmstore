# Advanced Yacht — Configuration

Edit the indicated config file and restart the resource after changes. Values are the exact uploaded defaults, not proposed settings. SQL-backed ownership, tax rates, stock and placement may override or outlive config seed values. Comments below are retained as source context and can include legacy notes; the usage/setup pages explain important current behavior.

All Config assignments in the supplied file are included. Vet pharmacy excerpts omit real-world dose/label fields; use the medicine guide for FiveM effects. Do not apply RP values as real treatment instructions.

## Config.Locale

Selects language where supported; most products supply da/en. Smoking/Pause have no generic locale switch.

Source: `config.lua`, line 3.

```lua
Config.Locale = 'da' -- da / en
```


## Config.Currency

Controls currency. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 4.

```lua
Config.Currency = 'DKK'
```


## Config.MoneyAccount

Controls money account. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 5.

```lua
Config.MoneyAccount = 'bank'
```


## Config.AdminAce

Controls admin ace. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 6.

```lua
Config.AdminAce = 'advanced_yacht.admin'
```


## Config.MaxYachtsPerCharacter

Controls max yachts per character. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 7.

```lua
Config.MaxYachtsPerCharacter = 1
```


## Config.RelocationFee

Controls relocation fee. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 8.

```lua
Config.RelocationFee = 25000
```


## Config.RenameFee

Controls rename fee. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 9.

```lua
Config.RenameFee = 25000
```


## Config.FlagChangeFee

Controls flag change fee. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 10.

```lua
Config.FlagChangeFee = 25000
```


## Config.PackageDowngradeFees

Controls package downgrade fees. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 11.

```lua
Config.PackageDowngradeFees = { orion = 500000, pisces = 1000000 } -- GTA Online-style post-purchase downgrade fees
```


## Config.HornCooldown

Controls horn cooldown. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 12.

```lua
Config.HornCooldown = 12 -- seconds
```


## Config.RelocationCooldown

Controls relocation cooldown. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 13.

```lua
Config.RelocationCooldown = 60 -- seconds
```


## Config.MaxGuests

Controls max guests. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 14.

```lua
Config.MaxGuests = 10
```


## Config.StorageDistance

Controls storage distance. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 15.

```lua
Config.StorageDistance = 85.0
```


## Config.InteractionDistance

Controls interaction distance. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 16.

```lua
Config.InteractionDistance = 120.0
```


## Config.ShowPublicYachtBlips

Controls show public yacht blips. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 17.

```lua
Config.ShowPublicYachtBlips = true
```


## Config.YachtBlipSprite

Controls yacht blip sprite. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 18.

```lua
Config.YachtBlipSprite = 455
```


## Config.YachtBlipColour

Controls yacht blip colour. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 19.

```lua
Config.YachtBlipColour = 3
```


## Config.YachtBlipScale

Controls yacht blip scale. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 20.

```lua
Config.YachtBlipScale = 0.72
```


## Config.FastTravel

Controls fast travel. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 21.

```lua
Config.FastTravel = true
```


## Config.FastTravelFadeMs

Controls fast travel fade ms. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 22.

```lua
Config.FastTravelFadeMs = 650

-- GTA Online-style scripted yacht cinematics. These use Rockstar/FiveM camera natives
-- so the sequence works on all 36 yacht moorings instead of relying on a fixed cutscene location.
```


## Config.Cinematics

Controls cinematics. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 26.

```lua
Config.Cinematics = {
    enabled = true,
    allowSkip = true,
    skipControl = 73, -- X
    letterbox = true,
    showTitle = true,
    timecycle = 'yacht_DLC',
    timecycleStrength = 0.22,
    fadeInMs = 550,
    fadeOutMs = 450,
    board = {
        sound = 'Arrive_Horn',
        soundset = 'DLC_Apartment_Yacht_Streams_Soundset',
        shots = {
            { offset = vec3(-118.0, -72.0, 35.0), lookAt = vec3(-12.0, -1.9, 8.0), fov = 48.0, duration = 1700, blend = 850 },
            { offset = vec3(-45.0, 67.0, 24.0), lookAt = vec3(-24.0, -1.9, 8.0), fov = 43.0, duration = 1750, blend = 900 },
            { offset = vec3(-47.0, -18.0, 15.5), lookAt = vec3(-30.8, -1.9, 6.6), fov = 38.0, duration = 1500, blend = 800 },
        }
    },
    leave = {
        sound = 'Leave_Horn',
        soundset = 'DLC_Apartment_Yacht_Streams_Soundset',
        shots = {
            { offset = vec3(-46.0, -17.0, 14.0), lookAt = vec3(-30.8, -1.9, 6.6), fov = 38.0, duration = 1300, blend = 750 },
            { offset = vec3(-79.0, 45.0, 23.0), lookAt = vec3(-24.0, -1.9, 8.0), fov = 44.0, duration = 1700, blend = 850 },
            { offset = vec3(-142.0, -92.0, 46.0), lookAt = vec3(-8.0, -1.9, 7.0), fov = 50.0, duration = 1850, blend = 900 },
        }
    }
}

-- ox_lib is the primary yacht frontend. All menus, confirmations, inputs and notifications
-- use ox_lib while yacht spawning, props, cameras and gameplay remain native GTA/FiveM.
```


## Config.OxLibUI

Controls ox lib u i. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 58.

```lua
Config.OxLibUI = {
    position = 'top-right',
    notifyPosition = 'top-right',
    notifyDuration = 4500,
    liveCustomizationPreview = true,
}

-- Optional physical yacht-name renderer. This is not a menu and only uses Rockstar's
-- YACHT_NAME render target on the hull.
```


## Config.HullName

Controls hull name. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 67.

```lua
Config.HullName = {
    enabled = true,
    distance = 350.0,
    disableWhenMultipleNearby = true,
}
```


## Config.DefenseRadius

Controls defense radius. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 73.

```lua
Config.DefenseRadius = 150.0
```


## Config.DefenseWeaponSafeRadius

Controls defense weapon safe radius. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 74.

```lua
Config.DefenseWeaponSafeRadius = 82.0
```


## Config.DefenseAircraftWarningSeconds

Controls defense aircraft warning seconds. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 75.

```lua
Config.DefenseAircraftWarningSeconds = 5
```


## Config.DefenseAircraftStrikeCooldown

Controls defense aircraft strike cooldown. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 76.

```lua
Config.DefenseAircraftStrikeCooldown = 8
```


## Config.Debug

Diagnostic verbosity; keep disabled outside a reproduction.

Source: `config.lua`, line 77.

```lua
Config.Debug = false
```


## Config.RemoveUnusedRockstarYachts

Controls remove unused rockstar yachts. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 78.

```lua
Config.RemoveUnusedRockstarYachts = true -- keep only DB-owned yachts visible

-- Optional wardrobe integration.
```


## Config.Appearance

Optional yacht wardrobe adapter.

Source: `config.lua`, line 81.

```lua
Config.Appearance = 'illenium-appearance' -- illenium-appearance / qb-clothing / custom / none
```


## Config.CustomWardrobeEvent

Controls custom wardrobe event. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 82.

```lua
Config.CustomWardrobeEvent = ''
```


## Config.Broker

Controls broker. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 84.

```lua
Config.Broker = {
    label = 'Puerto Del Sol Yacht Broker',
    coords = vec3(-794.84, -1510.32, 1.60),
    radius = 1.6,
    blip = { enabled = true, sprite = 410, colour = 3, scale = 0.75 }
}

-- GTA Online inspired packages. The yacht itself is Rockstar's static IPL yacht.
```


## Config.Packages

Yacht purchase/storage/features; vehicle upgrades not bundled.

Source: `config.lua`, line 92.

```lua
Config.Packages = {
    orion = {
        label = 'The Orion',
        price = 6000000,
        description = 'Klassisk Galaxy Super Yacht med storage, garderobe, gæsteadgang og helipad.',
        tier = 1,
        storage = { slots = 70, weight = 300000 },
        textureVariant = 0,
        defaults = { fittings = 'chrome', lighting = 'presidential_green', flag = 'denmark' },
        features = { storage = true, wardrobe = true, jacuzzi = false, defense = true, helipad = true },
        visual = { option = 'apa_mp_apa_yacht_option1', rail = 'apa_mp_apa_yacht_o1_rail_a', lights = 'apa_mp_apa_y1_l2b' }
    },
    pisces = {
        label = 'The Pisces',
        price = 7000000,
        description = 'Premium yacht med større storage, jacuzzi og udvidet crew-adgang.',
        tier = 2,
        storage = { slots = 90, weight = 450000 },
        textureVariant = 0,
        defaults = { fittings = 'chrome', lighting = 'presidential_green', flag = 'denmark' },
        features = { storage = true, wardrobe = true, jacuzzi = true, defense = true, helipad = true },
        visual = { option = 'apa_mp_apa_yacht_option2', rail = 'apa_mp_apa_yacht_o2_rail_a', lights = 'apa_mp_apa_y2_l2b' }
    },
    aquarius = {
        label = 'The Aquarius',
        price = 8000000,
        description = 'Topmodellen med maksimal storage, jacuzzi og valgfrit yacht-defense safezone.',
        tier = 3,
        storage = { slots = 120, weight = 650000 },
        textureVariant = 0,
        defaults = { fittings = 'chrome', lighting = 'presidential_green', flag = 'denmark' },
        features = { storage = true, wardrobe = true, jacuzzi = true, defense = true, helipad = true },
        visual = { option = 'apa_mp_apa_yacht_option3', rail = 'apa_mp_apa_yacht_o3_rail_a', lights = 'apa_mp_apa_y3_l2b' }
    }
}

-- Rockstar Apartment/Yacht IPL set: 12 groups x 3 berths = 36 real yacht positions.
-- The labels correspond to the surrounding GTA V coastline.
```


## Config.Moorings

Static Rockstar berth geometry; keep IDs consistent with IPLs.

Source: `config.lua`, line 130.

```lua
Config.Moorings = {
    [1] = { label = 'Lago Zancudo', slots = {
        [1] = vec4(-3542.8220, 1488.2500, 5.429909, -123.04490),
        [2] = vec4(-3148.3790, 2807.5550, 5.430044, 91.95499),
        [3] = vec4(-3280.5010, 2140.5070, 5.429955, 86.95500),
    }},
    [2] = { label = 'North Chumash', slots = {
        [1] = vec4(-2814.4890, 4072.7400, 5.428353, -108.04495),
        [2] = vec4(-3254.5520, 3685.6760, 5.429955, 81.95500),
        [3] = vec4(-2368.4410, 4697.8740, 5.429955, -133.04500),
    }},
    [3] = { label = 'Pacific Bluffs', slots = {
        [1] = vec4(-3205.3440, -219.0104, 5.429955, 176.95500),
        [2] = vec4(-3448.2540, 311.5018, 5.429955, -83.04494),
        [3] = vec4(-2697.8620, -540.6123, 5.429955, 146.95500),
    }},
    [4] = { label = 'Vespucci Beach', slots = {
        [1] = vec4(-1995.7250, -1523.6940, 5.429970, -38.04500),
        [2] = vec4(-2117.5810, -2543.3460, 5.429955, 36.95500),
        [3] = vec4(-1605.0740, -1872.4680, 5.429955, -68.04500),
    }},
    [5] = { label = 'Los Santos International Airport', slots = {
        [1] = vec4(-753.0817, -3919.0680, 5.429955, 11.95500),
        [2] = vec4(-351.0608, -3553.3230, 5.429955, -123.04500),
        [3] = vec4(-1460.5360, -3761.4670, 5.429955, 161.95500),
    }},
    [6] = { label = 'Terminal', slots = {
        [1] = vec4(1546.8920, -3045.6270, 5.430184, -118.04450),
        [2] = vec4(2490.8860, -2428.8480, 5.429955, -168.04500),
        [3] = vec4(2049.7900, -2821.6240, 5.429955, 31.95500),
    }},
    [7] = { label = 'Palomino Highlands', slots = {
        [1] = vec4(3029.0180, -1495.7020, 5.429968, -108.04500),
        [2] = vec4(3021.2540, -723.3903, 5.429986, 81.95500),
        [3] = vec4(2976.6220, -1994.7600, 5.429955, -133.04500),
    }},
    [8] = { label = 'Tataviam Mountains', slots = {
        [1] = vec4(3404.5100, 1977.0440, 5.429955, -103.04500),
        [2] = vec4(3411.1000, 1193.4450, 5.430062, 31.95502),
        [3] = vec4(3784.8020, 2548.5410, 5.429955, 86.95510),
    }},
    [9] = { label = 'San Chianski Mountain Range', slots = {
        [1] = vec4(4225.0280, 3988.0020, 5.429955, 61.95510),
        [2] = vec4(4250.5810, 4576.5650, 5.429955, 111.95500),
        [3] = vec4(4204.3560, 3373.7000, 5.429955, 81.95500),
    }},
    [10] = { label = 'Mount Gordo', slots = {
        [1] = vec4(3751.6810, 5753.5010, 5.429955, 136.95500),
        [2] = vec4(3490.1050, 6305.7850, 5.429955, 156.95500),
        [3] = vec4(3684.8530, 5212.2380, 5.429955, -58.04500),
    }},
    [11] = { label = 'Procopio Beach', slots = {
        [1] = vec4(581.5955, 7124.5580, 5.429955, 121.95500),
        [2] = vec4(2004.4620, 6907.1570, 5.429974, 6.95500),
        [3] = vec4(1396.6380, 6860.2030, 5.429959, 176.95500),
    }},
    [12] = { label = 'Paleto Bay', slots = {
        [1] = vec4(-1170.6900, 5980.6810, 5.429944, 91.95500),
        [2] = vec4(-777.4865, 6566.9070, 5.429955, 26.95490),
        [3] = vec4(-381.7739, 6946.9600, 5.429900, 71.95500),
    }},
}

-- GTA Online yacht deck points, based on Rockstar/Menyoo yacht geometry.
-- Z is local to apa_mp_apa_yacht and is only used as a raycast hint; collision decides the final position.
```


## Config.BoardCandidates

Controls board candidates. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 195.

```lua
Config.BoardCandidates = {
    vec3(-30.82, -1.87, 6.30), -- helipad / safest primary spawn
    vec3(-37.5245, -2.0054, 0.2776),
    vec3(-13.6966, -1.9615, 0.2808),
    vec3(-0.5604, -2.0216, 6.3030),
    vec3(5.0348, -1.9846, 6.3074),
    vec3(14.2079, -2.1206, 7.3519), -- captain deck
    vec3(23.3344, -1.6929, 3.5506), -- bar deck
}
```


## Config.BoardMinHeightAboveAnchor

Controls board min height above anchor. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 204.

```lua
Config.BoardMinHeightAboveAnchor = -1.0
```


## Config.BoardMaxHeightAboveAnchor

Controls board max height above anchor. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 205.

```lua
Config.BoardMaxHeightAboveAnchor = 24.0
```


## Config.BoardFallbackHeight

Controls board fallback height. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 206.

```lua
Config.BoardFallbackHeight = 6.30
```


## Config.BoardFallbackOffset

Controls board fallback offset. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 207.

```lua
Config.BoardFallbackOffset = vec3(-30.82, -1.87, 6.30)
```


## Config.ShoreReturn

Controls shore return. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 208.

```lua
Config.ShoreReturn = vec4(-795.55, -1507.93, 1.60, 112.0)

-- Exact GTA-yacht local geometry used by the static Rockstar assembly.
```


## Config.GTAO

Yacht local geometry, jacuzzi surface and fleet slots.

Source: `config.lua`, line 211.

```lua
Config.GTAO = {
    topOffset = vec3(0.0032, 0.0028, 14.5700),
    jacuzzi = {
        center = vec3(-50.8033, -1.9774, 0.1368),
        water = {
            enabled = true,
            model = 'apa_mp_apa_yacht_jacuzzi_ripple1',
            offset = vec3(-50.8033, -1.9774, 0.1368),
            zOffset = 0.0,
            headingOffset = 0.0,
        },
        seats = {
            vec3(-49.00, -1.9993, 0.10),
            vec3(-50.00, -4.0000, 0.10),
            vec3(-50.00,  0.0000, 0.10),
            vec3(-52.00,  0.0000, 0.10),
            vec3(-52.00, -4.0000, 0.10),
            vec3(-53.00, -1.9993, 0.10),
        },
        exit = vec3(-46.50, -1.95, 0.75),
    },
    captain = { model = 'mp_m_boatstaff_01', offset = vec3(14.2079, -2.1206, 7.3519), headingOffset = -88.2933 },
    bartender = { model = 'mp_f_boatstaff_01', offset = vec3(23.3344, -1.6929, 3.5506), headingOffset = 88.9650,
        animDict = 'anim@mini@yacht@bar@drink@idle_a', animName = 'idle_a_bartender' },
    -- Physical spawn slots on each Rockstar yacht tier. Vehicles are NOT included for free.
    -- Purchased add-ons are assigned to these slots by slotGroup.
    vehicleSlots = {
        [1] = {
            tender = {
                { key = 'tender_1', offset = vec3(-54.3528, -13.3907, -5.1819), heading = -109.0565 },
            },
            jetski = {
                { key = 'jetski_1', offset = vec3(-61.5043, -8.9306, -5.5869), heading = 116.3082 },
            },
            helicopter = {
                { key = 'heli_1', offset = vec3(-30.8168, -1.8687, 6.5134), heading = -90.0000 },
            },
        },
        [2] = {
            tender = {
                { key = 'tender_1', offset = vec3(-54.3522, -13.3903, -4.8438), heading = -109.0528 },
                { key = 'tender_2', offset = vec3(-53.7848, 9.1620, -4.6511), heading = -69.9578 },
            },
            jetski = {
                { key = 'jetski_1', offset = vec3(-61.5275, 4.6035, -5.3742), heading = 63.7883 },
                { key = 'jetski_2', offset = vec3(-61.5155, -8.8960, -5.3594), heading = -243.6808 },
            },
            helicopter = {
                { key = 'heli_1', offset = vec3(-30.8168, -1.8687, 6.5134), heading = -90.0000 },
            },
        },
        [3] = {
            tender = {
                { key = 'tender_1', offset = vec3(-54.3447, -13.3947, -5.4129), heading = -108.2869 },
                { key = 'tender_2', offset = vec3(-54.3726, 9.1093, -5.5979), heading = -69.8533 },
            },
            jetski = {
                { key = 'jetski_1', offset = vec3(-61.5189, 2.3503, -5.8703), heading = 64.4417 },
                { key = 'jetski_2', offset = vec3(-61.5050, -8.9017, -5.6858), heading = 116.2442 },
                { key = 'jetski_3', offset = vec3(-61.5228, 4.5982, -5.8566), heading = 64.5492 },
                { key = 'jetski_4', offset = vec3(-61.5087, -6.6536, -5.7382), heading = 114.6004 },
            },
            helicopter = {
                { key = 'heli_1', offset = vec3(-30.8329, -1.8728, 7.2883), heading = -90.0000 },
            },
        },
    },
}

-- Yacht vehicle add-on shop. Everything below is editable.
-- Prices are intentionally high by default so the yacht itself remains only the beginning of the luxury sink.
```


## Config.YachtVehicleShop

Paid fleet catalog/package allowance/slot groups/quantity/resale.

Source: `config.lua`, line 282.

```lua
Config.YachtVehicleShop = {
    enabled = true,
    autoSpawnOnBoard = true,
    purchaseRequiresOnYacht = false, -- true = køb/salg kræver at ejeren er tæt på yachten
    purchaseDistance = 140.0,
    sellEnabled = true,
    sellRefundPercent = 0.50,
    entries = {
        {
            key = 'seashark', label = 'Speedophile Seashark', model = 'seashark3', type = 'boat', slotGroup = 'jetski',
            price = 750000, maxQuantity = 4,
            allowedPackages = { orion = true, pisces = true, aquarius = true },
            description = 'Personlig jetski til yachten.'
        },
        {
            key = 'tropic', label = 'Shitzu Tropic', model = 'tropic2', type = 'boat', slotGroup = 'tender',
            price = 2750000, maxQuantity = 1,
            allowedPackages = { orion = true, pisces = true, aquarius = true },
            description = 'Klassisk luksus-tender.'
        },
        {
            key = 'dinghy', label = 'Nagasaki Dinghy', model = 'dinghy4', type = 'boat', slotGroup = 'tender',
            price = 2250000, maxQuantity = 1,
            allowedPackages = { pisces = true, aquarius = true },
            description = 'Praktisk tender til større yachtmodeller.'
        },
        {
            key = 'speeder', label = 'Pegassi Speeder', model = 'speeder2', type = 'boat', slotGroup = 'tender',
            price = 3500000, maxQuantity = 1,
            allowedPackages = { pisces = true, aquarius = true },
            description = 'Hurtig premium tender.'
        },
        {
            key = 'toro', label = 'Lampadati Toro', model = 'toro', type = 'boat', slotGroup = 'tender',
            price = 5500000, maxQuantity = 1,
            allowedPackages = { aquarius = true },
            description = 'Topklasse tender til The Aquarius.'
        },
        {
            key = 'swift_deluxe', label = 'Buckingham Swift Deluxe', model = 'swift2', type = 'heli', slotGroup = 'helicopter',
            price = 12500000, maxQuantity = 1,
            allowedPackages = { pisces = true, aquarius = true },
            description = 'Guldfarvet luksushelikopter til helipad.'
        },
        {
            key = 'supervolito_carbon', label = 'Buckingham SuperVolito Carbon', model = 'supervolito2', type = 'heli', slotGroup = 'helicopter',
            price = 17500000, maxQuantity = 1,
            allowedPackages = { aquarius = true },
            description = 'Den dyreste helikopteropgradering til The Aquarius.'
        },
    }
}
```


## Config.AutoSpawnPurchasedFleetOnBoard

Controls auto spawn purchased fleet on board. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 335.

```lua
Config.AutoSpawnPurchasedFleetOnBoard = true
```


## Config.SpawnRockstarYachtStaff

Controls spawn rockstar yacht staff. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 336.

```lua
Config.SpawnRockstarYachtStaff = true
```


## Config.FreezePurchasedFleetWhenEmpty

Controls freeze purchased fleet when empty. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 337.

```lua
Config.FreezePurchasedFleetWhenEmpty = true
```


## Config.YachtAccessModes

Controls yacht access modes. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 338.

```lua
Config.YachtAccessModes = {
    { key = 'everyone', label = 'Everyone' },
    { key = 'crew', label = 'Crew' },
    { key = 'friends', label = 'Friends' },
    { key = 'crew_friends', label = 'Crew + Friends' },
    { key = 'organization', label = 'Organization' },
    { key = 'associates', label = 'Associates' },
    { key = 'no_one', label = 'No-one' },
}
```


## Config.VehicleAccessModes

Controls vehicle access modes. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 347.

```lua
Config.VehicleAccessModes = {
    { key = 'everyone', label = 'Everyone' },
    { key = 'crew', label = 'Crew' },
    { key = 'friends', label = 'Friends' },
    { key = 'crew_friends', label = 'Crew + Friends' },
    { key = 'no_one', label = 'No-one' },
    { key = 'passengers', label = 'Passengers' },
    { key = 'organization', label = 'Organization' },
    { key = 'associates', label = 'Associates' },
}
```


## Config.HotTubClothingModes

Controls hot tub clothing modes. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 357.

```lua
Config.HotTubClothingModes = {
    { key = 'swimwear', label = 'Swimwear' },
    { key = 'current', label = 'Current' },
}
```


## Config.DefenseExclusionModes

Controls defense exclusion modes. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 361.

```lua
Config.DefenseExclusionModes = {
    { key = 'friends', label = 'Friends' },
    { key = 'crew', label = 'Crew' },
    { key = 'friends_crew', label = 'Friends & Crew' },
    { key = 'organization', label = 'Organization' },
    { key = 'motorcycle_club', label = 'Motorcycle Club' },
    { key = 'associates', label = 'Associates' },
    { key = 'no_one', label = 'No-one' },
}


-- GTA Online renovation pricing and ordering.
```


## Config.YachtColors

Controls yacht colors. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 373.

```lua
Config.YachtColors = {
    -- IDs are Rockstar SET_OBJECT_TINT_INDEX values, not storefront ordering.
    { id = 0, label = 'Pacific', price = 0 },
    { id = 1, label = 'Azure', price = 300000 },
    { id = 2, label = 'Nautical', price = 135000 },
    { id = 3, label = 'Continental', price = 450000 },
    { id = 4, label = 'Battleship', price = 475000 },
    { id = 5, label = 'Intrepid', price = 635000 },
    { id = 6, label = 'Uniform', price = 315000 },
    { id = 7, label = 'Classico', price = 620000 },
    { id = 8, label = 'Mediterranean', price = 365000 },
    { id = 9, label = 'Command', price = 495000 },
    { id = 10, label = 'Mariner', price = 170000 },
    { id = 11, label = 'Ruby', price = 340000 },
    { id = 12, label = 'Vintage', price = 425000 },
    { id = 13, label = 'Pristine', price = 220000 },
    { id = 14, label = 'Merchant', price = 195000 },
    { id = 15, label = 'Voyager', price = 650000 },
}
```


## Config.TextureVariants

Controls texture variants. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 392.

```lua
Config.TextureVariants = Config.YachtColors -- backwards compatibility
```


## Config.Fittings

Controls fittings. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 394.

```lua
Config.Fittings = {
    { key = 'chrome', label = 'Chrome', price = 0, railSuffix = 'a' },
    { key = 'gold', label = 'Gold', price = 750000, railSuffix = 'b' },
}

-- Rockstar uses l1/l2 lighting families and a/b/c/d colour variants.
-- a=gold/yellow, b=blue, c=rose/pink, d=green.
```


## Config.Lighting

Controls lighting. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 401.

```lua
Config.Lighting = {
    { key = 'presidential_green', label = 'Presidential Green', price = 0, family = 'l1', suffix = 'd' },
    { key = 'presidential_blue', label = 'Presidential Blue', price = 315000, family = 'l1', suffix = 'b' },
    { key = 'presidential_rose', label = 'Presidential Rose', price = 330000, family = 'l1', suffix = 'c' },
    { key = 'presidential_gold', label = 'Presidential Gold', price = 350000, family = 'l1', suffix = 'a' },
    { key = 'vivacious_green', label = 'Vivacious Green', price = 500000, family = 'l2', suffix = 'd' },
    { key = 'vivacious_blue', label = 'Vivacious Blue', price = 525000, family = 'l2', suffix = 'b' },
    { key = 'vivacious_rose', label = 'Vivacious Rose', price = 550000, family = 'l2', suffix = 'c' },
    { key = 'vivacious_gold', label = 'Vivacious Gold', price = 600000, family = 'l2', suffix = 'a' },
}

-- The 46 country flags available for the Galaxy Super Yacht in GTA Online.
```


## Config.Flags

Controls flags. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 413.

```lua
Config.Flags = {
    { key='scotland', label='Skotland', model='apa_prop_flag_scotland_yt' },
    { key='usa', label='USA', model='apa_prop_flag_us_yt' },
    { key='france', label='Frankrig', model='apa_prop_flag_france' },
    { key='italy', label='Italien', model='apa_prop_flag_italy' },
    { key='sweden', label='Sverige', model='apa_prop_flag_sweden' },
    { key='argentina', label='Argentina', model='apa_prop_flag_argentina' },
    { key='eu', label='EU', model='apa_prop_flag_eu_yt' },
    { key='finland', label='Finland', model='apa_prop_flag_finland' },
    { key='netherlands', label='Nederlandene', model='apa_prop_flag_netherlands' },
    { key='portugal', label='Portugal', model='apa_prop_flag_portugal' },
    { key='southkorea', label='Sydkorea', model='apa_prop_flag_southkorea' },
    { key='australia', label='Australien', model='apa_prop_flag_australia' },
    { key='germany', label='Tyskland', model='apa_prop_flag_german_yt' },
    { key='switzerland', label='Schweiz', model='apa_prop_flag_switzerland' },
    { key='belgium', label='Belgien', model='apa_prop_flag_belgium' },
    { key='turkey', label='Tyrkiet', model='apa_prop_flag_turkey' },
    { key='china', label='Kina', model='apa_prop_flag_china' },
    { key='hungary', label='Ungarn', model='apa_prop_flag_hungary' },
    { key='newzealand', label='New Zealand', model='apa_prop_flag_newzealand' },
    { key='puertorico', label='Puerto Rico', model='apa_prop_flag_puertorico' },
    { key='brazil', label='Brasilien', model='apa_prop_flag_brazil' },
    { key='japan', label='Japan', model='apa_prop_flag_japan_yt' },
    { key='jamaica', label='Jamaica', model='apa_prop_flag_jamaica' },
    { key='mexico', label='Mexico', model='apa_prop_flag_mexico_yt' },
    { key='ireland', label='Irland', model='apa_prop_flag_ireland' },
    { key='croatia', label='Kroatien', model='apa_prop_flag_croatia' },
    { key='israel', label='Israel', model='apa_prop_flag_israel' },
    { key='nigeria', label='Nigeria', model='apa_prop_flag_nigeria' },
    { key='slovakia', label='Slovakiet', model='apa_prop_flag_slovakia' },
    { key='spain', label='Spanien', model='apa_prop_flag_spain' },
    { key='colombia', label='Colombia', model='apa_prop_flag_columbia' },
    { key='austria', label='Østrig', model='apa_prop_flag_austria' },
    { key='wales', label='Wales', model='apa_prop_flag_wales' },
    { key='czechrep', label='Tjekkiet', model='apa_prop_flag_czechrep' },
    { key='liechtenstein', label='Liechtenstein', model='apa_prop_flag_lstein' },
    { key='palestine', label='Palæstina', model='apa_prop_flag_palestine' },
    { key='southafrica', label='Sydafrika', model='apa_prop_flag_southafrica' },
    { key='canada', label='Canada', model='apa_prop_flag_canadat_yt' },
    { key='uk', label='Storbritannien', model='apa_prop_flag_uk_yt' },
    { key='norway', label='Norge', model='apa_prop_flag_norway' },
    { key='russia', label='Rusland', model='apa_prop_flag_russia_yt' },
    { key='england', label='England', model='apa_prop_flag_england' },
    { key='denmark', label='Danmark', model='apa_prop_flag_denmark' },
    { key='malta', label='Malta', model='apa_prop_flag_malta' },
    { key='poland', label='Polen', model='apa_prop_flag_poland' },
    { key='slovenia', label='Slovenien', model='apa_prop_flag_slovenia' },
}

-- Rockstar yacht assembly offsets, relative to `apa_mp_apa_yacht`.
-- The main superstructure pieces share the same +14.57 local Z transform. This is the
-- correct yacht assembly transform and replaces the broken negative Z offsets from V3.0.
```


## Config.Assembly

Static yacht prop transforms; test custom changes against native IPLs.

Source: `config.lua`, line 465.

```lua
Config.Assembly = {
    top = vec3(0.0032, 0.0028, 14.5700),
    flag = { offset = vec3(-56.6221, -2.0013, 1.5937), rotation = vec3(49.6800, 0.0, -89.9500) },
    jacuzzi = { offset = vec3(-50.8033, -1.9774, 0.1368), rotation = vec3(0.0, 0.0, 0.0), seat = vec3(-50.80, -1.98, 0.10), exit = vec3(-46.50, -1.95, 0.75) },
    radars = {
        [1] = {
            { offset = vec3(0.95549, -2.1682, 9.6040), rotation = vec3(0.0, 0.0, 90.0) },
            { offset = vec3(1.2820, -1.9895, 13.4305), rotation = vec3(0.0, 0.0, -180.0) },
            { offset = vec3(5.4844, -1.9817, 18.1568), rotation = vec3(0.0, 0.0, -90.0) },
        },
        [2] = {
            { offset = vec3(-2.2487, -1.9926, 17.3200), rotation = vec3(0.0, 0.0, -90.0) },
            { offset = vec3(1.6188, -1.9927, 14.0505), rotation = vec3(0.0, 0.0, -180.0) },
            { offset = vec3(7.6349, -1.9927, 10.3491), rotation = vec3(0.0, 0.0, 90.0) },
        },
        [3] = {
            { offset = vec3(10.8361, -1.9899, 9.8530), rotation = vec3(0.0, 0.0, 90.0) },
            { offset = vec3(-0.2231, -1.9601, 12.8964), rotation = vec3(0.0, 0.0, 180.0) },
            { offset = vec3(-15.0487, -1.9918, 9.0674), rotation = vec3(0.0, 0.0, 90.0) },
        },
    }
}
```


## Config.RockstarProps

Controls rockstar props. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 488.

```lua
Config.RockstarProps = {
    base = 'apa_mp_apa_yacht',
    windows = 'apa_mp_apa_yacht_win',
    jacuzzi = 'apa_mp_apa_yacht_jacuzzi_cam',
    jacuzziRipples = { 'apa_mp_apa_yacht_jacuzzi_ripple1', 'apa_mp_apa_yacht_jacuzzi_ripple2', 'apa_mp_apa_yacht_jacuzzi_ripple003' },
    radar = 'apa_mp_apa_yacht_radar_01a',
    launchers = { 'apa_mp_apa_yacht_launcher_01a', 'apa_mp_apa_yacht_launcher_02a' },
    options = { 'apa_mp_apa_yacht_option1', 'apa_mp_apa_yacht_option2', 'apa_mp_apa_yacht_option3' },
    optionShells = {
        [1] = { 'apa_mp_apa_yacht_option1', 'apa_mp_apa_yacht_option1_cola' },
        [2] = { 'apa_mp_apa_yacht_option2', 'apa_mp_apa_yacht_option2_cola', 'apa_mp_apa_yacht_option2_colb' },
        [3] = { 'apa_mp_apa_yacht_option3', 'apa_mp_apa_yacht_option3_cola', 'apa_mp_apa_yacht_option3_colb', 'apa_mp_apa_yacht_option3_colc', 'apa_mp_apa_yacht_option3_cold', 'apa_mp_apa_yacht_option3_cole' },
    },
    rails = {
        'apa_mp_apa_yacht_o1_rail_a', 'apa_mp_apa_yacht_o1_rail_b',
        'apa_mp_apa_yacht_o2_rail_a', 'apa_mp_apa_yacht_o2_rail_b',
        'apa_mp_apa_yacht_o3_rail_a', 'apa_mp_apa_yacht_o3_rail_b'
    },
    lights = {
        'apa_mp_apa_y1_l1a','apa_mp_apa_y1_l1b','apa_mp_apa_y1_l1c','apa_mp_apa_y1_l1d',
        'apa_mp_apa_y1_l2a','apa_mp_apa_y1_l2b','apa_mp_apa_y1_l2c','apa_mp_apa_y1_l2d',
        'apa_mp_apa_y2_l1a','apa_mp_apa_y2_l1b','apa_mp_apa_y2_l1c','apa_mp_apa_y2_l1d',
        'apa_mp_apa_y2_l2a','apa_mp_apa_y2_l2b','apa_mp_apa_y2_l2c','apa_mp_apa_y2_l2d',
        'apa_mp_apa_y3_l1a','apa_mp_apa_y3_l1b','apa_mp_apa_y3_l1c','apa_mp_apa_y3_l1d',
        'apa_mp_apa_y3_l2a','apa_mp_apa_y3_l2b','apa_mp_apa_y3_l2c','apa_mp_apa_y3_l2d',
    },
    flagTemplateModels = { 'apa_prop_flag_script' },
}
```


## Config.Text

Controls text. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 517.

```lua
Config.Text = {
    da = {
        yacht = 'Yacht', broker = 'Yachtmægler', open_broker = 'Åbn yachtmægler', my_yacht = 'Min yacht',
        buy = 'Køb yacht', move = 'Flyt yacht', rename = 'Omdøb yacht', guests = 'Gæsteadgang', storage = 'Opbevaring',
        wardrobe = 'Garderobe', jacuzzi = 'Jacuzzi', board = 'Gå ombord', shore = 'Tilbage til land', defense = 'Yacht-defense',
        waypoint = 'Sæt waypoint', customize = 'Design / farve', purchased = 'Yachten er købt og fortøjet.', purchase_failed = 'Handlingen kunne ikke gennemføres.', moved = 'Kaptajnen har flyttet yachten.',
        no_money = 'Du har ikke penge nok.', no_access = 'Du har ikke adgang til denne yacht.', owner_only = 'Kun ejeren kan gøre dette.',
        no_slot = 'Der er ingen ledig yacht-plads i det område.', same_area = 'Yachten ligger allerede i det område.', cooldown = 'Kaptajnen er ikke klar til en ny flytning endnu.',
        renamed = 'Yachten er omdøbt.', guest_added = 'Gæsteadgang er givet.', guest_removed = 'Gæsteadgang er fjernet.', invalid_player = 'Spilleren blev ikke fundet.',
        too_far = 'Du er for langt fra yachten.', feature_off = 'Denne yachtpakke har ikke funktionen.', max_yachts = 'Du har allerede det maksimale antal yachts.',
        max_guests = 'Yachten har nået grænsen for gæster.', defense_on = 'Yacht-defense er aktiveret.', defense_off = 'Yacht-defense er deaktiveret.',
        debug_sync = 'Yachtverden synkroniseret.', deleted = 'Yachten er slettet.', given = 'Yachten er oprettet til spilleren.'
    },
    en = {
        yacht = 'Yacht', broker = 'Yacht broker', open_broker = 'Open yacht broker', my_yacht = 'My yacht',
        buy = 'Buy yacht', move = 'Move yacht', rename = 'Rename yacht', guests = 'Guest access', storage = 'Storage',
        wardrobe = 'Wardrobe', jacuzzi = 'Jacuzzi', board = 'Board yacht', shore = 'Return to shore', defense = 'Yacht defense',
        waypoint = 'Set waypoint', customize = 'Design / colour', purchased = 'Yacht purchased and moored.', purchase_failed = 'The action could not be completed.', moved = 'The captain moved the yacht.',
        no_money = 'You do not have enough money.', no_access = 'You do not have access to this yacht.', owner_only = 'Only the owner can do this.',
        no_slot = 'There is no free yacht berth in that area.', same_area = 'The yacht is already in that area.', cooldown = 'The captain is not ready to move the yacht again yet.',
        renamed = 'Yacht renamed.', guest_added = 'Guest access granted.', guest_removed = 'Guest access removed.', invalid_player = 'Player not found.',
        too_far = 'You are too far from the yacht.', feature_off = 'This yacht package does not have that feature.', max_yachts = 'You already own the maximum number of yachts.',
        max_guests = 'The yacht has reached its guest limit.', defense_on = 'Yacht defense enabled.', defense_off = 'Yacht defense disabled.',
        debug_sync = 'Yacht world synchronized.', deleted = 'Yacht deleted.', given = 'Yacht created for player.'
    }
}
```
