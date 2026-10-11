# Database

```sql
CREATE TABLE IF NOT EXISTS `stivendev_organizaciones` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `nombre` varchar(64) NOT NULL,
  `label` varchar(64) NOT NULL,
  `color` varchar(9) DEFAULT NULL,
  `miembros_maximos` int(11) NOT NULL DEFAULT 1,
  `jefe` varchar(128) DEFAULT NULL,
  `permisos` text DEFAULT NULL,
  `logos_orga` varchar(255) DEFAULT NULL,
  `tienda` longtext DEFAULT NULL,
  `notas_administracion` longtext DEFAULT NULL,
  `puntos_data` longtext DEFAULT NULL CHECK (json_valid(`puntos_data`)),
  `miembros` longtext DEFAULT NULL CHECK (json_valid(`miembros`)),
  `rangos` longtext DEFAULT NULL CHECK (json_valid(`rangos`)),
  `nivel` float NOT NULL DEFAULT 1,
  `dinero_orga` int(11) NOT NULL DEFAULT 0,
  `npc_data` longtext DEFAULT NULL CHECK (json_valid(`npc_data`)),
  PRIMARY KEY (`id`),
  UNIQUE KEY `uniq_nombre` (`nombre`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `stivendev_org_darkchat` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `label` varchar(50) NOT NULL,
  `org_label` varchar(50) DEFAULT NULL,
  `texto` text DEFAULT NULL,
  `message` longtext DEFAULT NULL,
  `identifier` varchar(64) NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp(),
  PRIMARY KEY (`id`),
  KEY `idx_identifier` (`identifier`),
  KEY `idx_label` (`label`),
  KEY `idx_org_label` (`org_label`)
) ENGINE=InnoDB AUTO_INCREMENT=50 DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `stivendev_org_garages_vehicles` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `vehicle` varchar(50) NOT NULL,
  `label` varchar(100) NOT NULL,
  `props` longtext DEFAULT NULL,
  `plate` varchar(20) NOT NULL,
  `banda_label` varchar(100) NOT NULL,
  `fuel` float(5,2) DEFAULT 100.00,
  `stored` tinyint(1) DEFAULT 1,
  `estado` enum('robado','veh_orga') NOT NULL DEFAULT 'veh_orga',
  PRIMARY KEY (`id`),
  UNIQUE KEY `plate_unique` (`plate`)
) ENGINE=InnoDB AUTO_INCREMENT=37 DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `stivendev_org_logs_money` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `info` longtext DEFAULT NULL,
  `label_banda` varchar(50) NOT NULL,
  `identifier` varchar(64) NOT NULL,
  `name` varchar(100) NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp(),
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=33 DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS `stivendev_org_misiones` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `org_id` int(11) NOT NULL,
  `mision_id` varchar(50) COLLATE utf8mb4_unicode_ci NOT NULL,
  `progreso` int(11) DEFAULT 0,
  `completada` tinyint(1) DEFAULT 0,
  `fecha_inicio` timestamp NOT NULL DEFAULT current_timestamp(),
  `fecha_actualizacion` timestamp NOT NULL DEFAULT current_timestamp() ON UPDATE current_timestamp(),
  PRIMARY KEY (`id`),
  KEY `idx_org_id` (`org_id`),
  KEY `idx_mision_id` (`mision_id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

CREATE TABLE IF NOT EXISTS `stivendev_org_territorios` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `label_banda` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL,
  `coords` longtext CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL CHECK (json_valid(`coords`)),
  `type` enum('droga') NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp(),
  `progreso` longtext CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL CHECK (json_valid(`progreso`)),
  PRIMARY KEY (`id`),
  KEY `idx_label_banda` (`label_banda`)
) ENGINE=InnoDB AUTO_INCREMENT=23 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

CREATE TABLE IF NOT EXISTS `stivendev_org_businesses` (
    `name` VARCHAR(50) PRIMARY KEY,
    `last_collected` BIGINT DEFAULT 0
)

```
