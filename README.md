# ProxyLib

> A modern Roblox UI library with theme support, acrylic effects, multi-language translation, search, notifications, a key system, and more.

---

## Table of Contents

1. [Getting Started](#1-getting-started)
2. [CreateWindow](#2-createwindow)
   - [Window Options](#21-window-options)
   - [TitleConfig](#22-titleconfig)
   - [ConfigPanel](#23-configpanel)
   - [FloatButton](#24-floatbutton)
   - [Acrylic](#25-acrylic)
   - [BackgroundImage](#26-backgroundimage)
   - [Window Methods](#27-window-methods)
3. [CreateTab](#3-createtab)
   - [Tab Methods](#31-tab-methods)
4. [Content Components](#4-content-components)
   - [CreateSection](#41-createsection)
   - [CreateParagraph](#42-createparagraph)
   - [CreateToggle](#43-createtoggle)
   - [CreateSlider](#44-createslider)
   - [CreateButton](#45-createbutton)
   - [CreateCheckBox](#46-createcheckbox)
   - [CreateDropdown](#47-createdropdown)
   - [CreateValueDropdown](#48-createvaluedropdown)
   - [CreateTextBox](#49-createtextbox)
   - [CreateKeyBind](#410-createkeybind)
   - [CreateColorPicker](#411-createcolorpicker)
   - [CreateDiscordInvite](#412-creatediscordinvite)
   - [CreateSeparatorLine](#413-createseparatorline)
5. [Sidebar Components](#5-sidebar-components)
   - [CreateSeparator](#51-createseparator)
   - [CreateSidebarLine](#52-createsidebarline)
6. [Notifications](#6-notifications)
7. [CreateKeySystem](#7-createkeysystem)
   - [KeySystem Options](#71-keysystem-options)
   - [KeySystem Methods](#72-keysystem-methods)
   - [CreateButton (KeySystem)](#73-createbutton-keysystem)
   - [CreateSocialButton](#74-createsocialbutton)
8. [Themes](#8-themes)
9. [Languages](#9-languages)
10. [AutoSave / AutoLoad](#10-autosave--autoload)
11. [ColoredWords / RichText](#11-coloredwords--richtext)
12. [Double Tab Layout](#12-double-tab-layout)
13. [Full Examples](#13-full-examples)

---

## 1. Getting Started

```lua
local ProxyLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/ProxyHubDev/ProxyLib/refs/heads/main/Documents/ProxyLibrary"))()
local Lib = ProxyLib.new()
```

`ProxyLib.new()` creates a new library instance. Call `Lib:Destroy()` to destroy all windows and disconnect every connection when you're done.

---

## 2. CreateWindow

```lua
local Window = Lib:CreateWindow(config)
```

### 2.1 Window Options

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"ProxyLib"` | Main window title |
| `Subtitle` | string | `""` | Subtitle shown below the title |
| `Icon` | string | `""` | Asset ID for the header icon (e.g. `"rbxassetid://..."`) |
| `Size` | Vector2 | `Vector2.new(520, 380)` | Initial window size |
| `MinSize` | Vector2 | `Vector2.new(380, 250)` | Minimum size when resizing |
| `MaxSize` | Vector2 | `Vector2.new(900, 650)` | Maximum size when resizing |
| `TypeUI` | string | `"Modern"` | UI style: `"Modern"` or `"Classic"` |
| `Theme` | string \| Color3 | `"Blue"` | Color theme (see [Themes](#8-themes)) |
| `Language` | string | `"English"` | Default language (see [Languages](#9-languages)) |
| `DefaultLanguage` | string | `nil` | Alias for `Language` |
| `Search` | boolean | `true` | Shows a search bar in the sidebar |
| `AutoSave` | boolean | `true` | Automatically saves component values to a file |
| `AutoLoad` | boolean | `true` | Restores saved values on startup |
| `DefaultFps` | boolean | `false` | Starts with the FPS overlay enabled |
| `DefaultPing` | boolean | `false` | Starts with the Ping overlay enabled |
| `DefaultProfile` | boolean | `false` | Starts with the player profile card visible |
| `TitleConfig` | table | `{}` | Title word appearance config |
| `ConfigPanel` | table | `{}` | Settings panel config |
| `FloatButton` | table | `nil` | Floating button to show/hide the window |
| `Acrylic` | table | `{}` | Acrylic effect config |
| `BackgroundImage` | table | `{}` | Background image or video |

```lua
local Window = Lib:CreateWindow({
    Title    = "My Hub",
    Subtitle = "v1.0",
    Icon     = "rbxassetid://XXXXXXX",
    Size     = Vector2.new(560, 400),
    Theme    = "Purple",
    TypeUI   = "Modern",
    Language = "English",
})
```

---

### 2.2 TitleConfig

Controls how highlighted words in the title are rendered. Highlighted words can use gradient colors or the theme's accent color.

```lua
TitleConfig = {
    Gradient = true,
    Colors = {
        Color3.fromRGB(100, 200, 255),
        Color3.fromRGB(50,  100, 255),
    },
    Words = {
        "Hub",
        {
            Text   = "Premium",
            Colors = {
                Color3.fromRGB(255, 200, 50),
                Color3.fromRGB(255, 120, 0),
            },
        },
    },
}
```

If `Gradient = false`, highlighted words use the theme's solid `Accent` color instead. Any word not listed in `Words` is rendered as normal text. Per-word `Colors` take priority over the global `Colors` array.

---

### 2.3 ConfigPanel

A slide-out panel accessible via the ⚙ button in the header. Set each property to `true` to enable that section.

```lua
ConfigPanel = {
    Enabled         = true,  -- shows the ⚙ button and enables the panel
    Acrylic         = true,  -- opacity slider (Modern only)
    Theme           = true,  -- theme picker (Modern only)
    Fps             = true,  -- FPS overlay toggle
    Ping            = true,  -- Ping overlay toggle
    Profile         = true,  -- player profile card toggle
    HideNotify      = true,  -- shows a notification when the window is hidden
    Language        = true,  -- language selector
    BackgroundImage = true,  -- background image controls (Modern only)
}
```

---

### 2.4 FloatButton

A draggable floating button that shows or hides the window. Useful on mobile or whenever you want a compact toggle.

```lua
FloatButton = {
    Shape = "Circle",           -- "Circle" or any other value (rounded square)
    Color = "Black",            -- "Black", "White", or "Translucent"
    Size  = 50,                 -- size in pixels (minimum 36)
    Icon  = "rbxassetid://...", -- optional image displayed on the button
}
```

A quick tap (without dragging) toggles the window's visibility.

---

### 2.5 Acrylic

Controls the background blur/transparency effect.

```lua
Acrylic = {
    Enabled = true,   -- enables the effect on open
    Opacity = 0.55,   -- 0 = fully transparent, 1 = fully opaque
}
```

Users can adjust the opacity live through the ConfigPanel.

---

### 2.6 BackgroundImage

Sets a background image or video for the window.

```lua
BackgroundImage = {
    Id     = "rbxassetid://XXXXXXX",  -- asset ID (image or video); use "Default" for the library default, or just the numeric ID
    Active = true,                     -- whether it's active on startup
}
```

Users can change the asset ID and toggle it on/off through the ConfigPanel when `BackgroundImage = true` is set there.

---

### 2.7 Window Methods

```lua
Window:GetContentFrame()  --> Frame           -- returns the tab content frame
Window:GetMainFrame()     --> Frame           -- returns the main window frame
Window:GetConfigPanel()   --> ScrollingFrame  -- returns the settings panel
Window:Notify(config)                         -- sends a notification
Window:Destroy()                              -- destroys the window completely
```

---

## 3. CreateTab

```lua
local Tab = Window:CreateTab(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Tab"` | Tab name shown in the sidebar |
| `Subtitle` | string | `""` | Optional subtitle below the name |
| `Icon` | string | `""` | Asset ID for the tab icon |
| `Double` | boolean | `false` | Two-column layout (see [Double Tab Layout](#12-double-tab-layout)) |

```lua
local Tab = Window:CreateTab({
    Title    = "Main",
    Subtitle = "Home",
    Icon     = "rbxassetid://XXXXXXX",
})
```

### 3.1 Tab Methods

```lua
Tab:GetPage()  --> ScrollingFrame  -- returns the tab's page frame
Tab:Select()                       -- selects this tab programmatically
```

---

## 4. Content Components

All content components are created inside a tab. Every component accepts a `Side` property (`1` or `2`) when the tab uses `Double = true`.

---

### 4.1 CreateSection

A visual header that groups components within a tab.

```lua
Tab:CreateSection(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Text` | string | `""` | Section label |
| `Icon` | string | `""` | Optional icon to the left of the text |
| `Side` | number | `1` | Column in a double-layout tab |

```lua
Tab:CreateSection({ Text = "Combat", Icon = "rbxassetid://..." })
```

---

### 4.2 CreateParagraph

A text block with a title and a body description.

```lua
local Para = Tab:CreateParagraph(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Info"` | Paragraph title |
| `Description` | string | `""` | Body text |
| `Icon` | string | `""` | Icon shown to the left (horizontal layout) |
| `ColoredWords` | table | `nil` | Colored words in the description (see [ColoredWords](#11-coloredwords--richtext)) |
| `TitleColoredWords` | table | `nil` | Colored words in the title |
| `DescriptionWords` | table | `nil` | Advanced rich-text format for the description |
| `Side` | number | `1` | Column in a double-layout tab |

```lua
Para:SetTitle("New Title")
Para:SetDescription("New description", wordColors)
Para:SetDescriptionWords(wordColors)
Para:GetDescriptionLabel()  --> TextLabel
Para:GetFrame()             --> Frame
```

---

### 4.3 CreateToggle

An on/off switch.

```lua
local Toggle = Tab:CreateToggle(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Toggle"` | Label |
| `Description` | string | `""` | Description below the title |
| `Icon` | string | `""` | Icon to the left |
| `Default` | boolean | `false` | Initial state |
| `Callback` | function | `nil` | `function(value: boolean)` called on change |
| `SaveId` | string | auto | Unique ID for AutoSave |
| `Side` | number | `1` | Column in a double-layout tab |

```lua
Toggle:Set(true)
Toggle:Get()              --> boolean
Toggle:GetFrame()         --> Frame
Toggle:SetTitle("Label")
Toggle:SetDescription("Desc")
```

```lua
local AutoAim = Tab:CreateToggle({
    Title    = "Auto Aim",
    Default  = false,
    Callback = function(val)
        print("Auto Aim:", val)
    end,
})
```

---

### 4.4 CreateSlider

A numerical slider. Users can also click the value label and type a number directly.

```lua
local Slider = Tab:CreateSlider(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Slider"` | Label |
| `Min` | number | `0` | Minimum value |
| `Max` | number | `100` | Maximum value |
| `Default` | number | `Min` | Initial value |
| `Callback` | function | `nil` | `function(value: number)` |
| `Side` | number | `1` | Column in a double-layout tab |

```lua
Slider:Set(50)
Slider:Get()      --> number
Slider:GetFrame() --> Frame
```

```lua
local FovSlider = Tab:CreateSlider({
    Title    = "Field of View",
    Min      = 30,
    Max      = 120,
    Default  = 70,
    Callback = function(val)
        workspace.Camera.FieldOfView = val
    end,
})
```

---

### 4.5 CreateButton

A clickable button with an optional title, description, and icon.

```lua
local Btn = Tab:CreateButton(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Button"` | Button text |
| `Description` | string | `""` | Description below the title |
| `Icon` | string | `""` | Icon to the left |
| `Callback` | function | `nil` | `function()` called on click |
| `Confirmation` | boolean | `false` | Shows a confirmation dialog before executing |
| `Side` | number | `1` | Column in a double-layout tab |

```lua
Btn:GetFrame()
Btn:SetTitle("New Text")
```

```lua
Tab:CreateButton({
    Title        = "Teleport to Lobby",
    Icon         = "rbxassetid://...",
    Confirmation = true,
    Callback     = function()
        -- your code here
    end,
})
```

---

### 4.6 CreateCheckBox

A checkbox with an animated checkmark.

```lua
local CB = Tab:CreateCheckBox(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"CheckBox"` | Label |
| `Description` | string | `""` | Description |
| `Default` | boolean | `false` | Initial state |
| `Confirmation` | boolean | `false` | Confirmation dialog on check |
| `Callback` | function | `nil` | `function(value: boolean)` |
| `SaveId` | string | auto | Unique ID for AutoSave |
| `Side` | number | `1` | Column in a double-layout tab |

```lua
CB:Set(true)
CB:Get()              --> boolean
CB:GetFrame()
CB:SetTitle("Label")
CB:SetDescription("Desc")
```

---

### 4.7 CreateDropdown

A dropdown menu with built-in search, optional multi-select, section dividers, per-option icons, per-option descriptions, and dynamic reloading.

```lua
local DD = Tab:CreateDropdown(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Dropdown"` | Label shown in the header |
| `Options` | table | `{}` | List of options (see formats below) |
| `Multiple` | boolean | `false` | Allows selecting multiple options at once |
| `Default` | any | `nil` | Default selection — a string, or a table if `Multiple = true` |
| `Icon` | string | `""` | Icon in the dropdown header (shown to the left of the title, tinted with the theme's `Accent` color) |
| `Callback` | function | `nil` | `function(value: string)` or `function(values: table)` when `Multiple = true` |
| `AutoReload` | function | `nil` | `function() return options` — called each time the menu opens to rebuild the list |
| `SaveId` | string | auto | Unique ID for AutoSave |
| `Side` | number | `1` | Column in a double-layout tab |

#### Header Icon

The root-level `Icon` field places an icon inside the closed dropdown header, to the left of the title. The title and current-selection label shift automatically to make room.

```lua
local DD = Tab:CreateDropdown({
    Title    = "Class",
    Icon     = "rbxassetid://XXXXXXX",
    Options  = { "Warrior", "Mage", "Archer" },
    Callback = function(val) end,
})
```

#### Per-Option Icons

Each option in table format accepts its own `Icon` field, shown inside the open menu to the left of the option text. The icon color reflects selection state:

- **Selected:** theme `AccentBright`
- **Unselected:** theme `TextSubtitle`

```lua
Options = {
    { Value = "Warrior", Icon = "rbxassetid://111111" },
    { Value = "Mage",    Icon = "rbxassetid://222222" },
}
```

#### Option Formats

Each entry in the `Options` table can be one of the following:

| Format | Fields | Description |
|---|---|---|
| `"string"` | — | Simple option; the string is both the value and the label |
| `{ Value, Icon }` | `Value` (string), `Icon` (asset ID) | Option with a per-item icon |
| `{ Value, Description }` | `Value` (string), `Description` (string) | Option with a description line (item height becomes 50px) |
| `{ Value, Icon, Description }` | all three | Option with both an icon and a description |
| `{ Section = true, Text }` | `Text` (string) | Visual section divider — not selectable, displayed in uppercase |

```lua
Options = {
    "Option A",

    { Value = "Sword",  Icon = "rbxassetid://111111" },
    { Value = "Bow",    Icon = "rbxassetid://222222", Description = "Long-range weapon" },
    { Value = "Magic",  Description = "Consumes mana" },

    { Section = true, Text = "Special Weapons" },

    { Value = "Spear",  Icon = "rbxassetid://333333" },
    "Axe",
}
```

> When `Description` is present, the item's height increases from 36px to 50px automatically.

#### Full Example — Header Icon + Per-Option Icons + Sections + Multi-Select

```lua
local WeaponDD = Tab:CreateDropdown({
    Title    = "Weapon Selection",
    Icon     = "rbxassetid://XXXXXXX",
    Multiple = true,
    Default  = { "Sword", "Bow" },
    Options  = {
        { Section = true, Text = "Melee" },
        { Value = "Sword", Icon = "rbxassetid://111111", Description = "High DPS" },
        { Value = "Axe",   Icon = "rbxassetid://222222", Description = "Area damage" },
        { Value = "Dagger",Icon = "rbxassetid://333333" },

        { Section = true, Text = "Ranged" },
        { Value = "Bow",      Icon = "rbxassetid://444444", Description = "Long range" },
        { Value = "Crossbow", Icon = "rbxassetid://555555" },

        { Section = true, Text = "Magic" },
        { Value = "Staff", Icon = "rbxassetid://666666", Description = "Consumes mana" },
        "Tome",
    },
    Callback = function(selected)
        for _, weapon in ipairs(selected) do
            print("Equipped:", weapon)
        end
    end,
})
```

#### Example with AutoReload

```lua
local PlayerDD = Tab:CreateDropdown({
    Title      = "Target Player",
    Icon       = "rbxassetid://XXXXXXX",
    AutoReload = function()
        local opts = {}
        for _, p in ipairs(game.Players:GetPlayers()) do
            table.insert(opts, {
                Value       = p.Name,
                Icon        = "rbxassetid://YYYYYYY",
                Description = "Ping: " .. math.floor(p:GetNetworkPing() * 1000) .. "ms",
            })
        end
        return opts
    end,
    Callback = function(name)
        print("Target:", name)
    end,
})
```

```lua
DD:Set("Sword")
DD:Set({"Sword", "Bow"})   -- multi-select
DD:Get()                   --> string or table
DD:Reload(newOptions)      -- replaces the option list and rebuilds the menu
DD:SetAutoReload(fn)
DD:Open()
DD:Close()
DD:GetFrame()
DD:SetTitle("New Title")
```

---

### 4.8 CreateValueDropdown

A dropdown where each option has its own editable numeric field. Good for things like per-ability damage or per-class speed values.

```lua
local VDD = Tab:CreateValueDropdown(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Dropdown"` | Label |
| `Options` | table | `{}` | Options as strings or `{Value, Default}` tables |
| `Min` | number | `0` | Minimum for all numeric fields |
| `Max` | number | `9999` | Maximum for all numeric fields |
| `Callback` | function | `nil` | `function(selectedKey: string, value: number)` |
| `Side` | number | `1` | Column in a double-layout tab |

```lua
Options = {
    "Sword",                              -- defaults to Min
    { Value = "Bow",   Default = 150 },
    { Value = "Magic", Default = 300 },
}
```

```lua
VDD:GetValues()              --> { key = number, ... }
VDD:GetValue("Sword")        --> number
VDD:GetSelected()            --> string
VDD:SetSelected("Bow")
VDD:SetValue("Sword", 120)
VDD:Open()
VDD:Close()
VDD:GetFrame()
VDD:SetTitle("Label")
```

```lua
local SpeedDD = Tab:CreateValueDropdown({
    Title    = "Speed by Class",
    Min      = 0,
    Max      = 500,
    Options  = {
        { Value = "Warrior", Default = 100 },
        { Value = "Archer",  Default = 150 },
        { Value = "Mage",    Default = 80  },
    },
    Callback = function(class, speed)
        print(class, "->", speed)
    end,
})
```

---

### 4.9 CreateTextBox

A text input field with a character counter and a focus animation.

```lua
local TB = Tab:CreateTextBox(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Text"` | Label |
| `Placeholder` | string | `"Type here..."` | Placeholder text |
| `MaxLength` | number | `100` | Character limit |
| `Default` | string | `""` | Initial value |
| `Callback` | function | `nil` | `function(text: string)` called on focus lost |
| `Side` | number | `1` | Column in a double-layout tab |

The character counter turns yellow above 60% capacity and red above 85%.

```lua
TB:Get()                 --> string
TB:Set("new text")
TB:GetFrame()
TB:SetTitle("Label")
TB:SetPlaceholder("Enter...")
```

---

### 4.10 CreateKeyBind

A hotkey picker. The user clicks the field and presses a key to assign it. Pressing ESC cancels.

```lua
local KB = Tab:CreateKeyBind(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"KeyBind"` | Label |
| `Default` | KeyCode \| table | `Enum.KeyCode.LeftAlt` | Default key (can be `{Enum.KeyCode.X}`) |
| `Callback` | function | `nil` | `function(keys: table)` e.g. `{Enum.KeyCode.F}` |
| `Side` | number | `1` | Column in a double-layout tab |

```lua
KB:Get()               --> { Enum.KeyCode.X }
KB:Set(Enum.KeyCode.G)
KB:GetFrame()
KB:SetTitle("Label")
```

```lua
local HotKey = Tab:CreateKeyBind({
    Title    = "Toggle ESP",
    Default  = Enum.KeyCode.H,
    Callback = function(keys)
        print("Key:", keys[1])
    end,
})
```

---

### 4.11 CreateColorPicker

A full HSV color picker with a hue bar, live preview, and readouts in Hex, RGB, HSL, and OKLCH.

```lua
local CP = Tab:CreateColorPicker(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Color"` | Label |
| `Default` | Color3 | `Color3.fromRGB(255, 65, 65)` | Initial color |
| `Callback` | function | `nil` | `function(color: Color3)` called when the user clicks Apply |
| `Side` | number | `1` | Column in a double-layout tab |

```lua
CP:Get()                        --> Color3 (last applied value)
CP:Set(Color3.fromRGB(0,255,0))
CP:GetFrame()
CP:SetTitle("Label")
```

Closing the panel without clicking **Apply** does not change the stored value.

---

### 4.12 CreateDiscordInvite

A Discord server invite card with a live online member count (fetched via the Discord API), a copy-link button, and optional banner/icon images.

```lua
local DC = Tab:CreateDiscordInvite(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Discord Server"` | Server name |
| `Description` | string | `""` | Short description |
| `Icon` | string | `""` | Asset ID for the server icon |
| `Banner` | string | `""` | Asset ID for the banner image |
| `Link` | string | `""` | Full invite link or invite code (e.g. `"discord.gg/abc"`) |
| `Button` | string | `"Join Server"` | Action button text |
| `Side` | number | `1` | Column in a double-layout tab |

Clicking the button copies the link to the clipboard. Online/total member counts refresh automatically every 5 seconds.

```lua
DC:GetFrame()
DC:SetTitle("Label")
```

---

### 4.13 CreateSeparatorLine

A simple horizontal divider line inside a tab's content.

```lua
Tab:CreateSeparatorLine({ Side = 1 })
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Side` | number | `1` | Column in a double-layout tab |

---

## 5. Sidebar Components

These components are created directly on the `Window`, not inside a tab.

### 5.1 CreateSeparator

A category label in the sidebar, placed between tab entries.

```lua
Window:CreateSeparator(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Text` | string | `""` | Label text (blank produces empty whitespace) |

```lua
Window:CreateSeparator({ Text = "COMBAT" })
local TabA = Window:CreateTab({ Title = "ESP" })
Window:CreateSeparator({ Text = "MISC" })
local TabB = Window:CreateTab({ Title = "Teleport" })
```

---

### 5.2 CreateSidebarLine

A thin horizontal line in the sidebar for visual separation between tab groups.

```lua
Window:CreateSidebarLine()
```

No parameters.

---

## 6. Notifications

Animated notifications that stack in the bottom-right corner of the screen.

```lua
Window:Notify(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Notification"` | Notification title |
| `Description` / `Text` | string | `""` | Body text (optional) |
| `Icon` | string | `"rbxassetid://..."` | Icon shown to the left |
| `Duration` | number | `4` | Display time in seconds (minimum 0.5) |
| `RichText` | boolean | `false` | Enables RichText in the description |
| `TitleColoredWords` | table | `nil` | Colored words in the title |
| `ColoredWords` | table | `nil` | Colored words in the description |
| `TitleWords` | table | `nil` | Advanced rich-text format for the title |
| `TextWords` | table | `nil` | Advanced rich-text format for the description |

```lua
-- Simple
Window:Notify({
    Title       = "Success!",
    Description = "Operation complete.",
    Duration    = 3,
})

-- With RichText
Window:Notify({
    Title       = "Warning",
    Description = 'Press <font color="#FF5555">ESC</font> to cancel.',
    RichText    = true,
    Duration    = 5,
})

-- With ColoredWords
Window:Notify({
    Title        = "Info",
    Description  = "Welcome to ProxyLib!",
    ColoredWords = {
        { Text = "ProxyLib", Colors = { Color3.fromRGB(100, 200, 255) } },
    },
})
```

Notifications sent before the window finishes loading are queued and shown in order once it's ready.

---

## 7. CreateKeySystem

An authentication screen shown before the main UI. The user enters a key, and your code decides whether to accept or reject it.

```lua
local KS = Lib:CreateKeySystem(config)
```

### 7.1 KeySystem Options

| Property | Type | Default | Description |
|---|---|---|---|
| `Title` | string | `"Key System"` | Title shown in the header |
| `Icon` | string | `""` | Asset ID for the header icon |
| `Theme` | string | `"Blue"` | Color theme |
| `Size` | Vector2 | `Vector2.new(420, 265)` | Card size |
| `BackgroundColor` | Color3 | `nil` | Overrides the background color |
| `Acrylic` | table | `{}` | `{ Enabled, Opacity }` acrylic effect config |

```lua
local KS = Lib:CreateKeySystem({
    Title = "Key Verification",
    Theme = "Green",
    Size  = Vector2.new(440, 280),
})
```

### 7.2 KeySystem Methods

```lua
KS:GetTextBox()        -- returns the input TextBox
KS:GetText()           -- returns the current input string
KS:SetText("key")      -- sets the input text
KS:Notify(config)      -- same notification format as Window:Notify
KS:Destroy()           -- closes the Key System with an animation
```

### 7.3 CreateButton (KeySystem)

Action buttons in the Key System, laid out in a 2-column grid.

```lua
local Btn = KS:CreateButton(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Description` | string | `"Button"` | Button text |
| `Icon` | string | `""` | Optional icon |
| `Callback` | function | `nil` | `function()` |

```lua
Btn:GetFrame()
Btn:SetDescription("New Text")
```

```lua
KS:CreateButton({
    Description = "Verify Key",
    Icon        = "rbxassetid://...",
    Callback    = function()
        if KS:GetText() == "MY-KEY-123" then
            KS:Destroy()
            -- load the main hub
        else
            KS:Notify({ Title = "Invalid key!", Duration = 3 })
        end
    end,
})
```

### 7.4 CreateSocialButton

Social link buttons shown below the main action buttons. Clicking copies the link.

```lua
KS:CreateSocialButton(config)
```

| Property | Type | Default | Description |
|---|---|---|---|
| `Type` | string | `"Discord"` | `"Discord"`, `"Youtube"`, or `"Website"` |
| `Link` | string | `""` | URL to copy on click |
| `Order` | number | `0` | Display order (lower = first) |

```lua
KS:CreateSocialButton({ Type = "Discord", Link = "https://discord.gg/abc", Order = 1 })
KS:CreateSocialButton({ Type = "Youtube", Link = "https://youtube.com/...", Order = 2 })
KS:CreateSocialButton({ Type = "Website", Link = "https://mysite.com",     Order = 3 })
```

---

## 8. Themes

Built-in themes available for the `Theme` property:

| Name | Description |
|---|---|
| `"Blue"` | Blue (default) |
| `"Red"` | Red |
| `"Green"` | Green |
| `"Purple"` | Purple |
| `"Pink"` | Pink |
| `"Yellow"` | Yellow |
| `"White"` | White |
| `"Grey"` | Grey |
| `"Custom"` | User-defined color (set through the ConfigPanel) |

You can also pass a `Color3` directly:

```lua
Theme = Color3.fromRGB(0, 180, 120),
```

When a `Color3` is provided, the library automatically generates the `AccentBright`, `AccentDark`, `AccentDeep`, and `AccentGlow` variants from it.

---

## 9. Languages

Languages with built-in translations for all internal UI text:

| Code | Language |
|---|---|
| `"English"` | English (default) |
| `"Portuguese"` | Portuguese |
| `"Vietnamese"` | Vietnamese |

For other languages, the library attempts automatic translation via the Google Translate / MyMemory API, which requires HttpGet to be enabled in the executor.

```lua
Language = "Portuguese",
```

Component text created by the developer (tab titles, toggle labels, etc.) is also translated automatically when the selected language isn't English, using a local cache to avoid redundant requests.

---

## 10. AutoSave / AutoLoad

When `AutoSave = true` (the default), the library saves the following to `ProxyLib_Cfg.json`:

- Selected theme
- Acrylic state and opacity
- FPS and Ping overlay states
- Profile card visibility
- Background image state
- Values of all components that have a `SaveId`

When `AutoLoad = true` (the default), these values are restored on startup.

To assign a stable save key to a component, set its `SaveId`:

```lua
Tab:CreateToggle({
    Title    = "ESP",
    SaveId   = "esp_toggle",
    Callback = function(v) end,
})
```

If `SaveId` isn't set, the library generates one automatically from the tab name and component title.

---

## 11. ColoredWords / RichText

A system for coloring specific words inside component text, supporting both solid colors and gradients.

```lua
ColoredWords = {
    {
        Text   = "ProxyLib",
        Colors = { Color3.fromRGB(100, 200, 255) },  -- solid color
    },
    {
        Text     = "Premium",
        Colors   = {
            Color3.fromRGB(255, 200, 0),
            Color3.fromRGB(255, 100, 0),
        },
        Gradient = true,
    },
}
```

```lua
Tab:CreateParagraph({
    Title       = "Welcome to ProxyLib Premium",
    Description = "Enjoy all features with your Premium license.",
    ColoredWords = {
        { Text = "ProxyLib", Colors = { Color3.fromRGB(80, 180, 255) } },
        { Text = "Premium",  Colors = { Color3.fromRGB(255,200,0), Color3.fromRGB(255,100,0) }, Gradient = true },
    },
})
```

For more granular control, `DescriptionWords` and `TextWords` accept a mixed array of plain strings and colored word tables:

```lua
DescriptionWords = {
    "Normal text ",
    { Text = "colored", Colors = { Color3.fromRGB(100, 255, 100) } },
    " more normal text.",
}
```

---

## 12. Double Tab Layout

Setting `Double = true` when creating a tab splits its content area into two independent columns with a divider between them.

```lua
local Tab = Window:CreateTab({ Title = "Settings", Double = true })
```

Every component inside a double tab accepts `Side = 1` (left column) or `Side = 2` (right column):

```lua
Tab:CreateSection({ Text = "Visual",   Side = 1 })
Tab:CreateSection({ Text = "Gameplay", Side = 2 })

Tab:CreateToggle({ Title = "ESP",    Side = 1, Callback = function(v) end })
Tab:CreateToggle({ Title = "Aimbot", Side = 2, Callback = function(v) end })

Tab:CreateSlider({ Title = "Speed",    Min = 0, Max = 100, Side = 1, Callback = function(v) end })
Tab:CreateDropdown({ Title = "Mode",   Options = {"A","B"}, Side = 2, Callback = function(v) end })
```

Each column scrolls independently — the mouse wheel only scrolls whichever column the cursor is hovering over.

---

## 13. Full Examples

### Hub with Key System

```lua
local ProxyLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/ProxyHubDev/ProxyLib/refs/heads/main/Documents/ProxyLibrary"))()
local Lib = ProxyLib.new()

local KS = Lib:CreateKeySystem({
    Title = "Authentication",
    Theme = "Blue",
})

KS:CreateSocialButton({ Type = "Discord", Link = "https://discord.gg/example", Order = 1 })

KS:CreateButton({
    Description = "Verify",
    Callback    = function()
        if KS:GetText() == "VALID-KEY" then
            KS:Destroy()

            local Window = Lib:CreateWindow({
                Title    = "My Hub",
                Subtitle = "v2.0",
                Theme    = "Blue",
                Size     = Vector2.new(560, 420),
                ConfigPanel = {
                    Enabled = true,
                    Theme   = true,
                    Fps     = true,
                    Ping    = true,
                    Profile = true,
                },
                TitleConfig = {
                    Gradient = true,
                    Words    = {
                        "My",
                        { Text = "Hub", Colors = { Color3.fromRGB(100,200,255), Color3.fromRGB(50,100,255) } },
                    },
                },
            })

            Window:CreateSeparator({ Text = "MAIN" })
            local TabMain = Window:CreateTab({ Title = "Home", Icon = "rbxassetid://..." })

            TabMain:CreateSection({ Text = "Welcome" })
            TabMain:CreateParagraph({
                Title       = "My Hub Premium",
                Description = "Use features responsibly.",
            })

            TabMain:CreateToggle({
                Title    = "ESP",
                Default  = false,
                Callback = function(v) print("ESP:", v) end,
            })

            TabMain:CreateSlider({
                Title    = "Walk Speed",
                Min      = 0,
                Max      = 50,
                Default  = 16,
                Callback = function(v)
                    game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = v
                end,
            })

            Window:Notify({
                Title       = "Welcome!",
                Description = "Hub loaded successfully.",
                Duration    = 4,
            })
        else
            KS:Notify({ Title = "Invalid key!", Duration = 3 })
        end
    end,
})
```

### Double Tab

```lua
local Tab = Window:CreateTab({ Title = "Config", Double = true })

Tab:CreateSection({ Text = "Visual",    Side = 1 })
Tab:CreateSection({ Text = "Movement",  Side = 2 })

Tab:CreateToggle({ Title = "Player ESP", Side = 1, Callback = function(v) end })
Tab:CreateToggle({ Title = "Item ESP",   Side = 1, Callback = function(v) end })
Tab:CreateToggle({ Title = "Speed Hack", Side = 2, Callback = function(v) end })

Tab:CreateSlider({ Title = "Speed", Min = 0, Max = 100, Default = 16, Side = 2,
    Callback = function(v) end })

Tab:CreateDropdown({ Title = "ESP Mode", Options = {"Box","Skeleton","Filled"},
    Side = 1, Callback = function(v) end })
```

### ValueDropdown

```lua
local Tab = Window:CreateTab({ Title = "Abilities" })

local VDD = Tab:CreateValueDropdown({
    Title    = "Damage per Ability",
    Min      = 0,
    Max      = 9999,
    Options  = {
        { Value = "Fireball",  Default = 150 },
        { Value = "Lightning", Default = 300 },
        { Value = "Heal",      Default = 0   },
    },
    Callback = function(ability, damage)
        print(ability, "will deal", damage, "damage")
    end,
})

print(VDD:GetValues())         -- { ["Fireball"]=150, ["Lightning"]=300, ["Heal"]=0 }
print(VDD:GetSelected())       -- "Fireball"
VDD:SetValue("Lightning", 500)
```

### ColorPicker + KeyBind

```lua
local Tab = Window:CreateTab({ Title = "Visual" })

local CP = Tab:CreateColorPicker({
    Title    = "ESP Color",
    Default  = Color3.fromRGB(255, 0, 0),
    Callback = function(color)
        -- apply color to ESP
    end,
})

local KB = Tab:CreateKeyBind({
    Title    = "Toggle ESP",
    Default  = Enum.KeyCode.Z,
    Callback = function(keys)
        print("Key set to:", keys[1])
    end,
})
```
