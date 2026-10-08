# Troubleshooting

| Symptom                 | Check                                                                       |
| ----------------------- | --------------------------------------------------------------------------- |
| URL accepted but silent | Check actual xSound/CEF support and shared/personal volume/range.           |
| Metadata absent         | oEmbed needs reachable HTTP; title/cover lookup is independent of playback. |
| Library wrong vehicle   | Normalized plate reuse/change needs stable identity integration.            |
| Quiet outside           | Expected closed leakage; compare door/window test.                          |
| Several F7 menus        | Rebind existing FiveM client mappings.                                      |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
