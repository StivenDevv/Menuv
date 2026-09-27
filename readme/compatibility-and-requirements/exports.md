# Exports

{% code overflow="wrap" %}
````
markdown# ⚡ Resource Exports & API ReferenceUse these exports to trigger garage actions, open menus from radial wheels or custom targets, store vehicles, and integrate with phones or external job scripts.---## 🚗 Core Garage Actions (Client-Side)### `OpenGarage`Opens any garage menu (Public, Job, Gang) programmatically for the local player.```lua-- Open a public garageexports['ST-advancedgarages']:OpenGarage("Legion Square", "public")-- Open a job garageexports['ST-advancedgarages']:OpenGarage("Police Department", "job")
````
{% endcode %}

* **Parameters:**
  * `garageName` _(string, optional)_: Name of the garage from config (defaults to `"Legion Square"`).
  * `garageType` _(string, optional)_: Type: `"public"`, `"job"`, `"gang"` (defaults to `"public"`).

***

#### `StoreVehicle` <a href="#user-content-storevehicle" id="user-content-storevehicle"></a>

Attempts to store the vehicle the player is currently driving or a specific vehicle entity into a garage.

{% code overflow="wrap" expandable="true" %}
```
lua-- Store the current vehicle the player is driving into Legion Squarelocal success = exports['ST-advancedgarages']:StoreVehicle(nil, "Legion Square")-- Or store a specific vehicle entitylocal vehicle = GetVehiclePedIsIn(PlayerPedId(), false)local success = exports['ST-advancedgarages']:StoreVehicle(vehicle, "Grove Street")
```
{% endcode %}

* **Parameters:**
  * `vehicleEntity` _(entity/number, optional)_: Vehicle entity handle. If `nil`, it detects the vehicle the player is currently in.
  * `garageName` _(string, optional)_: Target garage name (defaults to nearest/current garage or `"Legion Square"`).
* **Returns:**
  * `boolean`: `true` if vehicle was found and sent to storage, `false` otherwise.

***

#### `OpenImpound` <a href="#user-content-openimpound" id="user-content-openimpound"></a>

Opens the vehicle impound retrieval menu.

{% code overflow="wrap" expandable="true" %}
```
luaexports['ST-advancedgarages']:OpenImpound("Impound 1")
```
{% endcode %}

* **Parameters:**
  * `impoundName` _(string, optional)_: Name of the impound lot (defaults to `"Impound 1"`).

***

#### `OpenAdminPanel` <a href="#user-content-openadminpanel" id="user-content-openadminpanel"></a>

Opens the in-game Garage Creator & Editor tablet UI. _(Requires admin permissions)._

{% code overflow="wrap" expandable="true" %}
```
lua-- Open the admin creator panel directlyexports['ST-advancedgarages']:OpenAdminPanel()-- Or open directly focused on a specific garageexports['ST-advancedgarages']:OpenAdminPanel("Legion Square", "public")
```
{% endcode %}

***

### 📱 Phone & External App Integration <a href="#user-content--phone--external-app-integration" id="user-content--phone--external-app-integration"></a>

#### 🌐 Client: `GetVehicleLocation` <a href="#user-content--client-getvehiclelocation" id="user-content--client-getvehiclelocation"></a>

Returns the 3D GPS coordinates of a vehicle if it is currently spawned in the world.

{% code overflow="wrap" expandable="true" %}
```
lualocal coords = exports['ST-advancedgarages']:GetVehicleLocation("ABC 123")if coords then    SetNewWaypoint(coords.x, coords.y)end
```
{% endcode %}

* **Parameters:**
  * `plate` _(string)_: Vehicle license plate.
* **Returns:**
  * `table` `{ x = float, y = float, z = float }` or `nil`.

***

#### 🖥️ Server: `GetPlayerVehicles` <a href="#user-content-server-getplayervehicles" id="user-content-server-getplayervehicles"></a>

Returns a formatted list of all owned vehicles for a specific player ID.

{% code overflow="wrap" %}
```
lualocal vehicles = exports['ST-advancedgarages']:GetPlayerVehicles(source)for _, veh in ipairs(vehicles) do    print(veh.plate, veh.model, veh.garage, veh.state, veh.fuel)end
```
{% endcode %}

* **Parameters:**
  * `source` _(number)_: Player server ID.
* **Returns:**
  * `table`: Array of vehicle objects containing `plate`, `model`, `garage`, `state`, `fuel`, `engine`, `body`, `isStored`, `isImpounded`, `type`.

***

#### 🖥️ Server: `RecoverVehicle` <a href="#user-content-server-recovervehicle" id="user-content-server-recovervehicle"></a>

Sends a vehicle directly back to a specified garage (Valet service / Insurance).

{% code overflow="wrap" %}
```
lualocal success = exports['ST-advancedgarages']:RecoverVehicle("ABC 123", "Legion Square")
```
{% endcode %}

* **Parameters:**
  * `plate` _(string)_: Vehicle license plate.
  * `garageName` _(string, optional)_: Target garage name.
* **Returns:**
  * `boolean`: `true` if updated successfully.

***

#### 🖥️ Server: `SetVehicleImpounded` <a href="#user-content-server-setvehicleimpounded" id="user-content-server-setvehicleimpounded"></a>

Sends an owned vehicle to the police or state impound with a fine and reason.

{% code title="" overflow="wrap" lineNumbers="true" %}
```
lualocal success = exports['ST-advancedgarages']:SetVehicleImpounded("ABC 123", "Police Impound", "Illegal Parking", 250)
```
{% endcode %}

* **Parameters:**
  * `plate` _(string)_: Vehicle license plate.
  * `impoundName` _(string, optional)_: Target impound name.
  * `reason` _(string, optional)_: Reason text.
  * `fee` _(number, optional)_: Fee amount to release the vehicle.
