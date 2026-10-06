# Advanced Smoking — Troubleshooting

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
