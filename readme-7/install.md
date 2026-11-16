# Install

````markdown
# 🛠️ Installation & Configuration — ST_MenucacheoV2

Welcome to the official documentation for **ST_MenucacheoV2**. This resource provides a complete player interaction and search system (via F6 Context Menu or Target) featuring **real-time per-player permission management** through a built-in Admin Tablet UI.

---

## 📋 1. Requirements & Compatibility

Before installing the resource, make sure your server has the required dependencies installed and up to date:

### Required Dependencies
* [**ox_lib**](https://github.com/overextended/ox_lib) *(Required for context menus, notifications, and locales)*
* [**oxmysql**](https://github.com/overextended/oxmysql) *(Required for automatic database permission storage)*

### Automatic Compatibility (Bridge)
The script automatically detects your server environment when options are set to `'auto'` in `config.lua`:

| Category | Supported Systems |
| :--- | :--- |
| **Frameworks** | `ESX`, `QBCore`, `Qbox`, `Standalone` |
| **Inventories** | `ox_inventory`, `qb-inventory`, `ps-inventory`, `qs-inventory`, `core_inventory`, `esx_inventoryhud` |
| **Target Systems** *(Optional)* | `ox_target`, `qb-target` |
| **Included Locales** | English (`en`), Spanish (`es`), French (`fr`), Portuguese (`pt`), German (`de`) |

---

## 🚀 2. Step-by-Step Installation

### Step 1: Download and Place the Resource
1. Download **`ST_MenucacheoV2`** from your Cfx.re Portal / Keymaster.
2. Extract the folder into your server's `resources` directory (e.g., `resources/[scripts]/ST_MenucacheoV2`).

> ⚠️ **Important:** Keep the resource folder name intact or make sure your ACE permission settings match `Config.AcePermission`.

---

### Step 2: Database Setup (Automatic)
**You do not need to manually import any `.sql` file.**  
When the resource starts for the first time, it will automatically create and verify the `st_f6_permissions` table in your database using `oxmysql`.

---

### Step 3: Configure `server.cfg`
Add the ACE permissions for your administrators and ensure the resource starts **after** `oxmysql`, `ox_lib`, and your framework/inventory:

```cfg
# 1. Core Dependencies
ensure oxmysql
ensure ox_lib

# 2. ACE Permissions to access the Admin Tablet (/menucacheo)
add_ace group.admin ST_MenucacheoV2 allow
# Optional: Grant permission to a specific player via license
# add_ace identifier.license:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx ST_MenucacheoV2 allow

# 3. Start Resource
ensure ST_MenucacheoV2
````

***

### ⚙️ 2. Configuration (`config.lua`)

The `config.lua` file is completely unlocked (`escrow_ignore`) so you can customize it to fit your server:

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
Config.Locale = 'en'

-- ============================================================
--  4. COMMANDS & KEYBINDS
-- ============================================================
Config.AdminCommand = 'menucacheo'  -- Command to open the Admin Tablet to manage player permissions
Config.MenuKey = 'F6'               -- Default key to open interactions menu (only used when Config.UseTarget = false)

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
Config.AcePermission = 'ST_MenucacheoV2'
```

***

### 🖥️ 3. In-Game Permission Management (Admin Tablet)

Access to the interaction menu is managed through a granular per-player permission whitelist.

1. Join the server with an administrator account (via framework admin group or `ST_MenucacheoV2` ACE permission).
2. Run the **`/menucacheo`** command in chat.
3. From the Admin Tablet UI, you can:
   * **Grant access to an online player** by entering their **Server ID** and selecting which specific actions they are allowed to use.
   * **Edit permissions in real time** by toggling individual actions on or off with a single click.
   * **Revoke access** from any player stored in the database.

#### Configurable Actions per Player

Each authorized player can be granted or restricted from the following individual actions:

* 🔒 **Handcuff / Uncuff** (`handcuff`)
* 🚶 **Escort / Drag** (`drag`)
* 🚓 **Put in Vehicle** (`putInVeh`)
* 🚪 **Take out of Vehicle** (`putOutVeh`)
* 🔍 **Search / Steal Inventory** (`search`)
* 🛍️ **Place / Remove Headbag** (`headbag`)
* 🔫 **Take Hostage** (`hostage`)

***

### ❓ 4. Frequently Asked Questions (FAQ)

#### Why do I get a "No permission" notification when pressing F6?

Only players authorized through the **`/menucacheo`** Admin Panel can open and use the interaction menu. Open `/menucacheo` as an admin, add your Server ID, and enable the desired permissions.

#### Why didn't my keybind change after editing `Config.MenuKey`?

In FiveM, `RegisterKeyMapping` binds are cached per client after joining the server for the first time. Players can customize their keybind anytime in-game via:\
**GTA V Settings ➔ Key Bindings ➔ FiveM**.

#### How can I use my own notification script?

At the bottom of [config.lua](file:///c:/Users/Administrator/Desktop/BASEE%20SERVER%20ST%20SCRIPTS/txData/ESXLegacy_9C3805.base/resources/\[scripts]/\[utils]/ST_MenucacheoV2/config.lua#L66-L88), you will find `Config.Notify` (Server-side) and `Config.NotifyCL` (Client-side). By default, they use `ox_lib:notify`, which you can replace with your custom notification export or event.

```
```
