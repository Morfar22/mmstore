# Advanced Government — Exports and integrations

{% hint style="info" %}
Server exports are for trusted resources. Enforce caller authorization and source/amount checks. Client menu actions are not proof of payment or permission. Internal events are not a public adapter API.
{% endhint %}

Default native job synchronization is QBox only; QBCore/ESX/standalone use SQL political roles unless custom job sync is configured. Default society settlement still needs NRP resources/schema or an atomic custom society adapter. Payroll tax is an opt-in export, not an automatically installed payroll hook.

| Export | Side | Arguments | Implementation |
| --- | --- | --- | --- |
| `AddSocietyMoney` | server | `jobName, amount` | `server/main.lua` |
| `GetTaxRate` | server | `taxKey` | `server/main.lua` |
| `GetTaxPercent` | server | `taxKey` | `server/main.lua` |
| `GetTreasuryBalance` | server | `` | `server/main.lua` |
| `AddTreasuryMoney` | server | `amount, reason, metadata` | `server/main.lua` |
| `RemoveTreasuryMoney` | server | `amount, reason, metadata` | `server/main.lua` |
| `HasGovernmentPermission` | server | `source, permission` | `server/main.lua` |
| `IsGovernmentEmployee` | server | `source` | `server/main.lua` |
| `WithholdIncomeTax` | server | `source, gross` | `server/nrp_bridge.lua` |

Dynamic exports are described in their specialized integration guides; this literal index is not an exhaustive list of dynamically generated names. Consult [bridge integration](bridge.md) for return contracts and provider limitations, and [internal registrations](events.md) for module routing.
