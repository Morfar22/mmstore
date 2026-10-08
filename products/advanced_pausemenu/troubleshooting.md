# Troubleshooting

| Symptom             | Check                                                                                                          |
| ------------------- | -------------------------------------------------------------------------------------------------------------- |
| Two ESC menus       | Stop other replacement; check ReplaceDefaultPause.                                                             |
| Inventory fails     | Generic ox-style exports are used; implement actual TGIANN adapter or command fallback.                        |
| Settings loading    | Shipped frontend selects FE\_MENU\_VERSION\_MP\_PAUSE page 6; gather F8/native evidence, no later fix assumed. |
| Wrong text/services | Change config and hardcoded Danish UI; match exact job names.                                                  |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
