# 🦖 DinoHack — PeppermintGrave Dino Engine

> A custom JavaScript enhancement panel for the **Chrome Dino Game**, built by **PeppermintGrave**.

A sleek, customizable control panel that lets you modify the Chrome Dino experience directly from the browser.

---

## ✦ Features

### ⚡ Dino Engine

The **Dino Engine** provides a live control panel with:

- ✓ God Mode
- ⚡ Custom game speed
- 🎨 Multiple UI themes
- 🌈 Custom accent colors
- 👻 Panel opacity control
- ✨ Adjustable glow strength
- 📦 Compact mode
- ➖ Minimize / expand panel
- ⏹️ Stop Engine
- ▶️ Restart Engine
- 🔄 Reset speed
- 🖱️ Smooth draggable interface
- 📱 Mobile-friendly controls
- 💻 Desktop support

---

## 🎨 Themes

Dino Engine includes several built-in themes:

| Theme | Style |
|---|---|
| 🍃 `Peppermint` | Neon green |
| 🌹 `Rose` | Pink |
| ❄️ `Ice` | Cyan / blue |
| 💜 `Violet` | Purple |
| 🪙 `Gold` | Golden yellow |
| 🩸 `Blood` | Red |
| 🎨 `Custom` | Choose your own accent |

You can also select a completely custom accent color using the built-in color picker.

---

## 🛡️ God Mode

> **God Mode prevents the Dino game from triggering its normal `gameOver` behavior.**

When enabled:

```text
✓ God Mode
```

When disabled:

```text
ø God Mode
```

The engine also displays the current state:

```text
● GOD MODE ACTIVE
```

or:

```text
● GOD MODE OFF
```

---

## ⚡ Speed Control

Dino Engine allows the game speed to be adjusted from:

```text
1x → 100x
```

You can use the slider or the quick buttons:

```text
10x
25x
75x
100x
```

The current speed is displayed directly inside the panel.

---

## 🎛️ Panel Customization

### Panel Opacity

The panel opacity can be adjusted from:

```text
35% → 100%
```

### Glow Strength

The panel glow can be adjusted from:

```text
0 → 5
```

This changes the intensity of the neon glow effect around the panel.

---

## 📦 Compact Mode

**Compact Mode** hides the main panel controls while keeping the engine panel available.

It switches between:

```text
Compact mode
```

and:

```text
Expand panel
```

---

## ➖ Minimize

The `−` button collapses the panel body.

When minimized, the button changes to:

```text
+
```

Press it again to restore the controls.

---

## ⏹️ Engine Controls

### Stop Engine

Stops the custom engine and restores the original Dino game behavior.

The panel changes to:

```text
STOPPED
```

and:

```text
● ENGINE STOPPED
```

### Restart Engine

Reactivates the engine and restores the selected speed and God Mode state.

The panel returns to:

```text
ONLINE
```

and:

```text
● ENGINE ACTIVE
```

### Reset Speed

Restores the original game speed.

---

## 🖱️ Dragging

The panel can be moved around the screen by dragging the **Dino Engine header**.

The position is constrained to the visible browser window so the panel cannot be dragged completely off-screen.

The interface uses pointer events for smooth desktop and touch dragging.

---

# 💻 Desktop

The desktop version uses a **JavaScript bookmarklet**.

### Requirements

- Google Chrome / Chromium-based browser
- Chrome Dino Game
- JavaScript enabled

### Usage

1. Open the Chrome Dino Game.
2. Create a browser bookmark.
3. Edit the bookmark.
4. Paste the desktop script from the `Scripts` folder.
5. Save the bookmark.
6. Open the Dino Game.
7. Activate the bookmark.

> The script expects the Chrome Dino `Runner` object to be available.

If the Dino Game is not open, the script displays:

```text
Open Chrome Dino first!
```

---

# 📱 Mobile

The mobile version is also provided as a JavaScript bookmarklet.

It includes the same core Dino Engine interface:

