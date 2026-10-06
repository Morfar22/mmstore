# Advanced Vet DLC — SQL and installation reference

The following files are included in the uploaded product. No new SQL migration or third-party schema is invented here. Fresh CREATE TABLE IF NOT EXISTS definitions do not necessarily alter older existing tables. Inventory snippets can have server/client callbacks particular to a provider; use the matching file.

## install/ox_inventory_items.lua

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```lua
return {
    ['vet_prescription'] = {
        label = 'Veterinary Prescription',
        weight = 5,
        stack = false,
        close = false,
        consume = 0,
        description = 'Veterinary prescription document with patient, medicine, dose, warnings and issuing Vet metadata.',
    },
    ['vet_quietpaws'] = {
        label = "QuietPaws™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useQuietPaws',
        },
    },
    ['vet_gentleease'] = {
        label = "GentleEase™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useGentleEase',
        },
    },
    ['vet_happyjoints'] = {
        label = "HappyJoints™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useHappyJoints',
        },
    },
    ['vet_bellybloom'] = {
        label = "BellyBloom™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useBellyBloom',
        },
    },
    ['vet_peacefulpet'] = {
        label = "PeacefulPet™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.usePeacefulPet',
        },
    },
    ['vet_goldenpaws_daily'] = {
        label = "GoldenPaws Daily™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useGoldenPawsDaily',
        },
    },
    ['vet_meadowbowl'] = {
        label = "MeadowBowl™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useMeadowBowl',
        },
    },
    ['vet_softharvest'] = {
        label = "SoftHarvest™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useSoftHarvest',
        },
    },
    ['vet_sprinkle_of_sunshine'] = {
        label = "Sprinkle of Sunshine™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useSprinkleOfSunshine',
        },
    },
    ['vet_clearspring'] = {
        label = "ClearSpring™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useClearSpring',
        },
    },
    ['vet_pawpure'] = {
        label = "PawPure™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.usePawPure',
        },
    },
    ['vet_stillbrook'] = {
        label = "StillBrook™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useStillBrook',
        },
    },
}
```


## install/qbcore_items.lua

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```lua
return {
    vet_prescription = {
        name = 'vet_prescription',
        label = 'Veterinary Prescription',
        weight = 5,
        type = 'item',
        image = 'vet_prescription.png',
        unique = true,
        useable = false,
        shouldClose = false,
        description = 'Veterinary prescription document with full metadata.',
    },
    vet_quietpaws = {
        name = 'vet_quietpaws',
        label = "QuietPaws™",
        weight = 100,
        type = 'item',
        image = 'vet_quietpaws.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
    vet_gentleease = {
        name = 'vet_gentleease',
        label = "GentleEase™",
        weight = 100,
        type = 'item',
        image = 'vet_gentleease.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
    vet_happyjoints = {
        name = 'vet_happyjoints',
        label = "HappyJoints™",
        weight = 100,
        type = 'item',
        image = 'vet_happyjoints.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
    vet_bellybloom = {
        name = 'vet_bellybloom',
        label = "BellyBloom™",
        weight = 100,
        type = 'item',
        image = 'vet_bellybloom.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
    vet_peacefulpet = {
        name = 'vet_peacefulpet',
        label = "PeacefulPet™",
        weight = 100,
        type = 'item',
        image = 'vet_peacefulpet.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
    vet_goldenpaws_daily = {
        name = 'vet_goldenpaws_daily',
        label = "GoldenPaws Daily™",
        weight = 100,
        type = 'item',
        image = 'vet_goldenpaws_daily.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
    vet_meadowbowl = {
        name = 'vet_meadowbowl',
        label = "MeadowBowl™",
        weight = 100,
        type = 'item',
        image = 'vet_meadowbowl.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
    vet_softharvest = {
        name = 'vet_softharvest',
        label = "SoftHarvest™",
        weight = 100,
        type = 'item',
        image = 'vet_softharvest.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
    vet_sprinkle_of_sunshine = {
        name = 'vet_sprinkle_of_sunshine',
        label = "Sprinkle of Sunshine™",
        weight = 100,
        type = 'item',
        image = 'vet_sprinkle_of_sunshine.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
    vet_clearspring = {
        name = 'vet_clearspring',
        label = "ClearSpring™",
        weight = 100,
        type = 'item',
        image = 'vet_clearspring.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
    vet_pawpure = {
        name = 'vet_pawpure',
        label = "PawPure™",
        weight = 100,
        type = 'item',
        image = 'vet_pawpure.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
    vet_stillbrook = {
        name = 'vet_stillbrook',
        label = "StillBrook™",
        weight = 100,
        type = 'item',
        image = 'vet_stillbrook.png',
        unique = true,
        useable = true,
        shouldClose = true,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
    },
}
```


