# Database

```sql
CREATE TABLE IF NOT EXISTS `stiven_arenas` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `player` varchar(150) DEFAULT NULL,
  `username` varchar(150) DEFAULT NULL,
  `deaths` int(11) DEFAULT 0,
  `kills` int(11) DEFAULT 0,
  `score` int(11) DEFAULT 0,
  `wins` int(11) DEFAULT 0,
  `losses` int(11) DEFAULT 0,
  PRIMARY KEY (`id`),
  UNIQUE KEY `Columna 2` (`player`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

CREATE TABLE IF NOT EXISTS `stiven_arenas_players` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `player` varchar(150) NOT NULL DEFAULT '0',
  `status` int(11) NOT NULL DEFAULT 0,
  PRIMARY KEY (`id`),
  UNIQUE KEY `player` (`player`)
) ENGINE=InnoDB AUTO_INCREMENT=11 DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

```
