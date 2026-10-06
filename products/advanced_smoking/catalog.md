# Smoking — Required item catalog

The source defines these exact 41 keys. Prices are catalog defaults (— means no ordinary shop price), weights are source values, and rarity is cosmetic. Shop persisted pricing/stock can differ after management changes.

| Item key | Label | Kind | Weight | Default price | Rarity |
| --- | --- | --- | --- | --- | --- |
| smk_redwood_pack | Redwood · Original | pack | 70 | 95 | common |
| smk_debonaire_pack | Debonaire · Silver | pack | 70 | 145 | premium |
| smk_cardiaque_pack | Cardiaque · Mint | pack | 70 | 145 | premium |
| smk_nordlys_pack | Nordlys · N° 04 | pack | 70 | 220 | luxury |
| smk_redwood | Redwood | cigarette | 2 | — | common |
| smk_debonaire | Debonaire | cigarette | 2 | — | premium |
| smk_cardiaque | Cardiaque Mint | cigarette | 2 | — | premium |
| smk_nordlys | Nordlys N° 04 | cigarette | 2 | — | luxury |
| smk_cigarillo | Palomino · Cigarillo | cigar | 8 | 75 | common |
| smk_cigar | El Patrón · Reserva | cigar | 18 | 450 | luxury |
| smk_cigar_limited | Nordlys · Founder’s No. 27 | cigar | 18 | 1400 | limited |
| smk_disposable_blue | Fjord Bar · Blueberry Ice | vape | 45 | 175 | common |
| smk_disposable_melon | Fjord Bar · Watermelon | vape | 45 | 175 | common |
| smk_pod | Fjord · Pod One | vape | 90 | 700 | premium |
| smk_mod | Aurora · RGB Mod | vape | 160 | 1800 | luxury |
| smk_pod_mint | Fjord Pod · Mint | pod | 20 | 65 | common |
| smk_pod_mango | Fjord Pod · Mango | pod | 20 | 65 | common |
| smk_pod_cola | Fjord Pod · Cola Ice | pod | 20 | 65 | common |
| smk_pod_blue | Fjord Pod · Blueberry Ice | pod | 20 | 65 | common |
| smk_joint_relaxed | Cloud Nine · Relaxed | joint | 4 | 140 | common |
| smk_joint_social | Sunroom · Social | joint | 4 | 140 | common |
| smk_joint_sleepy | Moonflower · Sleepy | joint | 4 | 175 | premium |
| smk_joint_energy | Daybreak · Energized | joint | 4 | 175 | premium |
| smk_bong | Fjord Glass · Classic | bong | 650 | 850 | common |
| smk_bong_novelty | Moon Glass · Orbital | bong | 650 | 1300 | premium |
| smk_bong_luxury | Nordlys Glass · Signature | bong | 650 | 2400 | luxury |
| smk_rig | Aurora · Table Rig | rig | 550 | 2800 | luxury |
| smk_rig_limited | Aurora · Nightfall Edition | rig | 550 | 4800 | limited |
| smk_blend | Cloud Blend · RP refill | refill | 30 | 120 | common |
| smk_water | Glass Care · Vand | water | 250 | 20 | common |
| smk_cleaner | Glass Care · Rensesæt | cleaner | 120 | 80 | common |
| smk_lighter | Nordlys · Lighter | lighter | 25 | 35 | common |
| smk_zippo | Nordlys · Heritage Lighter | lighter | 65 | 700 | luxury |
| smk_matches | Nordlys · Tændstikker | lighter | 15 | 12 | common |
| smk_fuel | Heritage · Lighterrefill | fuel | 90 | 45 | common |
| smk_cutter | Reserva · Cigarklipper | cutter | 45 | 160 | premium |
| smk_charger | Fjord · Power Pack | charger | 180 | 350 | premium |
| smk_case | Nordlys · Cigaretetui | case | 200 | 450 | premium |
| smk_cigar_case | Reserva · Rejseetui | case | 350 | 850 | luxury |
| smk_humidor | Nordlys · Humidor | humidor | 3500 | 6500 | luxury |
| smk_roach | Joint-filter | litter | 1 | — | common |

## Definition integration checklist

1. Define all names in your TGIANN item registry, including pack child cigarettes and smk_roach.
2. Match kind/weight/label to catalog; supply corresponding icons (none are shipped).
3. Hook usable items to client export advanced_smoking.useItem with valid name/slot payload.
4. Keep independently tracked product metadata in info.smoking and do not stack unique UID/loan/serial states together.
5. Let resource actions handle item removal/consumption; verify your inventory callback does not consume an extra item automatically.
6. Confirm carry, add/remove, metadata update and native stash hooks on the installed inventory version.
7. Test packs, reusable/disposable products, accessories, loans/returns and containers separately.

This is a documentation contract, not a generated drop-in item adapter. The inventory's exact schema/consume callback must match your installed TGIANN version. Adding a new catalog entry also needs its definition/image and gameplay kind support.
