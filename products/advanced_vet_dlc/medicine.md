# Inventory and gameplay medicine

Use install/ox\_inventory\_items.lua, install/tgiann\_inventory\_items.lua or install/qbcore\_items.lua as appropriate. They contain 12 products plus vet\_prescription. Merge returned table entries; preserve existing items. Item images are not supplied.

| Item                        | Dedicated server export suffix | Duration            | FiveM effect                                                            |
| --------------------------- | ------------------------------ | ------------------- | ----------------------------------------------------------------------- |
| vet\_quietpaws              | useQuietPaws                   | 180 s               | Heavy sedation; move rate .62, blocks sprint/jump/attack; strong visual |
| vet\_gentleease             | useGentleEase                  | 240 s               | Pain-relief status, move .90 and mild visual; no wound healing          |
| vet\_happyjoints            | useHappyJoints                 | 600 s               | Joint support; no narcotic visual                                       |
| vet\_bellybloom             | useBellyBloom                  | 600 s               | GI support; no hunger restoration                                       |
| vet\_peacefulpet            | usePeacefulPet                 | 240 s               | Calming, move .88, blocks attack; mild visual                           |
| vet\_goldenpaws\_daily      | useGoldenPawsDaily             | 900 s               | Max HP x1.25; emergency +25% max HP restoration when no on-duty Vet     |
| vet\_meadowbowl             | useMeadowBowl                  | Instant need change | +45 hunger                                                              |
| vet\_softharvest            | useSoftHarvest                 | 300 s status        | +35 hunger / recovery nutrition                                         |
| vet\_sprinkle\_of\_sunshine | useSprinkleOfSunshine          | 300 s status        | +5 hunger / appetite support                                            |
| vet\_clearspring            | useClearSpring                 | Instant need change | +25 thirst                                                              |
| vet\_pawpure                | usePawPure                     | 300 s status        | +40 thirst / electrolyte status                                         |
| vet\_stillbrook             | useStillBrook                  | Instant need change | +30 thirst                                                              |

Dedicated export prefix is advanced\_vet\_dlc., e.g. advanced\_vet\_dlc.useQuietPaws. ox\_inventory generic callback is useVetMedicine; use the matching supplied item table rather than swapping callback identities across inventories. Dedicated TGIANN exports let the resource identify a product even if the callback omits its name.

Prescription issuance requires patient selection by default and gives product plus prescription document. Metadata records patient, medicine/product, issuing staff and RP label/effect information. Patient-match check is enabled for use. A human uses the item on a nearby player dog (3 m); a dog uses it on itself.

GoldenPaws vitality buff applies whether or not a vet is available. Only the additional emergency heal depends on absence of an on-duty job in vetOnlineJobs; police UI access does not count as veterinarian availability. Movement/attack restrictions are consumed by K9 action gates. Needs feed the existing framework/K9 care values.

All values on this page are FiveM gameplay settings. Real-world drug labels/dose strings in the source catalog are not instructions for treating an animal and are intentionally not reproduced as a dosing guide.

Validate item consumption once, metadata resolution, target mismatch rejection, effect expiry and max-HP restoration on your actual inventory/client. These interactions were not live-tested here.
