# Advanced Vet DLC — Internal registration reference

This index locates literal registrations in the uploaded code, including local handlers, network handlers, NUI and callback wrappers. It is a maintainer lookup, **not a stable public API contract**. Event signature parameters exclude the implicit server event source. Registration does not prove an event should be called externally. Preserve original sender, session, permission, proximity, metadata and state checks.

Dynamic commands/exports and config-selected names also exist. See the commands/export pages for resolved names. Entries in comments or unexecuted diagnostic branches can be present; developer-only registration conditions must be checked in source. Parameters are nearest inline handler signatures, not validated documentation of payload schemas.

| Registration | Side | Name | Handler parameters | Source |
| --- | --- | --- | --- | --- |
| RegisterNetEvent | client | `advanced_vet:client:openClinicModule` | `moduleType, payload` | `client/clinic_modules.lua:71` |
| RegisterNetEvent | client | `advanced_vet:client:procedureProgress` | `label, duration, procedureType` | `client/clinic_modules.lua:288` |
| RegisterCommand | client | `vetemotetest` | `_, args` | `client/clinic_modules.lua:404` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/clinic_modules.lua:447` |
| RegisterNetEvent | client | `advanced_vet:client:invoiceReceived` | `amount, description, clinicLabel` | `client/clinic_modules.lua:464` |
| RegisterCommand | client | `vetpay` | `` | `client/clinic_modules.lua:477` |
| RegisterKeyMapping | client | `vetpay` | `Named function/dynamic handler; inspect source` | `client/clinic_modules.lua:487` |
| RegisterNetEvent | client | `advanced_vet:client:consentRequest` | `token,         vetName,         label,         category,         timeout` | `client/consent.lua:18` |
| RegisterNetEvent | client | `advanced_vet:client:consentExpired` | `token` | `client/consent.lua:62` |
| RegisterNUICallback | client | `consentResponse` | `data, cb` | `client/consent.lua:74` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/consent.lua:105` |
| AddEventHandler | client | `onClientResourceStart` | `resourceName` | `client/inventory_metadata.lua:80` |
| RegisterNetEvent | client | `advanced_vet:client:kennelProps` | `rows` | `client/kennel_objects.lua:41` |
| RegisterNetEvent | client | `advanced_vet:client:placementOverrideUpdated` | `row` | `client/kennel_objects.lua:47` |
| RegisterNetEvent | client | `advanced_vet:client:placementOverrideDeleted` | `clinicId, kind, key` | `client/kennel_objects.lua:54` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/kennel_objects.lua:66` |
| RegisterNetEvent | client | `advanced_vet:client:openClinicPharmacy` | `Named function/dynamic handler; inspect source` | `client/locations.lua:37` |
| RegisterNetEvent | client | `advanced_vet:client:openPharmacy` | `locationId, label, patient, products, prescriptions` | `client/locations.lua:42` |
| RegisterNetEvent | client | `advanced_vet:client:runtimePlacements` | `overrides` | `client/locations.lua:315` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/locations.lua:392` |
| RegisterNetEvent | client | `advanced_vet:client:openNearestPatient` | `locationId` | `client/main.lua:28` |
| RegisterNetEvent | client | `advanced_vet:client:openPatient` | `patient, history, treatments` | `client/main.lua:54` |
| RegisterNetEvent | client | `advanced_vet:client:openRecords` | `history` | `client/main.lua:65` |
| RegisterNetEvent | client | `advanced_vet:client:notify` | `message` | `client/main.lua:72` |
| RegisterNetEvent | client | `advanced_vet:client:refreshPatient` | `` | `client/main.lua:79` |
| RegisterNetEvent | client | `advanced_vet:client:nativeRevive` | `` | `client/main.lua:109` |
| RegisterNetEvent | client | `advanced_vet:client:verifySkyInjuryClear` | `token, resourceName, delayMs` | `client/main.lua:169` |
| RegisterNetEvent | client | `advanced_vet:client:applyTreatment` | `treatment` | `client/main.lua:240` |
| RegisterNetEvent | client | `advanced_vet:client:applyEntityTreatment` | `netId, treatment` | `client/main.lua:252` |
| RegisterNetEvent | client | `advanced_vet:client:updateFrameworkNeeds` | `hunger, thirst` | `client/main.lua:284` |
| exports | client | `OpenNearestPatient` | `Named function/dynamic handler; inspect source` | `client/main.lua:328` |
| RegisterNetEvent | client | `advanced_vet:client:applyMedicineEffect` | `productKey, productName, effects` | `client/medicine.lua:328` |
| RegisterNetEvent | client | `advanced_vet:client:medicineAdministered` | `productName` | `client/medicine.lua:388` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/medicine.lua:415` |
| RegisterNUICallback | client | `close` | `_, cb` | `client/nui.lua:179` |
| RegisterNUICallback | client | `backToClinic` | `data, cb` | `client/nui.lua:184` |
| RegisterNUICallback | client | `triage` | `data, cb` | `client/nui.lua:210` |
| RegisterNUICallback | client | `treat` | `data, cb` | `client/nui.lua:239` |
| RegisterNUICallback | client | `clinicAction` | `data, cb` | `client/nui.lua:263` |
| RegisterNUICallback | client | `dispense` | `data, cb` | `client/nui.lua:300` |
| RegisterNUICallback | client | `placement` | `data, cb` | `client/nui.lua:326` |
| RegisterNUICallback | client | `moduleAction` | `data, cb` | `client/nui.lua:371` |
| RegisterNUICallback | client | `refresh` | `_, cb` | `client/nui.lua:435` |
| RegisterNetEvent | client | `advanced_vet:client:placeSelfOnTable` | `data` | `client/patient_placement.lua:514` |
| RegisterNetEvent | client | `advanced_vet:client:releaseSelfFromTable` | `release` | `client/patient_placement.lua:557` |
| RegisterNetEvent | client | `advanced_vet:client:placeEntityOnTable` | `netId, data` | `client/patient_placement.lua:581` |
| RegisterNetEvent | client | `advanced_vet:client:releaseEntityFromTable` | `netId, release` | `client/patient_placement.lua:631` |
| RegisterCommand | client | `vetbdogsleeptest` | `` | `client/patient_placement.lua:853` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/patient_placement.lua:894` |
| RegisterCommand | client | `vetposecheck` | `` | `client/patient_placement.lua:931` |
| RegisterCommand | client | `vetgetup` | `` | `client/patient_placement.lua:961` |
| RegisterCommand | client | `vettablepos` | `_, args` | `client/patient_placement.lua:979` |
| RegisterCommand | client | `vetkennelpos` | `_, args` | `client/patient_placement.lua:1042` |
| RegisterNetEvent | client | `advanced_vet:client:placementOverrides` | `overrides` | `client/placement_editor.lua:2035` |
| RegisterNetEvent | client | `advanced_vet:client:placementOverrideUpdated` | `row` | `client/placement_editor.lua:2055` |
| RegisterNetEvent | client | `advanced_vet:client:placementSaveResult` | `result` | `client/placement_editor.lua:2107` |
| RegisterNetEvent | client | `advanced_vet:client:placementOverrideSaved` | `row` | `client/placement_editor.lua:2156` |
| RegisterNetEvent | client | `advanced_vet:client:placementOverrideDeleted` | `clinicId, kind, key` | `client/placement_editor.lua:2165` |
| RegisterCommand | client | `vetsetup` | `` | `client/placement_editor.lua:2183` |
| AddEventHandler | client | `onResourceStop` | `resourceName` | `client/placement_editor.lua:2202` |
| RegisterNetEvent | server | `advanced_vet:server:consentResponse` | `token, accepted` | `server/consent.lua:123` |
| AddEventHandler | server | `playerDropped` | `` | `server/consent.lua:141` |
| RegisterNetEvent | server | `advanced_vet:server:skyInjuryVerifyResult` | `token,         supported,         hasProfile,         schema,         summary,         reason` | `server/death_bridge.lua:257` |
| AddEventHandler | server | `playerDropped` | `` | `server/death_bridge.lua:461` |
| RegisterNetEvent | server | `advanced_vet:server:openPatient` | `target, clinicId` | `server/main.lua:502` |
| RegisterNetEvent | server | `advanced_vet:server:triage` | `target, clinicId` | `server/main.lua:848` |
| RegisterNetEvent | server | `advanced_vet:server:treat` | `target, treatmentId, notes` | `server/main.lua:935` |
| RegisterNetEvent | server | `advanced_vet:server:records` | `` | `server/main.lua:1060` |
| RegisterNetEvent | server | `advanced_vet:server:openPharmacy` | `clinicId, target` | `server/main.lua:2108` |
| RegisterNetEvent | server | `advanced_vet:server:dispense` | `clinicId, target, productKey, notes` | `server/main.lua:2186` |
| RegisterNetEvent | server | `advanced_vet:server:patientPlacement` | `clinicId, station, target, action` | `server/main.lua:3116` |
| RegisterNetEvent | server | `advanced_vet:server:openModule` | `clinicId, moduleType, target` | `server/main.lua:3234` |
| RegisterNetEvent | server | `advanced_vet:server:moduleAction` | `clinicId, moduleType, target, action, data` | `server/main.lua:3342` |
| RegisterNetEvent | server | `advanced_vet:server:myInvoices` | `` | `server/main.lua:4607` |
| RegisterNetEvent | server | `advanced_vet:server:payInvoice` | `invoiceId, provider` | `server/main.lua:4634` |
| exports | server | `IsVeterinarian` | `src` | `server/main.lua:4813` |
| exports | server | `IsAdvancedK9Patient` | `src` | `server/main.lua:4822` |
| RegisterNetEvent | server | `advanced_vet:server:selfReleasePlacement` | `` | `server/main.lua:4868` |
| AddEventHandler | server | `playerDropped` | `` | `server/main.lua:5059` |
| AddEventHandler | server | `playerDropped` | `` | `server/main.lua:5176` |
| exports | server | `useVetMedicine` | `event, item, inventory, slot, data` | `server/medicine.lua:901` |
| AddEventHandler | server | `playerDropped` | `` | `server/medicine.lua:973` |
| AddEventHandler | server | `onResourceStart` | `resource` | `server/medicine.lua:984` |
| AddEventHandler | server | `onResourceStop` | `resource` | `server/medicine.lua:1008` |
| RegisterNetEvent | server | `advanced_vet:server:requestKennelProps` | `` | `server/placement_editor.lua:272` |
| RegisterNetEvent | server | `advanced_vet:server:requestPlacementOverrides` | `` | `server/placement_editor.lua:283` |
| RegisterNetEvent | server | `advanced_vet:server:requestRuntimePlacements` | `` | `server/placement_editor.lua:302` |
| RegisterNetEvent | server | `advanced_vet:server:savePlacementOverride` | `payload` | `server/placement_editor.lua:453` |
| RegisterNetEvent | server | `advanced_vet:server:deletePlacementOverride` | `clinicId, kind, key` | `server/placement_editor.lua:595` |
