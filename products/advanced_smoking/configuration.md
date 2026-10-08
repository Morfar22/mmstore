# Configuration

Edit the indicated config file and restart the resource after changes. Values are the exact uploaded defaults, not proposed settings. SQL-backed ownership, tax rates, stock and placement may override or outlive config seed values. Comments below are retained as source context and can include legacy notes; the usage/setup pages explain important current behavior.

All Config assignments in the supplied file are included. Vet pharmacy excerpts omit real-world dose/label fields; use the medicine guide for FiveM effects. Do not apply RP values as real treatment instructions.

## Config table

All settings in the single Config table are shown below. This resource has no generic locale selector.

```lua
Config = {
    Inventory = 'tgiann-inventory',
    WheelKey = 'G', PuffKey = 'H',
    MaxInhaleMs = 4000, MaxHoldMs = 5000, PuffCooldownMs = 1800,
    ShareDistance = 2.5, OfferSeconds = 20,
    VisualDistance = 45.0, MaxVisibleSmokers = 24,
    LitterSeconds = 90, MaxLitter = 40,
    MaxPlacedPerOwner = 5, MaxPlacedTotal = 150,
    WorldSyncSeconds = 8,
    ToleranceDecayPerHour = 8.0,
    MaxEffect = 0.65, EffectSeconds = 18,
    -- Visual mood only. No healing, damage, movement bonus or money multipliers.
    CameraEffects = true,
    AdminAce = 'advanced_smoking.admin',
    Shop = {
        id = 'nordlys', label = 'NORDLYS · Smoke & Supply',
        coords = { x = -1172.36, y = -1571.28, z = 4.66 },
        distance = 3.0, blip = true,
        -- Outside Smoke on the Water, Vespucci. No extra MLO dependency.
        stock = 40, limitedStock = 5, wholesaleFraction = 0.60,
    },
    Profiles = {
        cigarette = { scale = 0.16, duration = 1900, pulses = 2, colour = { 0.76, 0.78, 0.81 } },
        cigar = { scale = 0.30, duration = 3000, pulses = 3, colour = { 0.77, 0.75, 0.70 } },
        vape = { scale = 0.65, duration = 3400, pulses = 4, colour = { 0.89, 0.94, 1.0 } },
        joint = { scale = 0.24, duration = 2500, pulses = 3, colour = { 0.75, 0.78, 0.73 } },
        bong = { scale = 0.72, duration = 3100, pulses = 4, colour = { 0.85, 0.90, 0.85 } },
        rig = { scale = 0.85, duration = 3300, pulses = 5, colour = { 0.90, 0.89, 0.97 } },
    },
    Animations = {
        idle = { dict = 'amb@world_human_smoking@male@male_b@base', clip = 'base' },
        puff = { dict = 'amb@world_human_smoking@male@male_a@idle_a', clip = 'idle_c' },
        bong = { dict = 'anim@safehouse@bong', clip = 'bong_stage3' },
        give = { dict = 'mp_common', clip = 'givetake1_a' },
        light = { dict = 'amb@world_human_smoking@male@male_a@enter', clip = 'enter' },
    },
}
```
