# ESX

```sql
CREATE TABLE IF NOT EXISTS `owned_vehicles` (
    `id`             INT          AUTO_INCREMENT PRIMARY KEY,

    `owner`          VARCHAR(60)  NOT NULL,
    `plate`          VARCHAR(12)  NOT NULL,

    `vehicle`        LONGTEXT     NOT NULL,
    `props`          LONGTEXT     DEFAULT NULL,

    `type`           VARCHAR(20)  DEFAULT 'car',
    `job`            VARCHAR(20)  DEFAULT NULL,

    `stored`         TINYINT(1)   NOT NULL DEFAULT 1,
    `in_garage`      TINYINT(1)   NOT NULL DEFAULT 1,
    `parking`        VARCHAR(20)  DEFAULT 'IN',

    `garage_id`      VARCHAR(60)  NOT NULL DEFAULT 'Legion Square',

    `fuel`           FLOAT        NOT NULL DEFAULT 100,
    `body`           FLOAT        NOT NULL DEFAULT 1000,
    `engine`         FLOAT        NOT NULL DEFAULT 1000,

    `impound`        TINYINT(1)   NOT NULL DEFAULT 0,
    `impound_by`     VARCHAR(60)  DEFAULT NULL,
    `impound_reason` VARCHAR(255) DEFAULT NULL,
    `impound_time`   BIGINT       DEFAULT NULL,
    `return_fee`     INT          NOT NULL DEFAULT 0,

    `mileage`        INT          NOT NULL DEFAULT 0,
    `nickname`       VARCHAR(64)  DEFAULT NULL,

    UNIQUE KEY `plate` (`plate`),
    INDEX `idx_owner`   (`owner`),
    INDEX `idx_garage`  (`garage_id`),
    INDEX `idx_impound` (`impound`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

ALTER TABLE `owned_vehicles`
    ADD COLUMN IF NOT EXISTS `props`          LONGTEXT     DEFAULT NULL,
    ADD COLUMN IF NOT EXISTS `fuel`           FLOAT        NOT NULL DEFAULT 100,
    ADD COLUMN IF NOT EXISTS `body`           FLOAT        NOT NULL DEFAULT 1000,
    ADD COLUMN IF NOT EXISTS `engine`         FLOAT        NOT NULL DEFAULT 1000,
    ADD COLUMN IF NOT EXISTS `in_garage`      TINYINT(1)   NOT NULL DEFAULT 1,
    ADD COLUMN IF NOT EXISTS `stored`         TINYINT(1)   NOT NULL DEFAULT 1,
    ADD COLUMN IF NOT EXISTS `parking`        VARCHAR(20)  DEFAULT 'IN',
    ADD COLUMN IF NOT EXISTS `garage_id`      VARCHAR(60)  NOT NULL DEFAULT 'Legion Square',
    ADD COLUMN IF NOT EXISTS `impound`        TINYINT(1)   NOT NULL DEFAULT 0,
    ADD COLUMN IF NOT EXISTS `impound_by`     VARCHAR(60)  DEFAULT NULL,
    ADD COLUMN IF NOT EXISTS `impound_reason` VARCHAR(255) DEFAULT NULL,
    ADD COLUMN IF NOT EXISTS `impound_time`   BIGINT       DEFAULT NULL,
    ADD COLUMN IF NOT EXISTS `return_fee`     INT          NOT NULL DEFAULT 0,
    ADD COLUMN IF NOT EXISTS `mileage`        INT          NOT NULL DEFAULT 0,
    ADD COLUMN IF NOT EXISTS `nickname`       VARCHAR(64)  DEFAULT NULL;

CREATE INDEX IF NOT EXISTS `idx_owner`   ON `owned_vehicles` (`owner`);
CREATE INDEX IF NOT EXISTS `idx_garage`  ON `owned_vehicles` (`garage_id`);
CREATE INDEX IF NOT EXISTS `idx_impound` ON `owned_vehicles` (`impound`);


CREATE TABLE IF NOT EXISTS `private_garages` (
    `id`      INT          AUTO_INCREMENT PRIMARY KEY,
    `name`    VARCHAR(100) NOT NULL,
    `owner`   VARCHAR(60)  NOT NULL,

    `x`       FLOAT        NOT NULL,
    `y`       FLOAT        NOT NULL,
    `z`       FLOAT        NOT NULL,
    `heading` FLOAT        NOT NULL DEFAULT 0,

    `radius`  INT          NOT NULL DEFAULT 10,
    `type`    VARCHAR(20)  NOT NULL DEFAULT 'car',

    INDEX (`owner`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `private_garage_owners` (
    `id`         INT         AUTO_INCREMENT PRIMARY KEY,
    `garage_id`  INT         NOT NULL,
    `identifier` VARCHAR(60) NOT NULL,
    `name`       VARCHAR(80) NOT NULL,

    FOREIGN KEY (`garage_id`) REFERENCES `private_garages`(`id`) ON DELETE CASCADE,
    INDEX (`garage_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `st_dynamic_garages` (
    `id`           INT          AUTO_INCREMENT PRIMARY KEY,

    `name`         VARCHAR(100) NOT NULL UNIQUE,
    `garage_type`  VARCHAR(20)  NOT NULL DEFAULT 'public',

    `coords_x`     FLOAT        NOT NULL DEFAULT 0,
    `coords_y`     FLOAT        NOT NULL DEFAULT 0,
    `coords_z`     FLOAT        NOT NULL DEFAULT 0,

    `distance`     FLOAT        NOT NULL DEFAULT 5,
    `type`         VARCHAR(20)  NOT NULL DEFAULT 'car',

    `blip_id`      INT          NOT NULL DEFAULT 357,
    `blip_color`   INT          NOT NULL DEFAULT 3,
    `blip_scale`   FLOAT        NOT NULL DEFAULT 0.7,
    `hide_blip`    TINYINT(1)   NOT NULL DEFAULT 0,

    `marker_id`    INT          NOT NULL DEFAULT 36,
    `marker_scale` FLOAT        NOT NULL DEFAULT 0.3,
    `marker_r`     INT          NOT NULL DEFAULT 255,
    `marker_g`     INT          NOT NULL DEFAULT 255,
    `marker_b`     INT          NOT NULL DEFAULT 255,
    `marker_a`     INT          NOT NULL DEFAULT 120,
    `hide_markers` TINYINT(1)   NOT NULL DEFAULT 0,

    `spawn_data`   TEXT         DEFAULT NULL,
    `vehicles_data` TEXT        DEFAULT NULL,
    `jobs`         VARCHAR(255) DEFAULT NULL,

    `created_at`   TIMESTAMP    DEFAULT CURRENT_TIMESTAMP,

    INDEX (`garage_type`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

UPDATE `owned_vehicles` SET `in_garage` = 1   WHERE `in_garage` IS NULL;
UPDATE `owned_vehicles` SET `stored`    = 1   WHERE `stored`    IS NULL;
UPDATE `owned_vehicles` SET `parking`   = 'IN' WHERE `parking`  IS NULL;
UPDATE `owned_vehicles` SET `fuel`      = 100  WHERE `fuel`      IS NULL;
UPDATE `owned_vehicles` SET `body`      = 1000 WHERE `body`      IS NULL;
UPDATE `owned_vehicles` SET `engine`    = 1000 WHERE `engine`    IS NULL;
UPDATE `owned_vehicles` SET `garage_id` = 'Legion Square' WHERE `garage_id` IS NULL OR `garage_id` = '';
```
