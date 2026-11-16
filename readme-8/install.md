# Install

````markdown
# 🎒 ST Outfit Bag v2 — Installation Guide

{% hint style="info" %}
Quick installation guide for **ST Outfit Bag v2**.
{% endhint %}

---

## 📋 Requirements

* **Framework:** QBCore / Qbox or ESX
* **Database:** `oxmysql`
* **Clothing:** `illenium-appearance`, `fivem-appearance`, or `qb-clothing`
* **Target (Optional):** `ox_target` or `qb-target`

---

## 🚀 Installation

### 1. Database Setup

Run the SQL query in your database:

{% code title="st_outfits.sql" %}
```sql
CREATE TABLE IF NOT EXISTS `st_outfits` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `player` varchar(256) DEFAULT '0',
  `tag` varchar(50) DEFAULT '0',
  `data` longtext CHARACTER SET utf8mb4 COLLATE utf8mb4_bin DEFAULT NULL,
  `created_at` datetime NOT NULL DEFAULT current_timestamp(),
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
````

\{% endcode %\}

***

#### 2. Item Registration

\{% tabs %\} \{% tab title="ox\_inventory" %\} Add this to `ox_inventory/data/items.lua`:

```lua
['st_outfitbag'] = {
    label = 'Outfit Bag',
    weight = 4000,
    stack = false,
    close = true,
    consume = 0,
    server = {
        export = 'ST_outfitbagv2.UseBag',
    },
    client = {
        image = 'st_outfitbag.png',
    },
},
```

\{% endtab %\}

\{% tab title="QBCore / Qbox" %\} Add this to `qb-core/shared/items.lua`:

```lua
['st_outfitbag'] = {
    ['name'] = 'st_outfitbag',
    ['label'] = 'Outfit Bag',
    ['weight'] = 4000,
    ['type'] = 'item',
    ['image'] = 'st_outfitbag.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Store and change outfits on the go'
},
```

\{% endtab %\} \{% endtabs %\}

Copy `_INSTALLATION/icons/st_outfitbag.png` to your inventory images folder:

* **ox\_inventory:** `ox_inventory/web/images/`
* **qb-inventory:** `qb-inventory/html/images/`

***

#### 3. Configuration

Open `config.lua` and set your framework and systems:

\{% code title="config.lua" %\}

```lua
Config.locale = 'en'

Config.qbSettings = {
    enabled = true, -- true for QBCore / Qbox
}

Config.esxSettings = {
    enabled = false, -- true for ESX
    useNewESXExport = false
}

Config.target = {
    enabled = true,
    system = 'ox_target' -- 'ox_target', 'qb-target', or 'qtarget'
}

Config.clothingSystemSaving = {
    enabled = true,
    system = 'illenium-appearance', -- 'illenium-appearance', 'fivem-appearance', 'qb-clothing'
}
```

\{% endcode %\}

***

#### 4. Server Start

Add this to your `server.cfg`:

```cfg
ensure ST_outfitbagv2
```

***

### ⚡ Quick Reference

#### Exports

```lua
-- Client: Open a fixed bag (e.g. police locker)
exports['ST_outfitbagv2']:OpenFixedBag('bagName')

-- Server: Use bag from inventory
exports['ST_outfitbagv2']:UseBag(source)
```

#### Admin Outfit Generator

1. Set `Config.debug = true` in `config.lua`.
2. Dress your ped and run `/outfit-output <name>` in chat.
3. Paste the contents of `outfit-outputs/<name>.txt` into `Config.fixedBags`.
