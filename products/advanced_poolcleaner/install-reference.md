# Advanced Poolcleaner — SQL and installation reference

The following files are included in the uploaded product. No new SQL migration or third-party schema is invented here. Fresh CREATE TABLE IF NOT EXISTS definitions do not necessarily alter older existing tables. Inventory snippets can have server/client callbacks particular to a provider; use the matching file.

## ox_inventory_items_snippet.lua

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```lua
-- Valgfrit. Brug kun hvis Config.Inventory.mode = 'ox_inventory'.
-- Kopiér entries ind i ox_inventory/data/items.lua.

return {
    ['pool_chemicals'] = {
        label = 'Poolkemikalier',
        weight = 1500,
        stack = true,
        close = true,
        description = 'Doserede kemikalier til professionel poolservice.'
    },
    ['pool_filter'] = {
        label = 'Poolfilter',
        weight = 1200,
        stack = true,
        close = true,
        description = 'Udskiftningsfilter til poolens filtersystem.'
    }
}
```


## qbx_job_snippet.lua

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```lua
-- Kun nødvendig hvis Config.JobMode = 'whitelist'.
-- Kopiér værdien under `poolcleaner` ind i qbx_core/shared/jobs.lua blandt de øvrige jobs.
-- Filen er samtidig gyldig Lua, så den kan syntax-tjekkes separat.

return {
    poolcleaner = {
        label = 'Poolservice',
        type = 'civilian',
        defaultDuty = true,
        offDutyPay = false,
        grades = {
            [0] = { name = 'Poolmedhjælper', payment = 0 },
            [1] = { name = 'Pooltekniker', payment = 0 },
            [2] = { name = 'Senior pooltekniker', payment = 0 },
            [3] = { name = 'Driftsleder', payment = 0, isboss = true, bankAuth = true }
        }
    }
}
```


## sql/install.sql

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```sql
CREATE TABLE IF NOT EXISTS `advanced_pool_profiles` (
  `citizenid` varchar(64) NOT NULL,
  `level` int NOT NULL DEFAULT 1,
  `xp` int NOT NULL DEFAULT 0,
  `reputation` int NOT NULL DEFAULT 0,
  `completed_jobs` int NOT NULL DEFAULT 0,
  `total_earned` bigint NOT NULL DEFAULT 0,
  `tasks_completed` int NOT NULL DEFAULT 0,
  `skill_points` int NOT NULL DEFAULT 0,
  `skills` longtext NULL,
  `updated_at` timestamp NOT NULL DEFAULT current_timestamp() ON UPDATE current_timestamp(),
  PRIMARY KEY (`citizenid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_pool_locations` (
  `id` int NOT NULL AUTO_INCREMENT,
  `slug` varchar(100) NOT NULL,
  `name` varchar(100) NOT NULL,
  `anchor_x` double NOT NULL,
  `anchor_y` double NOT NULL,
  `anchor_z` double NOT NULL,
  `tasks` longtext NOT NULL,
  `enabled` tinyint(1) NOT NULL DEFAULT 1,
  `created_by` varchar(64) DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp(),
  PRIMARY KEY (`id`),
  UNIQUE KEY `uniq_slug` (`slug`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```


## tgiann_inventory_items_snippet.lua

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```lua
-- Valgfrit. Brug hvis Config.Inventory.mode = 'tgiann-inventory'.
-- Kopiér entries ind i din TGIANN inventory item-konfiguration.

return {
    ['pool_chemicals'] = {
        label = 'Poolkemikalier',
        weight = 1500,
        type = 'item',
        shouldClose = true,
        description = 'Doserede kemikalier til professionel poolservice.'
    },
    ['pool_filter'] = {
        label = 'Poolfilter',
        weight = 1200,
        type = 'item',
        shouldClose = true,
        description = 'Udskiftningsfilter til poolens filtersystem.'
    }
}
```
