---
description: "Current configuration excerpts for Advanced Car Radio."
---

# Advanced Car Radio — Configuration

Select common providers in [mm_bridge](../../bridge/configuration.md). These excerpts come from the delivered **1.2.0** configuration. Edit gameplay settings in the resource, not the shared bridge. SQL records may override initial defaults.

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
```

## Config.OpenCommand

Source file: `shared/config.lua`.

```lua
Config.OpenCommand = 'carradio'
```

## Config.DefaultKey

Source file: `shared/config.lua`.

```lua
Config.DefaultKey = 'F7'
```

## Config.RequireVehicle

Source file: `shared/config.lua`.

```lua
Config.RequireVehicle = true
```

## Config.RequireDriverToControl

Source file: `shared/config.lua`.

```lua
Config.RequireDriverToControl = false
```

## Config.AllowPassengers

Source file: `shared/config.lua`.

```lua
Config.AllowPassengers = true

-- xSound / 3D audio
```

## Config.MaxDistance

Source file: `shared/config.lua`.

```lua
Config.MaxDistance = 32.0
```

## Config.ActivationDistance

Source file: `shared/config.lua`.

```lua
Config.ActivationDistance = 48.0
```

## Config.PositionRefreshMs

Source file: `shared/config.lua`.

```lua
Config.PositionRefreshMs = 250
```

## Config.DefaultVehicleVolume

Source file: `shared/config.lua`.

```lua
Config.DefaultVehicleVolume = 0.65

-- How much of a vehicle radio leaks outside the cabin.
-- 1.0 = full radio volume, 0.0 = silent outside.
-- The listener's own inside/outside volume setting is applied afterwards.
```

## Config.CabinLeakage

Source file: `shared/config.lua`.

```lua
Config.CabinLeakage = {
    enabled = true,
    closed = 0.20,          -- all doors/windows closed
    oneWindowOpen = 0.55,   -- one open/broken window
    extraWindowStep = 0.12, -- added for each extra open/broken window
    maxWindowsOpen = 0.90,  -- cap when several windows are open
    doorOpen = 1.00,        -- any passenger door physically open
    convertibleOpen = 1.00, -- convertible roof down/opening/closing
    openVehicle = 1.00,     -- motorcycles, bicycles, boats etc.
    doorAngleThreshold = 0.08
}

-- Personal listener volumes. These do not change what other players hear.
```

## Config.DefaultSettings

Source file: `shared/config.lua`.

```lua
Config.DefaultSettings = {
    ownVolume = 1.00,
    insideOtherVolume = 0.28,
    outsideOtherVolume = 0.55,
    showNowPlaying = true
}
```

## Config.NowPlayingDurationMs

Source file: `shared/config.lua`.

```lua
Config.NowPlayingDurationMs = 6500
```

## Config.PersistenceIntervalSeconds

Source file: `shared/config.lua`.

```lua
Config.PersistenceIntervalSeconds = 15
```

## Config.ResumeAfterRestart

Source file: `shared/config.lua`.

```lua
Config.ResumeAfterRestart = true
```

## Config.MaxPlaylists

Source file: `shared/config.lua`.

```lua
Config.MaxPlaylists = 30
```

## Config.MaxTracksPerPlaylist

Source file: `shared/config.lua`.

```lua
Config.MaxTracksPerPlaylist = 250
```

## Config.MaxSavedTracksPerVehicle

Source file: `shared/config.lua`.

```lua
Config.MaxSavedTracksPerVehicle = 150
```

## Config.MaxQueueSize

Source file: `shared/config.lua`.

```lua
Config.MaxQueueSize = 250

-- Easy metadata lookup for pasted YouTube links. No API key required.
```

## Config.ResolveYouTubeMetadata

Source file: `shared/config.lua`.

```lua
Config.ResolveYouTubeMetadata = true

-- Empty = allow any http/https media URL. If you want a whitelist, add hosts here.
-- Example: { ['youtube.com'] = true, ['www.youtube.com'] = true, ['youtu.be'] = true }
```

## Config.AllowedHosts

Source file: `shared/config.lua`.

```lua
Config.AllowedHosts = {}
```

## Config.MaxUrlLength

Source file: `shared/config.lua`.

```lua
Config.MaxUrlLength = 1024
```

## Config.MaxTitleLength

Source file: `shared/config.lua`.

```lua
Config.MaxTitleLength = 160
```

## Config.MaxArtistLength

Source file: `shared/config.lua`.

```lua
Config.MaxArtistLength = 120
```

## Config.MaxArtworkLength

Source file: `shared/config.lua`.

```lua
Config.MaxArtworkLength = 1024

-- If true, /carradio only opens for the driver. Independent from control permissions.
```

## Config.DriverOnlyOpen

Source file: `shared/config.lua`.

```lua
Config.DriverOnlyOpen = false
```
