# Advanced Smoking — Exports and integrations

{% hint style="info" %}
Server exports are for trusted resources. Enforce caller authorization and source/amount checks. Client menu actions are not proof of payment or permission. Internal events are not a public adapter API.
{% endhint %}

Full item use requires individual slots and persistent metadata. Plain ESX inventory and standalone without a suitable inventory cannot run the full system. QB inventory supports ordinary items; containers remain locked until a safe local stash adapter is configured. Shop credits marked processing/review require reconciliation.

| Export | Side | Arguments | Implementation |
| --- | --- | --- | --- |
| `useItem` | client | `data,slot` | `client/main.lua` |

Dynamic exports are described in their specialized integration guides; this literal index is not an exhaustive list of dynamically generated names. Consult [bridge integration](bridge.md) for return contracts and provider limitations, and [internal registrations](events.md) for module routing.
