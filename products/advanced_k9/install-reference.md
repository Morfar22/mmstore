# SQL and installation reference

The following files are included in the uploaded product. No new SQL migration or third-party schema is invented here. Fresh CREATE TABLE IF NOT EXISTS definitions do not necessarily alter older existing tables. Inventory snippets can have server/client callbacks particular to a provider; use the matching file.

## sql/advanced\_k9.sql

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```sql
CREATE TABLE IF NOT EXISTS `advanced_k9_approvals` (
    `identifier` VARCHAR(100) NOT NULL,
    `handler` TINYINT(1) NOT NULL DEFAULT 0,
    `dog` TINYINT(1) NOT NULL DEFAULT 0,
    `last_name` VARCHAR(128) NULL,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`identifier`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_k9_progress` (
    `identifier` VARCHAR(100) NOT NULL,
    `xp` INT NOT NULL DEFAULT 0,
    `bond` INT NOT NULL DEFAULT 0,
    `obedience` INT NOT NULL DEFAULT 0,
    `fetches` INT NOT NULL DEFAULT 0,
    `sniffs` INT NOT NULL DEFAULT 0,
    `tracks` INT NOT NULL DEFAULT 0,
    `tackles` INT NOT NULL DEFAULT 0,
    `play` INT NOT NULL DEFAULT 0,
    `hunger` DOUBLE NOT NULL DEFAULT 100,
    `thirst` DOUBLE NOT NULL DEFAULT 100,
    `full_access` TINYINT(1) NOT NULL DEFAULT 0,
    `dog_type` VARCHAR(16) NOT NULL DEFAULT 'service',
    `civil_xp` INT NOT NULL DEFAULT 0,
    `civil_obedience` INT NOT NULL DEFAULT 0,
    `civil_social` INT NOT NULL DEFAULT 0,
    `civil_focus` INT NOT NULL DEFAULT 0,
    `civil_recall` INT NOT NULL DEFAULT 0,
    `civil_heel` INT NOT NULL DEFAULT 0,
    `civil_place` INT NOT NULL DEFAULT 0,
    `civil_impulse` INT NOT NULL DEFAULT 0,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`identifier`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_k9_adoptions` (
    `dog_identifier` VARCHAR(100) NOT NULL,
    `owner_identifier` VARCHAR(100) NOT NULL,
    `dog_name` VARCHAR(64) NOT NULL DEFAULT 'K9',
    `owner_name` VARCHAR(128) NULL,
    `owner_phone` VARCHAR(64) NULL,
    `phone_provider` VARCHAR(64) NULL,
    `owner_character_id` VARCHAR(128) NULL,
    `dog_character_id` VARCHAR(128) NULL,
    `created_at` BIGINT UNSIGNED NOT NULL DEFAULT 0,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`dog_identifier`),
    UNIQUE KEY `uniq_advanced_k9_owner` (`owner_identifier`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_k9_preferences` (
    `identifier` VARCHAR(100) NOT NULL,
    `position` VARCHAR(32) NOT NULL DEFAULT 'top-right',
    `command_duration` INT NOT NULL DEFAULT 9000,
    `sound_enabled` TINYINT(1) NOT NULL DEFAULT 1,
    `command_sound` TINYINT(1) NOT NULL DEFAULT 1,
    `success_sound` TINYINT(1) NOT NULL DEFAULT 1,
    `urgent_sound` TINYINT(1) NOT NULL DEFAULT 1,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`identifier`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;


CREATE TABLE IF NOT EXISTS `advanced_k9_passports` (
    `dog_identifier` VARCHAR(100) NOT NULL,
    `specialization` VARCHAR(32) NOT NULL DEFAULT 'general',
    `notes` VARCHAR(500) NULL,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`dog_identifier`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;


CREATE TABLE IF NOT EXISTS `advanced_k9_vehicle_anchors` (
    `model_key` VARCHAR(80) NOT NULL,
    `model_hash` BIGINT NOT NULL,
    `offset_x` DOUBLE NOT NULL,
    `offset_y` DOUBLE NOT NULL,
    `offset_z` DOUBLE NOT NULL,
    `rot_x` DOUBLE NOT NULL DEFAULT 0,
    `rot_y` DOUBLE NOT NULL DEFAULT 0,
    `rot_z` DOUBLE NOT NULL DEFAULT 0,
    `exit_x` DOUBLE NOT NULL DEFAULT -1,
    `exit_y` DOUBLE NOT NULL DEFAULT -1.8,
    `exit_z` DOUBLE NOT NULL DEFAULT 0,
    `door_index` INT NOT NULL DEFAULT 2,
    `posture_key` VARCHAR(24) NOT NULL DEFAULT 'sit',
    `updated_by` VARCHAR(100) NULL,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`model_key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_k9_vehicle_cameras` (
    `model_key` VARCHAR(80) NOT NULL,
    `model_hash` BIGINT NOT NULL,
    `offset_x` DOUBLE NOT NULL,
    `offset_y` DOUBLE NOT NULL,
    `offset_z` DOUBLE NOT NULL,
    `rot_x` DOUBLE NOT NULL DEFAULT 0,
    `rot_y` DOUBLE NOT NULL DEFAULT 0,
    `rot_z` DOUBLE NOT NULL DEFAULT 0,
    `fov` DOUBLE NOT NULL DEFAULT 62,
    `updated_by` VARCHAR(100) NULL,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`model_key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_k9_vehicle_slots` (
    `model_key` VARCHAR(80) NOT NULL,
    `model_hash` BIGINT NOT NULL,
    `slot_index` TINYINT UNSIGNED NOT NULL,
    `enabled` TINYINT(1) NOT NULL DEFAULT 1,
    `offset_x` DOUBLE NOT NULL,
    `offset_y` DOUBLE NOT NULL,
    `offset_z` DOUBLE NOT NULL,
    `rot_x` DOUBLE NOT NULL DEFAULT 0,
    `rot_y` DOUBLE NOT NULL DEFAULT 0,
    `rot_z` DOUBLE NOT NULL DEFAULT 0,
    `exit_x` DOUBLE NOT NULL DEFAULT -1,
    `exit_y` DOUBLE NOT NULL DEFAULT -1.8,
    `exit_z` DOUBLE NOT NULL DEFAULT 0,
    `door_index` INT NOT NULL DEFAULT 2,
    `posture_key` VARCHAR(24) NOT NULL DEFAULT 'sit',
    `template_model` VARCHAR(80) NOT NULL DEFAULT 'a_c_shepherd',
    `updated_by` VARCHAR(100) NULL,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`model_key`, `slot_index`),
    INDEX `idx_advanced_k9_vehicle_slots_hash` (`model_hash`, `slot_index`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;


CREATE TABLE IF NOT EXISTS `advanced_k9_stationary_kennels` (
    `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
    `label` VARCHAR(80) NOT NULL DEFAULT 'PD K9 Kennel',
    `model` VARCHAR(80) NOT NULL DEFAULT 'prop_doghouse_01',
    `prop_x` DOUBLE NOT NULL, `prop_y` DOUBLE NOT NULL, `prop_z` DOUBLE NOT NULL, `prop_h` DOUBLE NOT NULL DEFAULT 0,
    `dog_x` DOUBLE NOT NULL, `dog_y` DOUBLE NOT NULL, `dog_z` DOUBLE NOT NULL, `dog_h` DOUBLE NOT NULL DEFAULT 0,
    `release_x` DOUBLE NOT NULL, `release_y` DOUBLE NOT NULL, `release_z` DOUBLE NOT NULL, `release_h` DOUBLE NOT NULL DEFAULT 0,
    `created_by` VARCHAR(100) NULL,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```
