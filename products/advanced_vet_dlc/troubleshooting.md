# Troubleshooting

| Symptom                    | Check                                                                                                      |
| -------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Position not configured    | Save BOTH anchors via /vetsetup; config legacy coordinates do not satisfy editorOnly.                      |
| Invoice system unavailable | Supply NRP QBox invoice dependencies/schema or test local legacy provider.                                 |
| Medicine does nothing      | Merge correct inventory items/exports; TGIANN uses dedicated product exports and patient metadata.         |
| Pose fails/falls           | Check saved geometry/model, Onex commands and competing emotes.                                            |
| Sky profile remains        | sky\_ambulancejob:healPlayer is authoritative; residual profile is diagnostic, not failure acknowledgment. |
| Patient not found          | Check model/network identity/distance/line of sight; local decorations are different.                      |

## Live acceptance checklist

1. Confirm startup/dependency/SQL health.
2. Open/close UI and perform allowed gameplay actions.
3. Check denied role, distance and invalid-action responses.
4. Use two clients for shared state, locks, transfers and effects.
5. Restart/reconnect and confirm documented persistent data. Active UI/missions are not necessarily persisted.
6. Verify funds/items/stashes/cleanup after completion, cancel and disconnect.

Recommended checks, not live FiveM tests performed during this task.
