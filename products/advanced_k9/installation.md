# Installation

```cfg
ensure oxmysql
ensure advanced_k9
```

The hard dependency is oxmysql. `client/ui_bridge.lua` supplies an internal `lib` UI bridge; the manifest does not load ox\_lib init. Start your intended framework and optional target/inventory/phone providers first.

1. Configure AuthorityJobs and the staff ACE.
2. Approve both service handler and dog through `/k9admin`; job access alone is insufficient.
3. Review `CivilK9.publicAccess = true`: the civilian public path does not require service approvals.
4. Save actual vehicle cage geometry using `/k9setup` and check it with two players.
5. If using InteractSound, provide the matching `.ogg` bark/whine files. They are absent from the archive.

Keep the actual folder `advanced_k9`; the manifest's name `advanced_k9_handler` is metadata, while integrations reference the resource folder.

## Database

Automatic creation exists. Optional manual schema: `sql/advanced_k9.sql`.

| Resource-owned table             |
| -------------------------------- |
| `advanced_k9_adoptions`          |
| `advanced_k9_approvals`          |
| `advanced_k9_passports`          |
| `advanced_k9_preferences`        |
| `advanced_k9_progress`           |
| `advanced_k9_stationary_kennels` |
| `advanced_k9_vehicle_anchors`    |
| `advanced_k9_vehicle_cameras`    |
| `advanced_k9_vehicle_slots`      |

## Staff ACE

```cfg
add_ace group.admin advancedk9.admin allow
```

Source: manifest/config and loaded server database/bridge code.
