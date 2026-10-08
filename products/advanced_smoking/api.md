# Exports and integrations

Client export useItem(data, slot) is an inventory entrypoint. It extracts selected name/slot, requests advanced\_smoking:action and returns whether the existing use flow accepted it. Configure inventory client.export = 'advanced\_smoking.useItem' according to your TGIANN definition format; do not replace the server's slot validation with client-trusted metadata.

Replicated state key nrp:smoking describes the current visible session. Product data lives in shared/catalog.lua and info.smoking preserves UID/remaining/battery/liquid/condition/water/loan/serial information. Stashes use nrp\_smoking\_. Native TGIANN open/swap hooks protect ownership and allowed contents.

Optional audit calls are guarded when nrp\_core\_systems is absent; basic Smoking is not a hard NRP dependency. Database and inventory writes are separate; recovery journals are not one universal ACID transaction across both systems. There is no generic server export to grant arbitrary smoke bonuses.

Source: export declarations and loaded framework/inventory/billing bridges in the supplied product.
