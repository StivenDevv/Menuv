# Batabase

CREATE TABLE IF NOT EXISTS `ST_drugscreator` ( `key` varchar(100) NOT NULL, `data` longtext DEFAULT NULL, PRIMARY KEY (`key`) ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4\_general\_ci;

CREATE TABLE IF NOT EXISTS `ST_drugscreator_plants` ( `id` int(11) NOT NULL, `data` longtext DEFAULT NULL, PRIMARY KEY (`id`) ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4\_general\_ci;

CREATE TABLE IF NOT EXISTS `ST_drugscreator_lamps` ( `id` int(11) NOT NULL, `data` longtext DEFAULT NULL, PRIMARY KEY (`id`) ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4\_general\_ci;

CREATE TABLE IF NOT EXISTS `ST_drugscreator_labs` ( `index` int(11) NOT NULL, `entranceIndex` int(11) NOT NULL, `identifier` varchar(100) NOT NULL, `keys` longtext DEFAULT NULL, PRIMARY KEY (`index`, `entranceIndex`) ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4\_general\_ci;

CREATE TABLE IF NOT EXISTS `ST_drugscreator_tables` ( `id` int(11) NOT NULL, `data` longtext DEFAULT NULL, PRIMARY KEY (`id`) ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4\_general\_ci;

CREATE TABLE IF NOT EXISTS `ST_drugscreator_stats` ( `id` int(11) NOT NULL AUTO\_INCREMENT, `date` date NOT NULL, `drug_name` varchar(50) NOT NULL, `processed` int(11) DEFAULT 0, `sold` int(11) DEFAULT 0, PRIMARY KEY (`id`), UNIQUE KEY `date_drug` (`date`, `drug_name`) ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4\_general\_ci;
