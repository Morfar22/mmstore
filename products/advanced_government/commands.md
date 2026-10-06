# Advanced Government — Commands and controls

| Command (omit slash in console) | Purpose | Access/default |
| --- | --- | --- |
| government | Government dashboard | Public with permission-filtered actions |
| govadmin phase registration\|campaign\|voting\|finished | Force current phase | Admin |
| govadmin newvote | Start a new election | Admin |
| govadmin setmayor <citizenid> | Assign current mayor | Admin; citizenid not server ID |

Command names selected by config are shown with supplied defaults. +/- key-mapping handlers are input internals, not additional player slash-command features. Developer commands can be conditionally registered; use the source index to inspect the gate. Existing FiveM key mappings are client preferences.
