# Qbcore & Qbx

```sql
ALTER TABLE `player_vehicles`
    ADD COLUMN IF NOT EXISTS `garage_id`      VARCHAR(60)  NOT NULL DEFAULT 'Legion Square',
    ADD COLUMN IF NOT EXISTS `impound`        TINYINT(1)   NOT NULL DEFAULT 0,
    ADD COLUMN IF NOT EXISTS `impound_by`     VARCHAR(60)  DEFAULT NULL,
    ADD COLUMN IF NOT EXISTS `impound_reason` VARCHAR(255) DEFAULT NULL,
    ADD COLUMN IF NOT EXISTS `impound_time`   BIGINT       DEFAULT NULL,
    ADD COLUMN IF NOT EXISTS `return_fee`     INT          NOT NULL DEFAULT 0,
    ADD COLUMN IF NOT EXISTS `mileage`        INT          NOT NULL DEFAULT 0,
    ADD COLUMN IF NOT EXISTS `nickname`       VARCHAR(64)  DEFAULT NULL,
    ADD COLUMN IF NOT EXISTS `type`           VARCHAR(20)  NOT NULL DEFAULT 'car',
    ADD COLUMN IF NOT EXISTS `stored`         TINYINT(1)   NOT NULL DEFAULT 1,
    ADD COLUMN IF NOT EXISTS `in_garage`      TINYINT(1)   NOT NULL DEFAULT 1,
    ADD COLUMN IF NOT EXISTS `parking`        VARCHAR(20)  DEFAULT NULL;

ALTER TABLE `player_vehicles`
    MODIFY COLUMN `vehicle` VARCHAR(100) DEFAULT NULL;

CREATE INDEX IF NOT EXISTS `idx_citizenid_pv` ON `player_vehicles` (`citizenid`);
CREATE INDEX IF NOT EXISTS `idx_garage_pv`    ON `player_vehicles` (`garage_id`);
CREATE INDEX IF NOT EXISTS `idx_impound_pv`   ON `player_vehicles` (`impound`);
CREATE INDEX IF NOT EXISTS `idx_type_pv`      ON `player_vehicles` (`type`);
CREATE INDEX IF NOT EXISTS `idx_stored_pv`    ON `player_vehicles` (`stored`);
CREATE INDEX IF NOT EXISTS `idx_ingarage_pv`  ON `player_vehicles` (`in_garage`);

UPDATE `player_vehicles`
SET `garage_id` = 'Legion Square'
WHERE (`garage_id` IS NULL OR `garage_id` = '');

UPDATE `player_vehicles`
SET
    `stored`    = 1,
    `in_garage` = 1,
    `parking`   = NULL
WHERE
    `impound` = 0
    AND (
        (`stored` = 0 AND `in_garage` = 0 AND (`parking` = 'OUT' OR `parking` IS NULL))
        OR (`parking` = 'OUT' AND `stored` = 1)
    );

UPDATE `player_vehicles`
SET `vehicle` = SUBSTRING_INDEX(
                    SUBSTRING_INDEX(`vehicle`, '"name":"', -1),
                    '"', 1
                )
WHERE `vehicle` LIKE '{"name":"%'
  AND `vehicle` NOT LIKE '%}';

UPDATE `player_vehicles`
SET `vehicle` = SUBSTRING_INDEX(
                    SUBSTRING_INDEX(`vehicle`, '"model":"', -1),
                    '"', 1
                )
WHERE `vehicle` LIKE '{%'
  AND `vehicle` NOT LIKE '%}'
  AND `vehicle` LIKE '%"model":"%';

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
    INDEX idx_owner (`owner`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `private_garage_owners` (
    `id`         INT         AUTO_INCREMENT PRIMARY KEY,
    `garage_id`  INT         NOT NULL,
    `identifier` VARCHAR(60) NOT NULL,
    `name`       VARCHAR(80) NOT NULL,
    FOREIGN KEY (`garage_id`) REFERENCES `private_garages`(`id`) ON DELETE CASCADE,
    INDEX idx_garage_id (`garage_id`)
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
    INDEX idx_garage_type (`garage_type`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

SELECT
    SUM(CASE WHEN stored = 1 AND in_garage = 1 AND parking IS NULL THEN 1 ELSE 0 END) AS guardados,
    SUM(CASE WHEN stored = 0 AND in_garage = 0 AND parking = 'OUT'  THEN 1 ELSE 0 END) AS afuera,
    SUM(CASE WHEN impound = 1 THEN 1 ELSE 0 END)                                       AS en_deposito,
    COUNT(*) AS total
FROM `player_vehicles`;
```
