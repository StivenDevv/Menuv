# Database

```sql
CREATE TABLE IF NOT EXISTS `stiven_arenas` (
  DROP TABLE IF EXISTS `communityservice_items`;
DROP TABLE IF EXISTS `communityservice`;
DROP TABLE IF EXISTS `sanctions_history`;

CREATE TABLE `communityservice` (
  `identifier`        varchar(100) NOT NULL,
  `type`              enum('service','jail','animal') NOT NULL DEFAULT 'service',
  `actions_remaining` int(10)      NOT NULL DEFAULT 0,
  `reason`            varchar(255) DEFAULT 'Comportamiento inapropiado',
  `assigned_by`       varchar(100) DEFAULT 'Sistema',
  `saved_x`           float        DEFAULT NULL,
  `saved_y`           float        DEFAULT NULL,
  `saved_z`           float        DEFAULT NULL,
  `saved_heading`     float        DEFAULT NULL,
  `created_at`        timestamp    NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`identifier`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE `sanctions_history` (
  `id`          int(11)      NOT NULL AUTO_INCREMENT,
  `identifier`  varchar(100) NOT NULL,
  `player_name` varchar(100) NOT NULL DEFAULT '',
  `type`        enum('service','jail','animal') NOT NULL DEFAULT 'service',
  `duration`    int(10)      NOT NULL DEFAULT 0,
  `reason`      varchar(255) DEFAULT 'Sin razón',
  `assigned_by` varchar(100) DEFAULT 'Sistema',
  `created_at`  timestamp    NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  KEY `idx_identifier` (`identifier`),
  KEY `idx_type`       (`type`),
  KEY `idx_player_name`(`player_name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE `communityservice_items` (
  `id`         int(11)      NOT NULL AUTO_INCREMENT,
  `identifier` varchar(100) NOT NULL,
  `items`      longtext     NOT NULL,
  PRIMARY KEY (`id`),
  KEY `identifier` (`identifier`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

```
