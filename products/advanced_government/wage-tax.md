# Government — Payroll tax



WithholdIncomeTax(source,grossWage) now uses numeric source through the bridge, not a citizenid passed to a source-only money API. It is a SERVER export for a trusted payroll resource after successful gross wage payment. Only exact resource names in Config.IncomeTaxOwners are accepted.

```lua
-- In the authorized payroll resource AFTER confirmed gross payout:
local withheld = exports.advanced_government:WithholdIncomeTax(source, grossWage)
```

The export does not install payroll hooks automatically. Preserve an existing QBox wage hook if already installed. Add an explicit hook in QB/ESX payroll if desired and authorize its exact resource name. Other tax exports remain opt-in integrations; displaying a rate does not tax unrelated scripts automatically.

A treasury failure attempts an online refund to the same character. Replacement/disconnected characters are not credited accidentally; unconfirmed credits are logged for manual reconciliation. No offline money API is invented.
