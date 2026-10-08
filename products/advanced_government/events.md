# Internal registration reference

This index locates literal registrations in the uploaded code, including local handlers, network handlers, NUI and callback wrappers. It is a maintainer lookup, **not a stable public API contract**. Event signature parameters exclude the implicit server event source. Registration does not prove an event should be called externally. Preserve original sender, session, permission, proximity, metadata and state checks.

Dynamic commands/exports and config-selected names also exist. See the commands/export pages for resolved names. Entries in comments or unexecuted diagnostic branches can be present; developer-only registration conditions must be checked in source. Parameters are nearest inline handler signatures, not validated documentation of payload schemas.

| Registration        | Side   | Name                                            | Handler parameters                               | Source                      |
| ------------------- | ------ | ----------------------------------------------- | ------------------------------------------------ | --------------------------- |
| RegisterNetEvent    | client | `advanced_government:client:open`               | `Named function/dynamic handler; inspect source` | `client/main.lua:25`        |
| RegisterNUICallback | client | `close`                                         | `_, cb`                                          | `client/main.lua:26`        |
| RegisterNetEvent    | client | `advanced_government:client:refresh`            | \`\`                                             | `client/main.lua:45`        |
| AddEventHandler     | client | `QBCore:Client:OnPlayerUnload`                  | `Named function/dynamic handler; inspect source` | `client/main.lua:67`        |
| AddEventHandler     | client | `onClientResourceStop`                          | `resource`                                       | `client/main.lua:68`        |
| RegisterNetEvent    | client | `advanced_government:client:refreshAds`         | `Named function/dynamic handler; inspect source` | `client/main.lua:83`        |
| AddEventHandler     | client | `QBCore:Client:OnPlayerLoaded`                  | `Named function/dynamic handler; inspect source` | `client/main.lua:84`        |
| AddEventHandler     | server | `playerDropped`                                 | \`\`                                             | `server/main.lua:372`       |
| registerCallback    | server | `advanced_government:server:getDashboard`       | `source`                                         | `server/main.lua:374`       |
| registerCallback    | server | `advanced_government:server:getActiveAds`       | \`\`                                             | `server/main.lua:378`       |
| registerCallback    | server | `advanced_government:server:setTax`             | `source, data`                                   | `server/main.lua:384`       |
| registerCallback    | server | `advanced_government:server:treasuryTransfer`   | `source, data`                                   | `server/main.lua:398`       |
| registerCallback    | server | `advanced_government:server:registerCandidate`  | `source, data`                                   | `server/main.lua:411`       |
| registerCallback    | server | `advanced_government:server:donateCampaign`     | `source, data`                                   | `server/main.lua:451`       |
| registerCallback    | server | `advanced_government:server:vote`               | `source, data`                                   | `server/main.lua:477`       |
| registerCallback    | server | `advanced_government:server:assignCabinet`      | `source, data`                                   | `server/main.lua:491`       |
| registerCallback    | server | `advanced_government:server:removeCabinet`      | `source, data`                                   | `server/main.lua:510`       |
| registerCallback    | server | `advanced_government:server:createLaw`          | `source, data`                                   | `server/main.lua:523`       |
| registerCallback    | server | `advanced_government:server:voteLaw`            | `source, data`                                   | `server/main.lua:534`       |
| registerCallback    | server | `advanced_government:server:enactLaw`           | `source, data`                                   | `server/main.lua:552`       |
| registerCallback    | server | `advanced_government:server:createBudget`       | `source, data`                                   | `server/main.lua:562`       |
| registerCallback    | server | `advanced_government:server:createParty`        | `source, data`                                   | `server/main.lua:576`       |
| registerCallback    | server | `advanced_government:server:joinParty`          | `source, data`                                   | `server/main.lua:611`       |
| registerCallback    | server | `advanced_government:server:leaveParty`         | `source`                                         | `server/main.lua:627`       |
| registerCallback    | server | `advanced_government:server:purchaseCampaignAd` | `source, data`                                   | `server/main.lua:639`       |
| registerCallback    | server | `advanced_government:server:applyGrant`         | `source, data`                                   | `server/main.lua:674`       |
| registerCallback    | server | `advanced_government:server:reviewGrant`        | `source, data`                                   | `server/main.lua:689`       |
| registerCallback    | server | `advanced_government:server:createContract`     | `source, data`                                   | `server/main.lua:712`       |
| registerCallback    | server | `advanced_government:server:submitContractBid`  | `source, data`                                   | `server/main.lua:728`       |
| registerCallback    | server | `advanced_government:server:awardContract`      | `source, data`                                   | `server/main.lua:746`       |
| registerCallback    | server | `advanced_government:server:createReferendum`   | `source, data`                                   | `server/main.lua:765`       |
| registerCallback    | server | `advanced_government:server:voteReferendum`     | `source, data`                                   | `server/main.lua:781`       |
| registerCallback    | server | `advanced_government:server:closeReferendum`    | `source, data`                                   | `server/main.lua:794`       |
| exports             | server | `AddSocietyMoney`                               | `jobName, amount`                                | `server/main.lua:802`       |
| exports             | server | `GetTaxRate`                                    | `taxKey`                                         | `server/main.lua:807`       |
| exports             | server | `GetTaxPercent`                                 | `taxKey`                                         | `server/main.lua:812`       |
| exports             | server | `GetTreasuryBalance`                            | \`\`                                             | `server/main.lua:816`       |
| exports             | server | `AddTreasuryMoney`                              | `amount, reason, metadata`                       | `server/main.lua:820`       |
| exports             | server | `RemoveTreasuryMoney`                           | `amount, reason, metadata`                       | `server/main.lua:823`       |
| exports             | server | `GetMayor`                                      | `Named function/dynamic handler; inspect source` | `server/main.lua:827`       |
| exports             | server | `HasGovernmentPermission`                       | `source, permission`                             | `server/main.lua:828`       |
| exports             | server | `IsGovernmentEmployee`                          | `source`                                         | `server/main.lua:829`       |
| exports             | server | `WithholdIncomeTax`                             | `source, gross`                                  | `server/nrp_bridge.lua:121` |
