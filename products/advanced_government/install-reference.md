# SQL and installation reference

The following files are included in the uploaded product. No new SQL migration or third-party schema is invented here. Fresh CREATE TABLE IF NOT EXISTS definitions do not necessarily alter older existing tables. Inventory snippets can have server/client callbacks particular to a provider; use the matching file.

## install/install.sql

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```sql
CREATE TABLE IF NOT EXISTS `government_settings` (
  `key` varchar(64) NOT NULL,
  `value` longtext NOT NULL,
  PRIMARY KEY (`key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_treasury` (
  `id` int NOT NULL,
  `balance` bigint NOT NULL DEFAULT 0,
  `updated_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_treasury_transactions` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `direction` enum('in','out') NOT NULL,
  `amount` bigint NOT NULL,
  `balance_after` bigint NOT NULL,
  `reason` varchar(255) NOT NULL,
  `target_type` varchar(64) DEFAULT NULL,
  `target_id` varchar(128) DEFAULT NULL,
  `actor_citizenid` varchar(64) NOT NULL,
  `actor_name` varchar(128) NOT NULL,
  `metadata` longtext DEFAULT NULL,
  `reference` varchar(96) DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_gov_transaction_reference` (`reference`),
  KEY `idx_gov_transactions_created` (`created_at`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_taxes` (
  `tax_key` varchar(64) NOT NULL,
  `label` varchar(128) NOT NULL,
  `rate` decimal(6,2) NOT NULL DEFAULT 0,
  `min_rate` decimal(6,2) NOT NULL DEFAULT 0,
  `max_rate` decimal(6,2) NOT NULL DEFAULT 100,
  `updated_by` varchar(64) DEFAULT NULL,
  `updated_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`tax_key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_office` (
  `office` varchar(32) NOT NULL,
  `citizenid` varchar(64) NOT NULL,
  `name` varchar(128) NOT NULL,
  `term_started_at` datetime DEFAULT NULL,
  `term_ends_at` datetime DEFAULT NULL,
  PRIMARY KEY (`office`),
  KEY `idx_gov_office_citizenid` (`citizenid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_cabinet` (
  `id` int NOT NULL AUTO_INCREMENT,
  `citizenid` varchar(64) NOT NULL,
  `name` varchar(128) NOT NULL,
  `role` varchar(64) NOT NULL,
  `permissions` longtext DEFAULT NULL,
  `appointed_by` varchar(64) DEFAULT NULL,
  `appointed_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_gov_cabinet_citizen` (`citizenid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_elections` (
  `id` int NOT NULL AUTO_INCREMENT,
  `status` enum('registration','campaign','voting','finished') NOT NULL DEFAULT 'registration',
  `registration_ends_at` datetime DEFAULT NULL,
  `campaign_ends_at` datetime DEFAULT NULL,
  `voting_ends_at` datetime DEFAULT NULL,
  `winner_citizenid` varchar(64) DEFAULT NULL,
  `term_ends_at` datetime DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_candidates` (
  `id` int NOT NULL AUTO_INCREMENT,
  `election_id` int NOT NULL,
  `citizenid` varchar(64) NOT NULL,
  `name` varchar(128) NOT NULL,
  `party` varchar(64) NOT NULL DEFAULT 'Uafhængig',
  `slogan` varchar(128) DEFAULT NULL,
  `manifesto` text DEFAULT NULL,
  `deposit` bigint NOT NULL DEFAULT 0,
  `campaign_balance` bigint NOT NULL DEFAULT 0,
  `approved` tinyint(1) NOT NULL DEFAULT 1,
  `registered_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_gov_candidate` (`election_id`,`citizenid`),
  KEY `idx_gov_candidates_election` (`election_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_votes` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `election_id` int NOT NULL,
  `candidate_id` int NOT NULL,
  `voter_citizenid` varchar(64) NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_gov_vote_once` (`election_id`,`voter_citizenid`),
  KEY `idx_gov_votes_candidate` (`candidate_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_campaign_donations` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `election_id` int NOT NULL,
  `candidate_id` int NOT NULL,
  `donor_citizenid` varchar(64) NOT NULL,
  `donor_name` varchar(128) NOT NULL,
  `amount` bigint NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `idx_gov_donations_candidate` (`candidate_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_laws` (
  `id` int NOT NULL AUTO_INCREMENT,
  `title` varchar(150) NOT NULL,
  `body` text NOT NULL,
  `status` enum('proposal','active','rejected','repealed') NOT NULL DEFAULT 'proposal',
  `proposed_by_citizenid` varchar(64) NOT NULL,
  `proposed_by_name` varchar(128) NOT NULL,
  `votes_for` int NOT NULL DEFAULT 0,
  `votes_against` int NOT NULL DEFAULT 0,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `enacted_at` datetime DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_law_votes` (
  `law_id` int NOT NULL,
  `citizenid` varchar(64) NOT NULL,
  `vote` enum('for','against') NOT NULL,
  `voted_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`law_id`,`citizenid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_budgets` (
  `id` int NOT NULL AUTO_INCREMENT,
  `department` varchar(64) NOT NULL,
  `label` varchar(128) NOT NULL,
  `amount` bigint NOT NULL,
  `period_label` varchar(64) NOT NULL,
  `status` enum('draft','approved','spent','cancelled') NOT NULL DEFAULT 'approved',
  `created_by` varchar(64) NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_audit` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `actor_citizenid` varchar(64) NOT NULL,
  `actor_name` varchar(128) NOT NULL,
  `action` varchar(96) NOT NULL,
  `target_type` varchar(64) DEFAULT NULL,
  `target_id` varchar(128) DEFAULT NULL,
  `amount` bigint DEFAULT NULL,
  `metadata` longtext DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `idx_gov_audit_created` (`created_at`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

-- v2: Parties, campaign advertising, grants, contracts and referendums
CREATE TABLE IF NOT EXISTS `government_parties` (
  `id` int NOT NULL AUTO_INCREMENT,
  `name` varchar(64) NOT NULL,
  `short_name` varchar(12) NOT NULL,
  `color` varchar(16) DEFAULT '#d4af37',
  `description` text DEFAULT NULL,
  `leader_citizenid` varchar(64) NOT NULL,
  `leader_name` varchar(128) NOT NULL,
  `is_public` tinyint(1) NOT NULL DEFAULT 1,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_government_party_name` (`name`),
  UNIQUE KEY `uq_government_party_short` (`short_name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_party_members` (
  `party_id` int NOT NULL,
  `citizenid` varchar(64) NOT NULL,
  `name` varchar(128) NOT NULL,
  `role` enum('member','officer','leader') NOT NULL DEFAULT 'member',
  `joined_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`party_id`,`citizenid`),
  UNIQUE KEY `uq_government_party_member_once` (`citizenid`),
  KEY `idx_government_party_member_party` (`party_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_campaign_ads` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `election_id` int NOT NULL,
  `candidate_id` int NOT NULL,
  `zone_key` varchar(64) NOT NULL,
  `headline` varchar(128) NOT NULL,
  `slogan` varchar(255) DEFAULT NULL,
  `starts_at` datetime NOT NULL,
  `ends_at` datetime NOT NULL,
  `price` bigint NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `idx_government_campaign_ads_active` (`zone_key`,`ends_at`),
  KEY `idx_government_campaign_ads_election` (`election_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_grants` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `citizenid` varchar(64) NOT NULL,
  `applicant_name` varchar(128) NOT NULL,
  `job_name` varchar(64) NOT NULL,
  `job_label` varchar(128) NOT NULL,
  `amount` bigint NOT NULL,
  `reason` text NOT NULL,
  `status` enum('pending','approved','rejected','paid') NOT NULL DEFAULT 'pending',
  `reviewed_by` varchar(64) DEFAULT NULL,
  `review_note` varchar(500) DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `reviewed_at` datetime DEFAULT NULL,
  `paid_at` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `idx_government_grants_status` (`status`),
  KEY `idx_government_grants_job` (`job_name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_contracts` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `title` varchar(150) NOT NULL,
  `description` text NOT NULL,
  `max_budget` bigint NOT NULL,
  `status` enum('open','closed','awarded','cancelled','completed') NOT NULL DEFAULT 'open',
  `created_by` varchar(64) NOT NULL,
  `winner_bid_id` bigint DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `closes_at` datetime DEFAULT NULL,
  `awarded_at` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `idx_government_contracts_status` (`status`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_contract_bids` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `contract_id` bigint NOT NULL,
  `citizenid` varchar(64) NOT NULL,
  `bidder_name` varchar(128) NOT NULL,
  `job_name` varchar(64) NOT NULL,
  `job_label` varchar(128) NOT NULL,
  `amount` bigint NOT NULL,
  `proposal` text NOT NULL,
  `status` enum('submitted','won','lost','withdrawn') NOT NULL DEFAULT 'submitted',
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_government_contract_bid_job` (`contract_id`,`job_name`),
  KEY `idx_government_contract_bids_contract` (`contract_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_referendums` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `title` varchar(150) NOT NULL,
  `question` text NOT NULL,
  `status` enum('open','closed','cancelled') NOT NULL DEFAULT 'open',
  `created_by` varchar(64) NOT NULL,
  `created_by_name` varchar(128) NOT NULL,
  `closes_at` datetime NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `idx_government_referendums_status` (`status`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_referendum_votes` (
  `referendum_id` bigint NOT NULL,
  `citizenid` varchar(64) NOT NULL,
  `vote` enum('yes','no','abstain') NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`referendum_id`,`citizenid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

## install/migrate\_v1\_to\_v2.sql

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```sql
-- v2: Parties, campaign advertising, grants, contracts and referendums
CREATE TABLE IF NOT EXISTS `government_parties` (
  `id` int NOT NULL AUTO_INCREMENT,
  `name` varchar(64) NOT NULL,
  `short_name` varchar(12) NOT NULL,
  `color` varchar(16) DEFAULT '#d4af37',
  `description` text DEFAULT NULL,
  `leader_citizenid` varchar(64) NOT NULL,
  `leader_name` varchar(128) NOT NULL,
  `is_public` tinyint(1) NOT NULL DEFAULT 1,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_government_party_name` (`name`),
  UNIQUE KEY `uq_government_party_short` (`short_name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_party_members` (
  `party_id` int NOT NULL,
  `citizenid` varchar(64) NOT NULL,
  `name` varchar(128) NOT NULL,
  `role` enum('member','officer','leader') NOT NULL DEFAULT 'member',
  `joined_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`party_id`,`citizenid`),
  UNIQUE KEY `uq_government_party_member_once` (`citizenid`),
  KEY `idx_government_party_member_party` (`party_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_campaign_ads` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `election_id` int NOT NULL,
  `candidate_id` int NOT NULL,
  `zone_key` varchar(64) NOT NULL,
  `headline` varchar(128) NOT NULL,
  `slogan` varchar(255) DEFAULT NULL,
  `starts_at` datetime NOT NULL,
  `ends_at` datetime NOT NULL,
  `price` bigint NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `idx_government_campaign_ads_active` (`zone_key`,`ends_at`),
  KEY `idx_government_campaign_ads_election` (`election_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_grants` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `citizenid` varchar(64) NOT NULL,
  `applicant_name` varchar(128) NOT NULL,
  `job_name` varchar(64) NOT NULL,
  `job_label` varchar(128) NOT NULL,
  `amount` bigint NOT NULL,
  `reason` text NOT NULL,
  `status` enum('pending','approved','rejected','paid') NOT NULL DEFAULT 'pending',
  `reviewed_by` varchar(64) DEFAULT NULL,
  `review_note` varchar(500) DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `reviewed_at` datetime DEFAULT NULL,
  `paid_at` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `idx_government_grants_status` (`status`),
  KEY `idx_government_grants_job` (`job_name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_contracts` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `title` varchar(150) NOT NULL,
  `description` text NOT NULL,
  `max_budget` bigint NOT NULL,
  `status` enum('open','closed','awarded','cancelled','completed') NOT NULL DEFAULT 'open',
  `created_by` varchar(64) NOT NULL,
  `winner_bid_id` bigint DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `closes_at` datetime DEFAULT NULL,
  `awarded_at` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `idx_government_contracts_status` (`status`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_contract_bids` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `contract_id` bigint NOT NULL,
  `citizenid` varchar(64) NOT NULL,
  `bidder_name` varchar(128) NOT NULL,
  `job_name` varchar(64) NOT NULL,
  `job_label` varchar(128) NOT NULL,
  `amount` bigint NOT NULL,
  `proposal` text NOT NULL,
  `status` enum('submitted','won','lost','withdrawn') NOT NULL DEFAULT 'submitted',
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `uq_government_contract_bid_job` (`contract_id`,`job_name`),
  KEY `idx_government_contract_bids_contract` (`contract_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_referendums` (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `title` varchar(150) NOT NULL,
  `question` text NOT NULL,
  `status` enum('open','closed','cancelled') NOT NULL DEFAULT 'open',
  `created_by` varchar(64) NOT NULL,
  `created_by_name` varchar(128) NOT NULL,
  `closes_at` datetime NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `idx_government_referendums_status` (`status`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `government_referendum_votes` (
  `referendum_id` bigint NOT NULL,
  `citizenid` varchar(64) NOT NULL,
  `vote` enum('yes','no','abstain') NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`referendum_id`,`citizenid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

## install/qbx\_job.lua

Original supplied contents. Merge/import only as directed by the installation guide; this is not an automatically executed migration.

```lua
-- Add this entry permanently to qbx_core/shared/jobs.lua if your QBox build stores jobs there.
-- advanced_government also registers it at runtime, but a permanent entry prevents group cleanup
-- from treating the government job as unknown during qbx_core startup.

government = {
    label = 'Statsrådet',
    type = 'government',
    defaultDuty = true,
    offDutyPay = false,
    grades = {
        [0] = { name = 'Medarbejder', payment = 0 },
        [1] = { name = 'Rådmand', payment = 0 },
        [2] = { name = 'Minister', payment = 0 },
        [3] = { name = 'Viceborgmester', payment = 0, isboss = true },
        [4] = { name = 'Borgmester', payment = 0, isboss = true }
    }
}
```