- ✓ God Mode
- ⚡ Speed control
- 🎨 Themes
- 🎨 Custom colors
- 👻 Opacity
- ✨ Glow
- 📦 Compact mode
- ➖ Minimize
- ⏹️ Stop Engine
- ▶️ Restart Engine
- 🔄 Reset speed
- 🖱️ Touch-friendly dragging

The mobile script is stored separately inside the `Scripts` folder.

---

# 📁 Repository Structure

```text
DinoHack/
│
├── Scripts/
│   ├── Desktop
│   └── Mobile
│
└── README.md
```

> File names may change as the project develops.

---

# 🧩 How It Works

Dino Engine interacts with the Chrome Dino game's JavaScript `Runner` object.

Before modifying the game, the script stores the original state:

```javascript
window.dinoEngineOriginal
```

This allows the engine to restore the original game behavior when it is stopped.

The engine modifies:

```javascript
Runner.prototype.gameOver
```

and accesses the current Dino game instance through:

```javascript
Runner.instance_
```

or:

```javascript
Runner.getInstance()
```

The speed is controlled through the Dino Runner instance's:

```javascript
setSpeed()
```

method.

---

# 🔄 Engine Lifecycle

```text
Open Chrome Dino
       ↓
Run Dino Engine
       ↓
Detect Runner
       ↓
Create Control Panel
       ↓
Apply Settings
       ↓
Engine Active
       ↓
Stop / Restart / Close
```

When the engine is stopped, the original `gameOver` behavior and stored game speed are restored.

---

# 🎨 UI Design

The interface follows the **PeppermintGrave** aesthetic.

### Visual Elements

- Neon accent colors
- Dark backgrounds
- Rounded corners
- Animated glow
- Smooth entrance animation
- Pulsing engine status
- Minimal control layout
- Responsive width
- Touch-friendly interaction

The default theme is:

```text
PEPPERMINT
```

with a neon-green accent.

---

# 🧪 Status Indicators

### Engine Active

```text
● ENGINE ACTIVE
```

### Engine Stopped

```text
● ENGINE STOPPED
```

### God Mode Active

```text
● GOD MODE ACTIVE
```

### God Mode Disabled

```text
● GOD MODE OFF
```

---

# ⚠️ Compatibility

Dino Engine relies on the internal JavaScript structure of the Chrome Dino Game.

Browser updates can change internal objects such as:

```javascript
Runner
Runner.instance_
Runner.getInstance()
Runner.prototype.gameOver
```

If Chrome changes these internals, parts of the engine may stop working until the script is updated.

---

# 🔧 Troubleshooting

### `Open Chrome Dino first!`

Make sure the Chrome Dino Game is already open before running the script.

### The panel does not appear

Try:

1. Reloading the Dino Game.
2. Starting the Dino Game.
3. Running the script again.
4. Checking that JavaScript is enabled.

### Speed does not change

The engine depends on the Dino game's `Runner` instance and its `setSpeed()` method.

A browser update may change this behavior.

### Dragging does not work

Drag from the **DINO ENGINE header**, rather than directly from a button.

---

# 🚀 Project Goals

DinoHack is designed to provide a clean and customizable interface for experimenting with the Chrome Dino game's client-side JavaScript.

Future versions may introduce additional customization and experimental controls.

---

# 👤 Creator

## PeppermintGrave

> **PEPPERMINTGRAVE • DINO ENGINE**

Built with:

```text
JavaScript
HTML
CSS
Chrome Dino Runner
```

---

# 📜 Disclaimer

DinoHack is an experimental browser-side JavaScript project intended for educational and personal experimentation with the Chrome Dino Game.

Use it responsibly and only in environments where modifying the game is permitted.

---

# ⭐ Support

If you find the project interesting, consider giving the repository a ⭐.

**Repository:**  
https://github.com/PeppermintGrave/DinoHack

---

> 🦖 **PEPPERMINTGRAVE — DINO ENGINE**
>
> *Customize the run. Control the engine. Keep going.*
