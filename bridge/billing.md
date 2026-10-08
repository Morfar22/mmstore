# Billing behavior

Billing providers expose different operations. Call GetCapabilities('billing') before selecting an unsupported UI/action.

## framework

The built-in bridge ledger creates persistent player-to-player invoices for QBox, QBCore or ESX, using that framework's money API.
It does not masquerade as a native QBCore invoice resource or integrate an existing phone's invoices automatically.
There is no built-in invoice UI; a product can use CreateInvoice, GetInvoices, PayInvoice and CancelInvoice through its server flow.

Only the target character can pay, only the issuer can cancel a pending invoice. The issuer must be online to receive payment.
Society invoices require another billing adapter. Standalone without a custom economy cannot use this provider.
The journal records processing before external money calls, preventing reentrant duplicate payment.
A restart during processing or an ambiguous money error leaves review status; manual reconciliation is required.
Money and the file journal cannot form an atomic transaction. No automatic retry, compensation or offline credit is attempted
after an ambiguous external operation, because it could duplicate money.

Preserve billing-journal.json when replacing the resource. If the journal is unreadable, framework billing is disabled
instead of overwriting it with an empty ledger. Staff should reconcile review rows against framework transactions before changing them.

## esx_billing

Creation writes the original standard `(identifier,sender,target_type,target,label,amount)` schema using oxmysql.
`options.society` must be the full `society_...` account name. Provision the society and ensure your billing version uses this schema.
Read operations return the original billing rows. Pay through the original native resource; the bridge does not implement a second payment handler.
The standard resource has no public menu export; OpenBilling is unsupported. Use its native menu or register a client adapter for your fork.
No provider client event is used to create invoices with a forged source.

## nrp

Uses the CreateInvoice and PayInvoice contracts from the supplied nrp_core_systems integration.
Provide the account as options.society. Read/cancel operations are unsupported until a custom adapter implements your ledger API.
Provider resource and its own framework/economy dependencies must exist; selecting NRP on ESX does not convert NRP itself.

## okokBilling and other systems

The included okokBilling client adapter dispatches its documented My Invoices UI event. Server invoice creation is intentionally
not routed through its client event: version-specific server adapters should validate and create invoices directly.
Register a billing adapter for your installed provider with create/list/pay/cancel operations, or only the methods actually supported.
The same mechanism works for other phone/framework billing systems. Unsupported methods never claim successful payment.
