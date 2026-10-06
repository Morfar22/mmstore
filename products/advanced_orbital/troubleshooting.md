# Advanced Orbital — Troubleshooting

| Symptom | Check |
| --- | --- |
| Terminal denied | Check groups/grade/duty/ACE/proximity. |
| Strike denied | Mode, safe zone, price, SQL limits and cooldown. |
| Table missing | Import sql/advanced_orbital.sql. |
| No sound/impact unreliable | Check native sound bank, replicated vehicle damage and relevant clients with two players. |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
