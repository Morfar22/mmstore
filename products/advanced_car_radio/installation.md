# Advanced Car Radio — Installation

```cfg
ensure oxmysql
ensure ox_lib
ensure qbx_core
ensure xsound
ensure advanced_car_radio
```

Supply a compatible resource named xsound with the expected exports. Actual media playback depends on xSound/CEF; accepted URLs/metadata do not guarantee audio. Playlists use citizenid, vehicle libraries use normalized plates. Changing/reused plates need a stable vehicle-identity adapter. No custom item is required.

## Database

Automatic creation exists. Optional manual schema: `sql/install.sql`.

| Resource-owned table |
| --- |
| `advanced_car_radio_playlist_tracks` |
| `advanced_car_radio_playlists` |
| `advanced_car_radio_settings` |
| `advanced_car_radio_vehicle_state` |
| `advanced_car_radio_vehicle_tracks` |

## Staff ACE

Normal player use needs no additional product ACE; see restricted developer setup where relevant.

Source: manifest/config and loaded server database/bridge code.
