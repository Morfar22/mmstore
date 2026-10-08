# Exports and integrations

## Supported exports

Server-side:

| Export                  | Parameters                    | Purpose                                     |
| ----------------------- | ----------------------------- | ------------------------------------------- |
| GetActiveK9Teams        | none                          | Snapshot of active handler teams/dog roster |
| GetK9Passport           | dog server ID                 | Working-dog passport data                   |
| ApplyExternalCareNeeds  | dog, hunger, thirst           | Set active K9 needs, values clamped         |
| AdjustExternalCareNeeds | dog, hungerDelta, thirstDelta | Adjust current active K9 needs              |
| StartVetTrainingSession | trainer, dog                  | Start temporary external training channel   |
| EndVetTrainingSession   | trainer                       | End channel                                 |
| VetTrainerCommand       | trainer, command              | Send a configured allowed training order    |
| GetVetTrainingDog       | trainer                       | Resolve active external training dog        |
| GetStationaryKennels    | none                          | Saved kennel snapshot                       |
| GetDogStationaryKennel  | dog                           | Resolve current kennel assignment           |

Client-side: AreDogEmotesLocked() and CanUseHumanEmotes() return local lock state.

```lua
-- SERVER: inspect the player's dog passport.
local passport = exports.advanced_k9:GetK9Passport(dogServerId)
-- CLIENT: let a human emote resource respect K9 lock state.
if GetResourceState('advanced_k9') == 'started'
    and not exports.advanced_k9:CanUseHumanEmotes() then
    return
end
```

The replicated advancedK9Dog flag identifies an active K9 role; animal-model stamina/emote handling also has model-based logic. advancedK9EmotesLocked is the emote lock state key. Do not mutate these to bypass role creation.

Framework detection order: qbx\_core, qb-core, es\_extended, standalone. Phone order is in Config.PhoneIntegration; it tries supported exports/metadata/cache and restricted Sky schema fallbacks. Config.UISkins is cosmetic and separate from service permissions.

Sniff inventory code directly prefers ox\_inventory and then legacy framework inventories. There is no direct TGIANN sniff export adapter in server/sniff.lua. Verify whether your QBox/TGIANN setup populates the fallback PlayerData items or implement a bridge; do not promise working TGIANN contraband sniff just because other features work.

Use exported server APIs from trusted server resources. Internal events are not stable authorization-bypass integrations.

Source: export declarations and loaded framework/inventory/billing bridges in the supplied product.
