# Config

```lua
local config = {}

-- =============================================================================
-- 1. CORE DEPENDENCIES & FRAMEWORK INTEGRATION
-- =============================================================================
-- Auto-detection is supported for framework & ambulance systems ('auto').
config.framework       = 'auto'        -- Options: 'auto' | 'esx' | 'qbcore' | 'qbox'
config.target          = 'ox_target'   -- Options: 'ox_target' | 'qb-target' | 'qbox-target' | 'none'
config.ambulanceSystem = 'auto'        -- Options: 'auto' | 'ak47_ambulancejob' | 'ak47_qb_ambulancejob' | 'qb-ambulancejob' | 'wasabi_ambulance' | 'wasabi_ambulance_v2' | 'ars_ambulancejob' | 'esx_ambulancejob' | 'qbx_ambulancejob' | 'none'
config.inventory       = 'ox_inventory'-- Options: 'ox_inventory' | 'qb-inventory' | 'qs-inventory' | 'origen_inventory' | 'none'
config.clothingSystem  = 'illenium-appearance' -- Options: 'esx_skin' | 'illenium-appearance' | 'fivem-appearance' | 'qb-clothing'

-- =============================================================================
-- 2. GENERAL SETTINGS & BEHAVIOR
-- =============================================================================
config.locale              = 'en'      -- Active language: 'es' | 'en' | 'fr' | 'pt' | 'de' | 'it' | 'ru'
config.matchTime           = 600       -- Match duration limit in seconds (600s = 10 minutes)
config.maxRounds           = 50        -- Maximum selectable rounds per lobby/match
config.exitDuelCommand     = 'leave'   -- Command for players to forfeit/leave an active duel
config.exitCoords          = vector4(-279.7642, -2030.2855, 30.1456, 295.2265) -- Teleport location when leaving or finishing a match
config.clearStatsOnRestart = false     -- Reset player ranking/statistics tables when the resource restarts
config.toggleUIExport      = 'ST_PVP'  -- Resource export name used to interact with the UI
config.debug               = false     -- Enable detailed server/client debug prints in the server console & client F8

-- =============================================================================
-- 3. CONTROLS & WEAPON WHEEL
-- =============================================================================
config.disableScrollWeaponSwitch = true   -- Disables default GTA weapon switching on mouse scroll in duels (allows custom binds)
config.weaponWheelKey            = 'F12'  -- Key assigned to open the GTA weapon wheel (Registered FiveM keybind)

-- =============================================================================
-- 4. ADMIN PANEL & PERMISSIONS
-- =============================================================================
config.adminCommand        = 'pvpadmin'        -- Command to directly open the PVP Admin Dashboard
config.adminAcePermission  = 'st_pvp.admin'    -- ACE permission string for staff access (e.g. 'command' or 'st_pvp.admin')
config.adminGroups = {                         -- Allowed framework groups for admin access
    ['admin']      = true,
    ['superadmin'] = true,
    ['god']        = true,
    ['owner']      = true,
    ['mod']        = true,
}

-- =============================================================================
-- 5. LOBBY MENU NPC & BLIP
-- =============================================================================
config.menuPed = {
    model          = 'mp_m_weapexp_01',                                 -- Ped model
    coords         = vector4(-280.0961, -2033.6248, 30.1459, 308.3484), -- Ped coordinates & heading
    targetDistance = 2.5,                                               -- Target interaction radius in meters
    targetIcon     = 'fa-solid fa-list',                                -- FontAwesome icon displayed on target
}

config.menuBlip = {
    sprite  = 491,        -- Blip sprite icon ID
    display = 4,          -- Blip display mode
    scale   = 0.8,        -- Blip scale size on map
    colour  = 3,          -- Blip color ID (3 = Blue)
    name    = 'PVP ARENAS', -- Blip label on map
}
-- =============================================================================
-- 6. DUEL MODES CONFIGURATION
-- =============================================================================
-- Allowed team sizes when setting up a duel lobby
config.duelmodes = {
    '1vs1',
    '2vs2',
    '3vs3',
    '4vs4',
    '5vs5',
    '6vs6',
    '8vs8',
    '10vs10',
    '15vs15',
    '20vs20',
    '25vs25',
    '30vs30',
}

-- =============================================================================
-- 7. AVAILABLE WEAPONS
-- =============================================================================
-- Available weapon selections for duel configurations
config.weapons = {
    -- Handguns / Pistols
    { value = 'WEAPON_PISTOL',           label = 'Pistol',            category = 'Pistol'  },
    { value = 'WEAPON_PISTOL_MK2',       label = 'Pistol MK2',        category = 'Pistol'  },
    { value = 'WEAPON_APPISTOL',         label = 'AP Pistol',         category = 'Pistol'  },
    { value = 'WEAPON_COMBATPISTOL',     label = 'Combat Pistol',     category = 'Pistol'  },
    { value = 'WEAPON_HEAVYPISTOL',      label = 'Heavy Pistol',      category = 'Pistol'  },
    { value = 'WEAPON_VINTAGEPISTOL',    label = 'Vintage Pistol',    category = 'Pistol'  },
    { value = 'WEAPON_REVOLVER',         label = 'Revolver',          category = 'Pistol'  },
    { value = 'WEAPON_REVOLVER_MK2',     label = 'Revolver MK2',      category = 'Pistol'  },

    -- Submachine Guns (SMGs)
    { value = 'WEAPON_SMG',              label = 'SMG',               category = 'SMG'     },
    { value = 'WEAPON_SMG_MK2',          label = 'SMG MK2',           category = 'SMG'     },
    { value = 'WEAPON_MICROSMG',         label = 'Micro SMG',         category = 'SMG'     },
    { value = 'WEAPON_MINISMG',          label = 'Mini SMG',          category = 'SMG'     },
    { value = 'WEAPON_COMBATPDW',        label = 'Combat PDW',        category = 'SMG'     },
    { value = 'WEAPON_MACHINEPISTOL',    label = 'Machine Pistol',    category = 'SMG'     },

    -- Assault Rifles
    { value = 'WEAPON_ASSAULTRIFLE',     label = 'Assault Rifle',     category = 'Rifle'   },
    { value = 'WEAPON_ASSAULTRIFLE_MK2', label = 'Assault Rifle MK2', category = 'Rifle'   },
    { value = 'WEAPON_CARBINERIFLE',     label = 'Carbine Rifle',     category = 'Rifle'   },
    { value = 'WEAPON_CARBINERIFLE_MK2', label = 'Carbine MK2',       category = 'Rifle'   },
    { value = 'WEAPON_SPECIALCARBINE',   label = 'Special Carbine',   category = 'Rifle'   },
    { value = 'WEAPON_BULLPUPRIFLE',     label = 'Bullpup Rifle',     category = 'Rifle'   },

    -- Shotguns
    { value = 'WEAPON_PUMPSHOTGUN',      label = 'Pump Shotgun',      category = 'Shotgun' },
    { value = 'WEAPON_PUMPSHOTGUN_MK2',  label = 'Pump SG MK2',       category = 'Shotgun' },
    { value = 'WEAPON_COMBATSHOTGUN',    label = 'Combat Shotgun',    category = 'Shotgun' },
    { value = 'WEAPON_HEAVYSHOTGUN',     label = 'Heavy Shotgun',     category = 'Shotgun' },
    { value = 'WEAPON_SAWNOFFSHOTGUN',   label = 'Sawnoff SG',        category = 'Shotgun' },

    -- Sniper Rifles
    { value = 'WEAPON_SNIPERRIFLE',      label = 'Sniper Rifle',      category = 'Sniper'  },
    { value = 'WEAPON_HEAVYSNIPER',      label = 'Heavy Sniper',      category = 'Sniper'  },
    { value = 'WEAPON_MARKSMANRIFLE',    label = 'Marksman Rifle',    category = 'Sniper'  },
}

-- =============================================================================
-- 8. ARENAS & SPAWN COORDINATES
-- =============================================================================
config.maps = {

    -- Arena 0: Ramp Arena
    {
        value  = 'arena0',
        label  = 'Arena Rampa',
        coords = {
            player = {
                vector4(-1789.25, 3167.23, 472.69, 359.0),
                vector4(-1790.14, 3167.33, 472.69, 359.0),
                vector4(-1788.70, 3167.25, 472.69, 359.0),
                vector4(-1789.35, 3167.75, 472.69, 359.0),
                vector4(-1789.33, 3168.74, 472.69, 359.0),
            },
            opponent = {
                vector4(-1789.30, 3196.41, 472.69, 179.0),
                vector4(-1788.16, 3196.36, 472.69, 179.0),
                vector4(-1790.21, 3196.43, 472.69, 179.0),
                vector4(-1789.01, 3196.03, 472.69, 179.0),
                vector4(-1789.11, 3194.81, 472.69, 179.0),
            },
        },
    },

    -- Arena 1: Mini Arena
    {
        value  = 'arena1',
        label  = 'Arena Mini',
        coords = {
            player = {
                vector4(-2239.96, 3168.91, 473.46, 359.0),
                vector4(-2240.75, 3169.01, 473.46, 359.0),
                vector4(-2239.30, 3168.86, 473.46, 359.0),
                vector4(-2240.00, 3169.21, 473.46, 359.0),
                vector4(-2240.00, 3170.01, 473.46, 359.0),
            },
            opponent = {
                vector4(-2240.21, 3194.05, 473.48, 179.0),
                vector4(-2239.44, 3193.95, 473.48, 179.0),
                vector4(-2241.00, 3193.94, 473.48, 179.0),
                vector4(-2240.16, 3192.94, 473.48, 179.0),
                vector4(-2240.17, 3192.37, 473.48, 179.0),
            },
        },
    },

    -- Arena 2: Large Arena
    {
        value  = 'arena2',
        label  = 'Arena Grande',
        coords = {
            player = {
                vector4(-2070.19, 3218.85, 473.56, 178.0),
                vector4(-2068.65, 3218.75, 473.56, 177.0),
                vector4(-2066.62, 3218.98, 473.56, 176.0),
                vector4(-2072.01, 3219.41, 473.56, 178.0),
                vector4(-2070.18, 3221.03, 473.56, 178.0),
                vector4(-2064.50, 3219.00, 473.56, 176.0),
                vector4(-2074.00, 3219.50, 473.56, 178.0),
                vector4(-2068.00, 3221.50, 473.56, 177.0),
                vector4(-2072.50, 3221.00, 473.56, 178.0),
                vector4(-2066.00, 3221.50, 473.56, 176.0),
            },
            opponent = {
                vector4(-2070.90, 3144.71, 473.56, 359.0),
                vector4(-2069.43, 3144.63, 473.56, 358.0),
                vector4(-2067.54, 3144.49, 473.56, 358.0),
                vector4(-2074.29, 3144.46, 473.56, 356.0),
                vector4(-2070.67, 3145.92, 473.56, 357.0),
                vector4(-2065.50, 3144.40, 473.56, 358.0),
                vector4(-2076.50, 3144.50, 473.56, 356.0),
                vector4(-2068.50, 3146.50, 473.56, 357.0),
                vector4(-2073.00, 3146.50, 473.56, 357.0),
                vector4(-2066.00, 3146.50, 473.56, 358.0),
            },
        },
    },

    -- Arena 3: Double Arena
    {
        value  = 'arena3',
        label  = 'Arena Doble',
        coords = {
            player = {
                vector4(-1907.6813, 3166.2278, 474.6600, 355.5378),
                vector4(-1903.4517, 3165.5471, 474.6600,   3.2720),
                vector4(-1900.0764, 3165.9600, 474.6605,   3.9979),
                vector4(-1906.0856, 3160.7991, 474.6604, 359.9890),
                vector4(-1900.8365, 3160.0076, 474.6604,   0.2508),
                vector4(-1910.00,   3166.00,   474.6600, 355.0),
                vector4(-1897.50,   3166.00,   474.6600,   4.0),
                vector4(-1909.00,   3161.00,   474.6604, 359.0),
                vector4(-1897.50,   3160.00,   474.6604,   1.0),
                vector4(-1903.50,   3158.50,   474.6604,   0.0),
            },
            opponent = {
                vector4(-1899.9839, 3198.9680, 474.6599, 171.6304),
                vector4(-1904.2889, 3198.9316, 474.6604, 179.9934),
                vector4(-1907.4021, 3198.2776, 474.6604, 176.4501),
                vector4(-1907.6339, 3202.3032, 474.6604, 177.0185),
                vector4(-1901.7313, 3200.7527, 474.6604, 187.7979),
                vector4(-1897.50,   3199.00,   474.6599, 172.0),
                vector4(-1910.50,   3198.50,   474.6604, 176.0),
                vector4(-1910.50,   3202.50,   474.6604, 177.0),
                vector4(-1897.50,   3201.50,   474.6604, 187.0),
                vector4(-1904.00,   3203.50,   474.6604, 180.0),
            },
        },
    },

    -- Arena 4: Large Arena 2
    {
        value  = 'arena4',
        label  = 'Arena Grande 2',
        coords = {
            player = {
                vector4(-1828.7584, -3180.5459, 13.9444,  50.8562),
                vector4(-1821.2347, -3181.3169, 13.9444,  55.7032),
                vector4(-1820.0662, -3180.5005, 13.9444,  50.4420),
                vector4(-1819.0717, -3179.8098, 13.9444,  42.7563),
                vector4(-1813.6548, -3178.8091, 13.9444,  64.7816),
                vector4(-1812.8118, -3177.1050, 13.9444,  63.2020),
                vector4(-1810.8925, -3174.6418, 13.9444,  65.9245),
                vector4(-1810.0049, -3172.1804, 13.9444,  67.4173),
                vector4(-1811.7094, -3161.2563, 13.9444,  56.1457),
                vector4(-1803.1415, -3156.8171, 13.9444,  52.5033),
            },
            opponent = {
                vector4(-1896.9117, -3140.4014, 13.9444, 227.7135),
                vector4(-1897.7096, -3135.2976, 13.9444, 269.2485),
                vector4(-1897.6262, -3133.2488, 13.9444, 271.2684),
                vector4(-1897.5757, -3131.2739, 13.9444, 270.7928),
                vector4(-1897.8794, -3126.7783, 13.9444, 257.1465),
                vector4(-1893.9478, -3121.6406, 13.9444, 236.1957),
                vector4(-1891.7781, -3119.0481, 13.9444, 231.1943),
                vector4(-1889.8469, -3116.6162, 13.9444, 234.5111),
                vector4(-1888.8444, -3114.0193, 13.9444, 238.0444),
                vector4(-1881.6006, -3111.4321, 13.9443, 234.6505),
            },
        },
    },
}

-- =============================================================================
-- 9. RANKING & SCORE REWARDS
-- =============================================================================
config.scoreSettings = {
    win   = 10,  -- Points added for winning a match
    loss  = -5,  -- Points deducted for losing a match
    kill  = 2,   -- Points added per kill
    death = -1,  -- Points deducted per death
}

-- =============================================================================
-- 10. PODIUM & LEADERBOARD HOLOGRAPHIC PEDS
-- =============================================================================
-- Default fallback ped model if player appearance is not yet loaded
config.pedsDefaultModel = 'mp_m_freemode_01'

-- Physical podium prop object at the lobby
config.Podium = {
    enable = true,                                             -- Set to false to disable podium prop spawning
    model  = 'base_podio',                                      -- Prop model name
    coords = vector4(-275.7340, -2027.0001, 29.1456, 29.4897), -- World position and heading
}

-- Holographic top players displayed on the podium
config.PedsLeaderboard = {
    -- 1st Place (Champion)
    {
        top       = 1,
        coords    = vector4(-275.9939, -2026.9518, 31.7100, 213.5916),
        game      = 'rankeds', -- Ranking metric: 'rankeds' or 'kills'
        animation = {
            dict = 'anim@heists@heist_corona@single_team',
            name = 'single_team_loop_boss',
        },
    },
    -- 2nd Place
    {
        top       = 2,
        coords    = vector4(-278.3925, -2028.6143, 31.0843, 217.8952),
        game      = 'rankeds', -- Ranking metric: 'rankeds' or 'kills'
        animation = {
            dict = 'amb@world_human_cheering@male_a',
            name = 'base',
        },
    },
    -- 3rd Place
    {
        top       = 3,
        coords    = vector4(-273.3850, -2025.8585, 30.6616, 216.0795),
        game      = 'rankeds', -- Ranking metric: 'rankeds' or 'kills'
        animation = {
            dict = 'anim@mp_player_intuppersalute',
            name = 'idle_a',
        },
    },
}

return config
```
