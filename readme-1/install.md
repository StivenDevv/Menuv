# Install

````markdown
# 📦 Installation | ST_DrugsCreator

Welcome to the official installation guide for **ST_DrugsCreator** and its companion props package **ST_drugscreator_props**. Follow these straightforward steps to get the system running smoothly on your server.

---

## 📋 Prerequisites

Make sure the following dependencies are installed and updated to their latest versions:

* [ox_lib](https://github.com/overextended/ox_lib/releases)
* [oxmysql](https://github.com/overextended/oxmysql/releases)
* [ox_target](https://github.com/overextended/ox_target) or `qb-target`
* Supported Framework: **Qbox**, **QB-Core**, or **ESX Legacy**

---

## 🚀 Installation Steps

### 1. Place the Resources

Extract both folders into your server's `resources/` directory (we recommend placing them inside an organized subfolder like `[drugs]` or `[illegal]`):

```text
📁 resources/
 └── 📁 [illegal]/
      └── 📁 [drugs]/
           ├── 📁 ST_drugscreator
           └── 📁 ST_drugscreator_props
````

\{% hint style="warning" %\} **Crucial Step:** Do not rename the folders unless you update all internal references and manifests. The props resource **must** be named `ST_drugscreator_props`. \{% endhint %\}

***

#### 2. Import the Database SQL

Import the included SQL file into your server's MySQL database using HeidiSQL, phpMyAdmin, or your database management tool:

* 📄 File path: `ST_drugscreator/install/sql.sql`

This file automatically sets up the required tables (`st_drugscreator`, `st_drugscreator_plants`, `st_drugscreator_tables`, etc.) along with the default drug configurations and locations.

***

#### 3. Setup Items & Inventory Images

The resource provides ready-to-copy item definitions and UI images inside the `ST_drugscreator/install/` directory:

**A. For ox\_inventory:**

1. Copy the item definitions from `ST_drugscreator/install/items/ox_inventory.txt` and paste them into `ox_inventory/data/items.lua`.
2.  Copy all images from `ST_drugscreator/install/images/` and place them inside:

    ```
    ox_inventory/web/images/
    ```

**B. For qb-core / qb-inventory:**

1. Copy the contents of `ST_drugscreator/install/items/qb-core.txt` and append them to `qb-core/shared/items.lua`.
2. Copy all image files from `install/images/` into `qb-inventory/html/images/`.

***

#### 4. Configure Administrator ACE Permissions

To grant administrators access to open the in-game dashboard with `/drugscreator`, add the following ACE permission lines to your `server.cfg`:

```cfg
# Permission to access the Drugs Creator NUI menu
add_ace group.admin drugscreator_admin allow

# Ensure your admin identifier belongs to group.admin
add_principal identifier.license:YOUR_LICENSE_HERE group.admin
```

\{% hint style="info" %\} If you are running **Qbox**, the script also checks for admin permissions automatically via `qbx_core` exports. \{% endhint %\}

***

#### 5. Start the Resources in `server.cfg`

Open your `server.cfg` and ensure that the props package starts before (or alongside) the main script:

```cfg
# Ensure dependencies first
ensure ox_lib
ensure oxmysql

# Ensure Drugs Creator
ensure ST_drugscreator_props
ensure ST_drugscreator
```

_(Note: If both resources reside inside a folder bracket like `[drugs]`, using `ensure [drugs]` is sufficient)._

***

### 🎮 Commands & Controls

| Command / Key   | Description                                                           | Permissions |
| --------------- | --------------------------------------------------------------------- | ----------- |
| `/drugscreator` | Opens the NUI creation and management panel.                          | Admins only |
| `/sell`         | (Default command) Toggles retail street selling to nearby NPCs.       | All Players |
| `E` (Interact)  | Interact with plants, laboratory doors, tables, and harvesting nodes. | All Players |

***

### ❓ Troubleshooting & FAQ

\{% details title="Props or plants are invisible / 'Invalid harvesting model' error in console" %\}

1. Verify that `ST_drugscreator_props` started successfully in your server console.
2.  Confirm that `ST_drugscreator_props/fxmanifest.lua` points to the correct `.ytyp` file:

    ```lua
    data_file 'DLC_ITYP_REQUEST' 'stream/stiven_pack.ytyp'
    ```
3. Restart the server completely so players download the latest streaming assets from the `stream/` folder upon joining. \{% enddetails %\}

\{% details title="The `/drugscreator` command does not open the menu" %\} Check your server console or `server.cfg` to verify that `drugscreator_admin` is correctly assigned to your player's admin group or identifier. \{% enddetails %\}

***

### 💬 Technical Support

Need assistance or ran into an issue during installation? Open a ticket in our official community: 👉 [**ST Scripts Support Discord**](https://discord.gg/Gzw8e4HaAh)

```
```
