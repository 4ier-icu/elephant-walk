Public release history and verified platform support matrix for Elephant Walk.

## Platform Support Matrix (1.1)

| Platform | Supported Versions | Setup & Permissions | Auto-Update |
| --- | --- | --- | --- |
| **macOS** | Apple silicon (M1 or later), macOS 13+ | Native app; Local Network, Accessibility, Input Monitoring | Yes |
| **Windows** | Windows 10 / 11 (x64 portable `.exe` & ARM64 `.zip`) | Portable (no installer or admin rights needed) | Replace `.exe` / unpack zip (settings preserved) |
| **Linux** | 64-bit x86_64 (GNOME, KDE, X11, and niri; no ARM64 yet) | Native Wayland & X11; optional one-time `uinput` lock-screen permission | Yes |
| **Android** | Android 11+ phones and tablets | USB-C scan-free activation or one-time Wireless debugging setup; no root, no Shizuku, no persistent notification | In-app update |
| **iOS / iPadOS** | Not supported | Explicitly outside current product scope | — |

## Version 1.1.0 (November 2026)

Major connectivity, Android pairing, and trial upgrade across all four platforms.

- **USB-C direct connection & scan-free pairing for Android**: Plug in a USB-C cable to authorize and connect Android phones or tablets automatically, keeping cross-screen control reliable even on isolated Wi-Fi or offline setups.
- **Better campus, office & hotel Wi-Fi compatibility**: Improved device discovery and direct connections on restricted Wi-Fi and proxy setups, with clear guidance to switch to USB-C when Wi-Fi isolation is detected.
- **Simultaneous Android pairing QR across computers**: All computers in your group now show the pairing QR code at once—scan any one and the others dismiss automatically, with a centered dialog on Linux and automatic tray reveal on Windows.
- **7-day free trial & 1:1 email license binding**: Extended the full-featured free trial from 1 day to **7 days** (no card required; starts on your first screen crossing), with 1:1 email binding for license codes and a Hong Kong direct route for faster sign-in and activation in mainland China.
- **Layout convergence & stability fixes**: Fixed extra layout gaps that blocked edge crossing after joining or upgrading, repeated Android restarts before pairing, and a stray sign-in window on Linux startup.

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
