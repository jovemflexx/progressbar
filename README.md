# re-designed Progressbar for QB Framework
## Re-designed QB-ProgressBar
A modern and visually enhanced version of the qb-progressbar for FiveM's QBCore framework. This redesign includes improved UI/UX, better customization options, and optimized performance.

## Features:
- Sleek and modern design.
- Fully customizable progress bar settings (colors, sizes, animations, etc.).
- Smooth animations for a better user experience.
- Optimized for better performance in QBCore-based servers.
## Installation:
Download or clone this repository to your resources folder.
Add the resource to your server configuration (server.cfg):
ensure progressbar
Restart your server and enjoy the redesigned progress bar!
## Compatibility:
Built specifically for QBCore framework.
Tested with the latest QBCore updates.

Preview:



![progressbar](https://github.com/user-attachments/assets/d2d5c226-3265-473e-80b4-36edcf1a9945)







# Usage

### Client

- QBCore.Functions.Progressbar(**name**: string, **label**: string, **duration**: number, **useWhileDead**: boolean, **canCancel**: boolean, **disableControls**: table, **animation**: table, **prop**: table, **propTwo**: table, **onFinish**: function, **onCancel**: function)
  > Create a new progressbar from the built in qb-core functions.<br>
  > **Example:**
  > ```lua
  >QBCore.Functions.Progressbar("random_task", "Doing something", 5000, false, true, {
  >    disableMovement = false,
  >    disableCarMovement = false,
  >    disableMouse = false,
  >    disableCombat = true,
  >}, {
  >    animDict = "mp_suicide",
  >    anim = "pill",
  >    flags = 49,
  >}, {}, {}, function()
  >    -- Done
  >end, function()
  >    -- Cancel
  >end)
  > ```

## Exports

### Client

- Progress(**data**: string, **handler**: function)
  > Creates a new progress bar directly from the export, always use the built in qb-core function if possible.<br>
  > **Example:**
  > ```lua
  >exports['progressbar']:Progress({
  >    name = "random_task",
  >    duration = 5000,
  >    label = "Doing something",
  >    useWhileDead = false,
  >    canCancel = true,
  >    controlDisables = {
  >        disableMovement = false,
  >        disableCarMovement = false,
  >        disableMouse = false,
  >        disableCombat = true,
  >    },
  >    animation = {
  >        animDict = "mp_suicide",
  >        anim = "pill",
  >        flags = 49,
  >    },
  >    prop = {},
  >    propTwo = {}
  >}, function(cancelled)
  >    if not cancelled then
  >        -- finished
  >    else
  >        -- cancelled
  >    end
  >end)
  > ```
  > **Props Example:**
  > ```lua
  >exports['progressbar']:Progress({
  >    name = "random_task",
  >    duration = 5000,
  >    label = "Doing something",
  >    useWhileDead = false,
  >    canCancel = true,
  >    controlDisables = {
  >        disableMovement = false,
  >        disableCarMovement = false,
  >        disableMouse = false,
  >        disableCombat = true,
  >    },
  >    animation = {
  >        animDict = "missheistdockssetup1clipboard@base",
  >        anim = "pill",
  >        flags = 49,
  >    },
  >    prop = {
  >      model = 'prop_notepad_01',
  >      bone = 18905,
  >      coords = vec3(0.1, 0.02, 0.05),
  >      rotation = vec3(10.0, 0.0, 0.0),
  >    },
  >    propTwo = {
  >      model = 'prop_pencil_01',
  >      bone = 58866,
  >      coords = vec3(0.11, -0.02, 0.001),
  >      rotation = vec3(-120.0, 0.0, 0.0),
  >    }
  >}, function(cancelled)
  >    if not cancelled then
  >        -- finished
  >    else
  >        -- cancelled
  >    end
  >end)
  > ```

  - isDoingSomething()
    > Returns a boolean (true/false) depending on if a progressbar is present.<br>
    > **Example:**
    > ```lua
    > local busy = exports["progressbar"]:isDoingSomething()
    > ```

  - ProgressWithStartEvent(**data**: table, **start**: function, **finish**: function)
    > Works like a normal progressbar, the data parameter should be the same as the data passed into the `Progress` export above.<br>
    > The start function gets triggered upon the start of the progressbar.<br>
    > The finish handler is the same as the `handler` parameter in the `Progress` export above.

  - ProgressWithTickEvent(**data**: table, **tick**: function, **finish**: function)
    > Works like a normal progressbar, the data parameter should be the same as the data passed into the `Progress` export above.<br>
    > The tick function gets triggered every frame while the progressbar is active.<br>
    > The finish handler is the same as the `handler` parameter in the `Progress` export above.

  - ProgressWithTickEvent(**data**: table, **start**: function, **tick**: function, **finish**: function)
    > Works like a normal progressbar, the data parameter should be the same as the data passed into the `Progress` export above.<br>
    > The start function gets triggered upon the start of the progressbar.<br>
    > The tick function gets triggered every frame while the progressbar is active.<br>
    > The finish handler is the same as the `handler` parameter in the `Progress` export above.
