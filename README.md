# Elephant Walk (大象漫步)

**Local, TLS 1.3 encrypted software KVM for macOS, Windows, Linux (Wayland & X11), and Android.**

[Website (English)](https://ew.4ier.icu/en/) · [官网（简体中文）](https://ew.4ier.icu/zh/) · [简体中文说明](README.zh-CN.md) · [Install Guide](https://ew.4ier.icu/en/install/) · [Security](docs/security.md) · [Compare](docs/compare.md) · [FAQ](docs/faq.md)

> This repository is the public documentation hub, release log, and issue tracker for **Elephant Walk** (closed-source commercial software, $9.90 USD one-time purchase with a free 1-day full trial and no card required).

---

## What Elephant Walk Does

Move one keyboard, mouse, or touchpad smoothly across the computers, tablets, and phones on your desk—and copy/paste text and images in either direction over your local Wi-Fi.

- **Four platforms in one native app**:
  - **macOS**: Apple silicon (M1 or later), macOS 13+
  - **Windows**: Windows 10 & 11 (portable x64 `.exe` and ARM64)
  - **Linux**: 64-bit **GNOME, KDE, X11, and niri** (native Wayland & X11)
  - **Android**: Android 11+ phones & tablets (one-time Wireless debugging setup; **no root, no Shizuku, no accessibility service, no persistent notification**)
  - *Not supported*: iOS / iPadOS, Intel Macs
- **Zero-IP LAN auto-discovery**: Devices on the same local network discover and connect automatically—no IP addresses or ports to enter when switching Wi-Fi.
- **Physical millimeter-scale layout**: Arrange screens as they actually sit on your desk (12 mm snap, 0.5 mm seam tolerance). Rotating an Android tablet re-anchors along its neighbor seam instead of resetting to the top-left corner.
- **Bidirectional text & image clipboard**: Copy text or images on any desktop or Android device and paste directly on another—no chat apps or cloud relays.
- **Simple one-time pricing**: **$9.90 USD once** for unlimited personal devices (household sharing allowed on an honor basis), free lifetime updates, no subscription. Try free for 1 full day (starts on your first screen crossing, no card required).

---

## Security & Local Network Encryption

All keyboard input, pointer movements, touchpad gestures, clipboard contents, and screen layouts stay **strictly peer-to-peer on your local network** and are never sent to cloud servers:

- **Control & clipboard TCP lanes**: Enforces **TLS 1.3** with mutual certificate authentication (**mTLS**) and **Ed25519** SHA-256 public-key fingerprint pinning on every handshake.
- **High-frequency UDP pointer datagrams**: Per-connection directional 256-bit keys derived via TLS `ExportKeyingMaterial`, encrypted with **AES-256-GCM** and strictly monotonic 64-bit anti-replay nonces.
- **Zero in-app telemetry**: No behavioral analytics or usage tracking.

Read the full architecture and how to independently verify network traffic with Wireshark / Little Snitch: **[docs/security.md](docs/security.md)** (online: [ew.4ier.icu/en/security/](https://ew.4ier.icu/en/security/)).

---

## Honest Comparison

If **open-source auditability** is a hard requirement (e.g., regulated corporate machines), we explicitly recommend **Deskflow** (plus **scrcpy** if needed). If you want Bluetooth HID emulation reaching iPadOS/iOS without Linux, look at **Across**.

If your desk mixes **macOS, Windows, Linux (Wayland/X11), and Android** and you want zero-IP discovery, physical-scale geometry, and bidirectional image clipboard in one native app, see the full matrix in **[docs/compare.md](docs/compare.md)**.

---

## Reporting Issues & Contact

- Open a [GitHub Issue](https://github.com/41er1cu/elephant-walk/issues) with your OS/desktop environment (e.g. macOS 15, Fedora GNOME Wayland, niri, Windows 11, Android 14) and steps to reproduce.
- Direct email / security reports: **hello@4ier.icu**
- Developer homepage: **[四叶虫·4ier (https://4ier.icu/)](https://4ier.icu/)**
