# Bridge troubleshooting

| Symptom | Check | Next action |
| --- | --- | --- |
| unavailable provider | Selected resource name/start state | Start it or choose the intended adapter; no silent fallback |
| ambiguous provider | Several built-in candidates started with auto | Select one explicitly |
| unknown custom adapter | Registration, exact name and owner allow-list | Start adapter before consumers; select its name |
| unsupported_operation | Capability method absent | Supply a real adapter or disable the feature |
| money/item change not confirmed | Provider return/readback and logs | Reconcile actual provider state before retrying |
| duty access denied on ESX | Missing native duty field | Set EsxAssumeDuty only if server policy permits it |
| targets vanish after restart | Lost handles/provider restart | Restart affected consumers and verify cleanup |
| stash locked | Native open/transfer hooks absent | Install the documented local stash adapter |
| invoice requires review | Interrupted/two-provider settlement | Reconcile debit/credit and billing journal; do not auto replay |

Preserve mm_bridge/billing-journal.json across updates. Framework billing pays the online issuer and does not provide society settlement. Refer to [billing](billing.md) and your product integration guide.
