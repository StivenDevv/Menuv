# Config

```lua
Config = {}

-- ============================================================
--  1. FRAMEWORK & INVENTORY
-- ============================================================
-- Framework Auto-Detection: 'auto' (ESX, QBCore, Qbox, Standalone), 'esx', 'qb', 'qbox', 'standalone'
Config.Framework = 'auto'

-- Inventory Auto-Detection: 'auto' (ox_inventory, qb-inventory, ps-inventory, qs-inventory, esx_inventoryhud), 'ox', 'qb', 'ps', 'qs', 'core'
Config.Inventory = 'auto'

-- ============================================================
--  2. INTERACTION MODE (TARGET OR F6 MENU)
-- ============================================================
-- Set to true to use Target System (ox_target / qb-target) and disable F6 interaction menu
-- Set to false to use the ox_lib F6 Context Menu
Config.UseTarget = false

-- Target System Auto-Detection: 'auto' (detects ox_target or qb-target), 'ox_target', 'qb-target'
Config.Target = 'auto'

-- ============================================================
--  3. LOCALIZATION / LANGUAGE
-- ============================================================
-- Options: 'es' (Spanish), 'en' (English), 'fr' (French), 'pt' (Portuguese), 'de' (German)
Config.Locale = 'es'

-- ============================================================
--  4. COMMANDS & KEYBINDS
-- ============================================================
Config.AdminCommand = 'menucacheo'  -- Command to open the Admin Tablet to manage player permissions
Config.MenuKey = 'F6'                -- Default key to open interactions menu (only used when Config.UseTarget = false)

-- ============================================================
--  5. ALLOWED HOSTAGE WEAPONS
-- ============================================================
-- Weapons allowed for the Take Hostage interaction
Config.HostageWeapons = {
    `WEAPON_PISTOL`,
    `WEAPON_PISTOL_MK2`,
    `WEAPON_COMBATPISTOL`,
    `WEAPON_APPISTOL`,
    `WEAPON_PISTOL50`,
    `WEAPON_SNSPISTOL`,
    `WEAPON_SNSPISTOL_MK2`,
    `WEAPON_HEAVYPISTOL`,
    `WEAPON_VINTAGEPISTOL`,
    `WEAPON_CERAMICPISTOL`,
    `WEAPON_NAVYREVOLVER`,
    `WEAPON_GADGETPISTOL`,
    `WEAPON_DOUBLEACTION`,
    `WEAPON_REVOLVER`,
    `WEAPON_REVOLVER_MK2`,
    `WEAPON_GLOCK17`,
    `WEAPON_GLOCK18C`
}

-- ============================================================
--  6. ACE PERMISSIONS (server.cfg)
-- ============================================================
-- Grant admin access in your server.cfg by adding:
-- add_ace group.admin ST_MenucacheoV2 allow
-- add_ace identifier.license:xxxxxx ST_MenucacheoV2 allow
Config.AcePermission = 'ST_MenucacheoV2'

-- ============================================================
--  7. NOTIFICATIONS
-- ============================================================
-- Server-side notification handler
Config.Notify = function(source, type, message)
    if source then
        TriggerClientEvent('ox_lib:notify', source, {
            title = 'Interactions',
            description = message,
            type = type,
        })
    end
end

-- Client-side notification handler
Config.NotifyCL = function(type, message, duration)
    lib.notify({
        title = 'Interactions',
        description = message,
        type = type,
        duration = duration or 5000
    })
end
```
