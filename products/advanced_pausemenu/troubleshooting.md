# Advanced Pausemenu — Troubleshooting

{% hint style="warning" %}
The bridge reads inventory items but has no UI-open or weight API. Configure Inventory.command or a confirmed client Inventory.open hook; getWeight is a local hook. Unsupported balances show as unavailable. Service counts use duty but are not currently rendered by the UI.
{% endhint %}

## Bridge diagnostics

Run `mmbridge_status` in the server console. Confirm the selected provider is ready; an explicit missing provider never silently falls back. If auto detects multiple candidates, choose one explicitly. Restart dependent resources after bridge/provider restarts.

For failed credits, item mutations or billing operations, retain the exact error and reconcile provider records before retrying. Do not assume an error proves that no external mutation occurred.

See [support](../../getting-started/support.md) and [bridge troubleshooting](../../bridge/troubleshooting.md).


| Symptom | Check |
| --- | --- |
| Two ESC menus | Stop other replacement; check ReplaceDefaultPause. |
| Settings loading | Shipped frontend selects FE_MENU_VERSION_MP_PAUSE page 6; gather F8/native evidence, no later fix assumed. |
| Wrong text/services | Change config and hardcoded Danish UI; match exact job names. |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
