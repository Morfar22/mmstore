# Advanced K9 — Exports and integrations

{% hint style="info" %}
Server exports are for trusted resources. Enforce caller authorization and source/amount checks. Client menu actions are not proof of payment or permission. Internal events are not a public adapter API.
{% endhint %}

Standalone service authority needs ACE or explicit opt-in; civil play remains available. Needs and optional legacy phone adapters remain local extensions. The existing K9 UI and Vet exports are retained. Database keys default to legacy licenses; character mode requires a manual migration.

| Export | Side | Arguments | Implementation |
| --- | --- | --- | --- |
| `AreDogEmotesLocked` | client | `` | `client/dog_emote_lock.lua` |
| `CanUseHumanEmotes` | client | `` | `client/dog_emote_lock.lua` |
| `ApplyExternalCareNeeds` | server | `dog, hunger, thirst` | `server/care.lua` |
| `AdjustExternalCareNeeds` | server | `dog, hungerDelta, thirstDelta` | `server/care.lua` |
| `StartVetTrainingSession` | server | `trainer, dog` | `server/pairing.lua` |
| `EndVetTrainingSession` | server | `trainer` | `server/pairing.lua` |
| `VetTrainerCommand` | server | `trainer, command` | `server/pairing.lua` |
| `GetVetTrainingDog` | server | `trainer` | `server/pairing.lua` |
| `GetActiveK9Teams` | server | `` | `server/pairing.lua` |
| `GetK9Passport` | server | `dog` | `server/passport.lua` |
| `GetStationaryKennels` | server | `` | `server/stationary_kennels.lua` |
| `GetDogStationaryKennel` | server | `dog` | `server/stationary_kennels.lua` |

Dynamic exports are described in their specialized integration guides; this literal index is not an exhaustive list of dynamically generated names. Consult [bridge integration](bridge.md) for return contracts and provider limitations, and [internal registrations](events.md) for module routing.
