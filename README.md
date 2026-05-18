# 📚 ProxyLib — Complete Documentation

## 🔗 ProxyLibrary
- **Discord:** https://discord.gg/GMAFx8NxdK

> **Made By:** Zerozxk (@fixedbugs) & Araujo (@araujozwx)

---

## 📑 Table of Contents

- [Initialization](#-initialization)
- [CreateWindow](#-createwindow)
  - [Window Options](#window-options)
  - [ConfigPanel](#configpanel)
  - [TitleConfig](#titleconfig)
  - [FloatButton](#floatbutton)
  - [Acrylic](#acrylic)
  - [BackgroundImage](#backgroundimage)
- [Notify](#-notify)
- [CreateTab](#-createtab)
- [Tab Elements](#-tab-elements)
  - [CreateSection](#createsection)
  - [CreateSeparatorLine](#createseparatorline)
  - [CreateParagraph](#createparagraph)
  - [CreateToggle](#createtoggle)
  - [CreateCheckBox](#createcheckbox)
  - [CreateSlider](#createslider)
  - [CreateButton](#createbutton)
  - [CreateTextBox](#createtextbox)
  - [CreateDropdown](#createdropdown)
  - [CreateValueDropdown](#createvaluedropdown)
  - [CreateDiscordInvite](#creatediscordinvite)
- [Sidebar Elements](#-sidebar-elements)
  - [CreateSeparator](#createseparator)
  - [CreateSidebarLine](#createsidebarline)
- [CreateKeySystem](#-createkeysystem)
  - [KeySystem CreateButton](#keysystem-createbutton)
  - [KeySystem CreateSocialButton](#keysystem-createsocialbutton)
  - [KeySystem Notify](#keysystem-notify)
- [Window Methods](#-window-methods)
- [Themes](#-themes)
- [Languages](#-languages)
- [RichText & Colored Words](#-richtext--colored-words)
- [Full Example](#-full-example)

---

## 🚀 Initialization

```lua
local ProxyLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/ProxyHubDev/ProxyLib/refs/heads/main/Documents/ProxyLibrary"))()

local Library = ProxyLib.new()
```

---

## 🪟 CreateWindow

```lua
local Window = Library:CreateWindow({
    Title    = "My Hub",
    Subtitle = "v1.0",
    Icon     = "rbxassetid://0",
    Size     = Vector2.new(520, 380),
    MinSize  = Vector2.new(380, 250),
    MaxSize  = Vector2.new(900, 650),
    TypeUI   = "Modern",
    Theme    = "Blue",
    Language = "English",
    AutoSave = true,
    AutoLoad = true,

    Acrylic = {
        Enabled = true,
        Opacity = 0.55,
    },

    BackgroundImage = {
        Id     = "rbxassetid://000000000",
        Active = false,
    },

    TitleConfig = {
        Gradient = true,
        Colors   = { Color3.fromRGB(100, 180, 255), Color3.fromRGB(50, 100, 200) },
        Words    = {
            { Text = "My",  Colors = { Color3.fromRGB(255, 255, 255) } },
            { Text = "Hub", Colors = { Color3.fromRGB(35, 85, 170), Color3.fromRGB(55, 110, 200) } },
        },
    },

    FloatButton = {
        Shape = "Circle",
        Color = "Black",
        Size  = 50,
        Icon  = "rbxassetid://0",
    },

    ConfigPanel = {
        Enabled         = true,
        Acrylic         = true,
        Theme           = true,
        Fps             = true,
        Ping            = true,
        Profile         = true,
        HideNotify      = true,
        Language        = true,
        BackgroundImage = true,
    },
})
```

### Window Options

| Option | Type | Default | Description |
|---|---|---|---|
| `Title` | `string` | `"ProxyLib"` | Window title text |
| `Subtitle` | `string` | `""` | Subtitle shown below the title |
| `Icon` | `string` | `""` | Asset ID for the window icon |
| `Size` | `Vector2` | `Vector2.new(520, 380)` | Initial window size |
| `MinSize` | `Vector2` | `Vector2.new(380, 250)` | Minimum resize limit |
| `MaxSize` | `Vector2` | `Vector2.new(900, 650)` | Maximum resize limit |
| `TypeUI` | `string` | `"Modern"` | UI style: `"Modern"` or `"Classic"` |
| `Theme` | `string \| Color3` | `"Blue"` | Accent theme name or custom Color3 |
| `Language` | `string` | `"English"` | Default UI language |
| `AutoSave` | `boolean` | `true` | Auto-save config to file |
| `AutoLoad` | `boolean` | `true` | Auto-load config from file |

### ConfigPanel

Controls which settings appear in the gear (⚙) panel.

| Option | Type | Description |
|---|---|---|
| `Enabled` | `boolean` | Show the config button at all |
| `Acrylic` | `boolean` | Show the acrylic/opacity toggle |
| `Theme` | `boolean` | Show the theme picker |
| `Fps` | `boolean` | Show the FPS overlay toggle |
| `Ping` | `boolean` | Show the ping overlay toggle |
| `Profile` | `boolean` | Show the player profile card toggle |
| `HideNotify` | `boolean` | Show a notification when the window is hidden |
| `Language` | `boolean` | Show the language picker |
| `BackgroundImage` | `boolean` | Show the background image toggle and ID input |

### TitleConfig

Controls how the title text is styled.

| Option | Type | Description |
|---|---|---|
| `Gradient` | `boolean` | Enable gradient coloring on special words |
| `Colors` | `{Color3}` | Global gradient colors applied to all special words |
| `Words` | `{table}` | Per-word color config. Each entry: `{ Text = "Word", Colors = { Color3 } }` |

### FloatButton

A draggable floating button that shows/hides the window (also works on mobile).

| Option | Type | Description |
|---|---|---|
| `Shape` | `string` | `"Circle"` or `"Square"` |
| `Color` | `string` | `"Black"`, `"White"`, or `"Translucent"` |
| `Size` | `number` | Button size in pixels (minimum 36) |
| `Icon` | `string` | Asset ID for the button icon image |

### Acrylic

| Option | Type | Description |
|---|---|---|
| `Enabled` | `boolean` | Start with acrylic/blur transparency active |
| `Opacity` | `number` | Opacity from `0.0` (fully transparent) to `1.0` (solid) |

### BackgroundImage

| Option | Type | Description |
|---|---|---|
| `Id` | `string` | Asset ID (`"rbxassetid://..."`) or `"Default"` for the built-in image |
| `Active` | `boolean` | Whether the background image starts enabled |

---

## 🔔 Notify

Displays a toast notification on screen.

```lua
-- Basic
Window:Notify({
    Title    = "Hello!",
    Text     = "This is a notification.",
    Icon     = "rbxassetid://124914698428562",
    Duration = 4,
})

-- With colored words in the body
Window:Notify({
    Title    = "Update",
    Text     = "Version 2.0 is now available!",
    Duration = 5,
    ColoredWords = {
        { Text = "2.0", Colors = { Color3.fromRGB(100, 220, 100) } },
    },
})

-- With gradient colored words in the title
Window:Notify({
    Title = "Rainbow",
    TitleColoredWords = {
        {
            Text     = "Rainbow",
            Colors   = { Color3.fromRGB(255, 80, 80), Color3.fromRGB(80, 80, 255) },
            Gradient = true,
        },
    },
    Text     = "Gradient title example.",
    Duration = 4,
})

-- Using word builders (TitleWords / TextWords)
Window:Notify({
    TitleWords = {
        "Hello ",
        { Text = "World", Colors = { Color3.fromRGB(255, 200, 0) } },
    },
    TextWords = {
        "Status: ",
        { Text = "Online", Colors = { Color3.fromRGB(80, 220, 80) } },
    },
    Duration = 5,
})
```

| Option | Type | Description |
|---|---|---|
| `Title` | `string` | Notification title |
| `Text` / `Description` | `string` | Body text |
| `Icon` | `string` | Asset ID for the icon |
| `Duration` | `number` | How long (seconds) before it fades out |
| `RichText` | `boolean` | Enable RichText on the body text |
| `ColoredWords` | `{table}` | Color specific words in the body text |
| `TitleColoredWords` | `{table}` | Color specific words in the title |
| `TitleWords` | `{table}` | Full word-builder for the title |
| `TextWords` | `{table}` | Full word-builder for the body text |

---

## 📂 CreateTab

```lua
local Tab = Window:CreateTab({
    Title    = "Main",
    Subtitle = "General",
    Icon     = "rbxassetid://0",
})
```

| Option | Type | Description |
|---|---|---|
| `Title` | `string` | Tab label |
| `Subtitle` | `string` | Small subtitle below the label |
| `Icon` | `string` | Asset ID for the tab icon |

**Methods:**

```lua
Tab:Select()    -- Programmatically select this tab
Tab:GetPage()   -- Returns the internal ScrollingFrame page
```

---

## 🧩 Tab Elements

### CreateSection

A visual section header to group elements.

```lua
-- Text only
Tab:CreateSection({
    Text = "Combat Settings",
})

-- With an icon
Tab:CreateSection({
    Text = "Combat Settings",
    Icon = "rbxassetid://0",
})
```

| Option | Type | Description |
|---|---|---|
| `Text` | `string` | Section label |
| `Icon` | `string` | Optional icon. When set, replaces the accent bar with an image |

---

### CreateSeparatorLine

A thin horizontal line to visually divide content inside a tab page.

```lua
Tab:CreateSeparatorLine()
```

No configuration options.

---

### CreateParagraph

An info block with a title and a description body.

```lua
-- Basic
local Para = Tab:CreateParagraph({
    Title       = "About",
    Description = "This is some info text.",
})

-- With icon
local Para = Tab:CreateParagraph({
    Title       = "Info",
    Icon        = "rbxassetid://0",
    Description = "Text here.",
})

-- Colored words in description
local Para = Tab:CreateParagraph({
    Title       = "Status",
    Description = "The script is running fine.",
    ColoredWords = {
        { Text = "running", Colors = { Color3.fromRGB(80, 220, 80) } },
    },
})

-- Gradient colored words in description
local Para = Tab:CreateParagraph({
    Title       = "Gradient",
    Description = "Hello World!",
    ColoredWords = {
        {
            Text     = "Hello World!",
            Colors   = { Color3.fromRGB(255, 100, 100), Color3.fromRGB(100, 100, 255) },
            Gradient = true,
        },
    },
})

-- Colored title
local Para = Tab:CreateParagraph({
    Title = "Warning",
    TitleColoredWords = {
        { Text = "Warning", Colors = { Color3.fromRGB(255, 180, 0) } },
    },
    Description = "This is a warning message.",
})

-- Word builder for description
local Para = Tab:CreateParagraph({
    Title = "Info",
    DescriptionWords = {
        "Status: ",
        { Text = "Active", Colors = { Color3.fromRGB(80, 220, 80) } },
        " — All systems nominal.",
    },
})
```

| Option | Type | Description |
|---|---|---|
| `Title` | `string` | Paragraph heading |
| `Description` | `string` | Body text |
| `Icon` | `string` | Optional icon asset ID |
| `ColoredWords` | `{table}` | Color/gradient specific words in the description |
| `TitleColoredWords` | `{table}` | Color/gradient specific words in the title |
| `DescriptionWords` | `{table}` | Full word-builder for the description |

**Methods:**

```lua
Para:SetTitle("New Title")
Para:SetDescription("New description text.")
Para:SetDescriptionWords({
    "Status: ",
    { Text = "OK", Colors = { Color3.fromRGB(0, 255, 0) } },
})
Para:GetDescriptionLabel()  -- Returns the TextLabel instance
Para:GetFrame()
```

---

### CreateToggle

An on/off switch.

```lua
-- Basic
local Toggle = Tab:CreateToggle({
    Title    = "Enable Feature",
    Default  = false,
    Callback = function(state)
        print("Toggle:", state)
    end,
})

-- With description and icon
local Toggle = Tab:CreateToggle({
    Title       = "Enable Feature",
    Description = "Turns the feature on or off.",
    Icon        = "rbxassetid://0",
    Default     = false,
    SaveId      = "my_toggle",
    Callback    = function(state)
        print("Toggle:", state)
    end,
})
```

| Option | Type | Default | Description |
|---|---|---|---|
| `Title` | `string` | `"Toggle"` | Label text |
| `Description` | `string` | `""` | Optional subtitle |
| `Icon` | `string` | `""` | Optional icon asset ID |
| `Default` | `boolean` | `false` | Initial state |
| `SaveId` | `string` | auto-generated | Key used for auto-save/load |
| `Callback` | `function(bool)` | — | Called when state changes |

**Methods:**

```lua
Toggle:Set(true)
Toggle:Get()               -- Returns current boolean
Toggle:SetTitle("New Label")
Toggle:SetDescription("New description.")
Toggle:GetFrame()
```

---

### CreateCheckBox

A checkbox with a check mark animation. Functionally identical to Toggle but with a box visual.

```lua
-- Basic
local Check = Tab:CreateCheckBox({
    Title    = "Accept Terms",
    Default  = false,
    Callback = function(state)
        print("Checked:", state)
    end,
})

-- With description and confirmation dialog
local Check = Tab:CreateCheckBox({
    Title        = "Enable PvP",
    Description  = "Activates PvP mode.",
    Default      = false,
    Confirmation = true,
    SaveId       = "my_checkbox",
    Callback     = function(state)
        print("CheckBox:", state)
    end,
})
```

| Option | Type | Default | Description |
|---|---|---|---|
| `Title` | `string` | `"CheckBox"` | Label text |
| `Description` | `string` | `""` | Optional subtitle |
| `Default` | `boolean` | `false` | Initial checked state |
| `Confirmation` | `boolean` | `false` | Show a confirm dialog before checking |
| `SaveId` | `string` | auto-generated | Key used for auto-save/load |
| `Callback` | `function(bool)` | — | Called when state changes |

**Methods:**

```lua
Check:Set(true)
Check:Get()
Check:SetTitle("New Label")
Check:SetDescription("New description.")
Check:GetFrame()
```

---

### CreateSlider

A draggable slider with a numeric input box.

```lua
-- Basic
local Slider = Tab:CreateSlider({
    Title    = "Speed",
    Min      = 0,
    Max      = 100,
    Default  = 16,
    Callback = function(value)
        game:GetService("Players").LocalPlayer.Character.Humanoid.WalkSpeed = value
    end,
})
```

| Option | Type | Default | Description |
|---|---|---|---|
| `Title` | `string` | `"Slider"` | Label text |
| `Min` | `number` | `0` | Minimum value |
| `Max` | `number` | `100` | Maximum value |
| `Default` | `number` | `Min` | Initial value |
| `Callback` | `function(number)` | — | Called on value change |

**Methods:**

```lua
Slider:Set(75)
Slider:Get()       -- Returns current number
Slider:GetFrame()
```

---

### CreateButton

A clickable button with an optional confirmation dialog.

```lua
-- Basic
local Button = Tab:CreateButton({
    Title    = "Teleport",
    Callback = function()
        print("Clicked!")
    end,
})

-- With description, custom icon and confirmation
local Button = Tab:CreateButton({
    Title        = "Delete Data",
    Description  = "This action cannot be undone.",
    Icon         = "rbxassetid://88732835297181",
    Confirmation = true,
    Callback     = function()
        print("Confirmed and executed.")
    end,
})
```

| Option | Type | Default | Description |
|---|---|---|---|
| `Title` | `string` | `"Button"` | Label text |
| `Description` | `string` | `""` | Optional description below the title (supports RichText) |
| `Icon` | `string` | arrow icon | Asset ID for the right-side icon |
| `Confirmation` | `boolean` | `false` | Show a confirm dialog before firing the callback |
| `Callback` | `function()` | — | Called on click |

**Methods:**

```lua
Button:SetTitle("New Label")
Button:GetFrame()
```

---

### CreateTextBox

A single-line text input field.

```lua
-- Basic
local TextBox = Tab:CreateTextBox({
    Title    = "Username",
    Callback = function(text)
        print("Submitted:", text)
    end,
})

-- Full options
local TextBox = Tab:CreateTextBox({
    Title       = "Username",
    Placeholder = "Enter your username...",
    Default     = "",
    MaxLength   = 50,
    Callback    = function(text)
        print("Text:", text)
    end,
})
```

| Option | Type | Default | Description |
|---|---|---|---|
| `Title` | `string` | `"Text"` | Label above the input |
| `Placeholder` | `string` | `"Type here..."` | Placeholder text |
| `Default` | `string` | `""` | Initial text value |
| `MaxLength` | `number` | `100` | Maximum character count |
| `Callback` | `function(string)` | — | Called when the input loses focus |

**Methods:**

```lua
TextBox:Get()
TextBox:Set("hello")          -- Fires callback
TextBox:SetTitle("Label")
TextBox:SetPlaceholder("New placeholder...")
TextBox:GetFrame()
```

---

### CreateDropdown

A dropdown list supporting single or multi-selection, section headers, descriptions per option, and auto-reload.

```lua
-- Single selection
local Dropdown = Tab:CreateDropdown({
    Title    = "Weapon",
    Options  = { "Sword", "Bow", "Staff" },
    Default  = "Sword",
    Callback = function(selected)
        print("Selected:", selected)
    end,
})

-- Multi selection
local Dropdown = Tab:CreateDropdown({
    Title    = "Modes",
    Options  = { "PvP", "PvE", "Farm" },
    Multiple = true,
    Default  = { "PvP", "Farm" },
    Callback = function(selected)
        print(table.concat(selected, ", "))
    end,
})

-- Options with descriptions
local Dropdown = Tab:CreateDropdown({
    Title   = "Class",
    Options = {
        { Value = "Warrior", Description = "High HP and defense." },
        { Value = "Mage",    Description = "Strong area spells."  },
        { Value = "Rogue",   Description = "Fast and stealthy."   },
    },
    Callback = function(selected)
        print(selected)
    end,
})

-- Options with section headers
local Dropdown = Tab:CreateDropdown({
    Title   = "Items",
    Options = {
        { Section = true, Text = "Weapons" },
        "Sword",
        "Axe",
        { Section = true, Text = "Armor" },
        "Shield",
        "Helmet",
    },
    Callback = function(selected)
        print(selected)
    end,
})

-- Auto-reload options every time the dropdown opens
local Dropdown = Tab:CreateDropdown({
    Title      = "Players",
    Options    = {},
    AutoReload = function()
        local list = {}
        for _, p in ipairs(game:GetService("Players"):GetPlayers()) do
            table.insert(list, p.Name)
        end
        return list
    end,
    Callback = function(selected)
        print(selected)
    end,
})
```

| Option | Type | Default | Description |
|---|---|---|---|
| `Title` | `string` | `"Dropdown"` | Label text |
| `Options` | `{string \| table}` | `{}` | List of options |
| `Multiple` | `boolean` | `false` | Allow multiple selections |
| `Default` | `string \| {string}` | `nil` | Pre-selected option(s) |
| `AutoReload` | `function()` | `nil` | Called when the dropdown opens; return a new options table |
| `SaveId` | `string` | auto-generated | Key for auto-save/load |
| `Callback` | `function` | — | `function(string)` or `function(table)` when `Multiple = true` |

**Methods:**

```lua
Dropdown:Get()                    -- Returns selected (string or table)
Dropdown:Set("Sword")
Dropdown:Set({ "PvP", "PvE" })   -- Multi-select
Dropdown:Reload(newOptionsTable)  -- Rebuild the options list
Dropdown:SetAutoReload(function() return {...} end)
Dropdown:Open()
Dropdown:Close()
Dropdown:SetTitle("New Label")
Dropdown:GetFrame()
```

---

### CreateValueDropdown

A dropdown where each option has an associated editable numeric value.

```lua
local ValDrop = Tab:CreateValueDropdown({
    Title   = "Damage Settings",
    Min     = 0,
    Max     = 1000,
    Options = {
        { Value = "Sword", Default = 150 },
        { Value = "Bow",   Default = 80  },
        { Value = "Staff", Default = 220 },
    },
    Callback = function(selectedKey, numericValue)
        print("Key:", selectedKey, "| Value:", numericValue)
    end,
})
```

| Option | Type | Default | Description |
|---|---|---|---|
| `Title` | `string` | `"Dropdown"` | Label text |
| `Options` | `{table}` | `{}` | Each entry: `{ Value = "Name", Default = number }` |
| `Min` | `number` | `0` | Minimum numeric value |
| `Max` | `number` | `9999` | Maximum numeric value |
| `Callback` | `function(string, number)` | — | Called when the selection or a value changes |

**Methods:**

```lua
ValDrop:GetSelected()           -- Returns selected key (string)
ValDrop:GetValues()             -- Returns table { key = number, ... }
ValDrop:GetValue("Sword")       -- Returns the number for a specific key
ValDrop:SetSelected("Bow")
ValDrop:SetValue("Sword", 300)
ValDrop:Open()
ValDrop:Close()
ValDrop:SetTitle("New Label")
ValDrop:GetFrame()
```

---

### CreateDiscordInvite

A styled Discord server card with member count stats and a copy-link button.

```lua
local Card = Tab:CreateDiscordInvite({
    Title       = "Our Community",
    Description = "Join us for updates and support!",
    Icon        = "rbxassetid://0",
    Banner      = "rbxassetid://0",
    Link        = "https://discord.gg/GMAFx8NxdK",
    Button      = "Join Server",
})
```

| Option | Type | Description |
|---|---|---|
| `Title` | `string` | Server name |
| `Description` | `string` | Short description below the name |
| `Icon` | `string` | Server icon asset ID |
| `Banner` | `string` | Banner image asset ID (displayed at the top of the card) |
| `Link` | `string` | Full Discord invite URL |
| `Button` | `string` | Join button label text |

> Automatically fetches **online** and **total member** counts from the Discord API when `request` / `syn.request` is available.

**Methods:**

```lua
Card:SetTitle("New Name")
Card:GetFrame()
```

---

## 📌 Sidebar Elements

Placed in the tab sidebar, not inside a tab page.

### CreateSeparator

A text label or blank spacer between tab groups in the sidebar.

```lua
-- With label
Window:CreateSeparator({ Text = "Combat" })

-- Blank spacer
Window:CreateSeparator({})
```

| Option | Type | Description |
|---|---|---|
| `Text` | `string` | Label text. Leave empty for a blank spacer |

---

### CreateSidebarLine

A thin horizontal divider line in the sidebar.

```lua
Window:CreateSidebarLine()
```

No configuration options.

---

## 🔑 CreateKeySystem

A standalone authentication/key screen displayed before the main window.

```lua
local KeySystem = Library:CreateKeySystem({
    Title  = "Key System",
    Icon   = "rbxassetid://0",
    Theme  = "Blue",
    Size   = Vector2.new(420, 265),
    Acrylic = {
        Enabled = true,
        Opacity = 0.55,
    },
})
```

| Option | Type | Default | Description |
|---|---|---|---|
| `Title` | `string` | `"Key System"` | Window title |
| `Icon` | `string` | `""` | Icon asset ID |
| `Theme` | `string \| Color3` | `"Blue"` | Accent theme |
| `Size` | `Vector2` | `Vector2.new(420, 265)` | Window size |
| `Acrylic.Enabled` | `boolean` | `false` | Transparent background |
| `Acrylic.Opacity` | `number` | `0.55` | Opacity level |

**Root methods:**

```lua
KeySystem:GetText()         -- Returns the current value of the input box
KeySystem:SetText("key")    -- Set the input box text
KeySystem:GetTextBox()      -- Returns the TextBox instance directly
KeySystem:Notify({...})     -- Show a notification (same options as Window:Notify)
KeySystem:Destroy()         -- Close and destroy the key system UI
```

---

### KeySystem CreateButton

```lua
local Btn = KeySystem:CreateButton({
    Description = "Verify Key",
    Icon        = "rbxassetid://0",
    Callback    = function()
        local key = KeySystem:GetText()
        if key == "my-secret-key" then
            KeySystem:Destroy()
            -- open your main window here
        else
            KeySystem:Notify({
                Title    = "Invalid Key",
                Text     = "The key you entered is incorrect.",
                Duration = 3,
            })
        end
    end,
})
```

| Option | Type | Description |
|---|---|---|
| `Description` | `string` | Button label |
| `Icon` | `string` | Optional icon asset ID |
| `Callback` | `function()` | Called on click |

**Methods:**

```lua
Btn:SetDescription("New Label")
Btn:GetFrame()
```

---

### KeySystem CreateSocialButton

Small pill-shaped link buttons shown below the action buttons.

```lua
KeySystem:CreateSocialButton({
    Type  = "Discord",
    Link  = "https://discord.gg/GMAFx8NxdK",
    Order = 1,
})

KeySystem:CreateSocialButton({
    Type  = "Youtube",
    Link  = "https://youtube.com/@example",
    Order = 2,
})

KeySystem:CreateSocialButton({
    Type  = "Website",
    Link  = "https://example.com",
    Order = 3,
})
```

| Option | Type | Description |
|---|---|---|
| `Type` | `string` | Icon style: `"Discord"`, `"Youtube"`, or `"Website"` |
| `Link` | `string` | URL that is copied to clipboard on click |
| `Order` | `number` | Layout order (lower = further left) |

> Clicking copies the link to clipboard and briefly shows **"Copied!"** feedback.

---

### KeySystem Notify

Same options as the main window `Notify`.

```lua
KeySystem:Notify({
    Title    = "Welcome",
    Text     = "Please enter your key.",
    Duration = 4,
})
```

---

## 🛠 Window Methods

```lua
Window:Notify({...})          -- Show a notification
Window:GetContentFrame()      -- Returns the content Frame
Window:GetMainFrame()         -- Returns the main window Frame
Window:GetConfigPanel()       -- Returns the config panel ScrollingFrame
Window:Destroy()              -- Destroy the entire window and clean up connections
```

---

## 🎨 Themes

Pass any of the following strings to the `Theme` option, or pass a `Color3` directly for a fully custom accent.

| Name | Color |
|---|---|
| `"Blue"` | `RGB(35, 85, 170)` |
| `"Red"` | `RGB(170, 40, 40)` |
| `"Green"` | `RGB(35, 140, 70)` |
| `"Purple"` | `RGB(110, 60, 180)` |
| `"Pink"` | `RGB(200, 70, 130)` |
| `"Yellow"` | `RGB(175, 148, 30)` |
| `"White"` | `RGB(200, 200, 200)` |
| `"Grey"` | `RGB(108, 108, 108)` |

**Custom Color3:**

```lua
Theme = Color3.fromRGB(255, 100, 50)
```

The config panel also exposes a **Custom** color picker at runtime so users can pick any color visually.

---

## 🌐 Languages

| Value | Language |
|---|---|
| `"English"` | English (default) |
| `"Portuguese"` | Portuguese |
| `"Vietnamese"` | Vietnamese |

Any other language is fetched automatically at runtime via Google Translate / MyMemory when HTTP is available.

---

## ✨ RichText & Colored Words

The `ColoredWords`, `TitleColoredWords`, `DescriptionWords`, `TitleWords`, and `TextWords` systems let you color and gradient individual words anywhere they are supported (Paragraphs, Notifications).

### Single color

```lua
ColoredWords = {
    { Text = "active", Colors = { Color3.fromRGB(80, 220, 80)  } },
    { Text = "error",  Colors = { Color3.fromRGB(220, 80, 80)  } },
}
```

### Gradient (two or more colors)

```lua
ColoredWords = {
    {
        Text     = "Rainbow",
        Colors   = {
            Color3.fromRGB(255, 80,  80),
            Color3.fromRGB(255, 200, 80),
            Color3.fromRGB(80,  255, 80),
        },
        Gradient = true,
    },
}
```

### Word builder

Mix plain strings and colored word tables in a list:

```lua
DescriptionWords = {
    "The server has ",
    { Text = "42", Colors = { Color3.fromRGB(100, 200, 255) } },
    " players online.",
}
```

---

## 📦 Full Example

```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/ProxyHubDev/ProxyLib/refs/heads/main/Documents/ProxyLibrary"))()
local Library = ProxyLib.new()

local Window = Library:CreateWindow({
    Title = "My Script",
    Subtitle = "example",
    Theme = "Blue",
    Size = Vector2.new(520, 380)
})

Window:CreateSeparator({ Text = "Combat" })

local Tab = Window:CreateTab({
    Title = "Main"
})

Tab:CreateSection({
    Text = "Combat Settings",
})

Tab:CreateSeparatorLine()

local Dropdown = Tab:CreateDropdown({
    Title = "Weapon",
    Options = { "Sword", "Bow", "Staff" },
    Default = "Sword",
    Callback = function(selected)
        print("Selected weapon:", selected)
        Window:Notify({
            Title = "Weapon",
            Text = "You chose: " .. selected,
            Duration = 2
        })
    end
})

local Para = Tab:CreateParagraph({
    Title       = "About",
    Description = "This is some info text.",
})

local Toggle = Tab:CreateToggle({
    Title    = "Enable Feature",
    Default  = false,
    Callback = function(state)
        print("Toggle:", state)
    end,
})

local Toggle = Tab:CreateToggle({
    Title       = "Enable Feature",
    Description = "Turns the feature on or off.",
    Icon        = "rbxassetid://82431110954723",
    Default     = false,
    SaveId      = "my_toggle",
    Callback    = function(state)
        print("Toggle:", state)
    end,
})

local Check = Tab:CreateCheckBox({
    Title    = "Accept Terms",
    Default  = false,
    Callback = function(state)
        print("Checked:", state)
    end,
})

local Check = Tab:CreateCheckBox({
    Title        = "Enable PvP",
    Description  = "Activates PvP mode.",
    Default      = false,
    Confirmation = true,
    SaveId       = "my_checkbox",
    Callback     = function(state)
        print("CheckBox:", state)
    end,
})

local Slider = Tab:CreateSlider({
    Title    = "Speed",
    Min      = 0,
    Max      = 100,
    Default  = 16,
    Callback = function(value)
        game:GetService("Players").LocalPlayer.Character.Humanoid.WalkSpeed = value
    end,
})

local Button = Tab:CreateButton({
    Title    = "Teleport",
    Callback = function()
        print("Clicked!")
    end,
})

local Button = Tab:CreateButton({
    Title        = "Delete Data",
    Description  = "This action cannot be undone.",
    Icon         = "rbxassetid://88732835297181",
    Confirmation = true,
    Callback     = function()
        print("Confirmed and executed.")
    end,
})

local TextBox = Tab:CreateTextBox({
    Title    = "Username",
    Callback = function(text)
        print("Submitted:", text)
    end,
})

local TextBox = Tab:CreateTextBox({
    Title       = "Username",
    Placeholder = "Enter your username...",
    Default     = "",
    MaxLength   = 50,
    Callback    = function(text)
        print("Text:", text)
    end,
})

local Card = Tab:CreateDiscordInvite({
    Title       = "Our Community",
    Description = "Join us for updates and support!",
    Icon        = "rbxassetid://0",
    Banner      = "rbxassetid://0",
    Link        = "https://discord.gg/GMAFx8NxdK",
    Button      = "Join Server",
})

Window:Notify({
    Title = "Ready",
    Text = "UI Complete",
    Duration = 3
})
```
