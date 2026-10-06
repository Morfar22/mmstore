# Orbital — Payment, limits and impact

A requested manual/automatic strike validates active terminal session, current access/proximity, funds, cooldown, SQL day counts, network target/type or world coordinates and safe zones. It removes payment, inserts strike row and sets in-memory cooldown before the countdown finishes.

At impact, a moving target is resolved again and safe zones are checked again. If the target entered a safe zone, impact is cancelled. **This code path does not issue a refund**: the charge/log/count/cooldown were already applied. Document that rule to operators or implement a separate reconciled refund change before offering a different policy.

World particles/audio broadcast to clients; the operator creates GTA tag-59 explosion. Server picks players in lethal radius and instructs their client to apply lethal damage. Network vehicles in configured radius get damage/destruction state handled by owning clients. No generic NetworkExplodeVehicle is used for the primary visual.

Daily counts are SQL-persistent by server date. Cooldown/session tables are memory and restart behavior differs. A SQL insert failure after payment is not documented as a complete automatic refund transaction; inspect/reconcile with bank and strike logs. Live validation is required for money failures and moving targets.
