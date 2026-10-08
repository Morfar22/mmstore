# Advanced Yacht — Exports and integrations

{% hint style="info" %}
Server exports are for trusted resources. Enforce caller authorization and source/amount checks. Client menu actions are not proof of payment or permission. Internal events are not a public adapter API.
{% endhint %}

Items and money use the bridge. Stashes are a local secured extension: ox_inventory and TGIANN are provided; QB/custom stash support requires an adapter with real open/transfer controls. Framework changes do not migrate yacht ownership or stash contents.

| Export | Side | Arguments | Implementation |
| --- | --- | --- | --- |
| `HasYachtAccess` | server | `src, yachtId` | `server/main.lua` |
| `GetYacht` | server | `yachtId` | `server/main.lua` |

Dynamic exports are described in their specialized integration guides; this literal index is not an exhaustive list of dynamically generated names. Consult [bridge integration](bridge.md) for return contracts and provider limitations, and [internal registrations](events.md) for module routing.
