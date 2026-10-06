# Diving — Crew and objective lifecycle

Crew invite/start membership and objective states live on server. Boat/objects are shared network entities in the ordinary world. Each objective is reserved during a member action; pending underwater validation can use the configured anchor to tolerate OneSync drift.

Lift lifecycle: pending → reserved bag action → lifting → surfaced → boat load → done. Pickup/cut/recover complete through their corresponding action. Completion rechecks membership/state/reservation/proximity. Version 1.0.3 enables allowSwimming on progressCircle to avoid underwater cancellation.

The code retains an actionDurationOk helper/config grace but completeObjective deliberately does not enforce a second server progress timer. Do not describe client progress/skill check as a cryptographically trusted anti-cheat timer. Server reservation/state checks prevent shared duplicate completion, but this documentation is not a security audit.

After all goals: return phase → assigned boat near marina → per-member funds/XP → entity cleanup. Leader leaving cancels. Restart stops/cleans runs; SQL stores player XP/completion/earnings, not active crew missions. Test two members attempting same target, separate targets, disconnect and boat destruction.
