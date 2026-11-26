# SQL

```sql
CREATE TABLE IF NOT EXISTS `st_f6_permissions` (
    `id` INT AUTO_INCREMENT PRIMARY KEY,
    `identifier` VARCHAR(255) NOT NULL,
    `name` VARCHAR(255) NOT NULL,
    `permissions` LONGTEXT DEFAULT NULL,
    `added_by` VARCHAR(255) NOT NULL,
    `date_added` TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE KEY `unique_identifier` (`identifier`)
);

CREATE TABLE IF NOT EXISTS `st_admins` (
    `id` INT AUTO_INCREMENT PRIMARY KEY,
    `identifier` VARCHAR(255) NOT NULL,
    `name` VARCHAR(255) NOT NULL
);
```

