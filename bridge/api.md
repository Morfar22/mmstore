# Public API

Consumers load `@mm_bridge/init.lua` after `@ox_lib/init.lua` in shared_scripts and declare `dependency 'mm_bridge'`.
Use `MMBridge.Method(...)` or `exports.mm_bridge:Method(...)`. Version 0.3 preserves the migrated products' original methods.

## Server methods

| Method | Arguments | Return |
| --- | --- | --- |
| GetStatus | none | Provider names, readiness, errors, version |
| GetCapabilities | kind | provider and operations map, or nil/error |
| RegisterAdapter | kind, name, adapter | true or false/error |
| GetPlayer | source | Native QBox/QBCore player or ESX/standalone compatibility view, nil/error |
| GetNativePlayer | source | Native framework player, nil/error; standalone unsupported |
| GetCharacterId | source | Real character ID, nil/error |
| GetPlayerName | source | Character display name, nil/error |
| GetJob | source | name, label, numeric grade, onDuty, isBoss; nil/error |
| HasJob | source, name, minimumGrade?, requireDuty? | boolean, error? |
| HasAce / IsStaff | source, ace / source | boolean, error? |
| GetMoney | source, cash/bank/crypto | number or nil/error |
| AddMoney / RemoveMoney | source, account, positiveInteger, reason? | boolean, error? |
| GetItems | source | array of name, label, count, slot, metadata; nil/error |
| GetItemBySlot | source, slot | item, nil/error |
| GetItemCount | source, item, metadata? | total or nil/error |
| CanCarryItem | source, item, count, metadata? | boolean, error? |
| AddItem / RemoveItem | source, item, count, metadata?, slot? | boolean, error? |
| SetItemMetadata | source, slot, newMetadata, expectedMetadata? | boolean, error? |
| RegisterUsableItem | name, handler(source, nativeItem?) | boolean, error? |
| Notify | source, ox_lib notification | boolean, error? |
| GetPhoneNumber | source | string or nil/error |
| SendPhoneNotification | source, notification | provider receipt, nil/error |
| CreateInvoice | issuerSource, targetSource, amount, description, options? | invoice receipt, nil/error |
| GetInvoices | source | provider list, nil/error |
| PayInvoice / CancelInvoice | source, provider invoice ID | boolean, error? |

Kinds: framework, inventory, target, phone, billing. Capabilities report adapter method names documented
in custom-adapters.md. They differ on client/server; unsupported operations explicitly return `unsupported_operation`.
Server target status is configuration only; client GetStatus evaluates actual target adapters.

Sources and quantities must be numeric integers. Money amounts must be positive, finite, within configured limits.
Invalid inputs and missing providers never count as successful money/item mutations. ESX void money/item mutators
are confirmed by comparing before/after state. Metadata updates are confirmed by reading the slot back.

GetPlayer is a compatibility view for existing consumers, not a promise of QBox Player.Functions on ESX.
ESX job duty defaults to false when unavailable; explicitly choose EsxAssumeDuty if your server has no duty system.
ESX cash maps to the money account. Crypto is disabled by default; map only an actual account that exists.

Metadata filters are recursive partial matches. TGIANN and QB removal with metadata requires a specific slot,
checked before provider removal. These checks do not reserve capacity or lock slots; serialize multi-step purchases in the consumer.
Native ESX inventory refuses slot and metadata operations instead of silently dropping those fields.

## Client methods

| Method | Arguments | Return |
| --- | --- | --- |
| GetStatus / GetCapabilities / RegisterAdapter | as above | Client-scoped status/capabilities/registration |
| Notify | notification table | true or false/error |
| Progress | ox_lib progressCircle options | Completion/cancellation result |
| InputDialog | title, rows, options? | Input rows or nil |
| AddTargetZone | spec, options | Owned handle or nil/error |
| RemoveTargetZone | handle | boolean, error? |
| AddTargetEntity | localEntity, options, distance? | Owned handle or nil/error |
| RemoveTargetEntity | handle | boolean, error? |
| GetPhoneNumber / OpenPhone | none | Provider result, nil/error |
| SendPhoneNotification | notification | Provider receipt, nil/error |
| OpenBilling | none | Provider result, nil/error |

Target spec: `{name?, shape='sphere'|'box', coords=vector3, radius?, size=vector3?, rotation?, distance?, debug?}`.
Options: `{name?, label, icon?, onSelect(data)?, event?, serverEvent?, canInteract(entity,distance,data)?, jobs?, items?}`.
Use exactly one action. Portable item filters are strings; ox supports its own additional item table format.
For standalone, implement filters through canInteract; jobs/items are refused instead of ignored.
Use callbacks for portable behavior and validate every authoritative server action independently.
Handle removal is owner-scoped and attached to the original adapter even if configuration changes.
Restart consumers after target-provider restarts. QB/qtarget entity removal uses labels; avoid identical labels for different
resources on the same entity. Shape mapping uses native provider semantics; sphere/circle behavior is not geometrically identical.

There are no generic client-callable billing or money mutation endpoints. Consumers must validate permissions,
amounts, proximity and source before calling the server API. Notification, status, capability and own-phone-number
callbacks are the only built-in network surfaces. UI progress and target filters never authorize server actions.
