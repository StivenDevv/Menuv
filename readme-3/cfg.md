---
description: Put this in your cfg.
---

# cfg

ST PVP

#### Installation

Add this to your `server.cfg`:

```cfg
# Prevent inventory from removing match weapons
setr inventory:weaponmismatch false

# Resource start
ensure ST_PVP

# Admin permissions (Optional - for /pvpadmin)
add_ace group.admin st_pvp.admin allow
```
