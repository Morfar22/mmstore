# Advanced Government — Exports and integrations

## Server exports

| Export | Parameters | Result / behavior |
| --- | --- | --- |
| GetTaxRate | taxKey | Fraction, e.g. 0.18; missing rate 0 |
| GetTaxPercent | taxKey | Percentage, e.g. 18 |
| GetTreasuryBalance | none | Current balance |
| AddTreasuryMoney | amount, reason, metadata | Treasury transfer result; does not itself withdraw a payer |
| RemoveTreasuryMoney | amount, reason, metadata | Treasury transfer result; does not itself credit a recipient |
| AddSocietyMoney | jobName, amount | Credits NRP shared account directly; no treasury debit in this export |
| GetMayor | none | Current office row or no active mayor |
| HasGovernmentPermission | source, permission | Permission check |
| IsGovernmentEmployee | source | Current mayor/cabinet membership |
| WithholdIncomeTax | source, gross | Tax charged; only invoking resource qbx_core accepted |

```lua
-- SERVER: read one rate.
local fraction = exports.advanced_government:GetTaxRate('income')
local percent = exports.advanced_government:GetTaxPercent('income')
```

Amounts must be positive finite integers within MaxTransactionAmount. Add/RemoveTreasuryMoney operate the treasury ledger, not a complete standalone bank exchange. GetMayor returns government_office data; distinguish SQL row/term metadata from a player object.

See the wage integration guide before calling WithholdIncomeTax. Budget/tax UI alone does not patch any wage or purchase script. Internal callbacks validate caller/permission/inputs and are listed for maintainers, not as a public grant/award API.

Source: export declarations and loaded framework/inventory/billing bridges in the supplied product.
