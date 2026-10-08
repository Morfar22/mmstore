# Shop, ownership and storage

Stock seeds 40 per regular product and 5 per limited product once; saved shop stock/prices/staff/cash persist thereafter. Ownership assignment uses an online server ID. Ownership changes preserve existing inventory/staff. No automatic framework/society job is created.

Owner manages employees by citizenid, prices and withdrawal to bank. Employees order ordinary stock from their own bank; limited restock requires the manager/admin checks. The store is a configured point/UI with no new MLO.

Cases/humidor use unique nrp\_smoking\_ native stashes with slots/maxWeight and smoking-product whitelist. Humidor is owner-private; placed glass supports use and owner pickup. Container content weight is not automatically added to the carried case item's fixed weight. Loan/return recovery and prop placement use DB journals; SQL and inventory are still separate storage systems.

World props retain coordinates/bucket, max five per owner/150 total, refresh eight seconds by default. Twenty-four nearby smoker visuals maximum, visual distance 45 m; litter lifetime 90 s. Dynamic housing bucket remapping is outside the package.