## install/tgiann_inventory_items.lua

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```lua
return {
    ['vet_prescription'] = {
        label = 'Veterinary Prescription',
        weight = 5,
        stack = false,
        hasMetadata = true,
        close = false,
        consume = 0,
        description = 'Veterinary prescription document with patient, medicine, dose, warnings and issuing Vet metadata.',
    },
    ['vet_quietpaws'] = {
        label = "QuietPaws™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useQuietPaws',
        },
    },
    ['vet_gentleease'] = {
        label = "GentleEase™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useGentleEase',
        },
    },
    ['vet_happyjoints'] = {
        label = "HappyJoints™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useHappyJoints',
        },
    },
    ['vet_bellybloom'] = {
        label = "BellyBloom™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useBellyBloom',
        },
    },
    ['vet_peacefulpet'] = {
        label = "PeacefulPet™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.usePeacefulPet',
        },
    },
    ['vet_goldenpaws_daily'] = {
        label = "GoldenPaws Daily™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useGoldenPawsDaily',
        },
    },
    ['vet_meadowbowl'] = {
        label = "MeadowBowl™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useMeadowBowl',
        },
    },
    ['vet_softharvest'] = {
        label = "SoftHarvest™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useSoftHarvest',
        },
    },
    ['vet_sprinkle_of_sunshine'] = {
        label = "Sprinkle of Sunshine™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useSprinkleOfSunshine',
        },
    },
    ['vet_clearspring'] = {
        label = "ClearSpring™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useClearSpring',
        },
    },
    ['vet_pawpure'] = {
        label = "PawPure™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.usePawPure',
        },
    },
    ['vet_stillbrook'] = {
        label = "StillBrook™",
        weight = 100,
        stack = false,
        hasMetadata = true,
        close = true,
        consume = 1,
        description = 'Veterinary prescription/product from Advanced Vet DLC',
        server = {
            export = 'advanced_vet_dlc.useStillBrook',
        },
    },
}
```


