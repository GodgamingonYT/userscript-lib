# iOS 26 Glass UI Library

<div align="center">Lightweight, reusable iOS 26-style glass UI for userscripts (Bloxd/Roblox tools)
Build beautiful interfaces in minutes—no CSS knowledge required

https://fonts.google.com/icons?webview_progress_bar=1&push_animated=1&show_loading=0&theme=light

</div>✨ Features

· 🎨 iOS 26 Glass Morphism - Authentic frosted glass design
· ⚡ Lightweight - Minimal performance impact
· 🔧 Zero CSS Required - Everything works out of the box
· 📱 Fully Customizable - Colors, positions, and more
· 🎯 Easy Integration - Simple API for rapid development

🚀 Quick Start

Installation

Add this to your Tampermonkey script metadata:

```javascript
// @require [https://raw.githubusercontent.com/[YourUser]/[YourRepo]/main/iOS26GlassUILib](https://raw.githubusercontent.com/GodgamingonYT/userscript-lib/refs/heads/main/Sync%20UI).js
```

Basic Usage

```javascript
// Initialize the UI
const ui = new iOS26GlassUI({ 
  title: "My Awesome Tool" 
});

// Add a tab with icon
ui.addTab(
  "combat", 
  "Combat",
  `<svg viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z"/></svg>`
);

// Add a toggle switch
ui.addToggle(
  "combat",
  "killaura", 
  "KillAura",
  "Auto-target nearby players",
  (isOn) => console.log("KillAura:", isOn)
);

// Add a slider
ui.addSlider(
  "combat",
  "range",
  "Attack Range", 
  "1-6 blocks",
  { min: 1, max: 6, value: 4.5 },
  (val) => console.log("Range:", val)
);
```

📚 API Reference

addTab(tabId, tabName, iconSvg)

Add a navigation tab with icon.

Parameters:

· tabId (string) - Unique identifier (e.g., "combat")
· tabName (string) - Display name (e.g., "Combat")
· iconSvg (string) - SVG icon markup (24x24 recommended)

addToggle(tabId, toggleId, mainText, subText, onToggle)

Add a toggle switch component.

Parameters:

· tabId (string) - Parent tab ID
· toggleId (string) - Unique toggle ID
· mainText (string) - Primary label
· subText (string) - Secondary description
· onToggle (function) - Callback receiving boolean state

addSlider(tabId, sliderId, mainText, subText, opts, onInput)

Add a slider for numeric values.

Parameters:

· tabId (string) - Parent tab ID
· sliderId (string) - Unique slider ID
· mainText (string) - Primary label
· subText (string) - Secondary description
· opts (object) - { min, max, step, value } (defaults: 1-10)
· onInput (function) - Callback receiving current value

addButton(tabId, btnText, onClick)

Add a button component.

Parameters:

· tabId (string) - Parent tab ID
· btnText (string) - Button text
· onClick (function) - Click callback

getComponentState(componentId)

Retrieve current state of any component.

Returns:

· boolean for toggles
· string for sliders

⚙️ Configuration

Customize the UI appearance on initialization:

```javascript
const ui = new iOS26GlassUI({
  title: "Bloxd Tool",           // Header text
  openBtn: { 
    bottom: "30px",              // Button positioning
    right: "30px" 
  },
  colors: {
    toggleActive: "#34c759",     // iOS green for active toggles
    textMain: "#1d1d1f",         // Dark gray text
    glassBg: "rgba(255,255,255,0.15)"  // Glass effect background
  }
});
```

🛠️ Advanced Example

```javascript
// Complete tool example
const tool = new iOS26GlassUI({
  title: "Bloxd Pro Tools",
  openBtn: { bottom: "20px", right: "20px" }
});

// Combat Tab
tool.addTab("combat", "Combat", combatIcon);
tool.addToggle("combat", "aimbot", "Aimbot", "Auto-aim", onAimbotToggle);
tool.addSlider("combat", "fov", "FOV", "Field of view", {min:30,max:120,value:90}, onFovChange);

// Visuals Tab  
tool.addTab("visuals", "Visuals", eyeIcon);
tool.addToggle("visuals", "esp", "ESP", "Player outlines", onEspToggle);
tool.addButton("visuals", "Refresh", onRefreshClick);

// Get states later
const isAimbotOn = tool.getComponentState("aimbot");
const fovValue = tool.getComponentState("fov");
```

❓ Troubleshooting

Common Issues

Problem Solution
Components not showing Ensure tabId matches between addTab() and component calls
Button not visible Verify the tab exists before adding components
UI not loading Check @require URL is a raw GitHub link
Icons not displaying Use 24x24 SVG with proper viewBox attribute

Debug Tips

```javascript
// Check if tab was created
console.log("Tabs:", ui.tabs); 

// Verify component state
const state = ui.getComponentState("yourComponentId");
console.log("Component state:", state);
```

📄 License

MIT License - feel free to use in personal and commercial projects.

---

<div align="center">Need help? Open an issue or check the examples above! 🚀

</div>
