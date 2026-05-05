# cust-term 🖥️

> A clean Windows Terminal customization guide — themes, fonts, and fastfetch setup from scratch.

---

## 📸 Before & After

**Before** — the default Windows Terminal:

```
┌─────────────────────────────────────────────────┐
│  Windows PowerShell                             │
│  Copyright (C) Microsoft Corporation.           │
│                                                 │
│  PS C:\Users\user>  _                           │
│                                                 │
│  (default black background, Consolas font,      │
│   no transparency, no personality)              │
└─────────────────────────────────────────────────┘
```

**After** — with one of these themes applied:

```
┌─────────────────────────────────────────────────┐
│ PS ⚡  ×  +                    [frosted glass]  │
│▓▓▓▓▓▓▓▓▓▓▓▒▒▒▒▒▒▒▒▒▒▒░░░░░░░░░░░░░░░░░░░░░░░│
│                                                 │
│       ·   ·          nasru@Khans-Laptop         │
│     ·   ◇   ·        ──────────────────         │
│   ·   ◇   ◇   ·      OS    Windows 11 x86_64   │
│ ·   ◇   ◆   ◇   ·    CPU   i5-12450H @ 4.4GHz  │
│   ·   ◆   ◆   ·      RAM   6.28 / 7.72 GiB     │
│     ·   ◈   ·        Disk  163 / 226 GiB        │
│   ·   ◆   ◆   ·      Shell PowerShell           │
│ ·   ◇   ◆   ◇   ·                              │
│   ·   ◇   ◇   ·      ● ● ● ● ● ● ● ●          │
│     ·   ◇   ·                                   │
│       ·   ·                                     │
│                                                 │
│  PS C:\Users\nasru> _                           │
└─────────────────────────────────────────────────┘
```

---

## 🗂️ Repo Structure

```
cust-term/
├── themes/
│   ├── void-moody.json     # Dark purple — moody & deep
│   ├── ghost-wire.json     # Monochrome — minimal & sharp
│   ├── deep-tide.json      # Ocean blue — cool & clean
│   ├── ember-forge.json    # Warm sunset — orange & fire
│   └── matrix-rain.json    # Hacker green — classic matrix
├── fastfetch/
│   ├── ascii.txt           # Diamond ring ASCII art
│   └── config.jsonc        # Fastfetch configuration
└── README.md
```

---

## 🚀 Step 1 — Install Windows Terminal

If you don't have it yet, install it from the Microsoft Store or via `winget`:

```powershell
winget install Microsoft.WindowsTerminal
```

---

## 🔤 Step 2 — Install the Font

All themes use **JetBrainsMono Nerd Font Mono** — a monospace font with icon support.

1. Go to [nerdfonts.com](https://www.nerdfonts.com/font-downloads) and download **JetBrainsMono**
2. Extract the `.zip`
3. Select all `.ttf` files → Right-click → **Install for all users**
4. Restart Windows Terminal

> ⚠️ Without this font, you'll see a warning and icons won't render correctly.

---

## 🎨 Step 3 — Apply a Theme

### Method 1 — Replace the whole settings file (easiest)

1. Pick a theme from the `themes/` folder
2. Open Windows Terminal → Press `Ctrl + ,`
3. Click **Open JSON file** (bottom-left corner icon)
4. Replace everything in that file with the contents of your chosen theme JSON
5. Save → Fully close and reopen Windows Terminal

### Method 2 — Add just the color scheme

If you want to keep your existing settings and only add the color scheme:

1. Open your `settings.json` via `Ctrl + ,` → Open JSON file
2. Copy the object inside `"schemes": [...]` from your chosen theme
3. Paste it into the `"schemes"` array in your settings file
4. Change `"colorScheme"` inside `"profiles" > "defaults"` to match the scheme name

---

## 🎨 Themes

### 🟣 Void Moody
**File:** `themes/void-moody.json`

Deep near-black background with a full electric purple palette. Frosted glass at 75% opacity. Best for night sessions.

```
Background  #0D0D1A    Foreground  #CDB4F0
Accent      #E040FB    Cursor      #E040FB
```

---

### ⬜ Ghost Wire
**File:** `themes/ghost-wire.json`

Pure monochrome — near-black background, clean white/grey text. Minimal and sharp. Vintage cursor style.

```
Background  #0A0A0A    Foreground  #E0E0E0
Accent      #FFFFFF    Cursor      #FFFFFF
```

---

### 🔵 Deep Tide
**File:** `themes/deep-tide.json`

Deep navy background with cool cyan/blue highlights. Calm and focused.

```
Background  #050D18    Foreground  #A8D8EA
Accent      #29B6F6    Cursor      #29B6F6
```

---

### 🔶 Ember Forge
**File:** `themes/ember-forge.json`

Near-black background with warm orange/red tones. Feels like fire in the dark.

```
Background  #100800    Foreground  #FFCCBC
Accent      #FF5722    Cursor      #FF6D00
```

---

### 🟢 Matrix Rain
**File:** `themes/matrix-rain.json`

Pure black background with classic hacker green text. The one and only.

```
Background  #000300    Foreground  #00FF41
Accent      #00FF41    Cursor      #00FF41
```

---

## 💡 Step 4 — Enable Frosted Glass (Acrylic)

The themes have `"useAcrylic": true` set, but you also need to enable transparency in Windows itself:

1. Press `Win + I` → **Personalization** → **Colors**
2. Scroll down → Toggle **Transparency effects → On**

> ⚠️ Battery Saver mode disables transparency. Make sure it's off if the effect isn't showing.

---

## ⚡ Step 5 — Install & Configure Fastfetch

Fastfetch is a system info tool that shows your specs on terminal startup — like neofetch but faster.

### Install

```powershell
winget install fastfetch-cli.fastfetch
```

### Set up the ASCII art and config

1. Create the config folder if it doesn't exist:

```powershell
mkdir "$env:USERPROFILE\.config\fastfetch"
```

2. Copy `fastfetch/ascii.txt` and `fastfetch/config.jsonc` from this repo into that folder:

```
C:\Users\YOUR_USERNAME\.config\fastfetch\ascii.txt
C:\Users\YOUR_USERNAME\.config\fastfetch\config.jsonc
```

3. Open `config.jsonc` and replace `YOUR_USERNAME` with your actual Windows username in the `source` path.

### Run on startup (PowerShell)

To make fastfetch run every time you open the terminal, add it to your PowerShell profile:

```powershell
# Open your profile file
notepad $PROFILE
```

Add this line at the top:

```powershell
fastfetch
```

Save and restart Windows Terminal. Fastfetch will now greet you on every launch.

---

## ⌨️ Keybindings (all themes)

| Action | Shortcut |
|---|---|
| Copy | `Ctrl + C` |
| Paste | `Ctrl + V` |
| Find | `Ctrl + Shift + F` |
| New Tab | `Ctrl + T` |
| Split Pane | `Alt + Shift + D` |

---

## 🛠️ Tips

- You can mix themes — use one theme's color scheme with another's font settings
- To reset to defaults, press `Ctrl + ,` → click **Reset to defaults** (bottom-left)
- The `scrollbarState: hidden` setting hides the scrollbar for a cleaner look — remove it if you need it back
- All themes start in `%USERPROFILE%` (`C:\Users\yourname`) by default

---

## 📄 License

MIT — use, share, modify freely. Star the repo if it helped! ⭐
