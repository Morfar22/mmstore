---
description: "Provider setup and migration boundaries for Advanced Car Radio."
---

# Advanced Car Radio — Bridge integration

Requires xSound for audio, oxmysql for persistence and ox_lib. No target/inventory/phone adapter is required. Provider changes do not move saved radio ownership automatically.

Identity, jobs/money where used, ACE and notifications use mm_bridge. Configure the bridge centrally; the legacy product README start order is superseded by the installation page. Preserve the resource configuration and SQL.
