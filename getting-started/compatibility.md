# Compatibility and dependencies

| Product              | Hard dependencies                                                          | Scope                                                   |
| -------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------- |
| Advanced K9          | `oxmysql`                                                                  | QBox / QBCore / ESX / standalone adapters               |
| Advanced Vet DLC     | `oxmysql`                                                                  | Multi-framework adapters; default billing is QBox + NRP |
| Advanced Government  | `oxmysql`, `ox_lib`, `qbx_core`, `ox_target`, `nrp_core_systems`           | QBox + NRP banking                                      |
| Advanced Orbital     | `oxmysql`, `ox_lib`, `qbx_core`, `ox_target`                               | QBox                                                    |
| Advanced Pausemenu   | `ox_lib`, `qbx_core`                                                       | QBox                                                    |
| Advanced Cablecar    | `ox_lib`                                                                   | QBox by default; standalone fare mode                   |
| Advanced Car Radio   | `oxmysql`, `ox_lib`, `qbx_core`, `xsound`                                  | QBox                                                    |
| Advanced Diving      | `oxmysql`, `ox_lib`, `qbx_core`, `ox_target`                               | QBox                                                    |
| Advanced Poolcleaner | `oxmysql`, `ox_lib`, `qbx_core`                                            | QBox                                                    |
| Advanced Smoking     | `oxmysql`, `ox_lib`, `qbx_core`, `tgiann-inventory`, `ox_target` + OneSync | QBox + TGIANN Inventory                                 |
| Advanced Yacht       | `oxmysql`, `ox_lib`, `qbx_core`, `ox_inventory`, `ox_target`               | QBox                                                    |

Start runtime providers before resources. K9 has internal UI; Cablecar default fare still needs qbx\_core; Vet default billing needs NRP/QBox despite minimal manifest. Smoking is TGIANN-wired, Yacht storage/Diving optional gear are ox\_inventory-wired. No claim is made that all eleven run unchanged on a TGIANN-only server. Install one actual framework; multiple adapters are alternatives, not instructions to install multiple cores. External provider versions were not supplied or live-tested.
