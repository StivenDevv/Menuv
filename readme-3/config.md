# Config

```lua
Config = {}

Config.Framework        = 'qbox'            -- 'esx' | 'qbcore' | 'qbox'
Config.checkForUpdates  = true
Config.Language         = 'en'              -- 'es' | 'en'
Config.CommandMenu      = 'sanciones'     -- Command to open the sanctions menu (admins and allowed jobs)
Config.ShowBlips        = false             -- Activar o desactivar blips en el mapa (true o false)
-- ========================================
-- INTERACTION & PROGRESS
-- =======================================
Config.InteractionType  = 'points'          -- 'ox_target' | 'points'
Config.ProgressBar      = 'ox_lib'          -- 'ox_lib' | 'qb-progressbar' | 'progressBars' | 'esx_progressbar' | 'mythic_progbar'
Config.DrawText         = 'auto'            -- 'auto' | 'nui' | 'ox_lib' | 'okokTextUI' | 'jg-textui' | 'ps-ui' | 'qb-core' | 'cd_drawtextui' | 'native'

-- ========================================
-- INVENTORIES
-- =======================================
Config.Inventory            = 'ox_inventory'  -- ox_inventory | qs-inventory | origen_inventory | qb-inventory
Config.RemoveItemsOnService = true
Config.RemoveItemsOnJail    = true
Config.WhitelistItems = {
    'id_card',
    'driver_license',
}

-- ========================================
-- COMMUNITY SERVICE
-- =======================================
Config.StartLocation            = vector4(3074.1248, -4737.9067, 15.2616, 202.6774)
Config.ReleaseLocation          = vector4(426.8537,  -978.7916,  30.71013, 86.49715)
Config.ServiceCenter            = vector3(3064.1458, -4734.8726, 15.2616)
Config.ServiceRadius            = 35.0
Config.UseRandomPoints          = true
Config.RandomPointsCount        = 25
Config.MaxDistanceFromCenter    = 40.0
Config.ServiceExtensionOnEscape = 1
Config.EscapeReturnDelay        = 2000

Config.ServiceLocations = {
    { type = 'sweep', coords = vector4(3065.1255, -4753.6323, 15.2616, 153.1105) },
    { type = 'sweep', coords = vector4(3054.2781, -4743.3291, 15.2616, 37.5268)  },
}

-- ========================================
-- JAIL
-- ========================================
Config.JailEnabled              = true
Config.JailLocation             = vector4(1680.3977, 2512.9827, 45.5649, 138.8566)
Config.JailReleaseLocation      = vector4(1849.4, 2586.8, 45.6, 180.0)
Config.JailReturnToLastPosition = true  -- true = return to where you were | false = use JailReleaseLocation
Config.JailCenter               = vector3(1680.3977, 2512.9827, 45.5649)
Config.JailTaskRadius           = 20.0
Config.JailTasksEnabled         = true
Config.JailTasksCount           = 5
Config.JailTaskTimeReduction    = 10   -- seconds reduced per task

-- ========================================
-- CLOTHES (Jail)
-- =======================================
Config.JailClothesEnabled = true  -- false = do not change clothes upon entering jail

Config.JailClothes = {
    male = {
        arms       = { drawable = 0,   texture = 0 },
        pants      = { drawable = 29,  texture = 0 },
        shoes      = { drawable = 24,  texture = 0 },
        jewelry    = { drawable = 0,   texture = 0 },
        undershirt = { drawable = 15,  texture = 0 },
        vest       = { drawable = 0,   texture = 0 },
        top        = { drawable = 58,  texture = 1 },
        mask       = { drawable = 0,   texture = 0 },
        bag        = { drawable = 0,   texture = 0 },
    },
    female = {
        arms       = { drawable = 10,  texture = 0 },
        pants      = { drawable = 34,  texture = 0 },
        shoes      = { drawable = 35,  texture = 0 },
        jewelry    = { drawable = 0,   texture = 0 },
        undershirt = { drawable = 289, texture = 0 },
        vest       = { drawable = 0,   texture = 0 },
        top        = { drawable = 30,  texture = 1 },
        mask       = { drawable = 0,   texture = 0 },
        bag        = { drawable = 0,   texture = 0 },
    }
}

-- ========================================
-- ANIMAL PUNISHMENT
-- ========================================
Config.AnimalEnabled  = true       -- Activar/desactivar el castigo animal

-- Lugar donde se envía al jugador castigado
Config.AnimalLocation = vector4(2042.3700, 4935.8726, 41.0750, 232.2782)
Config.AnimalCenter   = vector3(2042.3700, 4935.8726, 41.0750)
Config.AnimalRadius   = 30.0     -- Radio máximo en metros (si sale se le penaliza)
Config.AnimalPenalty  = 30       -- Segundos que se añaden al escaparse del radio
Config.AnimalTasksEnabled      = true
Config.AnimalTasksCount        = 5
Config.AnimalTaskTimeReduction = 10   -- seconds reduced per task
Config.AnimalTaskRadius        = 20.0

-- Lista de modelos de animales disponibles (se elige uno al azar)
Config.AnimalPeds = {
    `a_c_cow`,         -- Vaca
    `a_c_rat`,         -- Rata
    `a_c_pig`,         -- Cerdo
    `a_c_cat_01`,      -- Gato
    `a_c_chickenhawk`, -- Pollo
    `a_c_rabbit_01`,   -- Conejo
    `a_c_deer`,        -- Venado
}

-- ========================================
-- PERMITS
-- =======================================
Config.AllowedJobs      = { 'police', 'sheriff' }
Config.AllowAdmins      = true
Config.AdminGroups      = { 'admin', 'superadmin', 'mod' }
Config.AdminPermissions = { 'admin', 'god' }
Config.PoliceJob        = 'police'

-- Ace Permissions (FiveM Native)
-- Add this to your server.cfg to give permissions: add_ace group.admin st_comunitarias.admin allow
Config.UseAcePermissions = true
Config.AcePermissionName = 'st_comunitarias.admin'

-- ========================================
-- DISCORD WEBHOOK
-- ========================================
Config.EnableWebhook      = true
Config.GlobalNotification = true
Config.Webhook            = 'PON_AQUI_TU_WEBHOOK'

-- ========================================
-- CLOTHING (Community Service)
-- =======================================
Config.Clothes = {
    male = {
        arms       = { drawable = 0,   texture = 0 },
        pants      = { drawable = 29,  texture = 0 },
        shoes      = { drawable = 24,  texture = 0 },
        jewelry    = { drawable = 0,   texture = 0 },
        undershirt = { drawable = 15,  texture = 0 },
        vest       = { drawable = 0,   texture = 0 },
        top        = { drawable = 58,  texture = 1 },
        mask       = { drawable = 0,   texture = 0 },
        bag        = { drawable = 0,   texture = 0 },
    },
    female = {
        arms       = { drawable = 10,  texture = 0 },
        pants      = { drawable = 34,  texture = 0 },
        shoes      = { drawable = 35,  texture = 0 },
        jewelry    = { drawable = 0,   texture = 0 },
        undershirt = { drawable = 289, texture = 0 },
        vest       = { drawable = 0,   texture = 0 },
        top        = { drawable = 30,  texture = 1 },
        mask       = { drawable = 0,   texture = 0 },
        bag        = { drawable = 0,   texture = 0 },
    }
}

-- ==========================================
-- GLOBAL FUNCTIONS
-- =========================================
function GetTranslation(key)
    local lang = Config.Translations[Config.Language] or Config.Translations['en']
    return lang[key] or key
end

function GenerateRandomServiceLocations()
    local locations = {}
    local center    = Config.ServiceCenter
    local radius    = Config.ServiceRadius
    for i = 1, Config.RandomPointsCount do
        local angle    = math.random() * 2 * math.pi
        local distance = math.sqrt(math.random()) * radius
        table.insert(locations, {
            type   = 'sweep',
            coords = vector4(
                center.x + (distance * math.cos(angle)),
                center.y + (distance * math.sin(angle)),
                center.z, math.random() * 360.0)
        })
    end
    return locations
end
```
