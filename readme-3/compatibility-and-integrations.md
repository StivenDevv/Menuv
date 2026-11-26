# Compatibility & Integrations

````markdown
# 🧩 Compatibility & Integrations

ST PVP is designed with a **Universal Plug & Play Architecture**. It features an intelligent auto-detection engine (`'auto'`) that detects your running resources on startup, eliminating the need for complex bridge setups.

---

## ⚡ Smart Auto-Detection

When set to `'auto'`, ST PVP will automatically listen to resource start states in FiveM/RedM and hook into the appropriate APIs, exports, and statebags.

```lua
config.framework       = 'auto'
config.target          = 'auto'
config.ambulanceSystem = 'auto'
config.inventory       = 'auto'
config.clothingSystem  = 'auto'
````

***

### 🏛️ Supported Frameworks

ST PVP works seamlessly with all major FiveM roleplay frameworks:

| Framework               | Supported Versions | Notes                                                                |
| ----------------------- | ------------------ | -------------------------------------------------------------------- |
| **Qbox** (`qbx_core`)   | v1.0+              | Native support via official exports & statebags.                     |
| **QBCore** (`qb-core`)  | Latest & Legacy    | Full CitizenID, metadata, and core integration.                      |
| **ESX** (`es_extended`) | Legacy, v1.2, v1.1 | Supports both modern and legacy database schemas (`users`).          |
| **Standalone**          | Any                | Match routing buckets and arena teleportation operate independently. |

***

### 🎒 Supported Inventories

During duel matches, ST PVP locks external inventories, hides hotbars, enables custom GTA weapon wheels, and equips weapons without cluttering players' persistent databases.

| Inventory                   | Config Key           | Special Features                                                    |
| --------------------------- | -------------------- | ------------------------------------------------------------------- |
| **ox\_inventory**           | `'ox_inventory'`     | Native `weaponWheel` integration and `invBusy` statebag management. |
| **ak47\_inventory**         | `'ak47_inventory'`   | Native inventory closing, hotbar lock & complete item restoration.  |
| **ak47\_qb\_inventory**     | `'ak47_inventory'`   | Full QBCore variant support for MenanAk47 inventory.                |
| **qs-inventory**            | `'qs-inventory'`     | Integrated `weaponWheel` toggle and hotkey restoration.             |
| **origen\_inventory**       | `'origen_inventory'` | Automatic weapon wheel toggle and inventory lock.                   |
| **qb-inventory**            | `'qb-inventory'`     | Automatic inventory closing and action block during matches.        |
| **Standalone / GTA Native** | `'none'`             | Direct GTA weapon allocation via client natives.                    |

***

### 🚑 Ambulance & Medical Systems

ST PVP prevents medical delays, "last stand" freezes, and black screen respawn bugs by synchronizing death handling and instantly reviving players upon round transitions and lobby exits.

| Medical System             | Config Key               | Features Handled                                                    |
| -------------------------- | ------------------------ | ------------------------------------------------------------------- |
| **ak47\_ambulancejob**     | `'ak47_ambulancejob'`    | Server-side skeleton fix, down/dead flag reset & zero delay revive. |
| **ak47\_qb\_ambulancejob** | `'ak47_qb_ambulancejob'` | Native QBCore death event reset & injury clearance.                 |
| **wasabi\_ambulance**      | `'wasabi_ambulance'`     | v1 & v2 support, injury wipe (`clearPlayerInjury`) and revive.      |
| **p\_ambulancejob**        | `'p_ambulancejob'`       | Instant death cam release & revive trigger.                         |
| **qbx\_medical**           | `'qbx_ambulancejob'`     | QBX bridge support and statebag synchronization.                    |
| **qb-ambulancejob**        | `'qb-ambulancejob'`      | Native hospital bed skip, `isdead` / `inlaststand` clearing.        |
| **esx\_ambulancejob**      | `'esx_ambulancejob'`     | Native ESX revive event trigger.                                    |
| **ars\_ambulancejob**      | `'ars_ambulancejob'`     | Animated revive bypass (`skipAnim = true`).                         |
| **Native GTA**             | `'none'`                 | NetworkResurrectLocalPlayer clean release.                          |

***

### 🎯 Target Systems

Used for interacting with the Lobby NPC to open the PvP menu:

| Target Resource            | Config Key      | Interaction Method                                |
| -------------------------- | --------------- | ------------------------------------------------- |
| **ox\_target**             | `'ox_target'`   | Clean entity option targeting.                    |
| **qbx\_target**            | `'qbox-target'` | Full Qbox target integration.                     |
| **qb-target**              | `'qb-target'`   | Standard target entity option.                    |
| **No Target (Standalone)** | `'none'`        | 3D World Floating Marker + `[E]` key interaction. |

***

### 👔 Clothing & Appearance Systems

Used for rendering holographic leaderboard podium characters and player avatars:

| Appearance System       | Config Key              | How it works                                                      |
| ----------------------- | ----------------------- | ----------------------------------------------------------------- |
| **ak47\_clothing**      | `'ak47_clothing'`       | Direct skinchanger/ESX hook + native component variation.         |
| **ak47\_qb\_clothing**  | `'ak47_qb_clothing'`    | QBCore outfit loader + podium ped skin application.               |
| **illenium-appearance** | `'illenium-appearance'` | Live appearance export (`getPedAppearance` / `setPedAppearance`). |
| **fivem-appearance**    | `'fivem-appearance'`    | Full appearance component & prop mapping.                         |
| **qb-clothing**         | `'qb-clothing'`         | `loadPlayerClothing` client event integration.                    |
| **esx\_skin**           | `'esx_skin'`            | Standard skinchanger component parsing.                           |

***

### ⚙️ Configuration Setup

In `ST_PVP/shared/config.lua`:

```lua
-- =============================================================================
-- 1. CORE DEPENDENCIES & FRAMEWORK INTEGRATION
-- =============================================================================
-- Auto-detection is supported for all core systems ('auto').
config.framework       = 'auto'        -- Options: 'auto' | 'esx' | 'qbcore' | 'qbox'
config.target          = 'auto'        -- Options: 'auto' | 'ox_target' | 'qb-target' | 'qbox-target' | 'none'
config.ambulanceSystem = 'auto'        -- Options: 'auto' | 'p_ambulancejob' | 'wasabi_ambulance' | 'wasabi_ambulance_v2' | 'ak47_ambulancejob' | 'ak47_qb_ambulancejob' | 'qb-ambulancejob' | 'ars_ambulancejob' | 'esx_ambulancejob' | 'qbx_ambulancejob' | 'none'
config.inventory       = 'auto'        -- Options: 'auto' | 'ox_inventory' | 'ak47_inventory' | 'qb-inventory' | 'qs-inventory' | 'origen_inventory' | 'none'
config.clothingSystem  = 'auto'        -- Options: 'auto' | 'ak47_clothing' | 'ak47_qb_clothing' | 'illenium-appearance' | 'fivem-appearance' | 'qb-clothing' | 'esx_skin'
```

***

### ❓ Frequently Asked Questions

**Does ST PVP duplicate or wipe player inventory items?**

No. ST PVP equips match weapons via client-side runtime handlers and locks your inventory during the match. Your real server inventory is never altered, wiped, or modified.

**Can I manually force a specific script instead of using `'auto'`?**

Yes! If you run multiple overlapping resources (e.g. testing two medical scripts), you can replace `'auto'` with the exact config key shown in the tables above.

**What happens if I don't use any target resource?**

If set to `'none'` (or if `'auto'` detects no target script), the lobby automatically displays a 3D animated ground marker and a floating text prompt: `[E] Open PVP Menu`.

```
```
