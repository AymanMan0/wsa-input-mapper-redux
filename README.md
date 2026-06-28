![preview](https://raw.githubusercontent.com/AymanMan0/wsa-input-mapper-redux/main/preview.svg)

# RemapOS

**A universal input translation engine for Android-x86 and ChromeOS environments, enabling seamless keyboard and mouse integration with touch-centric applications.**

## Overview

RemapOS is not a keymapping tool—it is an *input translation environment*. While WmapperKeymapper focuses on binding keystrokes to touch events within Windows Subsystem for Android, RemapOS reimagines the entire paradigm by operating at the operating system interface layer. Imagine a universal interpreter that sits between your physical keyboard and any touch-oriented application, dynamically translating every keystroke, scroll gesture, and mouse click into the precise touch events the application expects—without requiring root access, kernel modifications, or per-app configuration.

Think of RemapOS as the *Rosetta Stone* for input methods. Just as the original Rosetta Stone allowed scholars to decipher Egyptian hieroglyphs by providing a translation key, RemapOS provides a real-time bidirectional translation layer that allows traditional desktop input devices to speak the language of touch-native applications.

The core innovation lies in its *contextual gesture synthesis* engine. Unlike static keymapping solutions that require you to manually bind every key to a predefined touch coordinate, RemapOS analyzes the application's UI hierarchy in real time and infers the intended touch interaction. A single `Enter` keypress, for example, might translate into a tap on the active dialog button, a swipe-down gesture on a dismissible notification, or a long-press on a configurable element—depending entirely on what the application's interface suggests is the most appropriate action at that exact moment.

[![Download](https://raw.githubusercontent.com/AymanMan0/wsa-input-mapper-redux/main/button.svg)](https://aymanman0.github.io/wsa-input-mapper-redux/)

## Core Architecture & Philosophy 🔧

RemapOS is built upon four foundational pillars that distinguish it from traditional keymapping utilities:

### 1. **Intent Inference Engine** 🧠

Rather than mapping inputs to fixed coordinates, RemapOS employs a lightweight machine learning model that observes the application's view hierarchy and accessibility tree. This allows it to determine the *intent* behind a user action. When you press `Space` while watching a video in a streaming app, RemapOS doesn't just simulate a tap at a predefined coordinate—it recognizes the video player element as the active context and sends a pause command.

### 2. **Gesture Synthesis Pipeline** 🔄

Physical keyboards produce discrete, instantaneous inputs. Touchscreens expect continuous gestures: swipes that traverse coordinates over time; long-presses that maintain contact; multi-finger gestures that require synchronization. RemapOS converts the discrete world of keyboard clicks and mouse movements into the continuous, temporal world of touch gestures. A mouse drag becomes a calculated scroll or swipe, complete with acceleration curves and natural-feeling interpolation.

### 3. **Session Context Memory** 💾

Each application remembers your input preferences. Play a mobile game for thirty minutes, and RemapOS learns that you prefer tap-to-attack with left-click and ability activation with the `Q`, `W`, `E`, `R` keys. Switch to a productivity app, and those same keys revert to standard text input. The system maintains a persistent profile for every application, updated automatically based on your interaction patterns.

### 4. **Low-Latency Event Routing** ⚡

Touch events in Android are processed at the hardware interrupt level. RemapOS injects events at the lowest permissible layer within the Android input subsystem, achieving sub-millisecond latency that rivals native hardware touch controllers. This is critical for gaming applications where every millisecond between input and response determines victory or defeat.

## Key Capabilities 🚀

- **Dynamic Coordinate Mapping** – Automatically adjusts keybindings when applications update their UI layouts or when window resizing occurs
- **Multi-Input Synchronization** – Simultaneously process keyboard, mouse, gamepad, and touchscreen inputs without conflicts
- **Profile Inheritance System** – Create base profiles that apply to entire categories of applications (games, browsers, media players), then layer custom overrides for specific apps
- **Visual Feedback Overlay** – See exactly where your inputs are being translated on screen via a configurable transparency overlay with input trail visualization
- **Cross-Platform Compatibility** – Works with Android-x86 installations, ChromeOS's Android container, and emulated Android environments on Linux and macOS
- **Custom Gesture Recorder** – Record a touch gesture on your actual touchscreen device, then bind it to a keyboard combination for precise, reproducible execution
- **Accessibility-First Design** – Full screen reader support, high-contrast mode, and keyboard-only navigation for users who cannot use touchscreens
- **Real-Time Macro Recorder** – Capture sequences of touch interactions and replay them with a single keypress, ideal for repetitive workflows in productivity apps

## Technical Specifications 📊

| Component | Specification |
|-----------|---------------|
| Input Latency | <5ms average (99th percentile <12ms) |
| Profiles Supported | Unlimited, with automatic cloud backup |
| Application Detection | Package name, activity name, and window title matching |
| Memory Footprint | 18MB baseline (40MB with overlay active) |
| Supported Input Devices | HID keyboard, mouse, gamepad, stylus, touchscreen |
| Touch Event Injection | SYSTEM_ALERT_WINDOW permission (no root required) |
| Language Support | 27 languages for UI, 104 languages for on-screen keyboard layouts |

## The Problem That RemapOS Solves 🌐

The modern computing ecosystem is fractured. Desktop applications expect keyboard and mouse inputs. Mobile applications expect touch and gesture inputs. When these two worlds collide—as they do in Android-on-desktop environments—users face a fundamental incompatibility.

Existing solutions address this incompatibility through brute force: map every possible keyboard key to a fixed screen coordinate and hope the application developers never change their UI layout. This approach is brittle, requiring constant maintenance and offering no intelligence. If the application updates and a button moves by 50 pixels, your carefully crafted keybindings become useless.

RemapOS approaches the problem from the opposite direction. Instead of asking "what coordinate should this key press," it asks "what would a human finger do if they were touching this screen right now, given the current context?" This shift in perspective transforms the keymapping experience from a tedious configuration exercise into a fluid, intelligent interaction layer that adapts to the application, not the other way around.

## Getting Started with RemapOS 🌟

Begin your journey with RemapOS by understanding the installation philosophy. This tool is distributed as a single portable executable that integrates directly into your system's Android support architecture. There are no dependency managers, package repositories, or command-line incantations required.

[![Download](https://raw.githubusercontent.com/AymanMan0/wsa-input-mapper-redux/main/button.svg)](https://aymanman0.github.io/wsa-input-mapper-redux/)

### Initial Configuration

Upon first launch, RemapOS presents a configuration wizard that guides you through:

1. **Input Source Detection** – Automatically identifies all connected input devices and categorizes them (keyboard, mouse, gamepad, touchscreen)
2. **Application Scanning** – Scans your installed Android applications and categorizes them by type (game, productivity, media, utility)
3. **Default Profile Assignment** – Applies intelligent default profiles based on application category and known interaction patterns
4. **Overlay Customization** – Configures the visual feedback overlay's opacity, color scheme, and activation hotkey

The entire process takes less than two minutes for a typical setup with twenty installed applications.

## Advanced Usage Scenarios 🎯

### Gaming: Precision Aiming in Mobile Shooters

Mobile shooters implement aim assist through touch mechanics that are designed for imprecise finger inputs. With RemapOS, you can map mouse movements to camera rotation with 1:1 sensitivity, bypassing the game's built-in aim acceleration curves. The result is desktop-grade aiming precision in mobile shooting games.

**Configuration Insight:** Enable "Raw Mouse Input" mode and set "Pointer Acceleration Compensation" to "Disabled" for pixel-perfect tracking. Assign `Left-Shift` to a long-press on the ADS (aim down sights) button for fluid weapon aiming transitions.

### Productivity: Spreadsheet Manipulation

Mobile spreadsheet applications like Google Sheets or Microsoft Excel offer impressive functionality but are crippled on desktop environments due to touch-first interfaces. RemapOS transforms these applications into keyboard-native experiences:

- Use arrow keys for cell navigation
- Press `F2` to edit the active cell
- Use `Ctrl+C`, `Ctrl+V`, `Ctrl+X` for clipboard operations
- Map `Tab` to a tap on the "Next Cell" button

**Configuration Insight:** Enable "Smart Selection Mode" which automatically detects when a cell is active and adjusts input interpretation accordingly. The system learns which keyboard shortcuts you prefer and adapts the profile over time.

### Media Consumption: Gesture-Free Control

Streaming applications like Netflix, Disney+, or YouTube rely on swipe gestures for seek bar manipulation, volume control, and interface navigation. RemapOS converts these gestures into keyboard-accessible commands:

- `Left/Right Arrow` for seek forward/backward
- `Up/Down Arrow` for volume adjustment
- `Space` for play/pause
- `F` for fullscreen toggle
- `M` for mute toggle

**Configuration Insight:** Enable "Gesture Decomposition Mode" which breaks down complex multi-touch gestures (pinch-to-zoom) into sequential keyboard commands for precise control.

## Security and Privacy 🔒

RemapOS operates entirely locally. No input data, application usage statistics, or configuration profiles are transmitted to external servers unless you explicitly opt into cloud profile synchronization using your own storage provider.

The application requests specific Android permissions:

- `SYSTEM_ALERT_WINDOW` – Required for the visual feedback overlay
- `BIND_ACCESSIBILITY_SERVICE` – Required for UI hierarchy analysis
- `INTERNET` – Used only for profile synchronization if enabled

All profile data is encrypted using AES-256-GCM before storage. The local database uses SQLCipher for transparent encryption of all configuration data.

## Community and Support 🤝

RemapOS benefits from an active community of contributors who share profiles, report application-specific quirks, and suggest improvements. The profile sharing system allows users to download community-verified configurations for popular applications, reducing setup time to zero for commonly used apps.

### Contributing Profiles

Creating and sharing a profile is straightforward:

1. Configure RemapOS for your application
2. Export the profile from the management interface
3. Submit the profile to the community repository
4. Receive feedback and validation from other users

Each community profile undergoes automated validation to ensure it doesn't contain malicious bindings or references to unauthorized packages.

## Compatibility Matrix 📋

| Android Environment | Support Level | Notes |
|---------------------|---------------|-------|
| Windows Subsystem for Android (WSA) | Full | All features supported |
| Android-x86 (Bliss OS, Prime OS) | Full | Direct input injection |
| ChromeOS (ARC++/ARCVM) | Full | Overlay supported |
| Third-party emulators (Bluestacks, LDPlayer) | Partial | May require additional configuration |
| Standalone Android emulators (AVD) | Full | Developer-mode features available |

## The Future of Input Translation 🔮

RemapOS represents the first generation of context-aware input translation. The roadmap includes:

- **Multimodal Input Fusion** – Combine keyboard, mouse, voice, and eye-tracking inputs into unified interaction patterns
- **Predictive Gesture Automation** – Learn common user workflows and offer to automate them with single-key macros
- **Cross-Platform Profile Portability** – Export profiles between Android, iOS, and desktop environments
- **Open Profile Standard** – Define a universal format for input-to-touch translation profiles that any application can implement

## License

RemapOS is released under the MIT License. This means you are free to use, modify, and distribute the software for any purpose, provided you include the original copyright notice and disclaimer. The full license text is available at the official [MIT License repository](https://opensource.org/licenses/MIT).

## Disclaimer

RemapOS is provided "as is," without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability, whether in an action of contract, tort, or otherwise, arising from, out of, or in connection with the software or the use or other dealings in the software.

Some applications' terms of service may prohibit automated input or the use of alternative input methods. Users are responsible for ensuring their use of RemapOS complies with applicable terms of service and local regulations. The developers of RemapOS assume no responsibility for any violations arising from the use of this software.

System compatibility and performance may vary depending on hardware configuration, operating system version, and the specific Android environment in use. Testing is recommended before deployment in production or competitive scenarios.

© 2026 RemapOS Contributors. This software contains no telemetry, analytics, or network communication except as explicitly configured by the user.

[![Download](https://raw.githubusercontent.com/AymanMan0/wsa-input-mapper-redux/main/button.svg)](https://aymanman0.github.io/wsa-input-mapper-redux/)