# Advanced Cablecar — Exports and integrations

{% hint style="info" %}
Server exports are for trusted resources. Enforce caller authorization and source/amount checks. Client menu actions are not proof of payment or permission. Internal events are not a public adapter API.
{% endhint %}

Optional targets still call ox_target directly. Ticket-machine proximity interactions work without a target provider. Config.Framework='standalone' explicitly skips fares; legacy 'qbox' selects paid bridge behavior. Framework selection in mm_bridge does not override this resource fare setting.

| Export | Side | Arguments | Implementation |
| --- | --- | --- | --- |
| `HasCableCarTicket` | server | `source` | `server/main.lua` |

Dynamic exports are described in their specialized integration guides; this literal index is not an exhaustive list of dynamically generated names. Consult [bridge integration](bridge.md) for return contracts and provider limitations, and [internal registrations](events.md) for module routing.
