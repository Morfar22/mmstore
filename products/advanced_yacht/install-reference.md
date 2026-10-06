# Advanced Yacht — SQL and installation reference

The following files are included in the uploaded product. No new SQL migration or third-party schema is invented here. Fresh CREATE TABLE IF NOT EXISTS definitions do not necessarily alter older existing tables. Inventory snippets can have server/client callbacks particular to a provider; use the matching file.

## install.sql

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```sql
CREATE TABLE IF NOT EXISTS `advanced_yacht_properties` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `owner_citizenid` VARCHAR(64) NOT NULL,
  `owner_name` VARCHAR(96) NOT NULL,
  `package_key` VARCHAR(32) NOT NULL,
  `yacht_name` VARCHAR(32) NOT NULL,
  `mooring_group` TINYINT UNSIGNED NOT NULL,
  `mooring_slot` TINYINT UNSIGNED NOT NULL,
  `texture_variant` TINYINT UNSIGNED NOT NULL DEFAULT 0,
  `fittings` VARCHAR(16) NOT NULL DEFAULT 'chrome',
  `lighting_style` VARCHAR(32) NOT NULL DEFAULT 'presidential_green',
  `flag_key` VARCHAR(32) NOT NULL DEFAULT 'denmark',
  `defense_enabled` TINYINT(1) NOT NULL DEFAULT 0,
  `defense_exclusions` VARCHAR(24) NOT NULL DEFAULT 'no_one',
  `yacht_access_mode` VARCHAR(24) NOT NULL DEFAULT 'crew_friends',
  `vehicle_access_mode` VARCHAR(24) NOT NULL DEFAULT 'crew_friends',
  `hot_tub_clothing` VARCHAR(16) NOT NULL DEFAULT 'swimwear',
  `last_moved_at` TIMESTAMP NULL DEFAULT NULL,
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_advanced_yacht_mooring` (`mooring_group`,`mooring_slot`),
  KEY `idx_advanced_yacht_owner` (`owner_citizenid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_yacht_property_access` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `yacht_id` INT UNSIGNED NOT NULL,
  `citizenid` VARCHAR(64) NOT NULL,
  `display_name` VARCHAR(96) NOT NULL,
  `role` ENUM('guest','crew') NOT NULL DEFAULT 'guest',
  `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_advanced_yacht_property_access` (`yacht_id`,`citizenid`),
  KEY `idx_advanced_yacht_property_access_cid` (`citizenid`),
  CONSTRAINT `fk_advanced_yacht_property_access_yacht` FOREIGN KEY (`yacht_id`) REFERENCES `advanced_yacht_properties` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_yacht_vehicle_upgrades` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `yacht_id` INT UNSIGNED NOT NULL,
  `upgrade_key` VARCHAR(48) NOT NULL,
  `quantity` SMALLINT UNSIGNED NOT NULL DEFAULT 1,
  `purchased_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_advanced_yacht_vehicle_upgrade` (`yacht_id`,`upgrade_key`),
  KEY `idx_advanced_yacht_vehicle_upgrade_yacht` (`yacht_id`),
  CONSTRAINT `fk_advanced_yacht_vehicle_upgrade_yacht` FOREIGN KEY (`yacht_id`) REFERENCES `advanced_yacht_properties` (`id`) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```
