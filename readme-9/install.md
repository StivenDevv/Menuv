# Install

## 📢 Stiven Notifications

A modern, sleek, and high-performance notification system designed for FiveM servers with glassmorphism UI, animated timer bars, responsive typography, and sound effects.

{% hint style="info" %}
**Resource Dependency**: Make sure `Stiven_Notifications` starts **before** or **alongside** your core framework in your `server.cfg`.
{% endhint %}

***

### 📦 General Installation

1. Place the `Stiven_Notifications` folder into your server's `resources` directory (e.g., `resources/[core]/Stiven_Notifications`).
2. Add the start command to your `server.cfg`:

```cfg
ensure Stiven_Notifications
```

***

### ⚙️ Framework Integration

{% tabs %}
{% tab title="Qbox (QBX)" %}
#### Qbox Framework Setup

Qbox uses `qbx_core` for central notification dispatching. Follow these steps to route all server and client notifications through Stiven Notifications:

**1. Edit `qbx_core` Client Functions**

Open `resources/[core]/qbx_core/client/functions.lua` and locate the `Notify` function:

```lua
---@param text table|string text of the notification
---@param notifyType? string informs default styling. Defaults to 'inform'
---@param duration? integer milliseconds notification will remain on screen. Defaults to 5000
---@param subTitle? string extra text under the title
---@param notifyPosition? string
---@param notifyStyle? table
---@param notifyIcon? string
---@param notifyIconColor? string
function Notify(text, notifyType, duration, subTitle, notifyPosition, notifyStyle, notifyIcon, notifyIconColor)
```

Replace the function body with the following snippet:

```lua
function Notify(text, notifyType, duration, subTitle, notifyPosition, notifyStyle, notifyIcon, notifyIconColor)
    local msg
    if type(text) == 'table' then
        if text.text and text.caption then
            msg = text.text .. '<br>' .. text.caption
        else
            msg = text.text or text.caption or text.description or 'Placeholder'
        end
    elseif subTitle then
        msg = text .. '<br>' .. subTitle
    else
        msg = tostring(text)
    end

    local length = duration or 5000

    -- Automatic color formatting based on notification type
    if notifyType == 'error' and not msg:find('~') then
        msg = '~r~' .. msg .. '~s~'
    elseif notifyType == 'success' and not msg:find('~') then
        msg = '~g~' .. msg .. '~s~'
    elseif (notifyType == 'primary' or notifyType == 'inform' or notifyType == 'info') and not msg:find('~') then
        msg = '~b~' .. msg .. '~s~'
    elseif notifyType == 'warning' and not msg:find('~') then
        msg = '~y~' .. msg .. '~s~'
    end

    if GetResourceState('Stiven_Notifications') == 'started' then
        exports['Stiven_Notifications']:Notification(msg, length)
    else
        TriggerEvent('Stiven_Notifications:Show', msg, length)
    end
end
```

{% hint style="success" %}
Because QBX's `QBCore.Functions.Notify` and server-side `exports.qbx_core:Notify` both route through this client function, this single change handles **all** Qbox notifications server-wide.
{% endhint %}
{% endtab %}

{% tab title="QBCore" %}
#### QBCore Framework Setup

**1. Edit `qb-core` Client Functions**

Open `resources/[qb]/qb-core/client/functions.lua` and locate `QBCore.Functions.Notify` (typically around line 171):

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

Replace it with:

```lua
function QBCore.Functions.Notify(text, texttype, length)
    if type(text) == "table" then
        local ttext = text.text or 'Placeholder'
        local caption = text.caption or 'Placeholder'
        texttype = texttype or 'primary'
        length = length or 5000
        TriggerEvent('Stiven_Notifications:Show', ttext .. '<br>' .. caption, texttype, length)
    else
        texttype = texttype or 'primary'
        length = length or 5000
        TriggerEvent('Stiven_Notifications:Show', text, texttype, length)
    end
end
```
{% endtab %}

{% tab title="ESX Legacy" %}
#### ESX Legacy Setup

**1. Edit `es_extended` Client Functions**

Open `resources/[esx]/es_extended/client/functions.lua` and locate `ESX.ShowNotification` (typically around line 158):

```lua
function ESX.ShowNotification(message, notifyType, length, title, position)
    return IsResourceFound('esx_notify') and exports['esx_notify']:Notify(notifyType or "info", length or 5000, message, title, position)
end
```

Replace it with:

```lua
function ESX.ShowNotification(message, notifyType, length)
    exports['Stiven_Notifications']:Notification(message, notifyType, length)
end
```
{% endtab %}

{% tab title="Standalone / Direct" %}
#### Direct Exports & Events

You can use Stiven Notifications directly in any third-party script without framework bindings:

**Client-side Export**

```lua
-- Standard usage: (message, type, duration)
exports['Stiven_Notifications']:Notification('Vehicle successfully stored!', 'success', 5000)

-- Alternative usage: (message, duration)
exports['Stiven_Notifications']:Notification('~g~Vehicle successfully stored!~s~', 5000)
```

**Client-side Event**

```lua
TriggerEvent('Stiven_Notifications:Show', 'Access denied to this area.', 'error', 4000)
```

**Server-side Notification**

```lua
TriggerClientEvent('Stiven_Notifications:Show', targetSource, 'You received $500 cash.', 'success', 5000)
```

**Help Notifications**

```lua
-- Shows a floating instruction banner
exports['Stiven_Notifications']:Help('Press ~g~E~s~ to interact with the NPC.')
```
{% endtab %}
{% endtabs %}

***

### 🎨 Color Code Formatting

Stiven Notifications supports native GTA-style color tags directly within your message strings:

| Code          | Output Color     | Example Usage                             |
| ------------- | ---------------- | ----------------------------------------- |
| `~r~`         | Red (Error)      | `~r~Error:~s~ Insufficient funds.`        |
| `~g~`         | Green (Success)  | `~g~Success:~s~ Transaction completed.`   |
| `~b~`         | Blue (Inform)    | `~b~Info:~s~ Server restart scheduled.`   |
| `~y~`         | Yellow (Warning) | `~y~Warning:~s~ Engine temperature high.` |
| `~o~`         | Gold             | `~o~VIP reward claimed.~s~`               |
| `~p~`         | Purple           | `~p~Special event started.~s~`            |
| `~c~`         | Grey             | `~c~Inactive~s~`                          |
| `~m~`         | Dark Grey        | `~m~Hidden details~s~`                    |
| `~u~`         | Black            | `~u~Classified~s~`                        |
| `~s~` / `~w~` | White (Reset)    | Resets color to default text color        |
| `~h~`         | **Bold**         | Makes text bold                           |
| `~n~`         | New Line         | Inserts a `<br>` line break               |

***

### 🛠️ Assets & Customization

| Asset                  | Path                | Description                                                             |
| ---------------------- | ------------------- | ----------------------------------------------------------------------- |
| **Logo**               | `html/logo.png`     | Notification brand/server icon (recommended: 512x512 or 1024x1024 PNG). |
| **Styles**             | `html/style.css`    | Translucency, colors, fonts, margins, animations, and border-radii.     |
| **Notification Sound** | `html/pop.ogg`      | Audio file triggered when a notification pops up.                       |
| **Help Sound**         | `html/helpnoti.ogg` | Audio file triggered on help notifications.                             |
| **Font**               | `html/font.ttf`     | Custom server typography font.                                          |
