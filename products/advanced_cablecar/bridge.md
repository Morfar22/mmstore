---
description: "Provider setup and migration boundaries for Advanced Cablecar."
---

# Advanced Cablecar — Bridge integration

Optional targets still call ox_target directly. Ticket-machine proximity interactions work without a target provider. Config.Framework='standalone' explicitly skips fares; legacy 'qbox' selects paid bridge behavior. Framework selection in mm_bridge does not override this resource fare setting.

Identity, jobs/money where used, ACE and notifications use mm_bridge. Configure the bridge centrally; the legacy product README start order is superseded by the installation page. Preserve the resource configuration and SQL.
