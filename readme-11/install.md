# Install

````markdown
# ST TEXTUI

## Installation

Add `ST-textui` to your `server.cfg`:

```cfg
ensure ST-textui
````

***

## ESX Integration

**File:**

```
es_extended/client/functions.lua
```

**Find:**

```lua
function ESX.TextUI(...)
	return IsResourceFound('esx_textui') and exports['esx_textui']:TextUI(...)
end

---@return nil
function ESX.HideUI()
	return IsResourceFound('esx_textui') and exports['esx_textui']:HideUI()
end
```

**Replace with:**

```lua
function ESX.TextUI(text)
    if GetResourceState('ST-textui') == 'started' then
        exports['ST-textui']:DrawText(text)
    end
end

---@return nil
function ESX.HideUI()
    if GetResourceState('ST-textui') == 'started' then
        exports['ST-textui']:HideText()
    end
end
```

***

## QBCore Integration

**File:**

```
qb-core/client/drawtext.lua
```

**Find:**

```lua
local function hideText()
    SendNUIMessage({
        action = 'HIDE_TEXT',
    })
end

local function drawText(text, position)
    if type(position) ~= 'string' then position = 'left' end

    SendNUIMessage({
        action = 'DRAW_TEXT',
        data = {
            text = text,
            position = position
        }
    })
end

local function changeText(text, position)
    if type(position) ~= 'string' then position = 'left' end

    SendNUIMessage({
        action = 'CHANGE_TEXT',
        data = {
            text = text,
            position = position
        }
    })
end

local function keyPressed()
    CreateThread(function()
        SendNUIMessage({
            action = 'KEY_PRESSED',
        })
        Wait(500)
        hideText()
    end)
end

RegisterNetEvent('qb-core:client:DrawText', function(text, position)
    drawText(text, position)
end)

RegisterNetEvent('qb-core:client:ChangeText', function(text, position)
    changeText(text, position)
end)

RegisterNetEvent('qb-core:client:HideText', function()
    hideText()
end)

RegisterNetEvent('qb-core:client:KeyPressed', function()
    keyPressed()
end)

exports('DrawText', drawText)
exports('ChangeText', changeText)
exports('HideText', hideText)
exports('KeyPressed', keyPressed)
```

**Replace with:**

```lua
local function hideText()
    if GetResourceState('ST-textui') == 'started' then
        exports['ST-textui']:HideText()
    end
end

local function drawText(text, position)
    if GetResourceState('ST-textui') == 'started' then
        exports['ST-textui']:DrawText(text)
    end
end

local function changeText(text, position)
    if GetResourceState('ST-textui') == 'started' then
        exports['ST-textui']:DrawText(text)
    end
end

local function keyPressed()
    CreateThread(function()
        Wait(500)
        hideText()
    end)
end

RegisterNetEvent('qb-core:client:DrawText', function(text, position)
    drawText(text, position)
end)

RegisterNetEvent('qb-core:client:ChangeText', function(text, position)
    changeText(text, position)
end)

RegisterNetEvent('qb-core:client:HideText', function()
    hideText()
end)

RegisterNetEvent('qb-core:client:KeyPressed', function()
    keyPressed()
end)

exports('DrawText', drawText)
exports('ChangeText', changeText)
exports('HideText', hideText)
exports('KeyPressed', keyPressed)
```

***

## Usage

#### Show TextUI

```lua
exports['ST-textui']:DrawText('[E] Open Garage')
```

#### Hide TextUI

```lua
exports['ST-textui']:HideText()
```

***

### Support

**ST Scripts**

* **Website:** https://stscripts.tebex.io/
* **Discord:** https://discord.gg/Gzw8e4HaAh

```
```
