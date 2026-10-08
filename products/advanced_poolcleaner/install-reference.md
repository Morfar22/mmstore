# Advanced Poolcleaner — SQL and installation reference

Keep existing data when upgrading. Native install templates are examples for the indicated provider; merge entries, never replace your whole item registry. Source files below belong to release 1.2.0.

## sql/install.sql

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
