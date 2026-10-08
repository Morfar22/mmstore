# SQL and installation reference

The following files are included in the uploaded product. No new SQL migration or third-party schema is invented here. Fresh CREATE TABLE IF NOT EXISTS definitions do not necessarily alter older existing tables. Inventory snippets can have server/client callbacks particular to a provider; use the matching file.

## install.sql

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```sql
CREATE TABLE IF NOT EXISTS `advanced_diving_players` (
  `citizenid` varchar(50) NOT NULL,
  `xp` int NOT NULL DEFAULT 0,
  `jobs_completed` int NOT NULL DEFAULT 0,
  `total_earnings` int NOT NULL DEFAULT 0,
  `updated_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`citizenid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```
