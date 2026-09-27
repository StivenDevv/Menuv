# Compatibility & Requirements

## 🧩 Compatibility & Requirements

**ST-AdvancedGarages** is built with a modular and adaptive architecture featuring automatic detection (`"auto"`) for the vast majority of frameworks, dependencies, and standalone scripts in the FiveM ecosystem.

***

### ⚙️ Supported Frameworks

| Framework                        | Support Status |        Auto Detection       |
| -------------------------------- | :------------: | :-------------------------: |
| **ESX Legacy** (1.6.0 - 1.10.x+) |  `✅ Supported` | `Config.Framework = "auto"` |
| **QBCore** (Latest & Legacy)     |  `✅ Supported` | `Config.Framework = "auto"` |
| **Qbox Project** (`qbx_core`)    |  `✅ Supported` | `Config.Framework = "auto"` |

> \[!TIP] Setting `Config.Framework = "auto"` will automatically detect and import your framework's core object without requiring manual configuration.

***

### 🗄️ Database Drivers

* **oxmysql** `v2.0.0+` _(Highly Recommended)_
* **mysql-async** / **ghmattimysql** _(Supported)_

> \[!NOTE] Database tables (`st_dynamic_garages` and extra columns) are automatically created and migrated upon starting the server for the first time.

***

### 🎯 Interaction Systems (Target & Keybinds)

You can choose between interactive **NPC Peds**, **3D Markers**, or **Target systems**.

| Resource / System        |     Interaction Type    |              Config Option             |
| ------------------------ | :---------------------: | :------------------------------------: |
| **Native 3D Markers**    |       `E` Keybind       |         `Config.UsePed = false`        |
| **Interactive NPC Peds** | `E` Key / Custom Prompt |         `Config.UsePed = true`         |
| **ox\_target**           |   Target Zone / Entity  | `Config.PedTargetSystem = "ox_target"` |
| **qb-target**            |   Target Zone / Entity  | `Config.PedTargetSystem = "qb-target"` |

***

### 💬 TextUI Systems (DrawText)

Configurable via `Config.DrawText = "auto"` or by specifying the resource name directly:

* `ox_lib` _(lib.showTextUI)_
* `ST-textui`
* `okokTextUI`
* `qb-DrawText` / `qb-core`
* `esx_textui`
* `cd_drawtextui`
* `ps-ui`
* `jg-textui`

***

### 🔔 Notification Systems

Configurable via `Config.Notifications = "auto"`:

* `ox_lib` (`lib.notify`)
* `okokNotify`
* `ps-ui`
* Native **ESX** / **QBCore** notifications

***

### ⛽ Fuel Systems

Saves and synchronizes the exact fuel level when parking or taking vehicles out of the garage:

| Fuel Script    | Config Setting                     |
| -------------- | ---------------------------------- |
| **ox\_fuel**   | `Config.FuelSystem = "ox_fuel"`    |
| **LegacyFuel** | `Config.FuelSystem = "LegacyFuel"` |
| **ps-fuel**    | `Config.FuelSystem = "ps-fuel"`    |
| **cdn-fuel**   | `Config.FuelSystem = "cdn-fuel"`   |
| **nd\_fuel**   | `Config.FuelSystem = "nd_fuel"`    |
| **Disabled**   | `Config.FuelSystem = "none"`       |

***

### 🔑 Vehicle Key Systems

Automatically grants or revokes vehicle keys upon spawning and storing:

| Key Script               | Config Setting                                |
| ------------------------ | --------------------------------------------- |
| **qb-vehiclekeys**       | `Config.VehicleKeys = "qb-vehiclekeys"`       |
| **wasabi\_carlock**      | `Config.VehicleKeys = "wasabi_carlock"`       |
| **MrNewbVehicleKeys**    | `Config.VehicleKeys = "MrNewbVehicleKeys"`    |
| **jaksam-vehicles-keys** | `Config.VehicleKeys = "jaksam-vehicles-keys"` |
| **qs-vehiclekeys**       | `Config.VehicleKeys = "qs-vehiclekeys"`       |
| **mk\_vehiclekeys**      | `Config.VehicleKeys = "mk_vehiclekeys"`       |
| **Disabled**             | `Config.VehicleKeys = "none"`                 |

***

### 🌐 Supported Languages (Locales)

Complete localization covering server-side, client-side, and the entire In-Game Admin Panel UI:

* 🇬🇧 **English** (`en`)
* 🇪🇸 **Spanish** (`es`)
* 🇫🇷 **French** (`fr`)
* 🇩🇪 **German** (`de`)
* 🇵🇹 **Portuguese** (`pt`)

***

### ⚡ Performance (Resmon)

* **0.00 ms** at idle / driving normally.
* **0.01 ms** only at the exact moment of opening the UI or interacting with the menu.
