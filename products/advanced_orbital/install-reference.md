# Advanced Orbital — SQL and installation reference

Keep existing data when upgrading. Native install templates are examples for the indicated provider; merge entries, never replace your whole item registry. Source files below belong to release 1.3.0.

## sql/advanced_orbital.sql

```sql
CREATE TABLE IF NOT EXISTS `advanced_orbital_strikes` (
  `id` BIGINT UNSIGNED NOT NULL AUTO_INCREMENT,
  `citizenid` VARCHAR(64) NOT NULL,
  `player_name` VARCHAR(100) NOT NULL,
  `terminal_id` VARCHAR(64) NOT NULL,
  `mode` VARCHAR(32) NOT NULL,
  `price` INT UNSIGNED NOT NULL DEFAULT 0,
  `target_type` VARCHAR(32) NULL,
  `target_net_id` INT NULL,
  `impact_x` DOUBLE NOT NULL,
  `impact_y` DOUBLE NOT NULL,
  `impact_z` DOUBLE NOT NULL,
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `idx_orbital_citizen_date` (`citizenid`, `created_at`),
  KEY `idx_orbital_created_at` (`created_at`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```
