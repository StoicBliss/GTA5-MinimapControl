# Minimap Control Changelog

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
