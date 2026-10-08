# Troubleshooting

| Symptom                         | Check                                                                                              |
| ------------------------------- | -------------------------------------------------------------------------------------------------- |
| Missing dependency/vi\_accounts | Install NRP stack or replace adapter; Banking.resource string is insufficient.                     |
| Wages untaxed                   | External QBox hook not included; verify one post-gross-pay call.                                   |
| Tax doubles                     | Check duplicate payroll hooks; arbitrary repeated wage calls are not guaranteed idempotent.        |
| Grant rejected                  | Check boss, active private ownership/NRP business resource, permission, funds and account mapping. |
| Reference column missing        | v2 migration adds module tables; verify existing NRP v1 transaction schema.                        |
| Mayor job removed               | Install permanent job definition and verify office term/character.                                 |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
