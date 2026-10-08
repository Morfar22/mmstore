# Billing, Sky and K9 integrations

The supplied NRP invoice provider calls nrp\_core\_systems.CreateInvoice/PayInvoice and uses nrp\_invoices. New NRP invoices and older local advanced\_vet\_invoices are merged in the customer/clinic UI. They retain provider tags; existing local invoices are handled through their local route. Do not migrate them by deleting old rows.

Billing.nrpAccount defaults to vet for ACE-only staff without a usable job. Verify the actual issuing job/account mapping, especially police access: configured authorized jobs can determine the invoice society account. Local legacy invoices include processing/review recovery; review status needs reconciliation before another charge.

For a generic installation without NRP, a non-NRP provider value selects the existing local invoice route. Framework RemoveMoney must work; standalone payments are not free unless allowStandaloneFree explicitly permits them. Test issuance, unauthorized payment, double click, cancellation and resource-restart reconciliation.

Sky death integration uses auto detection and its public server heal event for definitive care, with separate revive/heal stages as appropriate. Injury profile is diagnostic, not a success acknowledgment contract. K9/Vet care uses server exports to synchronize needs. Temporary Vet training does not replace adoption/handler relationships. Clinical vitals/X-ray descriptions are RP simulation.
