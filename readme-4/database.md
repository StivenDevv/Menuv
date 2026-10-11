# Database

```sql
CREATE TABLE IF NOT EXISTS `reports`(
    `admin_identifier` varchar(255) NOT NULL,
    `responded_reports` varchar(255) NOT NULL DEFAULT 1,
    UNIQUE KEY abc_ndx (admin_identifier)
);

CREATE TABLE IF NOT EXISTS `active_reports`(
    `id` INT AUTO_INCREMENT PRIMARY KEY,
    `report_id` INT NOT NULL,
    `category` VARCHAR(50) NOT NULL,
    `title` VARCHAR(255) NOT NULL,
    `description` TEXT NOT NULL,
    `player_source` INT NOT NULL,
    `player_name` VARCHAR(255) NOT NULL,
    `player_identifier` VARCHAR(255) NOT NULL,
    `admin_name` VARCHAR(255) DEFAULT NULL,
    `admin_source` INT DEFAULT NULL,
    `admin_identifier` VARCHAR(255) DEFAULT NULL,
    `messages` LONGTEXT DEFAULT NULL,
    `is_being_helped` TINYINT(1) DEFAULT 0,
    `is_admin_assisting` TINYINT(1) DEFAULT 0,
    `bring_start_pos` VARCHAR(255) DEFAULT NULL,
    `admin_start_pos` VARCHAR(255) DEFAULT NULL,
    `created_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    `updated_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    INDEX `idx_player_source` (`player_source`),
    INDEX `idx_report_id` (`report_id`)
);

CREATE TABLE IF NOT EXISTS `concluded_reports`(
    `id` INT AUTO_INCREMENT PRIMARY KEY,
    `report_id` INT NOT NULL,
    `category` VARCHAR(50) NOT NULL,
    `title` VARCHAR(255) NOT NULL,
    `description` TEXT NOT NULL,
    `player_name` VARCHAR(255) NOT NULL,
    `player_identifier` VARCHAR(255) DEFAULT NULL,
    `player_discord` VARCHAR(255) DEFAULT NULL,
    `admin_name` VARCHAR(255) DEFAULT NULL,
    `admin_identifier` VARCHAR(255) DEFAULT NULL,
    `messages` LONGTEXT DEFAULT NULL,
    `concluded_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    INDEX `idx_concluded_report_id` (`report_id`),
    INDEX `idx_concluded_at` (`concluded_at`)
);
```
