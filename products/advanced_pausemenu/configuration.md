---
description: "Current configuration excerpts for Advanced Pausemenu."
---

# Advanced Pausemenu — Configuration

Select common providers in [mm_bridge](../../bridge/configuration.md). These excerpts come from the delivered **5.2.0** configuration. Edit gameplay settings in the resource, not the shared bridge. SQL records may override initial defaults.

## Config

Source file: `config.lua`.

```lua
Config = {}
```

## Config.ServerName

Source file: `config.lua`.

```lua
Config.ServerName = 'NORDISK RP'
```

## Config.ServerTagline

Source file: `config.lua`.

```lua
Config.ServerTagline = 'ROLEPLAY'
```

## Config.ReplaceDefaultPause

Source file: `config.lua`.

```lua
Config.ReplaceDefaultPause = true

-- Theme follows the Nordisk RP purple used elsewhere on the server.
```

## Config.Theme

Source file: `config.lua`.

```lua
Config.Theme = {
    accent = '#57007F',
    accentSoft = '#8A32B2',
    success = '#46D389',
    danger = '#F45B69',
}
```

## Config.Blur

Source file: `config.lua`.

```lua
Config.Blur = true
```

## Config.Services

Source file: `config.lua`.

```lua
Config.Services = {
    { job = 'police', label = 'POLITI' },
    { job = 'ambulance', label = 'EMS' },
}
```

## Config.Inventory

Source file: `config.lua`.

```lua
Config.Inventory = {
    enabled = true,
    command = 'inventory', -- exact command registered by YOUR inventory resource
    open = nil, -- optional client function() returning true only on confirmed opening
    getWeight = nil, -- optional client function() returning current,max in grams
    allowWithoutInventory = false, -- enable only for a custom UI without a bridge inventory adapter
}
```

## Config.Commands

Source file: `config.lua`.

```lua
Config.Commands = {
    { label = 'Telefon', command = 'phone', description = 'Åbn din telefon.' },
    { label = 'Emotes', command = 'emotes', description = 'Åbn emote-menuen.' },
    { label = 'ID', command = 'id', description = 'Vis dit server-ID.' },
}
```

## Config.FAQ

Source file: `config.lua`.

```lua
Config.FAQ = {
    {
        category = 'Generelt',
        question = 'Hvordan åbner jeg mit inventory?',
        answer = 'Brug inventory-kortet i ESC-menuen eller din normale inventory-tast.'
    },
    {
        category = 'Roleplay',
        question = 'Hvor finder jeg serverens regler?',
        answer = 'Regler og øvrig information findes på Nordisk RP Discord.'
    },
    {
        category = 'Support',
        question = 'Jeg sidder fast eller noget er gået i stykker. Hvad gør jeg?',
        answer = 'Opret en support-ticket på Discord og beskriv problemet så præcist som muligt.'
    },
}
```

## Config.Updates

Source file: `config.lua`.

```lua
Config.Updates = {
    {
        date = '03.10.2026',
        title = 'Ny ESC-menu',
        text = 'Nordisk RP har fået en helt ny responsiv ESC-menu med direkte adgang til kort, inventory og serverinfo.'
    },
    {
        date = '01.10.2026',
        title = 'Serverforbedringer',
        text = 'Flere systemer er blevet optimeret og opdateret frem mod åbningen.'
    },
}
```

## Config.Waypoints

Source file: `config.lua`.

```lua
Config.Waypoints = {
    { label = 'Mission Row PD', x = 425.13, y = -979.56 },
    { label = 'Pillbox Hospital', x = 307.14, y = -595.31 },
    { label = 'Bennys', x = -211.55, y = -1324.55 },
    { label = 'Legion Square', x = 215.76, y = -810.12 },
}
```
