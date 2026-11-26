# Install

## VIP Weapons

VIP weapon management system for FiveM servers with customizable ACE permissions.

### Installation

Add this to your `server.cfg`:

```cfg
setr inventory:weaponmismatch false
```

### Permissions

#### Full Access

```cfg
add_ace group.admin vipweapons allow
```

#### Specific User

```cfg
add_ace identifier.license:YOUR_LICENSE vipweapons allow
```

#### Available Permissions

| Permission            | Description             |
| --------------------- | ----------------------- |
| `vipweapons`          | Full access             |
| `vipweapons.open`     | Open admin panel        |
| `vipweapons.logs`     | Access logs             |
| `vipweapons.profiles` | Manage loadouts         |
| `vipweapons.weapons`  | Manage weapon templates |

### Get Your License

* Use `/status` in-game
* Check txAdmin → Players
* Server console:

```lua
print(GetPlayerIdentifier(playerId, 0))
```

### Notes

* Restart the server after changing permissions.
* Keep your license identifier private.
* Make backups before editing configuration files.



[https://github.com/StivenDevv/Menuv](https://github.com/StivenDevv/Menuv)
