# Advanced Pausemenu — Configuration

Edit the indicated config file and restart the resource after changes. Values are the exact uploaded defaults, not proposed settings. SQL-backed ownership, tax rates, stock and placement may override or outlive config seed values. Comments below are retained as source context and can include legacy notes; the usage/setup pages explain important current behavior.

All Config assignments in the supplied file are included. Vet pharmacy excerpts omit real-world dose/label fields; use the medicine guide for FiveM effects. Do not apply RP values as real treatment instructions.

## Config.ServerName

Pause menu branding; change shipped NORDISK RP text.

Source: `config.lua`, line 3.

```lua
Config.ServerName = 'NORDISK RP'
```


## Config.ServerTagline

Controls server tagline. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 4.

```lua
Config.ServerTagline = 'ROLEPLAY'
```


## Config.ReplaceDefaultPause

Controls replace default pause. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 5.

```lua
Config.ReplaceDefaultPause = true

-- Theme follows the Nordisk RP purple used elsewhere on the server.
```


## Config.Theme

Controls theme. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 8.

```lua
Config.Theme = {
    accent = '#57007F',
    accentSoft = '#8A32B2',
    success = '#46D389',
    danger = '#F45B69',
}
```


## Config.Blur

Controls blur. The source excerpt below shows the exact supplied value and inline units/comments; verify usage against the product guide before changing it.

Source: `config.lua`, line 15.

```lua
Config.Blur = true
```


## Config.Services

Pause menu exact service job names.

Source: `config.lua`, line 17.

```lua
Config.Services = {
    { job = 'police', label = 'POLITI' },
    { job = 'ambulance', label = 'EMS' },
}
```


## Config.Inventory

Actual inventory adapter/requirements; string/provider alone does not implement a new adapter.

Source: `config.lua`, line 22.

```lua
Config.Inventory = {
    resource = 'ox_inventory',
    fallbackCommand = 'inventory',
}
```


## Config.Commands

Player/staff command names; actual registrations are in the commands guide/reference.

Source: `config.lua`, line 27.

```lua
Config.Commands = {
    { label = 'Telefon', command = 'phone', description = 'Åbn din telefon.' },
    { label = 'Emotes', command = 'emotes', description = 'Åbn emote-menuen.' },
    { label = 'ID', command = 'id', description = 'Vis dit server-ID.' },
}
```


## Config.FAQ

Pause menu content entries; translate/customize.

Source: `config.lua`, line 33.

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

Pause menu editorial update entries, not automatic changelog fetching.

Source: `config.lua`, line 51.

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

Pause menu GPS destinations.

Source: `config.lua`, line 64.

```lua
Config.Waypoints = {
    { label = 'Mission Row PD', x = 425.13, y = -979.56 },
    { label = 'Pillbox Hospital', x = 307.14, y = -595.31 },
    { label = 'Bennys', x = -211.55, y = -1324.55 },
    { label = 'Legion Square', x = 215.76, y = -810.12 },
}
```
