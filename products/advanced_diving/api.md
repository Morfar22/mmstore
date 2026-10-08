# Advanced Diving — Exports and integrations

{% hint style="info" %}
Server exports are for trusted resources. Enforce caller authorization and source/amount checks. Client menu actions are not proof of payment or permission. Internal events are not a public adapter API.
{% endhint %}

This release still directly requires ox_target for its job NPC. Choosing qb-target/qtarget in mm_bridge does not replace that integration. Optional gear checks use the bridge; gear is not consumed. Failed crew payout completes progression with zero credited earnings and requires reconciliation.

| Export | Side | Arguments | Implementation |
| --- | --- | --- | --- |
| No literal export definitions found | — | — | — |

Dynamic exports are described in their specialized integration guides; this literal index is not an exhaustive list of dynamically generated names. Consult [bridge integration](bridge.md) for return contracts and provider limitations, and [internal registrations](events.md) for module routing.
