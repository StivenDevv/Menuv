# Config

```lua
Config = Config or {}

-- ============================
--        FRAMEWORK
-- ============================
Config.Framework = "qb" -- "esx" | "qb"
Config.Locale    = "en"  -- "es" | "en" | "fr" | "de" | "pt"
Config.Inventory = "ox"  -- "ox" | "qs-inventory" | "origen_inventory" | "origen_inventoryv2" | "codem-inventory" | "qb-inventory" | "esx_inventory"
Config.DrawText = "ST-textui" -- "auto" | "ST-textui" | "jg-textui" | "ox_lib" | "qb-drawtext" | "okokTextUI" | "ps-ui" | "esx_textui"
Config.VehicleKeys = "none" -- "none" | "qb-vehiclekeys" | "MrNewbVehicleKeys" | "jaksam-vehicles-keys" | "qs-vehiclekeys" | "mk_vehiclekeys" | "wasabi_carlock"
Config.FuelSystem = "ox_fuel" -- "none" | "LegacyFuel" | "ox_fuel" | "ps-fuel" | "cdn-fuel" | "nd_fuel"

-- ============================
--        ADMINISTRACIÓN
-- ============================
Config.CommandAdminPanel = 'admingang'     -- Comando para abrir el panel de administración
Config.AcePermission     = 'st_org.admin'  -- Permiso ACE configurado en server.cfg (ej: add_ace group.admin st_org.admin allow)

-- ============================
--        ORGANIZACIONES
-- ============================
Config.MaxOrgVehicles = 5     -- Max vehicles an org can have active at once
Config.ColorVehiculos = true  -- Paint vehicles in the org's color
Config.VehicleFix     = false -- Repair vehicles when spawned from garage


Config.RangosAjustes = { -- Ranks shown in the tablet settings section
    "jefe",
    "subjefe",
    "encargado",
    "administrador",
}

Config.OpenOrgMenuKey = "F6" -- Key to open the org action menu

-- ============================
--        TABLET ILEGAL
-- ============================
Config.TabletIlegal = {
    Enabled         = true,
    UseItem         = true,
    ItemName        = "tablet_ilegal",
    CommandName     = "tabletilegal",
    KeyMappingLabel = "Abrir tablet de la organización",
}

-- ============================
--        ALMACÉN
-- ============================
Config.Almacen = {
    slots     = 150,
    maxWeight = 2000000
}

-- ============================
--        NPC DEL BARRIO
-- ============================
Config.BarrioBlip = {
    enabled    = true,
    sprite     = 357,
    scale      = 0.7,
    colour     = 5,
    shortRange = false,
    label      = "Mi Barrio"
}

-- ============================
--        GPS & BLIPS
-- ============================
Config.UseGPS = true

Config.BlipsOrgas = {
    blip_players    = 630,
    blip_coche      = 225,
    blip_muerto     = 274,
    blip_barco      = 410,
    blip_helicoptero = 43
}

-- ============================
--        ESPOSAS & BOLSA
-- ============================
Config.BagStrength             = 1.0   -- Bag opacity (1.0 = full black)
Config.BagRequireHandcuff      = true  -- Bag only works when player is cuffed
Config.UsePropHandCuff         = true  -- Show cable tie prop when cuffing
Config.UseItemHandCuff         = false -- Require handcuff item to cuff
Config.HandcuffUseItemToArrest = false -- Use item to arrest

Config.HandcuffDisabledControls = {
--  1,    -- Pan
--  2,    -- Tilt
    21,   -- Sprint
    24,   -- Attack
    25,   -- Aim
    30,   -- D
    31,   -- S
    32,   -- W
    34,   -- A
    37,   -- Weapon Wheel
    44,   -- Cover
    45,   -- Reload
    47,   -- Weapon
    59,   -- Vehicle steering
    71,   -- Vehicle forward
    72,   -- Vehicle reverse
    73,   -- Clear animation
    75,   -- Exit vehicle
    140,  -- Melee
    141,  -- Melee
    142,  -- Melee
    143,  -- Melee
    167,  -- Job
    170,  -- Animations
--  199,  -- Pause
    257,  -- Attack 2
    263,  -- Melee Attack 1
    264,  -- Melee
    288,  -- Phone
    289,  -- Inventory
}

-- ============================
--        POLICÍA
-- ============================
Config.PoliceJobs = {
    "police",
    "sheriff",
    "fbi"
}

-- ============================
--        DARK CHAT
-- ============================
Config.DarkChat          = true
Config.FiltroPalabrotas  = true

Config.PalabrasProhibidas = {
    "polla", "cabron", "cabrón", "puta", "puto", "putas", "putos",
    "gilipollas", "maricon", "maricón", "subnormal", "retrasado",
    "idiota", "imbecil", "imbécil", "zorra", "perra", "perro",
    "estupido", "estúpido", "mierda", "cagon", "cagón", "pendejo",
    "culiao", "pelotudo", "baboso", "mamon", "mamón", "tarado",
    "anormal", "mongolo", "chupapollas", "comeojete", "payaso",
    "asco", "asqueroso", "asquerosa", "hijoputa", "hijo de puta",
    "hdp", "malparido", "bastardo", "cornudo", "nazi", "racista",
    "negro de mierda", "sidoso", "apestoso", "pajero", "lerdo",
    "gordo de mierda"
}

Config.RegexProhibidas = {}
for _, palabra in ipairs(Config.PalabrasProhibidas) do
    local pattern = palabra:gsub("([.*+?^$()%%[%]-])", "%%%1")
    pattern = pattern:gsub("a", "[a@4]+")
    pattern = pattern:gsub("e", "[e3]+")
    pattern = pattern:gsub("i", "[i1!íì]+")
    pattern = pattern:gsub("o", "[o0óò]+")
    pattern = pattern:gsub("u", "[uúù]+")
    pattern = pattern:gsub("(.)", "%1[ ._-]*")
    table.insert(Config.RegexProhibidas, pattern)
end

-- ============================
--        DEBUG
-- ============================
Config.Debug = false
Config.SecurityIMG = false

-- ============================
--    VENDER DROGAS A NPC
-- ============================
Config.VenderDrogas = {
    Enabled  = true,
    Account  = "black_money", -- Tipo de dinero a recibir: "money" / "cash" (dinero limpio en efectivo), "black_money" / "black" (dinero negro/sucio), "bank" (banco)
    Cooldown = 5,   -- Cooldown en segundos entre ventas
    VentasParaConquistar = 5, -- Número de ventas necesarias para conseguir el 100% del territorio
    AlertasPolicia = {
        enabled = true,
        -- Lista de umbrales basados en el % de control del territorio (de mayor a menor)
        -- Si la banda tiene 'control' o más de %, se dispara la alerta tras 'ventasParaAlerta' ventas.
        Umbrales = {
            { control = 80, ventasParaAlerta = 2 },
            { control = 70, ventasParaAlerta = 4 },
            { control = 0,  ventasParaAlerta = 6 }
        }
    },
    Drugs = {
        -- Puedes especificar Account individual por cada droga si deseas (o dejará la de Config.VenderDrogas.Account)
        { Items = "marijuana",      ItemsLabel = "Bolsa de marihuana",   PriceMin = 200, PriceMax = 500, MinAmount = 1, MaxAmount = 10, Account = "black_money" },
        { Items = "cocaprocesada",  ItemsLabel = "Bolsa de Cocaina",     PriceMin = 200, PriceMax = 500, MinAmount = 1, MaxAmount = 10, Account = "black_money" },
        { Items = "lsdprocesada",   ItemsLabel = "Extasis",              PriceMin = 200, PriceMax = 500, MinAmount = 1, MaxAmount = 10, Account = "black_money" },
        { Items = "hongoprocesada", ItemsLabel = "Hongos",               PriceMin = 200, PriceMax = 500, MinAmount = 1, MaxAmount = 10, Account = "black_money" },
        { Items = "crackprocesada", ItemsLabel = "Bolsa de Crack",       PriceMin = 200, PriceMax = 500, MinAmount = 1, MaxAmount = 10, Account = "black_money" },
        { Items = "opioprocesada",  ItemsLabel = "Bolsa de Opio",        PriceMin = 200, PriceMax = 500, MinAmount = 1, MaxAmount = 10, Account = "black_money" },
        { Items = "metaprocesada",  ItemsLabel = "Bolsa Metanfetamina",  PriceMin = 200, PriceMax = 500, MinAmount = 1, MaxAmount = 10, Account = "black_money" },
    }
}

-- ==========================================
--     TERRITORIES CONFIGURATION (USER)
-- ==========================================

Config.GangZones = {}

Config.GangZones['ROCKF'] = {
    name = 'ROCKF',
    label = 'Rockford Hills',
    neighbors = {
        'MORN',
        'WVINE',
        'MOVIE',
        'KOREAT',
        'BURTON'
    },
    parts = {
        { x1 = -1379.12, y1 = -257.26, x2 = -1299.88, y2 = -38.12 },
        { x1 = -920.61, y1 = -465.30, x2 = -521.31, y2 = -407.48 },
        { x1 = -1299.5, y1 = -407.3, x2 = -550.21, y2 = -126.82 },
        { x1 = -1299.55, y1 = -126.82, x2 = -743.39, y2 = 445.02 },
        { x1 = -743.39, y1 = -126.82, x2 = -594.91, y2 = 13.48 },
    },
    drugPreference = {
        CATEGORY_LOW = 1.0,
        CATEGORY_MED = 0.5,
        CATEGORY_HIGH = 1.3
    }
}
Config.GangZones['MORN'] = {
    name = 'MORN',
    label = 'Morningwood',
    neighbors = {
        'ROCKF',
        'MOVIE'
    },
    parts = {
        { x1 = -1635.47, y1 = -500.0, x2 = -1379.12, y2 = -107.29 },
        { x1 = -1379.12, y1 = -511.5, x2 = -1299.88, y2 = -257.26 },
    },
    drugPreference = {
        CATEGORY_LOW = 1.0,
        CATEGORY_MED = 0.5,
        CATEGORY_HIGH = 1.0
    }
}
Config.GangZones['MOVIE'] = {
    name = 'MOVIE',
    label = 'Richards Majestic',
    neighbors = {
        'MORN',
        'KOREAT',
        'ROCKF',
        'VCANA'
    },
    parts = {
        { x1 = -1380.23, y1 = -849.50, x2 = -1172.24, y2 = -511.48 },
        { x1 = -1172.24, y1 = -576.61, x2 = -1072.88, y2 = -543.51 },
        { x1 = -1172.24, y1 = -722.8, x2 = -1127.62, y2 = -576.61 },
        { x1 = -1172.24, y1 = -543.51, x2 = -998.41, y2 = -511.48 },
        { x1 = -1299.88, y1 = -511.48, x2 = -920.5, y2 = -407.23 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.3,
        CATEGORY_MED = 0.3,
        CATEGORY_HIGH = 1.0
    }
}
Config.GangZones['KOREAT'] = {
    name = 'KOREAT',
    label = 'Little Seoul',
    neighbors = {
        'ROCKF',
        'VCANA',
        'MOVIE',
        'STRAW',
        'PBOX'
    },
    parts = {
        { x1 = -1127.62, y1 = -723.01, x2 = -1072.88, y2 = -576.61 },
        { x1 = -1072.88, y1 = -723.01, x2 = -998.41, y2 = -543.51 },
        { x1 = -931.96, y1 = -849.49, x2 = -774.41, y2 = -723.01 },
        { x1 = -865.98, y1 = -907.78, x2 = -774.41, y2 = -849.49 },
        { x1 = -812.41, y1 = -1019.71, x2 = -774.41, y2 = -907.78 },
        { x1 = -998.41, y1 = -723.01, x2 = -403.51, y2 = -511.48 },
        { x1 = -920.61, y1 = -511.48, x2 = -521.31, y2 = -465.30 },
        { x1 = -573.84, y1 = -1425.40, x2 = -403.51, y2 = -1158.02 },
        { x1 = -774.41, y1 = -1158.02, x2 = -354.71, y2 = -723.01 },
    },
    drugPreference = {
        CATEGORY_LOW = 1.0,
        CATEGORY_MED = 1.0,
        CATEGORY_HIGH = 0.5
    }
}
Config.GangZones['MIRR'] = {
    name = 'MIRR',
    label = 'Mirror Park',
    neighbors = {
        'EAST_V',
        'LMESA'
    },
    parts = {
        { x1 = 869.70, y1 = -820.90, x2 = 1391.07, y2 = -282.32 },
    },
    drugPreference = {
        CATEGORY_LOW = 1.0,
        CATEGORY_MED = 0.15,
        CATEGORY_HIGH = 0.05
    }
}
Config.GangZones['LMESA'] = {
    name = 'LMESA',
    label = 'La Mesa',
    neighbors = {
        'MIRR',
        'TEXTI',
        'SKID',
        'RANCHO',
        'CYPRE',
        'EBURO'
    },
    parts = {
        { x1 = 921.45, y1 = -1901.45, x2 = 1118.89, y2 = -1708.33 },
        { x1 = 505.03, y1 = -1158.02, x2 = 934.14, y2 = -1006.57 },
        { x1 = 618.7, y1 = -1708.33, x2 = 1118.89, y2 = -1158.02 },
        { x1 = 505.03, y1 = -1006.57, x2 = 888.46, y2 = -820.90 },
        { x1 = 505.03, y1 = -820.90, x2 = 869.70, y2 = -510.0 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.5,
        CATEGORY_MED = 0.5,
        CATEGORY_HIGH = 0.2
    }
}
Config.GangZones['STRAW'] = {
    name = 'STRAW',
    label = 'Strawberry',
    neighbors = {
        'KOREAT',
        'PBOX',
        'SKID',
        'RANCHO',
        'DAVIS',
        'CHAMH'
    },
    parts = {
        { x1 = -63.92, y1 = -1700.53, x2 = 91.27, y2 = -1425.40 },
        { x1 = -403.51, y1 = -1425.40, x2 = 359.48, y2 = -1158.02 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.7,
        CATEGORY_MED = 1.0,
        CATEGORY_HIGH = 0.3
    }
}
Config.GangZones['RANCHO'] = {
    name = 'RANCHO',
    label = 'Rancho',
    neighbors = {
        'STRAW',
        'CYPRE',
        'SKID',
        'LMESA',
        'DAVIS'
    },
    parts = {
        { x1 = 359.48, y1 = -1761.99, x2 = 618.43, y2 = -1158.02 },
        { x1 = 271.51, y1 = -1761.99, x2 = 359.48, y2 = -1613.16 },
        { x1 = 222.40, y1 = -2022.57, x2 = 505.03, y2 = -1761.99 },
        { x1 = 123.73, y1 = -2168.95, x2 = 505.03, y2 = -2022.57 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.8,
        CATEGORY_MED = 0.9,
        CATEGORY_HIGH = 0.25
    }
}
Config.GangZones['CHAMH'] = {
    name = 'CHAMH',
    label = 'Chamberlain Hills',
    neighbors = {
        'STRAW',
        'DAVIS'
    },
    parts = {
        { x1 = -283.92, y1 = -1761.99, x2 = -63.92, y2 = -1425.40 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.9,
        CATEGORY_MED = 1.2,
        CATEGORY_HIGH = 0.2
    }
}
Config.GangZones['DAVIS'] = {
    name = 'DAVIS',
    label = 'Davis',
    neighbors = {
        'STRAW',
        'RANCHO',
        'CHAHM'
    },
    parts = {
        { x1 = -63.92, y1 = -1761.99, x2 = 271.51, y2 = -1700.53 },
        { x1 = 91.27, y1 = -1700.53, x2 = 271.51, y2 = -1613.16 },
        { x1 = 91.27, y1 = -1613.16, x2 = 359.48, y2 = -1425.40 },
        { x1 = -139.74, y1 = -2022.57, x2 = -9.70, y2 = -1761.99 },
        { x1 = -9.70, y1 = -2022.57, x2 = 115.40, y2 = -1761.99 },
        { x1 = 115.40, y1 = -2022.57, x2 = 222.40, y2 = -1761.99 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.8,
        CATEGORY_MED = 1.0,
        CATEGORY_HIGH = 0.4
    }
}
Config.GangZones['PBOX'] = {
    name = 'PBOX',
    label = 'Pillbox Hill',
    neighbors = {
        'TEXTI',
        'SKID',
        'KOREAT',
        'STRAW'
    },
    parts = {
        { x1 = -276.21, y1 = -722.91, x2 = 285.43, y2 = -573.01 },
        { x1 = -354.71, y1 = -1158.02, x2 = 119.43, y2 = -722.91 },
        { x1 = 199.43, y1 = -877.91, x2 = 285.43, y2 = -722.91 },
        { x1 = 119.43, y1 = -1158.02, x2 = 199.43, y2 = -722.91 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.8,
        CATEGORY_MED = 0.8,
        CATEGORY_HIGH = 1.1
    }
}
Config.GangZones['TEXTI'] = {
    name = 'TEXTI',
    label = 'Textile City',
    neighbors = {
        'LMESA',
        'PBOX',
        'SKID'
    },
    parts = {
        { x1 = 285.43, y1 = -877.91, x2 = 505.03, y2 = -510.0 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.9,
        CATEGORY_MED = 0.7,
        CATEGORY_HIGH = 0.5
    }
}
Config.GangZones['SKID'] = {
    name = 'SKID',
    label = 'Mission Row',
    neighbors = {
        'LMESA',
        'PBOX',
        'TEXTI',
        'RANCHO',
        'STRAW'
    },
    parts = {
        { x1 = 199.43, y1 = -1158.02, x2 = 505.03, y2 = -877.91 },
    },
    drugPreference = {
        CATEGORY_LOW = 1.2,
        CATEGORY_MED = 1.2,
        CATEGORY_HIGH = 1.2
    }
}
Config.GangZones['DTVINE'] = {
    name = 'DTVINE',
    label = 'Downtown Vinewood',
    neighbors = {
        'WVINE',
        'HAWICK',
        'ALTA',
        'EAST_V'
    },
    parts = {
        { x1 = 48.53, y1 = -20.78, x2 = 695.87, y2 = 445.02 },
    },
    drugPreference = {
        CATEGORY_LOW = 1.0,
        CATEGORY_MED = 0.85,
        CATEGORY_HIGH = 1.2
    }
}
Config.GangZones['WVINE'] = {
    name = 'WVINE',
    label = 'West Vinewood',
    neighbors = {
        'BURTON',
        'ROCKF',
        'DTVINE',
        'HAWICK'
    },
    parts = {
        { x1 = -743.39, y1 = 13.47, x2 = 48.53, y2 = 445.02 },
        { x1 = -246.39, y1 = -20.78, x2 = 48.53, y2 = 13.48 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.85,
        CATEGORY_MED = 1.0,
        CATEGORY_HIGH = 1.2
    }
}
Config.GangZones['BURTON'] = {
    name = 'BURTON',
    label = 'Burton',
    neighbors = {
        'WVINE',
        'HAWICK',
        'ALTA',
        'ROCKF'
    },
    parts = {
        { x1 = -594.91, y1 = -126.82, x2 = -246.39, y2 = 13.48 },
        { x1 = -550.21, y1 = -310.80, x2 = -246.39, y2 = -126.82 },
        { x1 = -246.39, y1 = -378.61, x2 = -90.0, y2 = -20.78 },
        { x1 = -246.39, y1 = -452.98, x2 = -90.0, y2 = -378.61 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.8,
        CATEGORY_MED = 0.8,
        CATEGORY_HIGH = 0.7
    }
}
Config.GangZones['VCANA'] = {
    name = 'VCANA',
    label = 'Vespucci Canals',
    neighbors = {
        'MORN',
        'MOVIE',
        'KOREAT',
        'VESP'
    },
    parts = {
        { x1 = -1319.77, y1 = -1074.78, x2 = -1095.41, y2 = -960.49 },
        { x1 = -1272.77, y1 = -960.49, x2 = -1095.41, y2 = -849.49 },
        { x1 = -1250.79, y1 = -1174.30, x2 = -1095.41, y2 = -1074.78 },
        { x1 = -1249.24, y1 = -1237.30, x2 = -1095.41, y2 = -1174.30 },
        { x1 = -1232.34, y1 = -1287.02, x2 = -1095.41, y2 = -1237.30 },
        { x1 = -1202.04, y1 = -1389.87, x2 = -1095.41, y2 = -1287.02 },
        { x1 = -1182.04, y1 = -1450.40, x2 = -1095.41, y2 = -1389.87 },
        { x1 = -1095.41, y1 = -1214.40, x2 = -774.41, y2 = -1019.71 },
        { x1 = -1095.41, y1 = -1019.71, x2 = -812.41, y2 = -907.78 },
        { x1 = -1095.41, y1 = -907.78, x2 = -865.98, y2 = -849.49 },
        { x1 = -1172.0, y1 = -849.49, x2 = -931.96, y2 = -723.01 },
    },
    drugPreference = {
        CATEGORY_LOW = 1.2,
        CATEGORY_MED = 0.4,
        CATEGORY_HIGH = 0.8
    }
}
Config.GangZones['ALTA'] = {
    name = 'ALTA',
    label = 'Alta',
    neighbors = {
        'BURTON',
        'DTVINE',
        'EAST_V',
        'HAWICK'
    },
    parts = {
        { x1 = -90.0, y1 = -480.90, x2 = 695.99, y2 = -177.0 },
    },
    drugPreference = {
        CATEGORY_LOW = 1.0,
        CATEGORY_MED = 1.0,
        CATEGORY_HIGH = 1.0
    }
}
Config.GangZones['EBURO'] = {
    name = 'EBURO',
    label = 'El Burro Heights',
    neighbors = {
        'LMESA'
    },
    parts = {
        { x1 = 1118.89, y1 = -1901.45, x2 = 1485.92, y2 = -1391.50 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.5,
        CATEGORY_MED = 0.5,
        CATEGORY_HIGH = 0.3
    }
}
Config.GangZones['CYPRE'] = {
    name = 'CYPRE',
    label = 'Cypress Flats',
    neighbors = {
        'RANCHO',
        'LMESA'
    },
    parts = {
        { x1 = 618.7, y1 = -2718.48, x2 = 921.45, y2 = -1708.33 },
        { x1 = 921.45, y1 = -2718.48, x2 = 1048.54, y2 = -1901.45 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.5,
        CATEGORY_MED = 0.5,
        CATEGORY_HIGH = 0.2
    }
}
Config.GangZones['VESP'] = {
    name = 'VESP',
    label = 'Vespucci',
    neighbors = {
        'VCANA'
    },
    parts = {
        { x1 = -1450.59, y1 = -1287.02, x2 = -1232.34, y2 = -1237.30 },
        { x1 = -1450.59, y1 = -1237.30, x2 = -1249.24, y2 = -1174.30 },
        { x1 = -1450.59, y1 = -1174.30, x2 = -1250.79, y2 = -1074.78 },
        { x1 = -1450.59, y1 = -1389.87, x2 = -1202.04, y2 = -1287.02 },
        { x1 = -1450.59, y1 = -1600.40, x2 = -1182.04, y2 = -1389.87 },
    },
    drugPreference = {
        CATEGORY_LOW = 1.0,
        CATEGORY_MED = 0.5,
        CATEGORY_HIGH = 0.75
    }
}
Config.GangZones['HAWICK'] = {
    name = 'HAWICK',
    label = 'Hawick',
    neighbors = {
        'EAST_V',
        'ALTA',
        'DTVINE',
        'BURTON',
        'WVINE'
    },
    parts = {
        { x1 = -90.0, y1 = -177.0, x2 = 695.87, y2 = -20.78 },
    },
    drugPreference = {
        CATEGORY_LOW = 1.0,
        CATEGORY_MED = 1.0,
        CATEGORY_HIGH = 0.9
    }
}
Config.GangZones['EAST_V'] = {
    name = 'EAST_V',
    label = 'East Vinewood',
    neighbors = {
        'HAWICK',
        'DTVINE',
        'ALTA'
    },
    parts = {
        { x1 = 696.0, y1 = -282.5, x2 = 1391.0, y2 = -35.97 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.5,
        CATEGORY_MED = 0.5,
        CATEGORY_HIGH = 0.6
    }
}
Config.GangZones['GRAPES'] = {
    name = 'GRAPES',
    label = 'Grapeseed',
    neighbors = {
        'SANDY'
    },
    parts = {
        { x1 = 1605.27, y1 = 4543.62, x2 = 2413.98, y2 = 5269.38 },
        { x1 = 2413.98, y1 = 5138.80, x2 = 2498.52, y2 = 5269.38 },
        { x1 = 2413.98, y1 = 4778.17, x2 = 2561.79, y2 = 5138.80 },
        { x1 = 2413.98, y1 = 4417.53, x2 = 2632.58, y2 = 4778.17 },
        { x1 = 2413.98, y1 = 4036.53, x2 = 2734.72, y2 = 4417.53 },
        { x1 = 1605.27, y1 = 4820.46, x2 = 1648.42, y2 = 4931.77 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.3,
        CATEGORY_MED = 0.3,
        CATEGORY_HIGH = 0.2
    }
}
Config.GangZones['SANDY'] = {
    name = 'SANDY',
    label = 'Sandy Shores',
    neighbors = {
        'GRAPES'
    },
    parts = {
        { x1 = 1295.66, y1 = 3455.35, x2 = 2145.09, y2 = 4012.51 },
        { x1 = 2413.98, y1 = 3554.05, x2 = 2807.76, y2 = 4036.53 },
        { x1 = 2145.09, y1 = 3554.05, x2 = 2413.98, y2 = 3819.50 },
        { x1 = 2145.09, y1 = 3294.46, x2 = 2693.05, y2 = 3554.05 },
        { x1 = 2083.31, y1 = 3925.83, x2 = 2145.09, y2 = 3954.88 },
        { x1 = 2057.38, y1 = 3954.88, x2 = 2145.09, y2 = 4012.50 },
        { x1 = 1990.20, y1 = 3973.64, x2 = 2057.38, y2 = 4012.51 },
        { x1 = 1976.69, y1 = 3981.51, x2 = 1990.20, y2 = 3995.50 },
        { x1 = 1752.23, y1 = 3995.50, x2 = 1990.20, y2 = 4012.50 },
        { x1 = 1691.23, y1 = 3983.57, x2 = 1752.23, y2 = 4012.50 },
        { x1 = 1691.23, y1 = 3967.40, x2 = 1713.04, y2 = 3983.58 },
        { x1 = 1446.97, y1 = 3954.97, x2 = 1691.23, y2 = 4012.50 },
        { x1 = 1446.97, y1 = 3930.21, x2 = 1683.75, y2 = 3954.97 },
        { x1 = 1446.97, y1 = 3888.02, x2 = 1508.13, y2 = 3930.21 },
        { x1 = 1508.13, y1 = 3888.02, x2 = 1540.87, y2 = 3904.46 },
        { x1 = 1532.13, y1 = 3856.76, x2 = 1584.82, y2 = 3888.02 },
        { x1 = 1446.97, y1 = 3819.74, x2 = 1532.13, y2 = 3888.02 },
        { x1 = 1295.66, y1 = 3888.02, x2 = 1446.97, y2 = 4012.51 },
        { x1 = 1295.66, y1 = 3812.33, x2 = 1388.96, y2 = 3888.02 },
        { x1 = 1295.66, y1 = 3741.06, x2 = 1356.98, y2 = 3812.33 },
        { x1 = 1295.66, y1 = 3713.35, x2 = 1325.48, y2 = 3741.06 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.4,
        CATEGORY_MED = 0.4,
        CATEGORY_HIGH = 0.1
    }
}
Config.GangZones['PALETO'] = {
    name = 'PALETO',
    label = 'Paleto Bay',
    neighbors = {},
    parts = {
        { x1 = -333.95, y1 = 6006.86, x2 = -188.97, y2 = 6147.87 },
        { x1 = -282.23, y1 = 6147.87, x2 = -137.25, y2 = 6288.88 },
        { x1 = -137.25, y1 = 6195.79, x2 = 7.74, y2 = 6336.80 },
        { x1 = -59.31, y1 = 6336.80, x2 = 66.28, y2 = 6452.00 },
        { x1 = 66.28, y1 = 6409.34, x2 = 211.26, y2 = 6518.35 },
        { x1 = 110.86, y1 = 6518.35, x2 = 516.84, y2 = 6614.36 },
        { x1 = -680.83, y1 = 6147.87, x2 = -282.23, y2 = 6288.88 },
        { x1 = -598.05, y1 = 6288.88, x2 = -137.25, y2 = 6477.81 },
        { x1 = 66.28, y1 = 6518.35, x2 = 110.86, y2 = 6614.36 },
        { x1 = -357.76, y1 = 6477.81, x2 = 66.28, y2 = 6614.36 },
        { x1 = 10.82, y1 = 6614.36, x2 = 133.50, y2 = 7165.53 },
        { x1 = -188.97, y1 = 6006.86, x2 = -39.51, y2 = 6147.87 },
        { x1 = -137.25, y1 = 6147.87, x2 = -39.51, y2 = 6195.79 },
        { x1 = 7.74, y1 = 6195.79, x2 = 66.28, y2 = 6336.80 },
        { x1 = -137.25, y1 = 6336.80, x2 = -59.31, y2 = 6477.81 },
        { x1 = -59.31, y1 = 6452.00, x2 = 66.28, y2 = 6477.81 },
        { x1 = -481.00, y1 = 6006.37, x2 = -333.95, y2 = 6147.87 },
        { x1 = -112.83, y1 = 6614.36, x2 = 10.82, y2 = 6786.93 },
        { x1 = -202.03, y1 = 6614.36, x2 = -112.83, y2 = 6703.23 },
        { x1 = -164.47, y1 = 6703.23, x2 = -112.83, y2 = 6744.03 },
        { x1 = 133.50, y1 = 6614.36, x2 = 465.00, y2 = 6785.33 },
        { x1 = 133.50, y1 = 6785.33, x2 = 387.30, y2 = 6900.54 },
        { x1 = 133.50, y1 = 6900.54, x2 = 284.08, y2 = 6996.90 },
        { x1 = 133.50, y1 = 6996.90, x2 = 224.78, y2 = 7065.80 },
        { x1 = 465.00, y1 = 6705.98, x2 = 617.57, y2 = 6745.77 },
        { x1 = 387.30, y1 = 6785.33, x2 = 473.72, y2 = 6840.19 },
        { x1 = 284.08, y1 = 6900.54, x2 = 386.59, y2 = 6949.75 },
        { x1 = 133.50, y1 = 7065.80, x2 = 193.80, y2 = 7165.53 },
        { x1 = 224.78, y1 = 6996.90, x2 = 277.79, y2 = 7065.80 },
        { x1 = 284.08, y1 = 6949.75, x2 = 332.08, y2 = 6996.90 },
        { x1 = 387.30, y1 = 6840.19, x2 = 430.30, y2 = 6900.54 },
        { x1 = 465.00, y1 = 6745.77, x2 = 541.00, y2 = 6785.33 },
        { x1 = 465.00, y1 = 6614.36, x2 = 617.57, y2 = 6705.98 },
        { x1 = -43.31, y1 = 6882.58, x2 = 10.82, y2 = 7165.53 },
        { x1 = -103.31, y1 = 6786.93, x2 = 10.82, y2 = 6882.58 },
        { x1 = -234.25, y1 = 6006.86, x2 = -188.97, y2 = 6046.44 },
        { x1 = -61.55, y1 = 6006.86, x2 = -39.51, y2 = 6025.03 },
        { x1 = -165.24, y1 = 6006.86, x2 = -149.20, y2 = 6021.46 },
        { x1 = -58.57, y1 = 6115.46, x2 = -39.51, y2 = 6147.87 },
        { x1 = -117.17, y1 = 6056.50, x2 = -39.51, y2 = 6115.46 },
        { x1 = -108.56, y1 = 6006.86, x2 = -88.03, y2 = 6017.70 },
        { x1 = -128.49, y1 = 6020.11, x2 = -93.62, y2 = 6045.88 },
    },
    drugPreference = {
        CATEGORY_LOW = 0.2,
        CATEGORY_MED = 0.2,
        CATEGORY_HIGH = 0.1
    }
}

Config.ZoneNames = {
    ['AIRP'] = 'Los Santos International Airport',
    ['ALAMO'] = 'Alamo Sea',
    ['ALTA'] = 'Alta',
    ['ARMYB'] = 'Fort Zancudo',
    ['BANHAMC'] = 'Banham Canyon Drive',
    ['BANNING'] = 'Banning',
    ['BEACH'] = 'Vespucci Beach',
    ['BHAMCA'] = 'Banham Canyon',
    ['BRADP'] = 'Braddock Pass',
    ['BRADT'] = 'Braddock Tunnel',
    ['BURTON'] = 'Burton',
    ['CALAFB'] = 'Calafia Bridge',
    ['CANNY'] = 'Raton Canyon',
    ['CCREAK'] = 'Cassidy Creek',
    ['CHAMH'] = 'Chamberlain Hills',
    ['CHIL'] = 'Vinewood Hills',
    ['CHU'] = 'Chumash',
    ['CMSW'] = 'Chiliad Mountain State Wilderness',
    ['CYPRE'] = 'Cypress Flats',
    ['DAVIS'] = 'Davis',
    ['DELBE'] = 'Del Perro Beach',
    ['DELPE'] = 'Del Perro',
    ['DESRT'] = 'Grand Senora Desert',
    ['DOWNT'] = 'Downtown',
    ['DTVINE'] = 'Downtown Vinewood',
    ['EAST_V'] = 'East Vinewood',
    ['EBURO'] = 'El Burro Heights',
    ['ELGORL'] = 'El Gordo Lighthouse',
    ['ELYSIAN'] = 'Elysian Island',
    ['GALFISH'] = 'Galilee',
    ['GOLF'] = 'GWC and Golfing Society',
    ['GRAPES'] = 'Grapeseed',
    ['GREATC'] = 'Great Chaparral',
    ['HARMO'] = 'Harmony',
    ['HAWICK'] = 'Hawick',
    ['HORS'] = 'Vinewood Racetrack',
    ['HUMLAB'] = 'Humane Labs and Research',
    ['JAIL'] = 'Bolingbroke Penitentiary',
    ['KOREAT'] = 'Little Seoul',
    ['LACT'] = 'Land Act Reservoir',
    ['LAGO'] = 'Lago Zancudo',
    ['LDAM'] = 'Land Act Dam',
    ['LEGSQU'] = 'Legion Square',
    ['LMESA'] = 'La Mesa',
    ['LOSPUER'] = 'La Puerta',
    ['MIRR'] = 'Mirror Park',
    ['MORN'] = 'Morningwood',
    ['MOVIE'] = 'Richards Majestic',
    ['MTCHIL'] = 'Mount Chiliad',
    ['MTGORDO'] = 'Mount Gordo',
    ['MTJOSE'] = 'Mount Josiah',
    ['MURRI'] = 'Murrieta Heights',
    ['NCHU'] = 'North Chumash',
    ['NOOSE'] = 'N.O.O.S.E',
    ['OBSERV'] = 'Galileo Observatory',
    ['OCEANA'] = 'Pacific Ocean',
    ['PALCOV'] = 'Paleto Cove',
    ['PALETO'] = 'Paleto Bay',
    ['PALFOR'] = 'Paleto Forest',
    ['PALHIGH'] = 'Palomino Highlands',
    ['PALMPOW'] = 'Palmer-Taylor Power Station',
    ['PBLUFF'] = 'Pacific Bluffs',
    ['PBOX'] = 'Pillbox Hill',
    ['PROCOB'] = 'Procopio Beach',
    ['RANCHO'] = 'Rancho',
    ['RGLEN'] = 'Richman Glen',
    ['RICHM'] = 'Richman',
    ['ROCKF'] = 'Rockford Hills',
    ['RTRAK'] = 'Redwood Lights Track',
    ['SANCHIA'] = 'San Chianski Mountain Range',
    ['SANDY'] = 'Sandy Shores',
    ['SKID'] = 'Mission Row',
    ['SLAB'] = 'Stab City',
    ['STAD'] = 'Maze Bank Arena',
    ['STRAW'] = 'Strawberry',
    ['TATAMO'] = 'Tataviam Mountains',
    ['TERMINA'] = 'Terminal',
    ['TEXTI'] = 'Textile City',
    ['TONGVAH'] = 'Tongva Hills',
    ['TONGVAV'] = 'Tongva Valley',
    ['VCANA'] = 'Vespucci Canals',
    ['VESP'] = 'Vespucci',
    ['VINE'] = 'Vinewood',
    ['WINDF'] = 'RON Alternates Wind Farm',
    ['WVINE'] = 'West Vinewood',
    ['ZANCUDO'] = 'Zancudo River',
    ['ZQ_UAR'] = 'Davis Quartz'
}

-- ==========================================
--     BUSINESSES / REWARDS CONFIGURATION
-- ==========================================
Config.BusinessRewardsConfig = {
    IntervalHours = 0.5, -- Cuantas horas deben pasar como minimo para reclamar (o proporcion)
    ChanceForDrugs = 30, -- Probabilidad en % de recibir drogas al reclamar
    DrugsToGive = {
        "marijuana",
        "cocaprocesada",
        "lsdprocesada",
        "crackprocesada",
        "opioprocesada",
        "hongoprocesada",
        "metaprocesada"
    },
    DrugsAmount = { min = 1, max = 5 }
}

Config.Businesses = {
    ['GLOBE_OIL_DTVINE'] = {
        name = 'GLOBE_OIL_DTVINE',
        label = 'Globe Oil, Downtown Vinewood',
        banner = 'shopui_title_gasstation',
        zone = 'DTVINE',
        hourlyIncome = 70,
        checkpoint = vec3(645.64, 267.62, 103.23)
    },
    ['XERO_GAS_KOREAT'] = {
        name = 'XERO_GAS_KOREAT',
        label = 'Xero Gas, Little Seoul',
        banner = 'shopui_title_gasstation',
        zone = 'KOREAT',
        hourlyIncome = 90,
        checkpoint = vec3(-531.24, -1220.81, 18.45)
    },
    ['XERO_GAS_STRAW'] = {
        name = 'XERO_GAS_STRAW',
        label = 'Xero Gas, Strawberry',
        banner = 'shopui_title_gasstation',
        zone = 'STRAW',
        hourlyIncome = 25,
        checkpoint = vec3(288.69, -1266.93, 29.44)
    },
    ['XERO_GAS_SANDY'] = {
        name = 'XERO_GAS_SANDY',
        label = 'Xero Gas, Sandy Shores',
        banner = 'shopui_title_gasstation',
        zone = 'SANDY',
        hourlyIncome = 20,
        checkpoint = vec3(2001.76, 3779.31, 32.18)
    },
    ['XERO_GAS_PALETO'] = {
        name = 'XERO_GAS_PALETO',
        label = 'Xero Gas, Paleto Bay',
        banner = 'shopui_title_gasstation',
        zone = 'PALETO',
        hourlyIncome = 18,
        checkpoint = vec3(-93.18, 6410.32, 31.64)
    },
    ['LTD_KOREAT'] = {
        name = 'LTD_KOREAT',
        label = 'LTD, Little Seoul',
        banner = 'shopui_title_gasstation',
        zone = 'KOREAT',
        hourlyIncome = 100,
        checkpoint = vec3(-709.26, -905.42, 19.22)
    },
    ['LTD_DAVIS'] = {
        name = 'LTD_DAVIS',
        label = 'LTD, Davis',
        banner = 'shopui_title_gasstation',
        zone = 'DAVIS',
        hourlyIncome = 38,
        checkpoint = vec3(-43.89, -1749.65, 29.42)
    },
    ['LTD_MIRR'] = {
        name = 'LTD_MIRR',
        label = 'LTD, Mirror Park',
        banner = 'shopui_title_gasstation',
        zone = 'MIRR',
        hourlyIncome = 22,
        checkpoint = vec3(1160.19, -315.20, 69.22)
    },
    ['LTD_GRAPES'] = {
        name = 'LTD_GRAPES',
        label = 'LTD, Grapeseed',
        banner = 'shopui_title_gasstation',
        zone = 'GRAPES',
        hourlyIncome = 10,
        checkpoint = vec3(1706.59, 4920.77, 42.06)
    },
    ['RON_MORN'] = {
        name = 'RON_MORN',
        label = 'Ron, Morningwood',
        banner = 'shopui_title_gasstation',
        zone = 'MORN',
        hourlyIncome = 50,
        checkpoint = vec3(-1428.70, -268.84, 46.21)
    },
    ['RON_DAVIS'] = {
        name = 'RON_DAVIS',
        label = 'Ron, Davis',
        banner = 'shopui_title_gasstation',
        zone = 'DAVIS',
        hourlyIncome = 35,
        checkpoint = vec3(167.32, -1553.84, 29.26)
    },
    ['RON_LMESA'] = {
        name = 'RON_LMESA',
        label = 'Ron, La Mesa',
        banner = 'shopui_title_gasstation',
        zone = 'LMESA',
        hourlyIncome = 30,
        checkpoint = vec3(818.17, -1040.34, 26.75)
    },
    ['RON_EBURO'] = {
        name = 'RON_EBURO',
        label = 'Ron, El Burro Heights',
        banner = 'shopui_title_gasstation',
        zone = 'EBURO',
        hourlyIncome = 25,
        checkpoint = vec3(1211.19, -1389.48, 35.38)
    },
    ['RON_PALETO'] = {
        name = 'RON_PALETO',
        label = 'Ron, Paleto Bay',
        banner = 'shopui_title_gasstation',
        zone = 'PALETO',
        hourlyIncome = 22,
        checkpoint = vec3(161.74, 6636.23, 31.57)
    },
    ['ROB_LIQUOR_MORN'] = {
        name = 'ROB_LIQUOR_MORN',
        label = 'Rob\'s Liquor, Morningwoord',
        banner = 'shopui_title_liquorstore2',
        zone = 'MORN',
        hourlyIncome = 33,
        checkpoint = vec3(-1479.83, -373.27, 39.16)
    },
    ['ROB_LIQUOR_VCANA'] = {
        name = 'ROB_LIQUOR_VCANA',
        label = 'Rob\'s Liquor, Vespucci Canals',
        banner = 'shopui_title_liquorstore2',
        zone = 'VCANA',
        hourlyIncome = 22,
        checkpoint = vec3(-1218.73, -915.63, 11.33)
    },
    ['247_DTVINE'] = {
        name = '247_DTVINE',
        label = '24/7, Downtown Vinewood',
        banner = 'shopui_title_conveniencestore',
        zone = 'DTVINE',
        hourlyIncome = 46,
        checkpoint = vec3(379.25, 332.62, 103.57)
    },
    ['247_STRAW'] = {
        name = '247_STRAW',
        label = '24/7, Strawberry',
        banner = 'shopui_title_conveniencestore',
        zone = 'STRAW',
        hourlyIncome = 15,
        checkpoint = vec3(29.45, -1339.67, 29.50)
    },
    ['247_SANDY'] = {
        name = '247_SANDY',
        label = '24/7, Sandy Shores',
        banner = 'shopui_title_conveniencestore',
        zone = 'SANDY',
        hourlyIncome = 13,
        checkpoint = vec3(1960.58, 3749.12, 32.34)
    },
    ['AMMO_KOREAT'] = {
        name = 'AMMO_KOREAT',
        label = 'Ammu-Nation, Little Seoul',
        banner = 'shopui_title_gunclub',
        zone = 'KOREAT',
        hourlyIncome = 80,
        checkpoint = vec3(-666.12, -933.69, 21.83)
    },
    ['AMMO_HAWICK'] = {
        name = 'AMMO_HAWICK',
        label = 'Ammu-Nation, Hawick',
        banner = 'shopui_title_gunclub',
        zone = 'HAWICK',
        hourlyIncome = 75,
        checkpoint = vec3(255.02, -46.89, 69.94)
    },
    ['AMMO_PBOX'] = {
        name = 'AMMO_PBOX',
        label = 'Ammu-Nation, Pillbox Hill',
        banner = 'shopui_title_gunclub',
        zone = 'PBOX',
        hourlyIncome = 45,
        checkpoint = vec3(18.94, -1104.31, 29.80)
    },
    ['AMMO_MORN'] = {
        name = 'AMMO_MORN',
        label = 'Ammu-Nation, Morningwood',
        banner = 'shopui_title_gunclub',
        zone = 'MORN',
        hourlyIncome = 30,
        checkpoint = vec3(-1303.30, -390.89, 36.70)
    },
    ['AMMO_LMESA'] = {
        name = 'AMMO_LMESA',
        label = 'Ammu-Nation, La Mesa',
        banner = 'shopui_title_gunclub',
        zone = 'LMESA',
        hourlyIncome = 22,
        checkpoint = vec3(846.25, -1035.176, 28.26)
    },
    ['AMMO_CYPRE'] = {
        name = 'AMMO_CYPRE',
        label = 'Ammu-Nation, Cypress Flats',
        banner = 'shopui_title_gunclub',
        zone = 'CYPRE',
        hourlyIncome = 20,
        checkpoint = vec3(814.06, -2158.91, 29.62)
    },
    ['AMMO_SANDY'] = {
        name = 'AMMO_SANDY',
        label = 'Ammu-Nation, Sandy Shores',
        banner = 'shopui_title_gunclub',
        zone = 'SANDY',
        hourlyIncome = 13,
        checkpoint = vec3(1689.75, 3758.06, 34.71)
    },
    ['AMMO_PALETO'] = {
        name = 'AMMO_PALETO',
        label = 'Ammu-Nation, Paleto Bay',
        banner = 'shopui_title_gunclub',
        zone = 'PALETO',
        hourlyIncome = 12,
        checkpoint = vec3(-334.26, 6082.17, 31.45)
    },
    ['SECOND_HAND_STRAW'] = {
        name = 'SECOND_HAND_STRAW',
        label = 'Second Hand, Strawberry',
        banner = 'shopui_title_lowendfashion',
        zone = 'STRAW',
        hourlyIncome = 15,
        checkpoint = vec3(71.64, -1391.20, 29.38)
    },
    ['SECOND_HAND_PALETO'] = {
        name = 'SECOND_HAND_PALETO',
        label = 'Second Hand, Paleto Bay',
        banner = 'shopui_title_lowendfashion',
        zone = 'PALETO',
        hourlyIncome = 10,
        checkpoint = vec3(6.23, 6508.64, 31.88)
    },
    ['SECOND_HAND_GRAPES'] = {
        name = 'SECOND_HAND_GRAPES',
        label = 'Second Hand, Grapeseed',
        banner = 'shopui_title_lowendfashion',
        zone = 'GRAPES',
        hourlyIncome = 8,
        checkpoint = vec3(1697.77, 4821.64, 42.06)
    },
    ['SUBURBAN_ALTA'] = {
        name = 'SUBURBAN_ALTA',
        label = 'Suburban, Alta',
        banner = 'shopui_title_midfashion',
        zone = 'ALTA',
        hourlyIncome = 78,
        checkpoint = vec3(117.67, -233.88, 54.56)
    },
    ['SUBURBAN_MOVIE'] = {
        name = 'SUBURBAN_MOVIE',
        label = 'Suburban, Richards Majestic',
        banner = 'shopui_title_midfashion',
        zone = 'MOVIE',
        hourlyIncome = 50,
        checkpoint = vec3(-1180.83, -764.08, 17.33)
    },
    ['PONSON_ROCKF'] = {
        name = 'PONSON_ROCKF',
        label = 'Ponsonbys, Rockford Hills',
        banner = 'shopui_title_highendfashion',
        zone = 'ROCKF',
        hourlyIncome = 50,
        checkpoint = vec3(-700.60, -151.85, 37.42)
    },
    ['PONSON_MORN'] = {
        name = 'PONSON_MORN',
        label = 'Ponsonbys, Morningwood',
        banner = 'shopui_title_highendfashion',
        zone = 'MORN',
        hourlyIncome = 37,
        checkpoint = vec3(-1446.40, -246.05, 49.82)
    },
    ['PONSON_BURTON'] = {
        name = 'PONSON_BURTON',
        label = 'Ponsonbys, Burton',
        banner = 'shopui_title_highendfashion',
        zone = 'BURTON',
        hourlyIncome = 25,
        checkpoint = vec3(-170.50, -296.60, 39.73)
    },
    ['BINCO_VCANA'] = {
        name = 'BINCO_VCANA',
        label = 'Binco, Vespucci Canals',
        banner = 'shopui_title_lowendfashion2',
        zone = 'VCANA',
        hourlyIncome = 45,
        checkpoint = vec3(-822.83, -1069.55, 11.33)
    },
    ['BINCO_TEXTI'] = {
        name = 'BINCO_TEXTI',
        label = 'Binco, Textile City',
        banner = 'shopui_title_lowendfashion2',
        zone = 'TEXTI',
        hourlyIncome = 37,
        checkpoint = vec3(429.27, -807.85, 29.49)
    },
    ['BARBER_ROCKF'] = {
        name = 'BARBER_ROCKF',
        label = 'Bob Mulét, Rockford Hills',
        banner = 'shopui_title_highendsalon',
        zone = 'ROCKF',
        hourlyIncome = 80,
        checkpoint = vec3(-808.94, -180.04, 37.57)
    },
    ['BARBER_VESP'] = {
        name = 'BARBER_VESP',
        label = 'Beachcombover Barbers, Vespucci',
        banner = 'shopui_title_barber2',
        zone = 'VESP',
        hourlyIncome = 40,
        checkpoint = vec3(-1278.78, -1119.22, 6.99)
    },
    ['BARBER_HAWICK'] = {
        name = 'BARBER_HAWICK',
        label = 'Hair on Hawick, Hawick',
        banner = 'shopui_title_barber4',
        zone = 'HAWICK',
        hourlyIncome = 35,
        checkpoint = vec3(-36.33, -155.71, 57.08)
    },
    ['BARBER_DAVIS'] = {
        name = 'BARBER_DAVIS',
        label = 'Herr Kutz Barber, Davis',
        banner = 'shopui_title_barber',
        zone = 'DAVIS',
        hourlyIncome = 32,
        checkpoint = vec3(141.14, -1706.17, 29.29)
    },
    ['BARBER_MIRR'] = {
        name = 'BARBER_MIRR',
        label = 'Herr Kutz Barber, Mirror Park',
        banner = 'shopui_title_barber',
        zone = 'MIRR',
        hourlyIncome = 28,
        checkpoint = vec3(1215.86, -475.74, 66.21)
    },
    ['BARBER_PALETO'] = {
        name = 'BARBER_PALETO',
        label = 'Herr Kutz Barber, Paleto Bay',
        banner = 'shopui_title_barber',
        zone = 'PALETO',
        hourlyIncome = 9,
        checkpoint = vec3(-276.55, 6223.67, 31.70)
    },
    ['BARBER_SANDY'] = {
        name = 'BARBER_SANDY',
        label = 'O\'Sheas Barbers, Sandy Shores',
        banner = 'shopui_title_barber3',
        zone = 'SANDY',
        hourlyIncome = 8,
        checkpoint = vec3(1931.28, 3735.05, 32.84)
    },
    ['TATTOO_DTVINE'] = {
        name = 'TATTOO_DTVINE',
        label = 'Blazing Tattoo, Downtown Vinewood',
        banner = 'shopui_title_tattoos',
        zone = 'DTVINE',
        hourlyIncome = 23,
        checkpoint = vec3(320.78, 183.50, 103.59)
    },
    ['TATTOO_VCANA'] = {
        name = 'TATTOO_VCANA',
        label = 'The Pit, Vespucci Canals',
        banner = 'shopui_title_tattoos3',
        zone = 'VCANA',
        hourlyIncome = 20,
        checkpoint = vec3(-1150.63, -1426.09, 4.95)
    },
    ['TATTOO_EBURO'] = {
        name = 'TATTOO_EBURO',
        label = 'Los Santos Tattoos, El Burro Heights',
        banner = 'shopui_title_tattoos4',
        zone = 'EBURO',
        hourlyIncome = 18,
        checkpoint = vec3(1326.30, -1652.38, 52.28)
    },
    ['TATTOO_SANDY'] = {
        name = 'TATTOO_SANDY',
        label = 'Tattoo Body Art & Piercing, Sandy Shores',
        banner = 'shopui_title_tattoos2',
        zone = 'SANDY',
        hourlyIncome = 7,
        checkpoint = vec3(1865.21, 3749.04, 33.05)
    }
}
```
