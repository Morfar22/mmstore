# Custom adapters

Add registrations to custom/server/*.lua or custom/client/*.lua. These load after built-in providers and before the public API. Register using MMBridgeRegistry.register(kind, name, adapter). Select that unique name in config.lua. Client and server registries are separate; register each required side.

A separate resource can use exports.mm_bridge:RegisterAdapter(kind, name, adapter). Add its exact resource name to MMBridgeConfig.CustomAdapterOwners, declare dependency 'mm_bridge', and start it before consuming scripts. A dependency starts the bridge first; consumers depending on this custom provider must also start after its adapter resource. Registrations disappear when their owner stops. Re-register on adapter startup and after a bridge restart; restart consumers after providers. Built-in names cannot be overwritten. Auto selection scans built-in candidates only, so explicitly select a custom provider.

## Contracts

Adapters are trusted server code. available() is optional and returns true only when operational. Omit unsupported functions; do not fabricate successes. Read failures return nil,error; mutations return true only when confirmed, otherwise false,error. The bridge catches provider exceptions as provider_error. The following are adapter method names, not public export names.

| Kind / side | Methods |
| --- | --- |
| Framework / server | getPlayer(source), getNativePlayer(source), getMoney(source,account), changeMoney(source,account,amount,reason,remove), registerUsable(name,handler) |
| Inventory / server | getItems(source), canCarry(source,name,count,metadata), addItem(source,name,count,metadata,slot), removeItem(source,name,count,metadata,slot), setMetadata(source,name,slot,metadata) |
| Target / client | addZone(spec,options), removeZone(providerHandle), addEntity(entity,options,distance), removeEntity(entity,optionNames,optionLabels,providerHandle) |
| Phone / server | getNumber(source), notify(source,data) |
| Phone / client | getNumber(), open(), notify(data) |
| Billing / server | create(issuerSource,targetSource,amount,description,options), list(source), pay(source,id), cancel(source,id) |
| Billing / client | open() |

getPlayer must return {PlayerData={source=source,citizenid='real-character-id',charinfo={firstname='...',lastname='...'},job={name='...',grade={level=0},onduty=false,isboss=false},money={}}}. Character IDs must be stable and distinguish characters where supported. Native player access belongs in getNativePlayer. Never expose a made-up balance.

Inventory getItems returns a table of entries with name, count/amount, slot (when supported), metadata/info. Set metadataRequiresSlot=true when your provider cannot remove a filtered item without a slot. setMetadata must support readback; the public API verifies it. Capacity checks are advisory; consumers must serialize their own multi-step transactions.

Target methods receive validated, owner-namespaced spec/options. addZone returns a provider handle; addEntity must return a handle or true. Removal must return true on confirmed cleanup. onSelect receives {entity,coords?,distance?,option?}; coords/distance can be absent on QB/qtarget. Targets must implement jobs/items or refuse unsupported filters. Custom targets must clean their physical zones/entities when their adapter resource stops; the bridge cannot call an unavailable owner after its resource stops.

Billing create returns a receipt table, list an array, and pay/cancel confirmed booleans. Validate ownership and provider authorization inside the adapter. Client menus and dispatched events never prove payment. Support native society accounts only when your provider implements them. Framework billing can use a custom economy framework if it implements identity and money contracts.

Phone getNumber returns a string. notify/open return a receipt (or true for open), and must distinguish dispatch from delivery. Signature differences should be translated inside your adapter, rather than forcing another provider's API on your phone.

## Minimal external phone example

```lua
-- my_mm_adapters/server.lua; dependency 'mm_bridge' in its fxmanifest.lua
local function register()
    local ok, err = exports.mm_bridge:RegisterAdapter('phone', 'my_phone', {
        available = function() return GetResourceState('your_phone') == 'started' end,
        getNumber = function(src)
            -- Replace with the installed phone's documented server export.
            return exports.your_phone:GetPhoneNumber(src)
        end
    })
    assert(ok, err)
end
AddEventHandler('onResourceStart', function(resource)
    if resource == GetCurrentResourceName() or resource == 'mm_bridge' then register() end
end)
```

Set CustomAdapterOwners = { ['my_mm_adapters'] = true } and Phone = 'my_phone' in the bridge config. Export names in this example are placeholders. The configured export phone adapter is preferable if its documented signatures already match; see phones.md.

Do not add generic unvalidated network endpoints for these exports. Consumer server handlers must enforce permission, proximity, source and amount before invoking the bridge.
