# Config

```lua
Config = {}

-- =============================================================================
--  VEHICLE IMAGES CONFIGURATION
-- =============================================================================
-- URL base del CDN para descargar imágenes de vehículos (por defecto FiveM Docs)
Config.VehicleCDN = "https://docs-backend.fivem.net/vehicles/"

-- =============================================================================
--  FRAMEWORK & LANGUAGE
-- =============================================================================

Config.Framework     = "auto"            -- "auto" | "ESX" | "QBCore" | "Qbox"
Config.Locale        = "en"              -- "es" | "en" | "fr" | "de" | "pt"
Config.Banking       = "auto"            -- "auto" | "esx_addonaccount"
Config.Notifications = "auto"            -- "auto" | "ox_lib" | "okokNotify" | "ps-ui"
Config.DrawText      = "auto"            -- "auto" | "ST-textui" | "ox_lib" | "qb-DrawText" | "okokTextUI" | "esx_textui" | "cd_drawtextui" | "ps-ui" | "jg-textui"
Config.FuelSystem    = "ox_fuel"         -- "none" | "ox_fuel" | "LegacyFuel" | "ps-fuel" | "cdn-fuel" | "nd_fuel"
Config.VehicleKeys   = "none"            -- "none" | "qb-vehiclekeys" | "MrNewbVehicleKeys" | "jaksam-vehicles-keys" | "qs-vehiclekeys" | "mk_vehiclekeys" | "wasabi_carlock"


-- =============================================================================
--  ADMIN COMMANDS  (requires "command.admin" ace in server.cfg)
-- =============================================================================

Config.GarageAdminCommand    = "creategarage"  -- /creategarage          → opens the garage admin panel
Config.DeleteVehicleFromDB   = "dvdb"          -- /dvdb   <plate>         → sends to impound
Config.ReturnVehicleToGarage = "vreturn"       -- /vreturn <plate>        → sends to impound
Config.GiveVehicleCommand    = "admincar"      -- /admincar <model> [plate] [garage] → Spawns a vehicle and saves it to the DB.

Config.Debug = false


-- =============================================================================
--  ECONOMY
-- =============================================================================

Config.Currency                  = "USD"
Config.GarageVehicleTransferCost = 500
Config.GarageVehicleReturnCost   = 500


-- =============================================================================
--  TRANSFERS
-- =============================================================================

Config.EnableTransfers = {
    betweenGarages = true,
    betweenPlayers = true,
}


-- =============================================================================
--  VEHICLE BEHAVIOR
-- =============================================================================

Config.SaveVehicleDamage          = true
Config.SaveVehiclePropsOnInsert   = true
Config.AllowInfiniteVehicleSpawns = false
Config.DoNotSpawnInsideVehicle    = false
Config.CheckVehicleModel          = true

Config.OpenGarageKeyBind   = 38        -- 38 = E
-- NOTE: TextUI prompts (Open Garage, Store Vehicle, etc.) are now managed directly in locales/*.lua

Config.ExitInteriorKeyBind = 38        -- E
-- NOTE: Exit interior prompt is managed in locales/*.lua


-- =============================================================================
--  PED SYSTEM
-- =============================================================================

Config.UsePed            = false    -- true = spawna el ped | false = usa marker + tecla E sin ped
Config.PedTargetSystem   = "none"   -- "ox_target" | "qb-target" | "none"
Config.PedTargetDistance = 3.0

Config.PedModels = {
    public  = { model = "a_m_y_business_01",  scenario = "WORLD_HUMAN_STAND_MOBILE"    },
    job     = { model = "s_m_y_cop_01",        scenario = "WORLD_HUMAN_GUARD_STAND"     },
    gang    = { model = "g_m_y_lost_01",       scenario = "WORLD_HUMAN_STAND_IMPATIENT" },
    impound = { model = "s_m_y_armymech_01",   scenario = "WORLD_HUMAN_CLIPBOARD"       },
}

-- NOTE: Ped labels (Open Garage, Store Vehicle, etc.) are now managed directly in locales/*.lua
Config.PedLabels = {
    -- Kept empty or removed, text is loaded from locales.
}

Config.PedIcons = {
    openPublic  = "fas fa-warehouse",
    openJob     = "fas fa-briefcase",
    openGang    = "fas fa-skull",
    openImpound = "fas fa-lock",
    insert      = "fas fa-car-side",
}


-- =============================================================================
--  PUBLIC GARAGES
--  - coords: Punto para abrir el menú / sacar vehículos (a pie o con NPC Ped).
--  - store:  (Opcional) Punto separado específico para aparcar y guardar el vehículo.
--            Si no se especifica, se usa 'coords' para ambas cosas como antes.
--  - storeDistance: (Opcional) Radio para guardar en el punto 'store' (por defecto: distance o 5.0).
--  - spawn:  Punto(s) de spawn donde aparece el coche.
-- =============================================================================

Config.GarageShowBlips = true

Config.GarageLocations = {

    ["Legion Square"] = {
        coords   = vector4(214.9537, -807.1387, 30.7945, 343.9731),
        store    = vector4(215.12,   -791.23,   30.75,   159.2),
        storeDistance = 6.0,
        spawn    = {
            vector4(214.3186, -795.0084, 30.8462, 160.1457),
            vector4(218.09,   -799.42,   30.76,    66.17),
            vector4(219.29,   -797.23,   30.75,    65.4),
            vector4(219.59,   -794.44,   30.75,    69.35),
            vector4(220.63,   -792.03,   30.75,    63.76),
        },
        distance = 5.0,
        type     = "car",
        blip     = { id = 357, color = 0, scale = 0.7 },
    },

    ["Grove Street"] = {
        coords   = vector4(45.9558, -1748.7343, 29.6117, 47.7274),
        store    = vector4(37.45,   -1736.21,   29.30,   230.0),
        storeDistance = 6.0,
        spawn    = vector4(31.2225, -1740.9283, 29.3032, 231.2441),
        distance = 5.0,
        type     = "car",
        blip     = { id = 357, color = 0, scale = 0.7 },
    },

    ["Mirror Park"] = {
        coords   = vector4(1035.3048, -765.3475, 57.9951, 151.2398),
        store    = vector4(1028.52,   -762.15,   57.98,   145.0),
        storeDistance = 6.0,
        spawn    = vector4(1021.1791, -769.0327, 57.9721, 223.9578),
        distance = 5.0,
        type     = "car",
        blip     = { id = 357, color = 0, scale = 0.7 },
    },

    ["Beach"] = {
        coords   = vector4(-1250.3894, -1424.8225, 4.3229, 306.0319),
        store    = vector4(-1245.85,   -1420.50,   4.32,   305.0),
        storeDistance = 6.0,
        spawn    = vector4(-1240.7754, -1416.7146, 4.3236, 305.4891),
        distance = 5.0,
        type     = "car",
        blip     = { id = 357, color = 0, scale = 0.7 },
    },

    ["Sandy South"] = {
        coords   = vector4(217.33, 2605.65, 46.04, 0.0),
        store    = vector4(221.80, 2615.10, 46.50, 15.0),
        storeDistance = 6.0,
        spawn    = vector4(216.0181, 2611.5164, 46.7093, 28.2299),
        distance = 5.0,
        type     = "car",
        blip     = { id = 357, color = 0, scale = 0.7 },
    },

    ["Sandy North"] = {
        coords   = vector4(1879.4971, 3764.4458, 32.9320, 207.6911),
        store    = vector4(1872.40,   3761.15,   33.00,   210.0),
        storeDistance = 6.0,
        spawn    = vector4(1880.14, 3757.73, 32.93, 215.54),
        distance = 5.0,
        type     = "car",
        blip     = { id = 357, color = 0, scale = 0.7 },
    },

    ["Grapeseed"] = {
        coords   = vector4(1695.7325, 4785.3027, 42.0055, 92.5914),
        store    = vector4(1705.50,   4793.80,   41.90,   95.0),
        storeDistance = 6.0,
        spawn    = vector4(1700.3824, 4800.5742, 41.8028, 98.6934),
        distance = 5.0,
        type     = "car",
        blip     = { id = 357, color = 0, scale = 0.7 },
    },

    ["Paleto Bay"] = {
        coords   = vector4(105.9851, 6612.4395, 31.9700, 229.5909),
        store    = vector4(115.50,   6615.20,   31.85,   235.0),
        storeDistance = 6.0,
        spawn    = vector4(110.84, 6607.82, 31.86, 265.28),
        distance = 5.0,
        type     = "car",
        blip     = { id = 357, color = 0, scale = 0.7 },
    },

    ["North Vinewood Blvd"] = {
        coords   = vector4(362.1708, 297.8179, 103.8838, 345.9844),
        store    = vector4(358.20,   288.50,   103.35,  165.0),
        storeDistance = 6.0,
        spawn    = vector4(364.84, 289.73, 103.42, 164.23),
        distance = 5.0,
        type     = "car",
        blip     = { id = 357, color = 0, scale = 0.7 },
    },

    ["Islington South"] = {
        coords   = vector4(275.9112, -343.1441, 44.9199, 15.4952),
        store    = vector4(280.10,   -336.50,   44.92,   160.0),
        storeDistance = 6.0,
        spawn    = vector4(274.4873, -332.2220, 44.9199, 161.9279),
        distance = 5.0,
        type     = "car",
        blip     = { id = 357, color = 0, scale = 0.7 },
    },

    ["Great Ocean Highway"] = {
        coords   = vector4(-2961.7122, 377.0632, 15.0048, 176.1870),
        store    = vector4(-2958.50,   368.20,   14.80,   85.0),
        storeDistance = 6.0,
        spawn    = vector4(-2964.96, 372.07, 14.78, 86.07),
        distance = 5.0,
        type     = "car",
        blip     = { id = 357, color = 0, scale = 0.7 },
    },

    ["Boats"] = {
        coords   = vector4(-795.15, -1510.79, 1.6, 0.0),
        store    = vector4(-804.20, -1503.50, -0.40, 105.0),
        storeDistance = 10.0,
        spawn    = vector4(-798.66, -1507.73, -0.47, 102.23),
        distance = 10.0,
        type     = "sea",
        blip     = { id = 356, color = 0, scale = 0.7 },
    },

    ["Hangar"] = {
        coords   = vector4(-1243.49, -3391.88, 13.94, 0.0),
        store    = vector4(-1010.50, -3485.20, 13.95, 335.0),
        storeDistance = 15.0,
        spawn    = vector4(-1024.1432, -3500.0127, 14.1434, 334.8109),
        distance = 15.0,
        type     = "air",
        blip     = { id = 359, color = 0, scale = 0.7 },
    },

}


-- =============================================================================
--  JOB GARAGES
-- =============================================================================

Config.JobGarageShowBlips = true

Config.JobGarageLocations = {

    ["Police"] = {
        coords   = vec4(460.1396, -1011.6098, 28.3730, 187.3890),
        store    = vec4(438.40,   -1023.20,   28.50,   90.0),
        storeDistance = 6.0,
        spawn    = vec4(449.5945, -1014.0656, 28.4895, 89.5490),
        distance = 5.0,
        job      = { "police" },
        type     = "car",
        blip     = { id = 357, color = 3, scale = 0.7 },

        vehiclesType           = "spawner",
        showLiveriesExtrasMenu = true,

        vehicles = {
            { model = "police",  plate = "POLICE", minJobGrade = 0, nickname = "Basic Patrol",    livery = 1, extras = {1, 2}, maxMods = true },
            { model = "police2", plate = "POLICE", minJobGrade = 3, nickname = "Advanced Patrol", livery = 2, extras = {},     maxMods = true },
            { model = "policeb", plate = "POLICE", minJobGrade = 2, nickname = "Police Bike",     livery = 1, extras = {},     maxMods = true },
        },
    },

    ["Mechanic"] = {
        coords   = vector4(-378.7856, -100.9213, 38.6843, 162.2831),
        store    = vector4(-368.50,   -114.20,   38.65,   25.0),
        storeDistance = 6.0,
        spawn    = {
            vector4(-376.8358, -122.4108, 38.6352, 24.5780),
            vector4(-373.4781, -137.5205, 38.6541, 23.3162),
        },
        distance = 5.0,
        job      = { "mechanic" },
        type     = "car",
        blip     = { id = 357, color = 5, scale = 0.7 },

        vehiclesType = "spawner",

        vehicles = {
            { model = "towtruck", plate = "Mechanic", minJobGrade = 0, nickname = "Tow Truck", maxMods = true },
            { model = "bison3",   plate = "Mechanic", minJobGrade = 0, nickname = "Van",       livery = 2, extras = {}, maxMods = true },
        },
    },

}


-- =============================================================================
--  GANG GARAGES
--  Note: ESX does not have a native gang system.
--  Enable the flag below for external gang scripts.
-- =============================================================================

Config.GangEnableCustomESXIntegration = false
Config.GangGarageShowBlips            = true

Config.GangGarageLocations = {

    ["LOS VAGOS"] = {
        coords       = vector4(313.4269, -2040.6183, 20.9364, 317.18410),
        store        = vector4(333.20,   -2035.50,   20.60,   140.0),
        storeDistance = 6.0,
        spawn        = vector4(327.3459, -2028.1289, 20.4267, 141.6012),
        distance     = 5.0,
        gang         = { "vagos" },
        type         = "car",
        blip         = { id = 357, color = 6, scale = 0.7 },
        vehiclesType = "personal",
    },

}


-- =============================================================================
--  IMPOUND  
-- =============================================================================

Config.ImpoundFeesSocietyFund = "police"                     -- job that receives retrieval fees (false = disabled)
Config.ImpoundShowBlips       = true
Config.ImpoundTimeOptions     = { 0, 1, 4, 12, 24, 72, 168 }  -- hours

Config.ImpoundLocations = {

["Impound A"] = {
    coords   = vec4(-229.7355, -1377.0602, 31.2582, 211.5547),
    spawn    = {
        vec4(-214.3312, -1397.1683, 31.2670, 357.0645),
        vec4(-211.2266, -1396.1777, 31.2483,   2.8385),
        vec4(-205.1463, -1388.1903, 31.2547, 115.0790),
        vec4(-230.2478, -1393.3782, 31.2582,  98.8272),
        vec4(-229.4363, -1396.3428, 31.2582,  97.2263),
    },
    distance = 10,
    type     = "car",
    job      = { "police" },
    blip     = { id = 68, color = 0, scale = 0.7 },
},

    ["Impound Boats"] = {
        coords   = vec4(-755.8043, -1413.3889, 1.5952, 57.6131),
        spawn    = {
            vec4(-831.4660, -1453.0204, 0.1195, 204.1329),
        },
        distance = 15,
        type     = "sea",
        job      = { "police" },
        blip     = { id = 68, color = 3, scale = 0.7 },
    },

    ["Impound Aircraft"] = {
        coords   = vec4(-1119.9048, -2840.2944, 14.3058, 142.8802),
        spawn    = {
            vec4(-1145.8453, -2864.0864, 13.9460, 153.3930),
        },
        distance = 20,
        type     = "air",
        job      = { "police" },
        blip     = { id = 68, color = 6, scale = 0.7 },
    },

}


-- =============================================================================
--  INTERIORS  (only for the Legion Square garage in this version)
-- =============================================================================

Config.PrivGarageEnableInteriors     = true
Config.GarageUniqueLocations         = true
Config.ReturnToPreviousRoutingBucket = true

Config.GarageInteriorCameraCutscene = {
    vector4(227.96, -977.81,  -98.99, 0.0),
    vector4(227.96, -1006.96, -98.99, 0.0),
}

Config.GarageInteriorEntrance = vector4(227.96, -1003.06, -99.0, 0.0)

Config.GarageInteriorVehiclePositions = {
    vector4(233.000000,  -984.000000,  -99.410004, 118.000000),
    vector4(233.000000,  -988.500000,  -99.410004, 118.000000),
    vector4(233.000000,  -993.000000,  -99.410004, 118.000000),
    vector4(233.000000,  -997.500000,  -99.410004, 118.000000),
    vector4(233.000000, -1002.000000,  -99.410004, 118.000000),
    vector4(223.600006,  -979.000000,  -99.410004, 235.199997),
    vector4(223.600006,  -983.599976,  -99.410004, 235.199997),
    vector4(223.600006,  -988.200012,  -99.410004, 235.199997),
    vector4(223.600006,  -992.799988,  -99.410004, 235.199997),
    vector4(223.600006,  -997.400024,  -99.410004, 235.199997),
    vector4(223.600006, -1002.000000,  -99.410004, 235.199997),
}
```
