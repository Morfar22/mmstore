# Advanced Poolcleaner — Exports and integrations

{% hint style="info" %}
Server exports are for trusted resources. Enforce caller authorization and source/amount checks. Client menu actions are not proof of payment or permission. Internal events are not a public adapter API.
{% endhint %}

Optional item requirements default to Inventory.mode='none'. Select mode='bridge' for generic bridge inventory reads. Required item mutations and payouts must be confirmed; failed payout completes progression but records zero earnings and needs staff reconciliation.

| Export | Side | Arguments | Implementation |
| --- | --- | --- | --- |
| No literal export definitions found | — | — | — |

Dynamic exports are described in their specialized integration guides; this literal index is not an exhaustive list of dynamically generated names. Consult [bridge integration](bridge.md) for return contracts and provider limitations, and [internal registrations](events.md) for module routing.
