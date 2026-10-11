# Config

```lua
Config = {
    EnablePreview = true, -- Muestra tu personaje en la pantalla
    SetScaleCommand = 'setscale', -- Comando para establecer la escala
    ResetScaleCommand = 'resetscale', -- Comando para restablecer la escala
    ScaleMenuCommand = 'scalemenu', -- Comando para abrir el menú de escala
    Permissions = {
        Enable = true, -- Cuando es falso, el menú es accesible para todos los jugadores.
        Groups = {"owner"}, -- Permisos de comando QB/QBOX/ESX
        Customs = {"license:xxx", "citizenid", "discord:xxx"}, -- Permisos personalizados
        DiscordRoles = {"xxx"} -- IDs de roles de Discord
    },
    DefaultScale = 1.0, -- No se recomienda cambiar.
    MinScale = 0.86, -- No se recomienda cambiar.
    MaxScale = 1.3, -- No se recomienda cambiar.
    DisableRagdoll = false, -- Si es verdadero, tu script de ragdoll no funcionará.
    ScenarioPeds = false, -- Los NPCs reaccionan según el tamaño de tu personaje.
    GiveScaleMenu = {
        Enable = true, -- Si es verdadero, puedes abrir el menú ingresando el ID del jugador con el comando.
        Command = "givescalemenu", -- Comando para abrir el menú
        Description = "Abre el menú de escala al jugador", -- Descripción del comando para abrir el menú
        Groups = {"admin","owner", "developer"} -- Permisos del comando para abrir el menú
    },
    HideWhen = {
        MaxDistance = 20.0, -- La escala se aplica a jugadores que están cerca de esta distancia.
        Invisible = true, -- Si el personaje no es visible, la escala se desactiva.
        CollisionDisabled = true, -- Si la colisión del personaje está desactivada, la escala se desactiva.
        Falling = true, -- Cuando el personaje está cayendo, la escala se desactiva.
        Ragdoll = true, -- Cuando el personaje está en ragdoll, la escala se desactiva.
        Climbing = true, -- Cuando el personaje está escalando, la escala se desactiva.
        Jumping = false, -- Si el personaje está saltando, la escala se desactiva.
        Swimming = true, -- Si el personaje está nadando, la escala se desactiva.
        Attached = true, -- Si el personaje está adjunto a una entidad o jugador, la escala se desactiva.
        OnVehicle = false, -- Si el personaje está en un vehículo, la escala se desactiva.
        Alpha = true -- Si el valor alfa no es 255
    },
    UpdatePedAccordingToScale = {
        RunSprintMultiplier = true -- La tasa de agotamiento de la respiración de tu personaje variará según el tamaño.
    },
    ScaledPlayerDamage = {
        Enable = true, -- Si es verdadero, los jugadores con altura modificada reciben daño extra
        HitsToKill = 2, -- Número de golpes con arma para matar a un jugador escalado (sin contar puños)
        ExcludeFists = true -- Si es verdadero, el daño de puños no cuenta para los golpes de muerte
    }
}
```
