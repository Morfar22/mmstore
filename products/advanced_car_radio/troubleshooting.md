# Advanced Car Radio — Troubleshooting

{% hint style="warning" %}
Requires xSound for audio, oxmysql for persistence and ox_lib. No target/inventory/phone adapter is required. Provider changes do not move saved radio ownership automatically.
{% endhint %}

## Bridge diagnostics

Run `mmbridge_status` in the server console. Confirm the selected provider is ready; an explicit missing provider never silently falls back. If auto detects multiple candidates, choose one explicitly. Restart dependent resources after bridge/provider restarts.

For failed credits, item mutations or billing operations, retain the exact error and reconcile provider records before retrying. Do not assume an error proves that no external mutation occurred.

See [support](../../getting-started/support.md) and [bridge troubleshooting](../../bridge/troubleshooting.md).


| Symptom | Check |
| --- | --- |
| URL accepted but silent | Check actual xSound/CEF support and shared/personal volume/range. |
| Metadata absent | oEmbed needs reachable HTTP; title/cover lookup is independent of playback. |
| Library wrong vehicle | Normalized plate reuse/change needs stable identity integration. |
| Quiet outside | Expected closed leakage; compare door/window test. |
| Several F7 menus | Rebind existing FiveM client mappings. |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
