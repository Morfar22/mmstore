# Advanced K9 — Internal registration reference

This index locates literal registrations in the uploaded code, including local handlers, network handlers, NUI and callback wrappers. It is a maintainer lookup, **not a stable public API contract**. Event signature parameters exclude the implicit server event source. Registration does not prove an event should be called externally. Preserve original sender, session, permission, proximity, metadata and state checks.

Dynamic commands/exports and config-selected names also exist. See the commands/export pages for resolved names. Entries in comments or unexecuted diagnostic branches can be present; developer-only registration conditions must be checked in source. Parameters are nearest inline handler signatures, not validated documentation of payload schemas.

| Registration | Side | Name | Handler parameters | Source |
| --- | --- | --- | --- | --- |
| RegisterNetEvent | client | `advanced_k9:client:approvalStatus` | `status` | `client/admin.lua:145` |
| RegisterNetEvent | client | `advanced_k9:client:adminPanelData` | `players` | `client/admin.lua:149` |
| RegisterNetEvent | client | `advanced_k9:client:adoptionInvite` | `owner, ownerName` | `client/adoption.lua:413` |
| RegisterNetEvent | client | `advanced_k9:client:adoptionStatus` | `status` | `client/adoption.lua:435` |
| RegisterNetEvent | client | `advanced_k9:client:collarData` | `data` | `client/adoption.lua:441` |
| RegisterNUICallback | client | `collarClose` | `_, cb` | `client/adoption.lua:457` |
| RegisterCommand | client | `k9collar` | `` | `client/adoption.lua:466` |
| AddEventHandler | client | `onClientResourceStart` | `resource` | `client/adoption.lua:501` |
| AddEventHandler | client | `onClientResourceStop` | `resource` | `client/adoption.lua:513` |
| RegisterCommand | client | `k9targetdebug` | `` | `client/adoption.lua:524` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/adoption.lua:556` |
| RegisterNetEvent | client | `advanced_k9:client:alertPending` | `token, kind, hint, ttl` | `client/alerts.lua:188` |
| RegisterNetEvent | client | `advanced_k9:client:alertExpired` | `` | `client/alerts.lua:218` |
| RegisterCommand | client | `k9alert` | `` | `client/alerts.lua:225` |
| RegisterNetEvent | client | `advanced_k9:client:receiveBite` | `damage, ragdollChance, ragdollTime` | `client/attack.lua:134` |
| RegisterCommand | client | `+k9_bite` | `` | `client/attack.lua:151` |
| RegisterCommand | client | `-k9_bite` | `` | `client/attack.lua:168` |
| RegisterKeyMapping | client | `+k9_bite` | `Named function/dynamic handler; inspect source` | `client/attack.lua:170` |
| RegisterNetEvent | client | `advanced_k9:client:buriedTrainingStatus` | `count, message` | `client/buried_training.lua:553` |
| RegisterNetEvent | client | `advanced_k9:client:searchBuriedTraining` | `` | `client/buried_training.lua:573` |
| RegisterNetEvent | client | `advanced_k9:client:startBuriedTrack` | `id, points` | `client/buried_training.lua:577` |
| RegisterNetEvent | client | `advanced_k9:client:handlerBuriedPrepared` | `id, pos` | `client/buried_training.lua:597` |
| RegisterNetEvent | client | `advanced_k9:client:buriedFound` | `id, pos` | `client/buried_training.lua:603` |
| RegisterCommand | client | `k9bury` | `Named function/dynamic handler; inspect source` | `client/buried_training.lua:818` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/buried_training.lua:823` |
| RegisterNetEvent | client | `advanced_k9:client:placeFoodBowl` | `` | `client/care.lua:132` |
| RegisterNetEvent | client | `advanced_k9:client:placeWaterBowl` | `` | `client/care.lua:136` |
| RegisterNetEvent | client | `advanced_k9:client:registerBowl` | `data` | `client/care.lua:140` |
| RegisterNetEvent | client | `advanced_k9:client:updateBowl` | `id,uses` | `client/care.lua:152` |
| RegisterNetEvent | client | `advanced_k9:client:removeBowl` | `id,netId` | `client/care.lua:158` |
| RegisterNetEvent | client | `advanced_k9:client:bowlRejected` | `netId,reason` | `client/care.lua:168` |
| RegisterCommand | client | `k9food` | `` | `client/care.lua:363` |
| RegisterCommand | client | `k9water` | `` | `client/care.lua:367` |
| RegisterCommand | client | `k9clearbowls` | `` | `client/care.lua:371` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/care.lua:376` |
| RegisterNetEvent | client | `advanced_k9:client:applyEsxNeeds` | `hunger,thirst` | `client/care.lua:455` |
| RegisterNetEvent | client | `advanced_k9:client:overfedDump` | `` | `client/care.lua:650` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/care.lua:667` |
| RegisterNetEvent | client | `advanced_k9:client:civilTrainingDrill` | `drill, handlerId` | `client/civil_training.lua:50` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/command_emotes.lua:243` |
| exports | client | `AreDogEmotesLocked` | `` | `client/dog_emote_lock.lua:124` |
| exports | client | `CanUseHumanEmotes` | `` | `client/dog_emote_lock.lua:128` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/dog_emote_lock.lua:168` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/fall_protection.lua:151` |
| RegisterNetEvent | client | `advanced_k9:client:foundBark` | `reason` | `client/found_bark.lua:18` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/found_bark.lua:79` |
| RegisterNetEvent | client | `advanced_k9:client:notify` | `message,typ,duration,soundKind` | `client/main.lua:103` |
| RegisterNetEvent | client | `advanced_k9:client:pairInvite` | `handlerId, handlerName, dogType` | `client/main.lua:277` |
| RegisterNetEvent | client | `advanced_k9:client:paired` | `role, partner, partnerName` | `client/main.lua:295` |
| RegisterNetEvent | client | `advanced_k9:client:handlerRoster` | `dogs, activeDog` | `client/main.lua:336` |
| RegisterNetEvent | client | `advanced_k9:client:activeDogChanged` | `dog, dogName` | `client/main.lua:351` |
| RegisterNetEvent | client | `advanced_k9:client:unpaired` | `reason` | `client/main.lua:358` |
| RegisterNetEvent | client | `advanced_k9:client:dogCommand` | `command, context` | `client/main.lua:390` |
| RegisterNetEvent | client | `advanced_k9:client:dogTypeChanged` | `dogType, stats` | `client/main.lua:2022` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/main.lua:2084` |
| RegisterNetEvent | client | `advanced_k9:client:selfTestResult` | `checks` | `client/main.lua:2092` |
| RegisterCommand | client | `k9selftest` | `` | `client/main.lua:2114` |
| RegisterCommand | client | `+k9_handler_heel` | `` | `client/main.lua:2283` |
| RegisterCommand | client | `-k9_handler_heel` | `` | `client/main.lua:2284` |
| RegisterKeyMapping | client | `+k9_handler_heel` | `Named function/dynamic handler; inspect source` | `client/main.lua:2285` |
| RegisterCommand | client | `+k9_handler_stay` | `` | `client/main.lua:2287` |
| RegisterCommand | client | `-k9_handler_stay` | `` | `client/main.lua:2288` |
| RegisterKeyMapping | client | `+k9_handler_stay` | `Named function/dynamic handler; inspect source` | `client/main.lua:2289` |
| RegisterCommand | client | `+k9_handler_recall` | `` | `client/main.lua:2291` |
| RegisterCommand | client | `-k9_handler_recall` | `` | `client/main.lua:2292` |
| RegisterKeyMapping | client | `+k9_handler_recall` | `Named function/dynamic handler; inspect source` | `client/main.lua:2293` |
| RegisterCommand | client | `+k9_handler_vehicleout` | `` | `client/main.lua:2297` |
| RegisterCommand | client | `-k9_handler_vehicleout` | `` | `client/main.lua:2298` |
| RegisterKeyMapping | client | `+k9_handler_vehicleout` | `Named function/dynamic handler; inspect source` | `client/main.lua:2299` |
| RegisterCommand | client | `+k9_dog_vehicleout` | `` | `client/main.lua:2301` |
| RegisterCommand | client | `-k9_dog_vehicleout` | `` | `client/main.lua:2302` |
| RegisterKeyMapping | client | `+k9_dog_vehicleout` | `Named function/dynamic handler; inspect source` | `client/main.lua:2303` |
| RegisterCommand | client | `k9nearby` | `` | `client/main.lua:2313` |
| RegisterNetEvent | client | `advanced_k9:client:preferences` | `data` | `client/notification_settings.lua:63` |
| RegisterCommand | client | `k9notify` | `` | `client/notification_settings.lua:305` |
| RegisterNetEvent | client | `advanced_k9:client:parkour` | `` | `client/parkour.lua:370` |
| RegisterCommand | client | `+k9_parkour` | `` | `client/parkour.lua:374` |
| RegisterCommand | client | `-k9_parkour` | `` | `client/parkour.lua:378` |
| RegisterKeyMapping | client | `+k9_parkour` | `Named function/dynamic handler; inspect source` | `client/parkour.lua:380` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/parkour.lua:387` |
| RegisterNetEvent | client | `advanced_k9:client:passport` | `passport` | `client/passport.lua:133` |
| RegisterCommand | client | `k9passport` | `` | `client/passport.lua:158` |
| RegisterNetEvent | client | `advanced_k9:client:petAnimation` | `role,otherServerId` | `client/petting.lua:59` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/petting.lua:87` |
| RegisterNetEvent | client | `advanced_k9:client:levelUp` | `level, levelName, unlocks` | `client/progression.lua:181` |
| RegisterNetEvent | client | `advanced_k9:client:civilRankUp` | `rank, rankName, unlocks` | `client/progression.lua:205` |
| RegisterCommand | client | `+k9_quick_sit` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:241` |
| RegisterCommand | client | `-k9_quick_sit` | `` | `client/quick_actions.lua:242` |
| RegisterKeyMapping | client | `+k9_quick_sit` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:243` |
| RegisterCommand | client | `+k9_quick_down` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:245` |
| RegisterCommand | client | `-k9_quick_down` | `` | `client/quick_actions.lua:246` |
| RegisterKeyMapping | client | `+k9_quick_down` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:247` |
| RegisterCommand | client | `+k9_quick_bark` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:249` |
| RegisterCommand | client | `-k9_quick_bark` | `` | `client/quick_actions.lua:250` |
| RegisterKeyMapping | client | `+k9_quick_bark` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:251` |
| RegisterCommand | client | `+k9_quick_bark4` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:253` |
| RegisterCommand | client | `-k9_quick_bark4` | `` | `client/quick_actions.lua:254` |
| RegisterKeyMapping | client | `+k9_quick_bark4` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:255` |
| RegisterCommand | client | `+k9_quick_whine1` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:257` |
| RegisterCommand | client | `-k9_quick_whine1` | `` | `client/quick_actions.lua:258` |
| RegisterKeyMapping | client | `+k9_quick_whine1` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:259` |
| RegisterCommand | client | `+k9_quick_whine2` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:261` |
| RegisterCommand | client | `-k9_quick_whine2` | `` | `client/quick_actions.lua:262` |
| RegisterKeyMapping | client | `+k9_quick_whine2` | `Named function/dynamic handler; inspect source` | `client/quick_actions.lua:263` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/quick_actions.lua:268` |
| RegisterCommand | client | `k9recalltest` | `` | `client/recall_outline.lua:380` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/recall_outline.lua:408` |
| RegisterNetEvent | client | `advanced_k9:client:scentArticleReady` | `targetName, ttl` | `client/scent_articles.lua:108` |
| RegisterNetEvent | client | `advanced_k9:client:scentArticleCleared` | `` | `client/scent_articles.lua:134` |
| RegisterCommand | client | `k9article` | `` | `client/scent_articles.lua:143` |
| RegisterNetEvent | client | `advanced_k9:client:sniff` | `` | `client/sniff.lua:9` |
| RegisterNetEvent | client | `advanced_k9:client:stationaryKennelsData` | `data` | `client/stationary_kennels.lua:73` |
| RegisterNetEvent | client | `advanced_k9:client:stationaryKennelEnter` | `kennel` | `client/stationary_kennels.lua:222` |
| RegisterNetEvent | client | `advanced_k9:client:stationaryKennelExit` | `kennel` | `client/stationary_kennels.lua:237` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/stationary_kennels.lua:266` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/swimming.lua:112` |
| RegisterNetEvent | client | `advanced_k9:client:tackle` | `` | `client/tackle.lua:48` |
| RegisterNetEvent | client | `advanced_k9:client:receiveTackle` | `duration` | `client/tackle.lua:121` |
| RegisterNetEvent | client | `advanced_k9:client:searchHandlerScent` | `` | `client/tracking.lua:109` |
| RegisterNetEvent | client | `advanced_k9:client:searchScent` | `` | `client/tracking.lua:129` |
| RegisterNetEvent | client | `advanced_k9:client:scentAcquired` | `target, segment, points, isHandlerTrail, isArticle` | `client/tracking.lua:148` |
| RegisterNetEvent | client | `advanced_k9:client:trail` | `points` | `client/tracking.lua:203` |
| RegisterNetEvent | client | `advanced_k9:client:trailBroken` | `reason` | `client/tracking.lua:218` |
| RegisterNetEvent | client | `advanced_k9:client:trailFinished` | `` | `client/tracking.lua:228` |
| RegisterNetEvent | client | `advanced_k9:client:stopTrack` | `silent` | `client/tracking.lua:233` |
| RegisterNetEvent | client | `advanced_k9:client:externalTrainerState` | `active, otherServerId` | `client/training.lua:3` |
| RegisterNetEvent | client | `advanced_k9:client:trainingStats` | `stats, requested` | `client/training.lua:147` |
| RegisterNetEvent | client | `advanced_k9:client:trainingRequest` | `requestId, drill, handlerId, timeoutMs` | `client/training.lua:286` |
| RegisterNetEvent | client | `advanced_k9:client:trainingRequestExpired` | `requestId` | `client/training.lua:330` |
| RegisterCommand | client | `k9trainingaccept` | `` | `client/training.lua:350` |
| RegisterCommand | client | `k9trainingdecline` | `` | `client/training.lua:358` |
| RegisterNetEvent | client | `advanced_k9:client:trainingDrill` | `drill, handlerId` | `client/training.lua:366` |
| RegisterCommand | client | `k9balltune` | `` | `client/training.lua:902` |
| RegisterCommand | client | `k9ballprint` | `Named function/dynamic handler; inspect source` | `client/training.lua:912` |
| RegisterNetEvent | client | `advanced_k9:client:throwFetchBall` | `` | `client/training.lua:956` |
| RegisterNetEvent | client | `advanced_k9:client:externalTrainerFetch` | `dogId` | `client/training.lua:1056` |
| RegisterNetEvent | client | `advanced_k9:client:fetchStarted` | `netId, handlerId` | `client/training.lua:1067` |
| RegisterNetEvent | client | `advanced_k9:client:cleanupFetch` | `netId` | `client/training.lua:1087` |
| RegisterNetEvent | client | `advanced_k9:client:fetchHandedToHandler` | `netId, handlerId` | `client/training.lua:1092` |
| RegisterNetEvent | client | `advanced_k9:client:receiveFetchBall` | `netId, dogId` | `client/training.lua:1116` |
| RegisterNetEvent | client | `advanced_k9:client:rethrowFetchBall` | `netId, dogId, power` | `client/training.lua:1171` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/training.lua:1399` |
| RegisterNUICallback | client | `contextSelect` | `data, cb` | `client/ui_bridge.lua:537` |
| RegisterNUICallback | client | `contextBack` | `_, cb` | `client/ui_bridge.lua:562` |
| RegisterNUICallback | client | `uiClose` | `_, cb` | `client/ui_bridge.lua:579` |
| RegisterNUICallback | client | `dialogResult` | `data, cb` | `client/ui_bridge.lua:584` |
| RegisterNUICallback | client | `progressComplete` | `data, cb` | `client/ui_bridge.lua:595` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/ui_bridge.lua:606` |
| RegisterCommand | client | `k9carsleep` | `` | `client/vehicle.lua:1196` |
| RegisterCommand | client | `k9carsit` | `` | `client/vehicle.lua:1206` |
| RegisterCommand | client | `k9cageprint` | `Named function/dynamic handler; inspect source` | `client/vehicle.lua:1767` |
| RegisterCommand | client | `k9cagecreate` | `` | `client/vehicle.lua:1773` |
| RegisterCommand | client | `k9cageadjust` | `` | `client/vehicle.lua:1789` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleSlotGranted` | `requestId,         netId,         slotIndex,         row` | `client/vehicle.lua:1980` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleSlotDenied` | `requestId,         reason,         configuredCount` | `client/vehicle.lua:2145` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleEnter` | `` | `client/vehicle.lua:2204` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleToggle` | `` | `client/vehicle.lua:2447` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleExit` | `` | `client/vehicle.lua:2482` |
| AddEventHandler | client | `advanced_k9:client:unpaired` | `` | `client/vehicle.lua:2552` |
| RegisterCommand | client | `k9safetest` | `` | `client/vehicle.lua:2575` |
| RegisterCommand | client | `k9vehiclestate` | `` | `client/vehicle.lua:2653` |
| RegisterCommand | client | `k9cam` | `` | `client/vehicle.lua:4527` |
| RegisterCommand | client | `k9setup` | `` | `client/vehicle.lua:4537` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/vehicle.lua:4795` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleAnchors` | `cache` | `client/vehicle_anchors.lua:27` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleAnchorUpdated` | `anchor` | `client/vehicle_anchors.lua:37` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleAnchorDeleted` | `modelKey, modelHash` | `client/vehicle_anchors.lua:58` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleCameras` | `cache` | `client/vehicle_cameras.lua:27` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleCameraUpdated` | `camera` | `client/vehicle_cameras.lua:37` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleCameraDeleted` | `modelKey, modelHash` | `client/vehicle_cameras.lua:58` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleDiagDump` | `entries` | `client/vehicle_diag.lua:135` |
| RegisterCommand | client | `k9diaglocal` | `` | `client/vehicle_diag.lua:173` |
| RegisterCommand | client | `k9diagserver` | `` | `client/vehicle_diag.lua:204` |
| RegisterCommand | client | `k9diagtoggle` | `` | `client/vehicle_diag.lua:214` |
| RegisterCommand | client | `k9camsetup` | `` | `client/vehicle_premium_setup.lua:711` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/vehicle_premium_setup.lua:723` |
| RegisterNetEvent | client | `advanced_k9:client:softCageState` | `state` | `client/vehicle_remote_sync.lua:52` |
| RegisterNetEvent | client | `advanced_k9:client:softCageClear` | `dog, reason` | `client/vehicle_remote_sync.lua:61` |
| RegisterNetEvent | client | `advanced_k9:client:softCageStates` | `states` | `client/vehicle_remote_sync.lua:86` |
| AddEventHandler | client | `playerSpawned` | `` | `client/vehicle_remote_sync.lua:148` |
| RegisterCommand | client | `k9remotesync` | `` | `client/vehicle_remote_sync.lua:288` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleSlotStatus` | `netId, summary` | `client/vehicle_slot_setup.lua:2276` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleCageAdminAccess` | `allowed` | `client/vehicle_slot_setup.lua:2487` |
| RegisterCommand | client | `k9templatesclear` | `` | `client/vehicle_slot_setup.lua:2694` |
| AddEventHandler | client | `onResourceStop` | `resource` | `client/vehicle_slot_setup.lua:2704` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleSlots` | `cache` | `client/vehicle_slots.lua:106` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleSlotUpdated` | `row` | `client/vehicle_slots.lua:122` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleSlotDeleted` | `modelKey, modelHash, slotIndex` | `client/vehicle_slots.lua:141` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleSlotsModelCleared` | `modelKey, modelHash` | `client/vehicle_slots.lua:188` |
| RegisterNetEvent | client | `advanced_k9:client:vehicleSlotsAllCleared` | `` | `client/vehicle_slots.lua:217` |
| RegisterNetEvent | server | `advanced_k9:server:requestAdoptionStatus` | `` | `server/adoption.lua:400` |
| RegisterNetEvent | server | `advanced_k9:server:requestAdoption` | `` | `server/adoption.lua:405` |
| RegisterNetEvent | server | `advanced_k9:server:adoptionResponse` | `owner, accepted` | `server/adoption.lua:478` |
| RegisterNetEvent | server | `advanced_k9:server:renameAdoptedDog` | `name` | `server/adoption.lua:604` |
| RegisterNetEvent | server | `advanced_k9:server:dissolveAdoption` | `` | `server/adoption.lua:663` |
| RegisterNetEvent | server | `advanced_k9:server:getCollar` | `dog` | `server/adoption.lua:731` |
| AddEventHandler | server | `sky_phone:server:apiReady` | `` | `server/adoption.lua:808` |
| AddEventHandler | server | `onServerResourceStart` | `resource` | `server/adoption.lua:814` |
| RegisterCommand | server | `k9phonedebug` | `src` | `server/adoption.lua:825` |
| AddEventHandler | server | `playerDropped` | `` | `server/adoption.lua:907` |
| RegisterNetEvent | server | `advanced_k9:server:manualAlert` | `token, style` | `server/alerts.lua:92` |
| AddEventHandler | server | `playerDropped` | `` | `server/alerts.lua:220` |
| RegisterNetEvent | server | `advanced_k9:server:requestApprovalStatus` | `` | `server/approvals.lua:252` |
| RegisterNetEvent | server | `advanced_k9:server:requestAdminPanel` | `` | `server/approvals.lua:262` |
| RegisterNetEvent | server | `advanced_k9:server:setApproval` | `target,role,value` | `server/approvals.lua:277` |
| RegisterNetEvent | server | `advanced_k9:server:setBothApprovals` | `target,value` | `server/approvals.lua:336` |
| RegisterNetEvent | server | `advanced_k9:server:setFullLevelAccess` | `target,value` | `server/approvals.lua:388` |
| RegisterNetEvent | server | `advanced_k9:server:bitePlayer` | `target` | `server/attack.lua:7` |
| RegisterNetEvent | server | `advanced_k9:server:buryTrainingArticle` | `payload` | `server/buried_training.lua:106` |
| RegisterNetEvent | server | `advanced_k9:server:searchBuriedScent` | `pos` | `server/buried_training.lua:181` |
| RegisterNetEvent | server | `advanced_k9:server:markBuriedFound` | `id, pos` | `server/buried_training.lua:292` |
| AddEventHandler | server | `playerDropped` | `` | `server/buried_training.lua:387` |
| exports | server | `ApplyExternalCareNeeds` | `dog, hunger, thirst` | `server/care.lua:287` |
| exports | server | `AdjustExternalCareNeeds` | `dog, hungerDelta, thirstDelta` | `server/care.lua:314` |
| RegisterNetEvent | server | `advanced_k9:server:syncNeedsFromHud` | `reportedHunger,reportedThirst` | `server/care.lua:321` |
| RegisterNetEvent | server | `advanced_k9:server:registerBowl` | `kind,netId,coords` | `server/care.lua:336` |
| RegisterNetEvent | server | `advanced_k9:server:useBowl` | `id` | `server/care.lua:463` |
| RegisterNetEvent | server | `advanced_k9:server:removeMyBowls` | `` | `server/care.lua:597` |
| AddEventHandler | server | `playerDropped` | `` | `server/care.lua:689` |
| RegisterNetEvent | server | `advanced_k9:server:setDogType` | `dogType` | `server/civil_training.lua:51` |
| RegisterNetEvent | server | `advanced_k9:server:startCivilDrill` | `drill` | `server/civil_training.lua:141` |
| RegisterNetEvent | server | `advanced_k9:server:civilDrillResult` | `drill, success` | `server/civil_training.lua:218` |
| AddEventHandler | server | `playerDropped` | `` | `server/civil_training.lua:274` |
| RegisterNetEvent | server | `advanced_k9:server:tackleReached` | `target` | `server/main.lua:1` |
| RegisterNetEvent | server | `advanced_k9:server:selfTest` | `` | `server/main.lua:31` |
| exports | server | `StartVetTrainingSession` | `trainer, dog` | `server/pairing.lua:390` |
| exports | server | `EndVetTrainingSession` | `trainer` | `server/pairing.lua:400` |
| exports | server | `VetTrainerCommand` | `trainer, command` | `server/pairing.lua:409` |
| exports | server | `GetVetTrainingDog` | `trainer` | `server/pairing.lua:419` |
| exports | server | `GetActiveK9Teams` | `` | `server/pairing.lua:570` |
| RegisterNetEvent | server | `advanced_k9:server:setActiveDog` | `dog` | `server/pairing.lua:886` |
| RegisterNetEvent | server | `advanced_k9:server:inviteDog` | `target` | `server/pairing.lua:895` |
| RegisterNetEvent | server | `advanced_k9:server:pairResponse` | `handler, accepted` | `server/pairing.lua:976` |
| RegisterNetEvent | server | `advanced_k9:server:handlerCommand` | `command` | `server/pairing.lua:1050` |
| RegisterNetEvent | server | `advanced_k9:server:unpair` | `` | `server/pairing.lua:1133` |
| AddEventHandler | server | `playerDropped` | `` | `server/pairing.lua:1150` |
| AddEventHandler | server | `playerDropped` | `` | `server/pairing.lua:1217` |
| RegisterCommand | server | `k9teamdiag` | `src` | `server/pairing.lua:1233` |
| RegisterNetEvent | server | `advanced_k9:server:requestPassport` | `` | `server/passport.lua:182` |
| RegisterNetEvent | server | `advanced_k9:server:setPassportSpecialization` | `value` | `server/passport.lua:206` |
| exports | server | `GetK9Passport` | `dog` | `server/passport.lua:295` |
| AddEventHandler | server | `onServerResourceStart` | `resource` | `server/phone_bridge.lua:1184` |
| RegisterNetEvent | server | `advanced_k9:server:requestPreferences` | `` | `server/preferences.lua:124` |
| RegisterNetEvent | server | `advanced_k9:server:savePreferences` | `data` | `server/preferences.lua:160` |
| RegisterNetEvent | server | `advanced_k9:server:createScentArticle` | `target` | `server/scent_articles.lua:47` |
| RegisterNetEvent | server | `advanced_k9:server:clearScentArticle` | `` | `server/scent_articles.lua:122` |
| AddEventHandler | server | `playerDropped` | `` | `server/scent_articles.lua:141` |
| RegisterNetEvent | server | `advanced_k9:server:sniff` | `target` | `server/sniff.lua:36` |
| RegisterNetEvent | server | `advanced_k9:server:requestStationaryKennels` | `` | `server/stationary_kennels.lua:76` |
| RegisterNetEvent | server | `advanced_k9:server:saveStationaryKennel` | `data` | `server/stationary_kennels.lua:80` |
| RegisterNetEvent | server | `advanced_k9:server:deleteStationaryKennel` | `id` | `server/stationary_kennels.lua:128` |
| RegisterNetEvent | server | `advanced_k9:server:deleteAllStationaryKennels` | `confirm` | `server/stationary_kennels.lua:142` |
| RegisterNetEvent | server | `advanced_k9:server:stationaryKennelEnter` | `id` | `server/stationary_kennels.lua:208` |
| RegisterNetEvent | server | `advanced_k9:server:stationaryKennelExit` | `` | `server/stationary_kennels.lua:227` |
| RegisterNetEvent | server | `advanced_k9:server:stationaryKennelToggle` | `id` | `server/stationary_kennels.lua:238` |
| AddEventHandler | server | `playerDropped` | `` | `server/stationary_kennels.lua:249` |
| exports | server | `GetStationaryKennels` | `` | `server/stationary_kennels.lua:272` |
| exports | server | `GetDogStationaryKennel` | `dog` | `server/stationary_kennels.lua:273` |
| RegisterNetEvent | server | `advanced_k9:server:scentPoint` | `data` | `server/tracking.lua:163` |
| RegisterNetEvent | server | `advanced_k9:server:searchNearbyScent` | `pos` | `server/tracking.lua:227` |
| RegisterNetEvent | server | `advanced_k9:server:searchHandlerScent` | `pos` | `server/tracking.lua:385` |
| RegisterNetEvent | server | `advanced_k9:server:trackScentArticle` | `pos` | `server/tracking.lua:511` |
| RegisterNetEvent | server | `advanced_k9:server:trackingStatus` | `status` | `server/tracking.lua:680` |
| RegisterNetEvent | server | `advanced_k9:server:getTrail` | `target, segment, lastReachedId` | `server/tracking.lua:716` |
| RegisterNetEvent | server | `advanced_k9:server:endTrailSearch` | `target, pos` | `server/tracking.lua:730` |
| AddEventHandler | server | `playerDropped` | `` | `server/tracking.lua:782` |
| RegisterNetEvent | server | `advanced_k9:server:trainingStats` | `silent` | `server/training.lua:860` |
| RegisterNetEvent | server | `advanced_k9:server:petDog` | `` | `server/training.lua:867` |
| RegisterNetEvent | server | `advanced_k9:server:treatDog` | `` | `server/training.lua:895` |
| RegisterNetEvent | server | `advanced_k9:server:trainingRequestResponse` | `requestId, accepted` | `server/training.lua:1094` |
| AddEventHandler | server | `playerDropped` | `` | `server/training.lua:1261` |
| RegisterNetEvent | server | `advanced_k9:server:startTrainingDrill` | `drill` | `server/training.lua:1316` |
| RegisterNetEvent | server | `advanced_k9:server:trainingDrillResult` | `drill, success` | `server/training.lua:1352` |
| RegisterNetEvent | server | `advanced_k9:server:startFetch` | `netId` | `server/training.lua:1432` |
| RegisterNetEvent | server | `advanced_k9:server:fetchComplete` | `netId` | `server/training.lua:1460` |
| RegisterNetEvent | server | `advanced_k9:server:rethrowFetch` | `netId, power` | `server/training.lua:1492` |
| RegisterNetEvent | server | `advanced_k9:server:endFetch` | `netId` | `server/training.lua:1540` |
| AddEventHandler | server | `playerDropped` | `` | `server/training.lua:1567` |
| RegisterNetEvent | server | `advanced_k9:server:requestVehicleAnchors` | `` | `server/vehicle_anchors.lua:258` |
| RegisterNetEvent | server | `advanced_k9:server:saveVehicleAnchor` | `payload` | `server/vehicle_anchors.lua:269` |
| RegisterNetEvent | server | `advanced_k9:server:deleteVehicleAnchor` | `modelKey, modelHash` | `server/vehicle_anchors.lua:436` |
| RegisterNetEvent | server | `advanced_k9:server:requestVehicleCameras` | `` | `server/vehicle_cameras.lua:157` |
| RegisterNetEvent | server | `advanced_k9:server:saveVehicleCamera` | `payload` | `server/vehicle_cameras.lua:168` |
| RegisterNetEvent | server | `advanced_k9:server:deleteVehicleCamera` | `modelKey, modelHash` | `server/vehicle_cameras.lua:301` |
| RegisterNetEvent | server | `advanced_k9:server:vehicleDiag` | `entry` | `server/vehicle_diag.lua:146` |
| RegisterNetEvent | server | `advanced_k9:server:requestVehicleDiagDump` | `` | `server/vehicle_diag.lua:204` |
| AddEventHandler | server | `playerDropped` | `` | `server/vehicle_diag.lua:222` |
| RegisterNetEvent | server | `advanced_k9:server:requestVehicleCageAdmin` | `` | `server/vehicle_slots.lua:677` |
| RegisterNetEvent | server | `advanced_k9:server:adminDeleteModelCages` | `modelKey, modelHash` | `server/vehicle_slots.lua:704` |
| RegisterNetEvent | server | `advanced_k9:server:adminDeleteAllCages` | `confirmation` | `server/vehicle_slots.lua:794` |
| RegisterNetEvent | server | `advanced_k9:server:requestVehicleSlots` | `` | `server/vehicle_slots.lua:867` |
| RegisterNetEvent | server | `advanced_k9:server:saveVehicleSlot` | `payload` | `server/vehicle_slots.lua:883` |
| RegisterNetEvent | server | `advanced_k9:server:deleteVehicleSlot` | `modelKey, modelHash, slotIndex` | `server/vehicle_slots.lua:1131` |
| RegisterNetEvent | server | `advanced_k9:server:reserveVehicleSlot` | `netId, modelKey, requestId` | `server/vehicle_slots.lua:1213` |
| RegisterNetEvent | server | `advanced_k9:server:softCageEntered` | `netId, slotIndex, postureKey` | `server/vehicle_slots.lua:1445` |
| RegisterNetEvent | server | `advanced_k9:server:updateSoftCagePosture` | `netId, slotIndex, postureKey` | `server/vehicle_slots.lua:1505` |
| RegisterNetEvent | server | `advanced_k9:server:requestSoftCageStates` | `` | `server/vehicle_slots.lua:1576` |
| RegisterNetEvent | server | `advanced_k9:server:vehicleSlotHeartbeat` | `netId, slotIndex` | `server/vehicle_slots.lua:1597` |
| RegisterNetEvent | server | `advanced_k9:server:releaseVehicleSlot` | `netId, slotIndex, reason` | `server/vehicle_slots.lua:1643` |
| RegisterNetEvent | server | `advanced_k9:server:requestVehicleSlotStatus` | `netId` | `server/vehicle_slots.lua:1678` |
| AddEventHandler | server | `playerDropped` | `` | `server/vehicle_slots.lua:1777` |
| AddEventHandler | shared | `onResourceStart` | `resource` | `shared/framework.lua:21` |
