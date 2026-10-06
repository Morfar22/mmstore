# Government — Wage tax integration

Changing income percent in the UI does not install a QBox payroll hook. The archive contains the export but not a modified QBox core. The calling resource must be qbx_core, otherwise WithholdIncomeTax returns 0.

Illustrative insertion inside your existing QBox payroll code, **after** successful gross bank deposit:

```lua
-- Inside qbx_core only. Match your payroll's actual variables.
-- Do not repeat the existing wage deposit here.
if GetResourceState('advanced_government') == 'started' then
    local withheld = exports.advanced_government:WithholdIncomeTax(playerSource, grossWage)
    -- Optional: use withheld for the wage receipt/notification.
end
```

Do not paste this without matching the real payroll success branch/variables. No framework file was modified by this documentation task. Call once per paid wage; there is no unique external payroll receipt key in the export to make duplicate arbitrary invocations safe.

The export reads persisted income rate, floors gross*rate/100, removes tax from bank, credits treasury via Gov.transfer, and attempts a refund if treasury transfer fails. It returns actual withholding or 0. It accepts positive integer gross values under MaxTransactionAmount.

At supplied 18% rate, gross 10,000 produces tax 1,800, net bank increase 8,200 and treasury increase 1,800. Test one payer, offline/disconnect/failure paths and console receipts on staging. Disable unrelated income-tax mechanisms to prevent double withholding. Other purchase/tax types require their own integrations using the rate/treasury APIs; they are not automatically charged.
