# Install

## 📢 Stiven Notifications — Integración ESX & QBCore

Sistema de notificaciones personalizado para ESX y QBCore. Sigue exactamente los pasos a continuación para integrar correctamente.

***

### ⚙️ Integración ESX

Para esx ir a es\_extendex client - functions linea 158

```lua
---@param message string The message to show
---@param notifyType? string The type of notification to show
---@param length? number The length of the notification
---@param title? string The title of the notification
---@param position? string The position of the notification
---@return nil
function ESX.ShowNotification(message, notifyType, length, title, position)
	return IsResourceFound('esx_notify') and exports['esx_notify']:Notify(notifyType or "info", length or 5000, message, title, position)
end
```

Remplazarla por esta

```lua
---@param message string The message to show
---@param notifyType? string The type of notification to show
---@param length? number The length of the notification
---@param title? string The title of the notification
---@return nil
function ESX.ShowNotification(message, type, length)
	exports['Stiven_Notifications']:Notification(message, type, length)
end
```

***

### ⚙️ Integración QBCore

Para qbcore Ir a qb-core client functions linea 171

```lua
function QBCore.Functions.Notify(text, texttype, length, icon)
    local message = {
        action = 'notify',
        type = texttype or 'primary',
        length = length or 5000,
    }

    if type(text) == 'table' then
        message.text = text.text or 'Placeholder'
        message.caption = text.caption or 'Placeholder'
    else
        message.text = text
    end

    if icon then
        message.icon = icon
    end

    SendNUIMessage(message)
end
```

Remplzar por esta

```lua
function QBCore.Functions.Notify(text, texttype, length)
    -- Verifica si el texto es una tabla
    if type(text) == "table" then
        local ttext = text.text or 'Placeholder'
        local caption = text.caption or 'Placeholder'
        texttype = texttype or 'primary'
        length = length or 5000
        -- Usar tu sistema de notificaciones
        TriggerEvent('Stiven_Notifications:Show', ttext, length)
    else
        texttype = texttype or 'primary'
        length = length or 5000
        -- Usar tu sistema de notificaciones
        TriggerEvent('Stiven_Notifications:Show', text, length)
    end
end
```
