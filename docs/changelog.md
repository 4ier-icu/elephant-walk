# Changelog & Platform Support

Public release history and verified platform support matrix for Elephant Walk.

## Platform Support Matrix (1.0)

| Platform | Supported Versions | Setup & Permissions | Auto-Update |
| --- | --- | --- | --- |
| **macOS** | Apple silicon (M1 or later), macOS 13+ | Native app; Local Network, Accessibility, Input Monitoring | Yes |
| **Windows** | Windows 10 / 11 (x64 portable & ARM64) | Portable `.exe`, no installer or admin rights needed | Replace `.exe` (settings preserved) |
| **Linux** | 64-bit GNOME, KDE, X11, and niri | Native Wayland & X11; optional one-time `uinput` lock-screen permission | Yes |
| **Android** | Android 11+ phones and tablets | One-time Wireless debugging setup; no root, no Shizuku, no persistent notification | In-app update |
| **iOS / iPadOS** | Not supported | Explicitly outside current product scope | — |

## Version 1.0 (November 2026)

First public release across all four platforms.

- **Four-platform local software KVM**: Move one mouse, touchpad, and keyboard seamlessly across macOS, Windows, Linux (Wayland & X11), and Android along physical screen edges, with fused input across computers in the same workspace.
- **True physical-scale layout**: Millimeter-accurate screen layout with 12 mm snap distance and 0.5 mm seam tolerance; rotating a tablet or changing display geometry re-anchors along its neighbor seam instead of resetting to the top-left corner.
- **Bidirectional text & image clipboard**: Copy text or images on any computer or Android device and paste directly on another over the local network—no messaging apps or cloud relays.
- **Multi-finger gestures on Android**: Tap, two-finger scroll, swipe right to go back, three-finger left/right to switch apps, swipe up for app switcher, and swipe down for notifications.
- **Encrypted local architecture**: Direct peer-to-peer LAN connections using TLS 1.3 mutual authentication (mTLS) with Ed25519 public-key pinning for control/clipboard lanes, and per-session AES-256-GCM with anti-replay nonces for UDP pointer datagrams; zero in-app telemetry.
- **Simple licensing**: Full 1-day free trial (no card required; starts on your first screen crossing) and $9.90 USD one-time purchase covering unlimited personal devices with free lifetime updates, plus account-based LAN isolation.
- **16 languages**: Automatically follows system language across English, Simplified/Traditional Chinese, Japanese, Korean, Spanish, French, German, Brazilian Portuguese, Russian, Italian, Turkish, Vietnamese, Indonesian, Thai, and Arabic.
- **Post-launch refinements**: Improved macOS Mission Control and bottom-seam Dock arbitration during remote sharing, seamless layout edits without stale-version rejections, and preserving device groups and layouts across account sign-in/sign-out.
