# Config

```lua
Config = {}

-- 'auto' automatically detects the framework (esx, qbcore, qbox)
Config.Framework = 'auto'

-- Notification System: 'auto' | 'esx' | 'qbcore' | 'qbox' | 'ox_lib'
-- 'auto' will use your framework's native system, or ox_lib if not found
Config.NotifySystem = 'auto'

Config.Settings = {
    Locale      = 'es',   -- Language: 'es' (Spanish) | 'en' (English)
    Debug       = false,
    ShowMessage = true,   -- Shows a message when entering the safe zone
    ShowMapBlip = false,  -- Shows the blip on the map (can be toggled via panel)
}

-- ─────────────────────────────────────────────
-- Menu UI Config (Tablet Opacity)
-- ─────────────────────────────────────────────
Config.Menu = {
    Opacity  = 92,                 -- Admin menu tablet opacity (10 to 100%, e.g. 92 = 92% opacity)
}

-- ─────────────────────────────────────────────
-- TextUI Config (Message / Position / Color / Opacity)
-- ─────────────────────────────────────────────
Config.TextUI = {
    Message  = "Safe Zone",        -- Text to display
    Position = "bottom-center",    -- Options: 'top-center', 'left-center', 'right-center', 'bottom-center'
    Color    = "#009103",          -- Hex color for the background
    Opacity  = 80,                 -- Safezone badge background opacity (10 to 100%)
}


-- Permissions & Administration

Config.Admins = {
    -- Add license or discord id as shown in the examples:
    -- 'license:0000000000000000000000000000000000000000',
    -- 'discord:0000000000000000',

    'license:70a4add6dab762c43b4bcf2ae7fc27c85ed89682',
}

Config.AdminCommands = {
    createzone = 'createzone',
}

-- Non Restricted Jobs
Config.NonRestrictedJobs = {
    { name = 'police',     label = 'Police' },
    { name = 'dealership', label = 'Dealership' },
    { name = 'ambulance',  label = 'Ambulance' },
}

```
