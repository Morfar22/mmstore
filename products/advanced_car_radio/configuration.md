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

## Config.OpenCommand

Controls open command. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 6.

```lua
Config.OpenCommand = 'carradio'
```

## Config.DefaultKey

Controls default key. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 7.

```lua
Config.DefaultKey = 'F7'
```

## Config.RequireVehicle

Controls require vehicle. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 8.

```lua
Config.RequireVehicle = true
```

## Config.RequireDriverToControl

Controls require driver to control. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 9.

```lua
Config.RequireDriverToControl = false
```

## Config.AllowPassengers

Controls allow passengers. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 10.

```lua
Config.AllowPassengers = true

-- xSound / 3D audio
```

## Config.MaxDistance

Controls max distance. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 13.

```lua
Config.MaxDistance = 32.0
```

## Config.ActivationDistance

Controls activation distance. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 14.

```lua
Config.ActivationDistance = 48.0
```

## Config.PositionRefreshMs

Controls position refresh ms. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 15.

```lua
Config.PositionRefreshMs = 250
```

## Config.DefaultVehicleVolume

Controls default vehicle volume. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 16.

```lua
Config.DefaultVehicleVolume = 0.65

-- How much of a vehicle radio leaks outside the cabin.
-- 1.0 = full radio volume, 0.0 = silent outside.
-- The listener's own inside/outside volume setting is applied afterwards.
```

## Config.CabinLeakage

Source vehicle sound leakage multipliers, independent of listener volumes.

Source: `shared/config.lua`, line 21.

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

Per-character listening preferences and Now Playing.

Source: `shared/config.lua`, line 34.

```lua
Config.DefaultSettings = {
    ownVolume = 1.00,
    insideOtherVolume = 0.28,
    outsideOtherVolume = 0.55,
    showNowPlaying = true
}
```

## Config.NowPlayingDurationMs

Controls now playing duration ms. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 41.

```lua
Config.NowPlayingDurationMs = 6500
```

## Config.PersistenceIntervalSeconds

Controls persistence interval seconds. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 42.

```lua
Config.PersistenceIntervalSeconds = 15
```

## Config.ResumeAfterRestart

Controls resume after restart. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 43.

```lua
Config.ResumeAfterRestart = true
```

## Config.MaxPlaylists

Controls max playlists. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 45.

```lua
Config.MaxPlaylists = 30
```

## Config.MaxTracksPerPlaylist

Controls max tracks per playlist. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 46.

```lua
Config.MaxTracksPerPlaylist = 250
```

## Config.MaxSavedTracksPerVehicle

Controls max saved tracks per vehicle. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 47.

```lua
Config.MaxSavedTracksPerVehicle = 150
```

## Config.MaxQueueSize

Controls max queue size. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 48.

```lua
Config.MaxQueueSize = 250

-- Easy metadata lookup for pasted YouTube links. No API key required.
```

## Config.ResolveYouTubeMetadata

Controls resolve you tube metadata. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 51.

```lua
Config.ResolveYouTubeMetadata = true

-- Empty = allow any http/https media URL. If you want a whitelist, add hosts here.
-- Example: { ['youtube.com'] = true, ['www.youtube.com'] = true, ['youtu.be'] = true }
```

## Config.AllowedHosts

Media URL host allowlist; empty accepts valid HTTP/HTTPS.

Source: `shared/config.lua`, line 55.

```lua
Config.AllowedHosts = {}
```

## Config.MaxUrlLength

Controls max url length. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 56.

```lua
Config.MaxUrlLength = 1024
```

## Config.MaxTitleLength

Controls max title length. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 57.

```lua
Config.MaxTitleLength = 160
```

## Config.MaxArtistLength

Controls max artist length. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 58.

```lua
Config.MaxArtistLength = 120
```

## Config.MaxArtworkLength

Controls max artwork length. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 59.

```lua
Config.MaxArtworkLength = 1024

-- If true, /carradio only opens for the driver. Independent from control permissions.
```

## Config.DriverOnlyOpen

Controls driver only open. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `shared/config.lua`, line 62.

```lua
Config.DriverOnlyOpen = false
```
