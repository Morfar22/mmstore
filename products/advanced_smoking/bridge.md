# Smoking — Bridge integration

Configure common framework, inventory and target providers in mm_bridge. Requires mm_bridge 0.3.0+, ox_lib and oxmysql. Keep the resource name advanced_smoking and the existing nrp_smoking_* SQL tables.

## Item-use contract

Full Smoking requires an inventory with authoritative individual slots and persistent metadata. ox_inventory, TGIANN and qb-inventory use the bridge for reads, counts, capacity, item mutations and metadata. Plain ESX inventory and standalone without a suitable inventory cannot support full product state. Framework selection does not convert an inventory into a standalone resource.

Merge install/ox_items.lua into ox_inventory's item definitions. consume=0 and stack=false are required because Smoking owns consumption. The client export advanced_smoking.useItem receives the slot/name and requests server validation. QB definitions are in install/qb_items.lua with unique/useable settings; verify the installed inventory's use flow. TGIANN item schemas differ by version: keep compatible entries and connect the supplied use export rather than assuming the QB template imports unchanged.

Metadata includes product UID, serial, usage, battery/liquid, condition, water and loans. Do not stack independently tracked products. Item images are not supplied.

## Local storage extension

The central bridge has no generic stash API. server/bridge.lua provides secured ox_inventory/TGIANN stash integrations that follow the selected inventory. Config.Storage.resources must match real resource names. Native opening and item-transfer hooks are required; a provider without those hooks leaves containers locked.

QB/custom inventories can use regular Smoking items but need a safe local container adapter. Config.Storage.enabled=false disables case/humidor storage without disabling other item use.

Config.Storage.custom is a trusted SERVER table:

| Method | Required behavior |
| --- | --- |
| resource | Optional resource name; must be started if provided |
| install(check, allowed) | Install native opening AND transfer authorization; return true only when installed |
| register(data) | Confirm real registration; data contains name,label,slots,maxWeight in grams and whitelist |
| open(source,data) | Use the provider server API; return confirmed true for accepted handoff, false on failure |

check(source,stashID) returns true/false for Smoking stashes and nil for unrelated inventories. allowed(itemName) enforces the Smoking whitelist. The adapter must enforce authorization even when a client opens the provider UI directly. Do not return true from install merely to unlock storage. Provider restart requires hooks again and consumer restart.

## Money, refunds and reconciliation

Shop money and SQL writes are separate operations. Confirm a refund only on true from the bridge. Unconfirmed refunds are recorded in shopdata.review for staff reconciliation.

Owner withdrawal reserves funds and writes a processing record before attempting credit. Confirmed credit becomes paid; unconfirmed credit becomes review. A processing record after a crash also requires review. Funds are not automatically released or retried after an ambiguous result because the external provider may have credited the player already. Review nrp_smoking_shops.data against actual provider transactions before replaying/releasing money. No automatic review UI or retry queue is included.

## Identity and restart behavior

Existing QBox citizen IDs and nrp_smoking_UID stash names remain. ESX uses real character identifiers; standalone licenses do not separate characters. Changing framework or inventory does not migrate profiles, ownership or stash contents.

Restart Smoking after bridge/target/inventory restarts. Existing audit events remain optional. Validate normal items, accessories, sharing/loans, containers, full inventory and failed payment against the installed provider version on staging.
