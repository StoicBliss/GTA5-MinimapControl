# Minimap Control for Grand Theft Auto V

[![GTA V](https://img.shields.io/badge/Game-Grand%20Theft%20Auto%20V-blue.svg)](https://www.rockstargames.com/gta-v)
[![ScriptHookVDotNet](https://img.shields.io/badge/ScriptHookVDotNet-v3.0+-orange.svg)](https://github.com/scripthookvdotnet/scripthookvdotnet)
[![Platform](https://img.shields.io/badge/Platform-PC%20%28x64%29-lightgrey.svg)]()
[![Target](https://img.shields.io/badge/.NET%20Framework-4.8-purple.svg)]()
[![Version](https://img.shields.io/badge/Version-1.2.0-green.svg)](CHANGELOG.md)

**Minimap Control** is a lightweight, responsive utility for Grand Theft Auto V that gives you complete control over your radar and HUD navigation.

Whether you want clean, immersive cinematic exploration on foot or automatic radar activation the instant you enter a vehicle, Minimap Control delivers instant toggling without gameplay interruptions or framerate drops.

---

## Key Features

- **Keep Health & Armor Visible (`KeepHealthArmorVisible = true`)**:
  - Keep your vital Health and Armor meters on screen even when the minimap/radar is hidden.
  - Automatically adjusts to all monitor aspect ratios and user safe-zone settings with low-health alert pulsing.

- **Dynamic Vehicle-Only Mode (`VehicleOnlyMode = true`)**:
  - Automatically hides the radar and minimap while exploring on foot for maximum immersion.
  - Automatically restores the minimap when you step into any vehicle (car, motorcycle, aircraft, boat).
  - Smoothly hides the minimap again upon exiting the vehicle.

- **Configurable Keyboard & Controller Controls**:
  - **Keyboard**: Press **B** (customizable to any key or modifier combination) for an instant on-demand toggle.
  - **Controller / Gamepad**: Hold **D-Pad Down** (450ms hold threshold) to toggle the minimap. Quick-tapping preserves native game functions (e.g. multiplayer player list / character wheel) without conflict.

- **Expanded Minimap Toggle**:
  - Optional hotkey to instantly switch between standard and expanded large radar view.

- **Mutually Exclusive Display Modes**:
  - Choose between clean **Subtitles** at the bottom of the screen or **Tickers** above the radar (`Minimap: ON` / `Minimap: OFF`).
  - When subtitle notifications are enabled, ticker alerts are automatically suppressed to avoid duplicate on-screen messages.

- **Cross-Mod Peek Interoperability**:
  - Seamlessly interoperates with [**RealWeather**](https://github.com/StoicBliss/GTA5-RealWeather) and radar-peeking mods via cross-script memory signals (`MinimapPeekUntil`), ensuring temporary weather alerts or radar peeks are never prematurely hidden.

- **Safe Lifecycle & Pause Guards**:
  - Automatically suspends toggles during pause menus, cutscenes, and loading transitions.

---

## Default Controls

| Action | Default Keyboard | Default Controller | Config Key |
| :--- | :--- | :--- | :--- |
| **Toggle Minimap** | `B` | `D-Pad Down` *(Hold 450ms)* | `ToggleKey` / `ControllerToggleControl` |
| **Toggle Modifier** | `None` | — | `ToggleModifier` |
| **Expanded Minimap** | `None` *(Disabled)* | — | `ExpandKey` |

*All keybinds and hold thresholds can be customized in `MinimapControl.ini`.*

---

## Requirements

* [Script Hook V](http://www.dev-c.com/gtav/scripthookv/) by Alexander Blade
* [ScriptHookVDotNet v3](https://github.com/scripthookvdotnet/scripthookvdotnet/releases) (v3.7.0 nightly or later)
* Microsoft .NET Framework 4.8 runtime

---

## Installation

1. Install **Script Hook V** and **ScriptHookVDotNet v3** into your main GTA V game directory (where `GTA5.exe` is located).
2. Extract **`MinimapControl.dll`** and **`MinimapControl.ini`** into your GTA V **`scripts/`** folder:
   ```
   <Grand Theft Auto V>\scripts\MinimapControl.dll
   <Grand Theft Auto V>\scripts\MinimapControl.ini
   ```
3. *(Optional)* Customize your hotkeys and vehicle modes in `MinimapControl.ini`.
4. Launch GTA V!

---

## Building from Source

To compile from source, open PowerShell in the project directory and run:

```powershell
.\build.ps1
```

To compile and package a distribution release zip:

```powershell
.\build.ps1 -Package
```

---

## Author & Credits

- Developed by **StoicBliss** ([@StoicBliss](https://github.com/StoicBliss))
- Built on [ScriptHookVDotNet](https://github.com/scripthookvdotnet/scripthookvdotnet) by crosire and contributors
