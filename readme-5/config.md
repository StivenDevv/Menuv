# Config

```lua
Config = {}

-- Framework Settings: 'qbcore', 'qbox', 'esx', 'auto'
Config.Framework = 'auto'

-- Language: 'en', 'es', 'fr', 'pt', 'de', 'it', 'tr'
Config.Locale = 'en'

-- Debug Logs in Console (Prints table-by-table wipe breakdown and dynamic discovery)
Config.Debug = false

-- Admin permissions allowed to execute CK
Config.AdminGroups = {
    'admin',
    'god',
    'superadmin',
    'owner',
    'mod'
}

-- Commands
Config.Commands = {
    CK = 'ck',              -- /ck [id] [motivo] (Admins)
    AdminMenu = 'adminck',  -- /adminck (Admins - Interfaz interactiva Online/Offline)
    SelfCK = 'solicitarck'  -- /solicitarck [motivo] (Players can request or self-CK if enabled)
}

-- Search Settings for Offline Characters
Config.MaxOfflineSearchResults = 50


-- Self CK Settings
Config.AllowSelfCK = false -- If true, players can CK themselves directly. If false, it sends a log / alert to staff.

-- Cinematic Death Sequence
Config.Cinematic = {
    Enabled = true,
    Duration = 12000,          -- Duration of death screen in milliseconds before disconnect/respawn
    PlaySound = true,          -- Dramatic cinematic sound
    SoundVolume = 0.5,
    ScreenFade = true,         -- Fade to black / red blood overlay
    RagdollPlayer = true,      -- Make player ragdoll on floor
    KillPlayer = true          -- Set player health to 0
}

-- Post-CK Action:
-- 'disconnect' -> Drops player with a dramatic CK goodbye message.
-- 'multichar' -> Forces player back to character selection screen (qb-multicharacter / esx_multicharacter).
Config.PostCKAction = 'disconnect'

-- Discord Logs & Webhooks
Config.DiscordLogs = {
    Enabled = true,
    Webhook = '', -- Paste your Discord Webhook URL here
    ServerName = 'ST Roleplay Server',
    AvatarURL = 'https://i.imgur.com/8QzQ6rY.png',
    EmbedColor = 15158332 -- Red color (0xE74C3C)
}

-- Dynamic Database Scan & Wipe Settings
-- If true, ST_CK will automatically inspect INFORMATION_SCHEMA.COLUMNS to detect ALL tables
-- in your database that store character/player identifiers, ensuring 100% clean deletion for any custom scripts.
Config.DynamicTableWipe = true

-- Column names to detect dynamically across any table in the database
Config.IdentifierColumns = {
    'identifier',
    'owner',
    'citizenid',
    'cid',
    'charid',
    'char_id',
    'user_id',
    'player_id',
    'playerId',
    'player'
}

-- Safety Blacklist: Tables that should NEVER be wiped, even if they contain one of the columns above
Config.IgnoredTables = {
    'items',
    'jobs',
    'job_grades',
    'vehicles',
    'addon_account',
    'addon_inventory',
    'datastore',
    'licenses',
    'fine_types',
    'bans',
    'banlist',
    'baninfo',
    'admin_logs',
    'st_characterkill_logs',
    'ox_doorlock'
}

-- Explicit / Fallback Tables to wipe upon CK (OxMySQL)
-- Used when DynamicTableWipe is false or merged alongside dynamic scan.
Config.DatabaseWipe = {
    qbcore = {
        { table = 'players', column = 'citizenid' },
        { table = 'player_vehicles', column = 'citizenid' },
        { table = 'player_houses', column = 'citizenid' },
        { table = 'player_mails', column = 'citizenid' },
        { table = 'player_contacts', column = 'citizenid' },
        { table = 'player_outfits', column = 'citizenid' },
        { table = 'bank_accounts', column = 'citizenid' },
        { table = 'bank_statements', column = 'citizenid' },
        { table = 'apartments', column = 'citizenid' },
        { table = 'crypto_transactions', column = 'citizenid' },
        { table = 'phone_messages', column = 'citizenid' },
        { table = 'phone_invoices', column = 'citizenid' },
        { table = 'ox_inventory', column = 'owner' },
    },
    esx = {
        { table = 'users', column = 'identifier' },
        { table = 'owned_vehicles', column = 'owner' },
        { table = 'addon_account_data', column = 'owner' },
        { table = 'addon_inventory_items', column = 'owner' },
        { table = 'datastore_data', column = 'owner' },
        { table = 'user_licenses', column = 'owner' },
        { table = 'billing', column = 'identifier' },
        { table = 'ox_inventory', column = 'owner' },
    }
}


```
