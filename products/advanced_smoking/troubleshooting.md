# Advanced Smoking — Troubleshooting

{% hint style="warning" %}
Full item use requires individual slots and persistent metadata. Plain ESX inventory and standalone without a suitable inventory cannot run the full system. QB inventory supports ordinary items; containers remain locked until a safe local stash adapter is configured. Shop credits marked processing/review require reconciliation.
{% endhint %}

## Bridge diagnostics

Run `mmbridge_status` in the server console. Confirm the selected provider is ready; an explicit missing provider never silently falls back. If auto detects multiple candidates, choose one explicitly. Restart dependent resources after bridge/provider restarts.

For failed credits, item mutations or billing operations, retain the exact error and reconcile provider records before retrying. Do not assume an error proves that no external mutation occurred.

See [support](../../getting-started/support.md) and [bridge troubleshooting](../../bridge/troubleshooting.md).


| Symptom | Check |
| --- | --- |
| Shop/items fail | Inventory definitions/icons are absent; install all catalog keys and compatible use export. |
| Missing selected slot | TGIANN use callback must reach advanced_smoking.useItem with valid slot/name. |
| Containers locked | Native registerHook unavailable; read startup error, adapt/version-check bridge. |
| Cannot light/refill | Correct accessory, cigar cut, and reusable vs disposable distinction. |
| House props wrong | Bucket ID is not stable housing identity; external adapter needed. |
| Unexpected effect | Config CameraEffects is true; set false if desired. |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
