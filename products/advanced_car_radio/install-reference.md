# Advanced Car Radio — SQL and installation reference

The following files are included in the uploaded product. No new SQL migration or third-party schema is invented here. Fresh CREATE TABLE IF NOT EXISTS definitions do not necessarily alter older existing tables. Inventory snippets can have server/client callbacks particular to a provider; use the matching file.

## sql/install.sql

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```sql
CREATE TABLE IF NOT EXISTS `advanced_car_radio_settings` (
  `citizenid` varchar(64) NOT NULL,
  `own_volume` decimal(4,3) NOT NULL DEFAULT 1.000,
  `inside_other_volume` decimal(4,3) NOT NULL DEFAULT 0.280,
  `outside_other_volume` decimal(4,3) NOT NULL DEFAULT 0.550,
  `show_now_playing` tinyint(1) NOT NULL DEFAULT 1,
  `updated_at` timestamp NOT NULL DEFAULT current_timestamp() ON UPDATE current_timestamp(),
  PRIMARY KEY (`citizenid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_car_radio_playlists` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `citizenid` varchar(64) NOT NULL,
  `name` varchar(80) NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp(),
  PRIMARY KEY (`id`),
  KEY `idx_acr_playlists_citizenid` (`citizenid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_car_radio_playlist_tracks` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `playlist_id` bigint unsigned NOT NULL,
  `title` varchar(160) NOT NULL,
  `artist` varchar(120) NOT NULL DEFAULT '',
  `url` text NOT NULL,
  `artwork` text NULL,
  `duration` int unsigned NOT NULL DEFAULT 0,
  `position_index` int unsigned NOT NULL DEFAULT 0,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp(),
  PRIMARY KEY (`id`),
  KEY `idx_acr_playlist_tracks_playlist` (`playlist_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_car_radio_vehicle_tracks` (
  `id` bigint unsigned NOT NULL AUTO_INCREMENT,
  `plate` varchar(16) NOT NULL,
  `title` varchar(160) NOT NULL,
  `artist` varchar(120) NOT NULL DEFAULT '',
  `url` text NOT NULL,
  `artwork` text NULL,
  `duration` int unsigned NOT NULL DEFAULT 0,
  `added_by` varchar(64) NULL,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp(),
  PRIMARY KEY (`id`),
  KEY `idx_acr_vehicle_tracks_plate` (`plate`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `advanced_car_radio_vehicle_state` (
  `plate` varchar(16) NOT NULL,
  `title` varchar(160) NULL,
  `artist` varchar(120) NULL,
  `url` text NULL,
  `artwork` text NULL,
  `duration` int unsigned NOT NULL DEFAULT 0,
  `queue_json` longtext NULL,
  `queue_index` int unsigned NOT NULL DEFAULT 1,
  `position_seconds` decimal(12,3) NOT NULL DEFAULT 0.000,
  `is_playing` tinyint(1) NOT NULL DEFAULT 0,
  `volume` decimal(4,3) NOT NULL DEFAULT 0.650,
  `loop_mode` varchar(12) NOT NULL DEFAULT 'off',
  `updated_at` timestamp NOT NULL DEFAULT current_timestamp() ON UPDATE current_timestamp(),
  PRIMARY KEY (`plate`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```
