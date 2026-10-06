# Vet — Inventory and gameplay medicine

Use install/ox_inventory_items.lua, install/tgiann_inventory_items.lua or install/qbcore_items.lua as appropriate. They contain 12 products plus vet_prescription. Merge returned table entries; preserve existing items. Item images are not supplied.

| Item | Dedicated server export suffix | Duration | FiveM effect |
| --- | --- | --- | --- |
| vet_quietpaws | useQuietPaws | 180 s | Heavy sedation; move rate .62, blocks sprint/jump/attack; strong visual |
| vet_gentleease | useGentleEase | 240 s | Pain-relief status, move .90 and mild visual; no wound healing |
| vet_happyjoints | useHappyJoints | 600 s | Joint support; no narcotic visual |
| vet_bellybloom | useBellyBloom | 600 s | GI support; no hunger restoration |
| vet_peacefulpet | usePeacefulPet | 240 s | Calming, move .88, blocks attack; mild visual |
| vet_goldenpaws_daily | useGoldenPawsDaily | 900 s | Max HP x1.25; emergency +25% max HP restoration when no on-duty Vet |
| vet_meadowbowl | useMeadowBowl | Instant need change | +45 hunger |
| vet_softharvest | useSoftHarvest | 300 s status | +35 hunger / recovery nutrition |
| vet_sprinkle_of_sunshine | useSprinkleOfSunshine | 300 s status | +5 hunger / appetite support |
| vet_clearspring | useClearSpring | Instant need change | +25 thirst |
| vet_pawpure | usePawPure | 300 s status | +40 thirst / electrolyte status |
| vet_stillbrook | useStillBrook | Instant need change | +30 thirst |

Dedicated export prefix is advanced_vet_dlc., e.g. advanced_vet_dlc.useQuietPaws. ox_inventory generic callback is useVetMedicine; use the matching supplied item table rather than swapping callback identities across inventories. Dedicated TGIANN exports let the resource identify a product even if the callback omits its name.

Prescription issuance requires patient selection by default and gives product plus prescription document. Metadata records patient, medicine/product, issuing staff and RP label/effect information. Patient-match check is enabled for use. A human uses the item on a nearby player dog (3 m); a dog uses it on itself.

GoldenPaws vitality buff applies whether or not a vet is available. Only the additional emergency heal depends on absence of an on-duty job in vetOnlineJobs; police UI access does not count as veterinarian availability. Movement/attack restrictions are consumed by K9 action gates. Needs feed the existing framework/K9 care values.

All values on this page are FiveM gameplay settings. Real-world drug labels/dose strings in the source catalog are not instructions for treating an animal and are intentionally not reproduced as a dosing guide.

Validate item consumption once, metadata resolution, target mismatch rejection, effect expiry and max-HP restoration on your actual inventory/client. These interactions were not live-tested here.
