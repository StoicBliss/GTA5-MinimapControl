# Minimap Control Changelog

## [1.2.0] - 2026-10-28

### Added
* **Keep Health & Armor Visible (`KeepHealthArmorVisible=true`)**:
  * Added `KeepHealthArmorVisible` setting under `[Display]` in `MinimapControl.ini` (default: `true`).
  * Preserves and renders the player's vital Health and Armor meters on screen when the minimap/radar is hidden.
  * Dynamically accounts for screen aspect ratios (16:9, 16:10, 21:9) and user safe-zone settings for pixel-perfect placement.
  * Includes low-health pulsing red alert when health drops below 25%.

### Fixed
* **Fixed Game Hang / Crash on Startup & Ticking (`AppHangB1` & `0xC0000005`)**:
  * Fixed crash caused by passing an unexpected argument (`0`) to native `Hash.GET_SCREEN_ASPECT_RATIO` (`0xB2EBE8CBC58B90E9`), which misaligned the ScriptHook native stack frame every frame. Migrated to `GTA.UI.Screen.AspectRatio` with zero-parameter native fallback.
  * Removed unsafe `THEFEED_REMOVE_ITEM` calls on expired ticker notification IDs. Ticker notifications in GTA V automatically self-dismiss; forcibly removing expired handles caused memory access violations (`0xC0000005`) inside the game's feed manager.
  * Added robust null and validity guards for `Game.Player` and `Game.Player.Character` during pause and cutscenes.
* **Universal ScriptHookVDotNet Compatibility (`TypeLoadException`)**:
  * Fixed `[TypeLoadException MinimapController.PlayFeedback()]` caused by nightly SHVDN wrapper types (`GTA.UI.FeedPost`, `PlaySoundFrontendAndForget`) missing from stable SHVDN v3.6.0 releases.
  * Migrated all notifications, audio clicks, and subtitle rendering to direct GTA V engine native calls (`PLAY_SOUND_FRONTEND`, `BEGIN_TEXT_COMMAND_THEFEED_POST`, `END_TEXT_COMMAND_THEFEED_POST_TICKER`, `BEGIN_TEXT_COMMAND_PRINT`).
  * Works out-of-the-box on all ScriptHookVDotNet v3 installations (v3.0.0 through v3.7+ nightly) with zero TypeLoad or MissingMethod exceptions.
* **Unhandled Guard in Key Handler**:
  * Wrapped `OnKeyDown` event dispatch in comprehensive `try/catch` guards so unhandled script exceptions never escape to SHVDN or flash on-screen.

---

## [1.1.0] - 2026-09-13

### Changed & Enhanced
* **Vehicle-Only Mode by Default**:
  * Set `VehicleOnlyMode=true` by default in configuration.
  * The minimap now automatically hides while exploring on foot and seamlessly restores whenever the player enters any vehicle.
* **Mutually Exclusive Notifications**:
  * Set `UseSubtitleNotification=false` by default (standard ticker notification enabled).
  * Enforced strict mutual exclusivity: when subtitle notifications are enabled, radar ticker notifications are automatically suppressed, eliminating duplicate on-screen alerts when toggling the minimap.
* **Cross-Mod Peek Interoperability**:
  * Integrated `AppDomain.CurrentDomain` synchronization (`MinimapPeekUntil`) with [RealWeather](https://github.com/StoicBliss/GTA5-RealWeather).
  * Temporary radar peeks triggered by weather notifications or external scripts are cleanly honored and will not be prematurely dismissed.

---

## [1.0.0] - 2026-09-09

### Initial Release
* **Instant Radar & Minimap Toggle**:
  * Keyboard shortcut `B` (fully rebindable with optional modifiers).
  * Controller gamepad support with customizable hold threshold (`D-Pad Down` / 450ms hold).
  * Dedicated expanded minimap view key support.
* **Dynamic Vehicle Modes**:
  * Automatic state tracking across pedestrian, vehicle entry, and vehicle exit events.
* **Custom Display & Audio**:
  * Ticker and subtitle display options with configurable duration.
  * Optional audio feedback on toggle.
