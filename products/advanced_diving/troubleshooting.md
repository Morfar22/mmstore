# Advanced Diving — Troubleshooting

{% hint style="warning" %}
This release still directly requires ox_target for its job NPC. Choosing qb-target/qtarget in mm_bridge does not replace that integration. Optional gear checks use the bridge; gear is not consumed. Failed crew payout completes progression with zero credited earnings and requires reconciliation.
{% endhint %}

## Bridge diagnostics

Run `mmbridge_status` in the server console. Confirm the selected provider is ready; an explicit missing provider never silently falls back. If auto detects multiple candidates, choose one explicitly. Restart dependent resources after bridge/provider restarts.

For failed credits, item mutations or billing operations, retain the exact error and reconcile provider records before retrying. Do not assume an error proves that no external mutation occurred.

See [support](../../getting-started/support.md) and [bridge troubleshooting](../../bridge/troubleshooting.md).


| Symptom | Check |
| --- | --- |
| Salvage cancels/no error | Deploy v1.0.3 allowSwimming fix; Debug progress diagnostics and explicit callback responses. |
| Lift will not load | Must be surfaced; boat within 14 m. |
| Cannot return | All goals done, assigned boat alive, 16 m return radius. |
| Cannot invite | Leader only; max crew/range/no active mission. |
| Gear denied | When enabled, ox_inventory and configured item required. |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
