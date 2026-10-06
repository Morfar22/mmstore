# K9 — Vehicle cages and camera setup

Vehicle profiles are model-based. Saved geometry applies to vehicles of that model, while reservations occupy a particular networked vehicle slot. Up to four cage slots are supported; a model can enable only a subset. Existing legacy single-anchor data can supply slot one.

1. Place the actual custom vehicle at a safe test point and open /k9setup with setup permission.
2. Select the vehicle through the setup menu/current vehicle selection. Confirm the selected model before editing.
3. Choose the cage slot and use the local ghost dog preview. It is not a networked replacement for a player's dog.
4. Move/rotate the dog anchor inside the cage. Choose the intended sit/sleep posture and preview multiple breeds when needed.
5. Save a safe exit point and correct door index for that vehicle. Door indices are GTA native door indices; rear-left defaults to 2.
6. Save/enable the slot. Repeat only for slots supported by your model.
7. Configure a model camera using /k9camsetup/freecam and save. Auto-use of saved camera is enabled; safe fallback camera exists if none is saved.
8. Clear preview templates, pair a real dog and test I entry/exit, posture and camera from both clients. Test driver movement, ownership migration and a handler disconnect/death.

Soft-cage mode follows saved offsets without attaching the real dog or forcing a passenger seat. Posture/camera start in delayed stages. This reduces simultaneous native operations but is not a guarantee against all custom-model/client crashes.

The ordinary I mapping toggles entry/exit for active role context. Legacy forced-exit mappings are unbound. Handler death response is enabled. /k9cagestaff manages saved profiles; bulk removal is guarded with DELETE ALL confirmation. Use the staff interface rather than deleting database rows manually.

Tables: advanced_k9_vehicle_slots, advanced_k9_vehicle_anchors, advanced_k9_vehicle_cameras. Preserve them when updating. Geometry diagnostics are disabled by default; enable temporarily for a reproduction. Source: vehicle_slot_setup.lua, vehicle_premium_setup.lua, vehicle.lua and server vehicle modules.
