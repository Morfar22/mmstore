# Advanced Vet DLC — Commands and controls

| Command (omit slash in console) | Purpose | Access/default |
| --- | --- | --- |
| vet | Nearby patient | F10/use access |
| vetrecords | Records | Vet access |
| vetpay | Customer invoices | No default key |
| vetsetup | Placement editor | advanced_vet.setup by default |
| vetgetup | Emergency patient release | Placed local patient |
| vettablepos <clinic> <station> / vetkennelpos <clinic> <slot> | Legacy debug coordinates | Developer/context checks |
| vetdiag / vetemotetest / vetposecheck / vetbdogsleeptest | Diagnostics | DeveloperMode-dependent |

Command names selected by config are shown with supplied defaults. +/- key-mapping handlers are input internals, not additional player slash-command features. Developer commands can be conditionally registered; use the source index to inspect the gate. Existing FiveM key mappings are client preferences.
