# Advanced Cablecar — Troubleshooting

{% hint style="warning" %}
Optional targets still call ox_target directly. Ticket-machine proximity interactions work without a target provider. Config.Framework='standalone' explicitly skips fares; legacy 'qbox' selects paid bridge behavior. Framework selection in mm_bridge does not override this resource fare setting.
{% endhint %}

## Bridge diagnostics

Run `mmbridge_status` in the server console. Confirm the selected provider is ready; an explicit missing provider never silently falls back. If auto detects multiple candidates, choose one explicitly. Restart dependent resources after bridge/provider restarts.

For failed credits, item mutations or billing operations, retain the exact error and reconcile provider records before retrying. Do not assume an error proves that no external mutation occurred.

See [support](../../getting-started/support.md) and [bridge troubleshooting](../../bridge/troubleshooting.md).


| Symptom | Check |
| --- | --- |
| No money deduction | Standalone intentionally free; start QBox for qbox fares. |
| No target | Disabled by default; use E proximity or enable started provider. |
| Bad rider position | Check cabin interior Z -5.30 and real station/collision points. |
| Dev denied | Check Developer.restricted group.admin. |
| Old Scaleform errors | Deploy complete v1.7.0 and restart; it uses ox_lib. |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
