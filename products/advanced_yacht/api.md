# Advanced Yacht — Exports and integrations

Server exports:

| Export | Parameters | Return |
| --- | --- | --- |
| HasYachtAccess | src, yachtId | allowed, isOwner, role for explicit owner/access list |
| GetYacht | yachtId | Current in-memory yacht row, or nil |

```lua
-- SERVER
local allowed, owner, role = exports.advanced_yacht:HasYachtAccess(src, yachtId)
local yacht = exports.advanced_yacht:GetYacht(yachtId)
```

HasYachtAccess is the explicit owner/guest-list check. Service/vehicle access modes are evaluated separately in modeAllows; public everyone access does not make the explicit export return true. Organization/club/friends categories map to explicit crew/guest records.

Storage uses ox_inventory RegisterStash and open access checks. Wardrobe provider is configuration-driven. Purchased fleet is server-managed and position validation is separate from client visual yacht IPLs. These exports expose current runtime data; avoid mutating returned tables as an undocumented write API.

Source: export declarations and loaded framework/inventory/billing bridges in the supplied product.
