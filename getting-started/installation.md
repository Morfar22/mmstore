# Install your first resource

## 1. Choose the product and release

Use the release shown in the [catalog](../products/README.md). The documentation targets the bridge releases, not the pre-bridge archive.

## 2. Start the integration layer

```cfg
ensure oxmysql
ensure ox_lib
# Start your chosen framework/inventory/target/phone here.
ensure mm_bridge
# Start an external custom adapter here, if selected.
ensure advanced_k9
# Add only the products you actually install.
```

This is an example, not a list of dependencies for every product. Car Radio needs xsound; Diving currently needs ox_target; Government society settlement needs its selected banking adapter. Check the product installation page.

## 3. Configure providers once

Edit mm_bridge/config.lua. Select QBox, QBCore, ESX or standalone only where the product's gameplay requirements are met. Choose one inventory/target and any required phone/billing adapter. Then edit the product's own config for prices, access, locations and controls.

## 4. Prepare SQL and items

Use the product SQL/install reference. Keep existing identity keys, records and stored items. Merge item entries and install needed optional assets; do not overwrite whole registries.

## 5. Verify one real workflow

Complete a solo workflow, a two-player flow if applicable, a reconnect and one failed-provider case. Confirm payment/item consumption happens once. Local mocked checks do not certify gameplay or your installed provider versions.
