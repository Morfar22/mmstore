---
description: "Provider setup and migration boundaries for Advanced Orbital."
---

# advanced_orbital

Orbital surveillance/strike resource for FiveM using MM Bridge v0.3.0 or newer.

## Dependencies
- mm_bridge v0.3.0+
- ox_lib
- Selected target provider (ox_target, qb-target, qtarget, or bridge standalone target)
- oxmysql

## Install
1. Import `sql/advanced_orbital.sql`.
2. Put the folder in your resources directory.
3. Add `ensure advanced_orbital` after the dependencies.
4. Edit `shared/config.lua`, especially terminal coordinates, prices, jobs and safe zones.

## Bridge configuration

Select Framework and Target in mm_bridge/config.lua. QBox, QBCore and ESX use the same exported identity/job/money API. ox_target, qb-target, qtarget and the bridge standalone target are supported. Inventory, phone and billing are not used by this resource.

```cfg
ensure ox_lib
ensure oxmysql
# Start your selected framework and target provider here.
ensure mm_bridge
ensure advanced_orbital
```

Standalone requires Framework = 'standalone', Target = 'standalone' (or a supported target), ACE/public access, Config.DefaultPrice = 0 and price = 0 on EVERY terminal. A terminal's explicit price overrides DefaultPrice. Standalone has no native economy: paid strikes fail unless your custom framework adapter implements money. Standalone still requires ox_lib, oxmysql and the SQL table.

Job access checks the active job and grade; it does not authorize inactive QBox multijob memberships. RequireDuty checks the selected framework's active duty field. ESX without a duty field defaults to off-duty unless explicitly configured in the bridge. Public/ACE access is independent of job access.

Existing QBox citizenid values remain unchanged. ESX uses the actual character identifier; standalone uses a license identifier with no character separation. Switching frameworks does not migrate historic SQL rows. Terminal marker/drawSprite settings are provider-specific and are not part of the portable target API.

Restart this resource after bridge/target-provider restarts. Target registration failures are logged with terminal IDs; they never become fake handles. Target filters/UI never authorize strikes: the server rechecks access, session, location, cooldown and pricing.

## ACE example
```cfg
add_ace group.admin advanced_orbital.admin allow
add_ace group.admin advanced_orbital.use allow
```

A terminal can authorize access through active framework jobs, one or more ACE permissions, or `public = true`.

## Modes
- Surveillance: camera only, no firing.
- Manual: ground targeting plus automatic lock when the reticle rests on a networked ped/vehicle.
- Automatic: seeks the nearest valid streamed vehicle around the reticle and follows it once locked.

## Controls
- WASD: move orbital camera
- Shift: fast movement
- Mouse wheel: zoom
- V: normal/night/thermal
- Q: lock/unlock
- Space: request strike
- Backspace: exit

## Security model
Pricing, access, cooldown, daily limits, target validation and safe-zone checks are server-side. Strike requests are written to SQL. A moving network target is resolved again immediately before impact.

## Strike behaviour
- Impact visuals and audio are broadcast to clients instead of existing only on the operator.
- Players inside `Config.Strike.lethalRadius` are selected server-side and receive a lethal hit on their own client.
- All networked vehicles inside `Config.Strike.vehicleDestroyRadius`, including empty vehicles, are marked server-side and destroyed by their owning client.
- Vehicle destruction does **not** use `NetworkExplodeVehicle`, so it cannot spawn the normal GTA vehicle explosion at impact.
- The operator creates only explosion tag 59 (`EXP_TAG_ORBITAL_CANNON`) at the final impact point, alongside GTA's `scr_xm_orbital_blast` effect.

## GTA audio
The resource requests GTA V's built-in `DLC_CHRISTMAS2017/XM_ION_CANNON` audio bank. It uses the orbital cannon activation/background/charge/countdown sounds and the original `DLC_XM_Explosions_Orbital_Cannon` impact sound. No external copyrighted audio files are included.

## Notes
The default terminal and price are examples. The included orbital particle effect uses GTA V's `scr_xm_orbital` / `scr_xm_orbital_blast` asset.

## v1.3.0 — MM Bridge migration
- Identity, character names, active jobs/duty, ACE and money now use MMBridge.
- Terminal creation/removal uses portable bridge target handles.
- Both notification paths use the bridge.
- Payment requires an explicit true confirmation; failed or unsupported mutations cannot trigger a strike.
- Removed hard dependencies on qbx_core and ox_target; added mm_bridge.
- Offline migration tests included; no live GTA/provider validation was performed.

## Validation and existing limits
Run `texlua tests/bridge_spec.lua` from this resource directory. 25 migration tests use mocked FiveM/bridge/SQL calls; 9 Lua files passed syntax compilation. Live camera controls, GTA damage/audio and every provider combination remain untested. SQL logging and framework payment are separate operations, not an atomic transaction; an SQL failure after a successful charge still requires staff reconciliation, as in the original implementation. Daily limits use SQL counts and are not a global transaction lock across concurrent users.

## v1.2.0
- Fixed orbital strikes not reliably destroying vehicles.
- Added server-side vehicle-radius enumeration plus replicated state-bag destruction for network ownership safety.
- Empty vehicles can now be destroyed as well as occupied vehicles.
- Removed `NetworkExplodeVehicle`, which caused the normal GTA vehicle explosion.
- Impact world explosion is hard-locked to GTA explosion tag 59 (`EXP_TAG_ORBITAL_CANNON`).
- Added stronger physical vehicle damage and radial force without adding a second explosion type.

## v1.1.0
- Fixed strikes not reliably killing remote players.
- Added server-selected lethal blast radius.
- Added synced impact event for targets and nearby players.
- Added GTA orbital activation, background, charge, countdown and impact audio.
- Added vehicle destruction for struck occupants.
- Added impact camera shake for nearby players.

## Original implementation
This resource was written from scratch from publicly described functionality. It does not contain SOSOMODS source code, escrowed files, or proprietary assets.
