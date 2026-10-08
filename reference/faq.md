# Frequently asked questions

## Is every provider supported by every product?

No. The bridge supports several providers; the product must use that API and meet its own feature requirements. Cablecar's optional target and Diving's NPC still use ox_target directly. Stash hooks, needs, inventory opening and offline job administration are documented local extensions.

## Can I use QBox with TGIANN?

Configure the bridge inventory as tgiann and its exact resource name. Read your product's item-use/metadata and stash requirements. Validate TGIANN hooks against the installed version. A provider name is not proof of compatible item definitions or native UI signatures.

## Does standalone include an economy?

No. Free/no-charge gameplay may work where explicitly supported. Paid gameplay needs a real custom economy adapter; unsupported paid operations fail. Cablecar's explicit standalone fare mode skips fares.

## Does changing framework migrate data?

No. Citizen IDs, ESX character identifiers and standalone licenses differ. K9 and Vet retain legacy-license database keys by default. Plan any actual identity/inventory migration separately.

## Are the local tests a live server certification?

No. They check mocked integration behavior and syntax. GTA visuals/audio, SQL/schema, native inventory callbacks and real multi-player behavior still need staging verification.
