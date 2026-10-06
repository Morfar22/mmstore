# Vet — Mandatory patient and kennel placement

The current editorOnly runtime needs a database placement with both patient and release positions. Config.PatientTables.locations/legacy kennel offsets are not a runtime substitute. This differs from older README history claiming config fallback.

1. Grant advanced_vet.setup to the actual setup staff principal. allowVeterinarian is false by default.
2. Visit the actual clinic and run /vetsetup.
3. Select clinic and table key (treatment, xray, surgery, chip, vaccination) or kennel slot A-01…B-04.
4. Place/move/rotate the patient ghost dog directly on the real table/floor. Use the on-screen editor controls; Enter confirms and the model-cycle R helps compare body sizes.
5. Save a separate release anchor safely beside the workstation. Verify heading and ground height.
6. For kennels, save the physical kennel/doghouse prop separately from dog/release anchors.
7. Save permanently, reopen the editor and preview the saved geometry. Test placement with another player dog, treatment and /vetgetup.
8. Repeat for every workstation/slot you intend to use. After restart verify saved geometry and release behavior.

Overrides are in advanced_vet_placement_overrides, including preview models and prop-related data. Authoritative save checks validate clinic/key/finite coordinates and setup permissions. Keep custom Config.Locations station coordinates in sync with your MLO.

Default player-dog pose uses the configured Onex bdogsleep command; ghost/NPC pose uses native sleep_in_kennel. Staff procedure animation is configured separately. Exiting can use bdogupk. Avoid competing human emote locks cancelling the canine placement pose.

No clinic interior is shipped. Current paleto_bay key has supplied coordinates around 560, 2770; it is an ID/label, not a guarantee of the map area's name. Preserve your intended custom layout and check every point.
