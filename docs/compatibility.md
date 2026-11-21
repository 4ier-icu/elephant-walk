# Platform & Desktop Compatibility Matrix

This document tracks the verified operating systems, Linux desktop environments, permissions, and explicit non-goals for **Elephant Walk 1.0**.

## Supported Platforms

| Platform | Supported Versions | Architecture | Required Permissions / Setup | Auto-Update |
| --- | --- | --- | --- | --- |
| **macOS** | macOS 13 (Ventura) or newer | Apple silicon (M1 or later) | Local Network, Accessibility, Input Monitoring | Built-in |
| **Windows** | Windows 10, Windows 11 | x64 (portable `.exe`) & ARM64 (`.zip`) | No installer or admin rights needed; allow Private network in Windows Firewall | Replace `.exe` (settings preserved) |
| **Linux** | 64-bit distributions running **GNOME, KDE, X11, or niri** | x86_64 & ARM64 | User-local install (`~/.local/share/elephant-walk`); optional one-time local password for `uinput` lock-screen input (never adds user to `input` group) | Built-in |
| **Android** | Android 11 or newer (phones & tablets) | ARM64 | One-time setup via Developer options + Wireless debugging (**no root, no Shizuku, no accessibility service, no notification permission**) | In-app update |

## Explicitly Not Supported

- **iOS / iPadOS (iPhone & iPad)**: Outside current product scope.
- **Intel Macs (x86_64 macOS)**: Only Apple silicon Macs are supported.
- **Android 10 or older**: Wireless debugging authorization requires Android 11+.

## Platform-Specific Notes

### Linux (Wayland & X11)
- **GNOME & KDE (Wayland)**: Uses system input portals; GNOME/KDE will prompt you to allow keyboard/mouse sharing when starting a session.
- **niri (Wayland) & X11**: Supported out of the box.
- **Lock-screen input**: Optional one-time `uinput` setup during install. If declined, cross-screen sharing still works normally after unlocking the desktop.
- **Other Wayland compositors (e.g. Hyprland, Sway)**: Not yet listed as officially verified—if you test on another compositor, please share your findings in [Issues](https://github.com/4ier-icu/elephant-walk/issues).

### Windows
- Distributed as a portable `ElephantWalk.exe` (`%LOCALAPPDATA%\Elephant Walk` stores settings and sign-in state).
- **SmartScreen note**: Windows may show "Windows protected your PC" on first launch because Elephant Walk does not yet have a commercial publisher certificate recognized by Microsoft. You can verify the download source is `https://ew.4ier.icu/windows` (`download.4ier.icu`).
- Requires Microsoft WebView2 Runtime (pre-installed on Windows 11 and most Windows 10 systems).

### Android
- Supports edge-to-edge pointer movement, full physical keyboard input, bidirectional text & image clipboard sync, and multi-finger touchpad gestures (tap, two-finger scroll, swipe right for Back, three-finger left/right to switch apps, swipe up for app switcher, swipe down for notifications).
- Rotating a tablet between portrait and landscape automatically re-anchors the screen along its neighbor seam without resetting layout coordinates.

For full install steps, see [https://ew.4ier.icu/en/install/](https://ew.4ier.icu/en/install/) (中文: [https://ew.4ier.icu/zh/install/](https://ew.4ier.icu/zh/install/)).
