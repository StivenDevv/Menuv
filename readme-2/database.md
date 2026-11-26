# Database

```sql
CREATE TABLE IF NOT EXISTS `Stiven_vipweapons_attachments` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `label` varchar(50) NOT NULL DEFAULT '0',
  `hash` varchar(50) NOT NULL DEFAULT '0',
  `weapon_id` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=76 DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

CREATE TABLE IF NOT EXISTS `Stiven_vipweapons_profiles` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(50) NOT NULL DEFAULT '0',
  `identifier` longtext DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `identifier` (`identifier`) USING HASH
) ENGINE=InnoDB AUTO_INCREMENT=127 DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

CREATE TABLE IF NOT EXISTS `Stiven_vipweapons_profiles_attachments` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `owner` longtext DEFAULT NULL,
  `data_weapon_id` int(11) NOT NULL DEFAULT 0,
  `attachment_id` int(11) DEFAULT NULL,
  `active` int(11) DEFAULT 1,
  `enabled` int(11) DEFAULT 1,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=478 DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

CREATE TABLE IF NOT EXISTS `Stiven_vipweapons_profiles_weapons` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `owner` longtext DEFAULT NULL,
  `weapon_id` int(11) NOT NULL DEFAULT 0,
  `weapon_label` varchar(50) NOT NULL DEFAULT '',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=235 DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;

CREATE TABLE IF NOT EXISTS `Stiven_vipweapons_weapons` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `label` varchar(50) NOT NULL DEFAULT '0',
  `hash` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=75 DEFAULT CHARSET=utf8mb3 COLLATE=utf8mb3_general_ci;
```
