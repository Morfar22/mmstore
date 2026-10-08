# Advanced K9 — Troubleshooting

{% hint style="warning" %}
Standalone service authority needs ACE or explicit opt-in; civil play remains available. Needs and optional legacy phone adapters remain local extensions. The existing K9 UI and Vet exports are retained. Database keys default to legacy licenses; character mode requires a manual migration.
{% endhint %}

## Bridge diagnostics

Run `mmbridge_status` in the server console. Confirm the selected provider is ready; an explicit missing provider never silently falls back. If auto detects multiple candidates, choose one explicitly. Restart dependent resources after bridge/provider restarts.

For failed credits, item mutations or billing operations, retain the exact error and reconcile provider records before retrying. Do not assume an error proves that no external mutation occurred.

See [support](../../getting-started/support.md) and [bridge troubleshooting](../../bridge/troubleshooting.md).


| Symptom | Check |
| --- | --- |
| Service pairing denied | Approve both service roles, authority job and initial 8 m proximity; distinguish public civil path. |
| Keys do nothing | Enable Active K9 handler, select dog and check unlocks/medicine/placement gates and saved bindings. |
| No vehicle/cage | Select nearby vehicle in /k9setup; save/enable slots for actual model, verify reservations/exit. |
| No scent | Check water/vehicle breaks, lifetime, progression and manual alert; defaults pink. |
| Custom bark silent | Provide named InteractSound ogg files or choose no backend. |
| Collar phone missing | Check phone provider/character metadata/cache and phone bridge; sanitize diagnostics. |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
