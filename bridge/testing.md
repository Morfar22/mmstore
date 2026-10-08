# Validation

Offline validation: 45 server behavior tests and 24 client behavior tests, plus compilation of every Lua file. Provider exports and FiveM natives are mocked. The deliberate credit-error and corrupt-journal logs are expected test cases.

Run from the mm_bridge directory with texlua (Lua 5.3), or a compatible Lua interpreter:

```sh
texlua tests/server_spec.lua
texlua tests/client_spec.lua
```

Compile all files with tests/syntax.lua, passing each .lua path as an argument. Mock JSON serialization uses cloned Lua tables; it does not exercise FiveM's actual JSON encoder or disk durability.

Covered behavior includes missing/ambiguous providers, identity and legacy wrapper forwarding, QBox/QBCore/ESX money, standalone unsupported capabilities, inventory slots and metadata, target option mapping/ownership/cleanup, phone exports, custom registration allowlists, invoice ownership, insufficient funds, reentrant payment, journal failure, interrupted settlement and corrupt-journal preservation.

No live FiveM server validation was performed. Standalone target registration is tested; the actual GTA input/render loop and ox_lib menus require live testing. Phone exports, TGIANN versions, native billing schemas and provider restart behavior must be checked against the installed resources.

Before a production upgrade, test one chosen framework/inventory/target combination with your actual consumers: reconnect/multicharacter identity, jobs/duty, positive and failed money/item operations, filtered item removal/metadata readback, target interaction/removal/restarts, actual phone UI/notifications and invoice creation/payment. Check your consumer's own access validation and dependencies. A successful bridge test does not migrate the remaining products or validate every combination.
