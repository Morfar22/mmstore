# Troubleshooting

| Symptom               | Check                                                          |
| --------------------- | -------------------------------------------------------------- |
| No suitable pools     | Need sufficient task types, six for long route; use creator.   |
| Task busy             | Another member reserved it; use another task or await release. |
| Completion denied     | Check current pool, distance, elapsed time and item removal.   |
| Creator denied        | Grant poolcleaner.admin; deletion supports DB-created pools.   |
| No return payout step | Final task automatically pays in this version.                 |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
