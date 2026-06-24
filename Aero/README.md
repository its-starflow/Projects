<p align="center">  
  <img src="https://raw.githubusercontent.com/its-starflow/Aero/Core/Images/Logo.png" width="250" alt="Aero Logo">  
</p>  

> Version: 0.5  

Aero is a clean and simple GUI library for Roblox focused on being easy to use and easy to customize.

---

# Features

```lua
Aero:New("UI")        -- Main window
Aero:New("Tab")       -- Tab container

Aero:New("Section")   -- Text separator
Aero:New("Button")    -- Clickable button
Aero:New("Toggle")    -- Boolean switch
Aero:New("Slider")    -- Number slider
Aero:New("InputBox")  -- Text input

Aero:Notify()         -- Notification popup
```

---

# Installation

## Method 1 — Loadstring

```lua
local Aero = loadstring(game:HttpGet("https://raw.githubusercontent.com/itsstarflow/Aero/Core/Source"))()
```

---

## Method 2 — ModuleScript

1. Download the `Aero.rbxmx` file.
2. Drag and drop the file into your Roblox game.
3. Place it anywhere you want in your project.

Examples:

```
ReplicatedStorage.Aero
ReplicatedStorage.Libraries.Aero
StarterPlayer.StarterPlayerScripts.Aero
YourProject.Libraries.Aero
Workspace.Modules.Aero
```

Aero is **not limited to `ReplicatedStorage`** — it can be stored anywhere as long as your script can access it.

Require it from a `LocalScript`:

```lua
local Aero = require(game.YourProject.Libraries.Aero)
```

Example using `ReplicatedStorage`:

```lua
local Aero = require(game.ReplicatedStorage.Aero)
```

After loading:

```lua
Aero:New("Element")({})
Aero:Notify("Hello", 3)
```

---

# Example

```lua
local UI = Aero:New("UI")({
    Title = "Aero Example"
})

local Tab1 = Aero:New("Tab", UI)({
    Text = "Tab 1"
})

local Tab2 = Aero:New("Tab", UI)({
    Text = "Tab 2"
})

Aero:Notify("Aero Loaded!", 3)

Aero:New("Section", Tab1)({
    Text = "Examples"
})

Aero:New("Button", Tab1)({
    Text = "Button",
    Callback = function()
        print("Button clicked")
    end
})

Aero:New("Toggle", Tab1)({
    Text = "Toggle",
    Default = false,
    Callback = function(state)
        if state then
            print("Toggle is enabled")
        else
            print("Toggle is disabled")
        end
    end
})

Aero:New("Slider", Tab1)({
    Text = "Slider",
    MinValue = 0,
    MaxValue = 100,
    DefaultValue = 25,
    Callback = function(value)
        print("Slider value: " .. value)
    end
})

Aero:New("InputBox", Tab1)({
    Text = "InputBox",
    Placeholder = "type here...",
    Callback = function(text)
        print("InputBox text: " .. text)
    end
})

Aero:New("Button", Tab2)({
    Text = "Show Notification",
    Callback = function()
        Aero:Notify("Hello from Tab 2!", 3)
    end
})
```

---

# Custom Parents

Elements can be parented to custom UI containers instead of tabs.

Supported:
- Button
- Toggle
- Slider
- InputBox
- Section

Example:

```lua
Aero:New("Button", game.Players.LocalPlayer.PlayerGui.ScreenGui.Frame)({
    Text = "Custom Button",
    Callback = function()
        print("clicked")
    end
})
```

---

# Custom Sizing

All elements support a custom `Size`.

```lua
Aero:New("Button", Tab1)({
    Text = "Large Button",
    Size = UDim2.new(1, 0, 0, 50)
})

Aero:New("Slider", Tab1)({
    Text = "Wide Slider",
    Size = UDim2.new(0, 450, 0, 40),
    MinValue = 0,
    MaxValue = 100
})
```

> Tabs do not support custom parents because of internal UI structure.
