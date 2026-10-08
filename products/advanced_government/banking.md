# NRP banking architecture

server/nrp\_bridge.lua is loaded before server/main.lua and implements the active Gov.transfer transaction. Public recipients map to Config.PublicAccounts; private jobs map through BusinessAccounts to nrp\_business\_. Business table status/owner is verified.

The SQL transaction updates government\_treasury and recipient vi\_accounts, settles grant/contract records when applicable, inserts treasury transaction reference, vi\_transactions and government\_audit. A receipt lookup determines whether the conditional update actually happened. Do not replace just Banking.resource and assume the transaction schema changed.

Required external structures include vi\_accounts, vi\_transactions, nrp\_businesses and the NRP resources/export/audit contracts. They are not defined by this package's 22 government tables. Private boss checks additionally call nrp\_businesses.GetBossBankAccount.

For another bank provider, design a complete adapter with equivalent validations/reconciliation and review all direct NRP calls. The old README Renewed-Banking example is historical context. Imported government rows do not install the external account schema. Defaults such as treasury seed/taxes may only initialize missing rows; config edits do not guarantee overwriting persisted rates/balances.