## sql/advanced_vet.sql

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```sql
CREATE TABLE IF NOT EXISTS `advanced_vet_patients` (
    `patient_key` VARCHAR(140) NOT NULL,
    `patient_name` VARCHAR(128) NOT NULL,
    `patient_type` VARCHAR(40) NOT NULL DEFAULT 'animal',
    `model` VARCHAR(80) NULL,
    `advanced_k9` TINYINT(1) NOT NULL DEFAULT 0,
    `last_seen` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`patient_key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `advanced_vet_visits` (
    `id` BIGINT UNSIGNED NOT NULL AUTO_INCREMENT,
    `patient_key` VARCHAR(140) NOT NULL,
    `patient_name` VARCHAR(128) NOT NULL,
    `patient_type` VARCHAR(40) NOT NULL DEFAULT 'animal',
    `advanced_k9` TINYINT(1) NOT NULL DEFAULT 0,
    `veterinarian_identifier` VARCHAR(100) NOT NULL,
    `veterinarian_name` VARCHAR(128) NOT NULL,
    `treatment` VARCHAR(80) NOT NULL,
    `notes` VARCHAR(500) NULL,
    `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (`id`),
    INDEX `idx_advanced_vet_patient` (`patient_key`),
    INDEX `idx_advanced_vet_vet` (`veterinarian_identifier`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;


CREATE TABLE IF NOT EXISTS `advanced_vet_prescriptions` (
    `id` BIGINT UNSIGNED NOT NULL AUTO_INCREMENT,
    `patient_key` VARCHAR(140) NOT NULL,
    `patient_name` VARCHAR(128) NOT NULL,
    `clinic_id` VARCHAR(80) NOT NULL,
    `product_key` VARCHAR(80) NOT NULL,
    `product_name` VARCHAR(128) NOT NULL,
    `generic_name` VARCHAR(128) NULL,
    `category` VARCHAR(128) NOT NULL,
    `instructions` VARCHAR(500) NULL,
    `notes` VARCHAR(500) NULL,
    `prescribed_by_identifier` VARCHAR(100) NOT NULL,
    `prescribed_by_name` VARCHAR(128) NOT NULL,
    `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (`id`),
    INDEX `idx_advanced_vet_rx_patient` (`patient_key`),
    INDEX `idx_advanced_vet_rx_clinic` (`clinic_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `advanced_vet_stock` (
    `clinic_id` VARCHAR(80) NOT NULL,
    `product_key` VARCHAR(80) NOT NULL,
    `stock` INT NOT NULL DEFAULT 0,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`clinic_id`, `product_key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;


CREATE TABLE IF NOT EXISTS `advanced_vet_xrays` (
    `id` BIGINT UNSIGNED NOT NULL AUTO_INCREMENT,
    `patient_key` VARCHAR(140) NOT NULL,
    `patient_name` VARCHAR(128) NOT NULL,
    `clinic_id` VARCHAR(80) NOT NULL,
    `region` VARCHAR(80) NOT NULL,
    `result_text` VARCHAR(500) NOT NULL,
    `veterinarian_identifier` VARCHAR(100) NOT NULL,
    `veterinarian_name` VARCHAR(128) NOT NULL,
    `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (`id`),
    INDEX `idx_advanced_vet_xray_patient` (`patient_key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `advanced_vet_surgeries` (
    `id` BIGINT UNSIGNED NOT NULL AUTO_INCREMENT,
    `patient_key` VARCHAR(140) NOT NULL,
    `patient_name` VARCHAR(128) NOT NULL,
    `clinic_id` VARCHAR(80) NOT NULL,
    `procedure_key` VARCHAR(80) NOT NULL,
    `procedure_label` VARCHAR(128) NOT NULL,
    `notes` VARCHAR(500) NULL,
    `veterinarian_identifier` VARCHAR(100) NOT NULL,
    `veterinarian_name` VARCHAR(128) NOT NULL,
    `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (`id`),
    INDEX `idx_advanced_vet_surgery_patient` (`patient_key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `advanced_vet_admissions` (
    `id` BIGINT UNSIGNED NOT NULL AUTO_INCREMENT,
    `patient_key` VARCHAR(140) NOT NULL,
    `patient_name` VARCHAR(128) NOT NULL,
    `clinic_id` VARCHAR(80) NOT NULL,
    `kennel_slot` VARCHAR(32) NOT NULL,
    `status` VARCHAR(24) NOT NULL DEFAULT 'admitted',
    `notes` VARCHAR(500) NULL,
    `admitted_by_identifier` VARCHAR(100) NOT NULL,
    `admitted_by_name` VARCHAR(128) NOT NULL,
    `admitted_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    `discharged_at` TIMESTAMP NULL DEFAULT NULL,
    PRIMARY KEY (`id`),
    INDEX `idx_advanced_vet_admission_patient` (`patient_key`),
    INDEX `idx_advanced_vet_admission_clinic` (`clinic_id`, `status`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `advanced_vet_chips` (
    `patient_key` VARCHAR(140) NOT NULL,
    `chip_id` VARCHAR(64) NOT NULL,
    `patient_name` VARCHAR(128) NOT NULL,
    `owner_name` VARCHAR(128) NULL,
    `owner_phone` VARCHAR(64) NULL,
    `implanted_by_identifier` VARCHAR(100) NOT NULL,
    `implanted_by_name` VARCHAR(128) NOT NULL,
    `implanted_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`patient_key`),
    UNIQUE KEY `uq_advanced_vet_chip` (`chip_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `advanced_vet_vaccinations` (
    `id` BIGINT UNSIGNED NOT NULL AUTO_INCREMENT,
    `patient_key` VARCHAR(140) NOT NULL,
    `patient_name` VARCHAR(128) NOT NULL,
    `clinic_id` VARCHAR(80) NOT NULL,
    `vaccine_key` VARCHAR(80) NOT NULL,
    `vaccine_label` VARCHAR(128) NOT NULL,
    `next_due` DATE NULL,
    `administered_by_identifier` VARCHAR(100) NOT NULL,
    `administered_by_name` VARCHAR(128) NOT NULL,
    `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (`id`),
    INDEX `idx_advanced_vet_vaccine_patient` (`patient_key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `advanced_vet_invoices` (
    `id` BIGINT UNSIGNED NOT NULL AUTO_INCREMENT,
    `clinic_id` VARCHAR(80) NOT NULL,
    `customer_identifier` VARCHAR(100) NOT NULL,
    `customer_name` VARCHAR(128) NOT NULL,
    `amount` INT NOT NULL,
    `description` VARCHAR(255) NOT NULL,
    `status` VARCHAR(24) NOT NULL DEFAULT 'unpaid',
    `created_by_identifier` VARCHAR(100) NOT NULL,
    `created_by_name` VARCHAR(128) NOT NULL,
    `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    `paid_at` TIMESTAMP NULL DEFAULT NULL,
    PRIMARY KEY (`id`),
    INDEX `idx_advanced_vet_invoice_customer` (`customer_identifier`, `status`),
    INDEX `idx_advanced_vet_invoice_clinic` (`clinic_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `advanced_vet_appointments` (
    `id` BIGINT UNSIGNED NOT NULL AUTO_INCREMENT,
    `clinic_id` VARCHAR(80) NOT NULL,
    `client_name` VARCHAR(128) NOT NULL,
    `client_phone` VARCHAR(64) NULL,
    `patient_name` VARCHAR(128) NOT NULL,
    `appointment_at` DATETIME NOT NULL,
    `notes` VARCHAR(500) NULL,
    `status` VARCHAR(24) NOT NULL DEFAULT 'scheduled',
    `created_by_identifier` VARCHAR(100) NOT NULL,
    `created_by_name` VARCHAR(128) NOT NULL,
    `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (`id`),
    INDEX `idx_advanced_vet_appointment_clinic` (`clinic_id`, `appointment_at`),
    INDEX `idx_advanced_vet_appointment_status` (`status`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;


CREATE TABLE IF NOT EXISTS `advanced_vet_triage` (
    `id` BIGINT UNSIGNED NOT NULL AUTO_INCREMENT,
    `patient_key` VARCHAR(140) NOT NULL,
    `patient_name` VARCHAR(128) NOT NULL,
    `clinic_id` VARCHAR(80) NULL,
    `status` VARCHAR(24) NOT NULL,
    `health_percent` INT NOT NULL DEFAULT 0,
    `heart_rate` INT NOT NULL DEFAULT 0,
    `respiration` INT NOT NULL DEFAULT 0,
    `temperature` DECIMAL(4,1) NOT NULL DEFAULT 0.0,
    `pain_score` INT NOT NULL DEFAULT 0,
    `veterinarian_identifier` VARCHAR(100) NOT NULL,
    `veterinarian_name` VARCHAR(128) NOT NULL,
    `created_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (`id`),
    INDEX `idx_advanced_vet_triage_patient` (`patient_key`),
    INDEX `idx_advanced_vet_triage_clinic` (`clinic_id`, `created_at`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;


CREATE TABLE IF NOT EXISTS `advanced_vet_placement_overrides` (
    `clinic_id` VARCHAR(80) NOT NULL,
    `placement_type` VARCHAR(24) NOT NULL,
    `placement_key` VARCHAR(64) NOT NULL,
    `x` DOUBLE NOT NULL,
    `y` DOUBLE NOT NULL,
    `z` DOUBLE NOT NULL,
    `heading` DOUBLE NOT NULL DEFAULT 0,
    `release_x` DOUBLE NULL,
    `release_y` DOUBLE NULL,
    `release_z` DOUBLE NULL,
    `release_heading` DOUBLE NULL,
    `ped_model` VARCHAR(80) NULL,
    `release_ped_model` VARCHAR(80) NULL,
    `updated_by` VARCHAR(100) NULL,
    `updated_at` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    PRIMARY KEY (`clinic_id`, `placement_type`, `placement_key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```


## sql/v15_6_1_migration.sql

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```sql
ALTER TABLE `advanced_vet_placement_overrides`
    ADD COLUMN `ped_model` VARCHAR(80) NULL AFTER `release_heading`,
    ADD COLUMN `release_ped_model` VARCHAR(80) NULL AFTER `ped_model`;
```
