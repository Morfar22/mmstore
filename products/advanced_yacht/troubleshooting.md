# Advanced Yacht — Troubleshooting

| Symptom | Check |
| --- | --- |
| Yacht invisible | Check Rockstar IPL streaming and conflicting yacht resources. |
| Jacuzzi dry | Check ripple1 water model/offset/noncollision. |
| Storage fails | ox_inventory required plus explicit access/proximity. |
| Upgrade denied | Package allowance, physical slots, bank and quantity. |
| Cannot relocate | Free berth, owner access, fee and cooldown. |
| Wardrobe fails | Start configured appearance or implement custom event. |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
