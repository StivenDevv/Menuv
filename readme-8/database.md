# Database

```sql
CREATE TABLE `ST_safezone` (
    `id` INT(11) NOT NULL AUTO_INCREMENT,
    `data` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
    PRIMARY KEY (`id`) USING BTREE
)
    COLLATE='utf8mb3_general_ci'
    ENGINE=InnoDB
;

```

