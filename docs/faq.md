# Frequently Asked Questions

### Which operating systems and Linux desktops does Elephant Walk support?

Elephant Walk runs on four platforms:
- **macOS**: Apple silicon (M1 or later) on macOS 13 or newer.
- **Windows**: Windows 10 and Windows 11 (portable x64 `.exe` and ARM64 package).
- **Linux**: 64-bit Linux on **GNOME, KDE, X11, and niri** (supporting both Wayland and X11).
- **Android**: Android 11 or newer phones and tablets.

iPhone and iPad (iOS / iPadOS) and Intel Macs are **not** supported.

### Are keystrokes and clipboard data encrypted over Wi-Fi?

Yes. All keyboard input, pointer movement, gestures, and clipboard text/images travel directly over your local network with no cloud relay:
- Control and clipboard lanes enforce **TLS 1.3 with mutual certificate authentication (mTLS)** and **Ed25519 SHA-256 public-key fingerprint pinning** on every handshake.
- High-frequency pointer UDP datagrams use per-connection directional keys derived via TLS `ExportKeyingMaterial` and encrypted with **AES-256-GCM** plus strictly monotonic 64-bit anti-replay nonces.

See [Security & encryption](https://ew.4ier.icu/en/security/) for the full technical breakdown and how to inspect traffic yourself.

### Does Android require root or Shizuku?

No. On Android 11 or newer, Elephant Walk uses a one-time on-screen setup with Developer options and Wireless debugging. It does not require root, Shizuku, accessibility services, or notification permissions, while still delivering full cross-app mouse, keyboard, multi-finger gestures, and background bidirectional text and image clipboard sync.

### Does it work on Linux Wayland without typing IP addresses?

Yes. Elephant Walk natively supports Wayland (GNOME, KDE, niri) and X11, and discovers nearby devices automatically on the local network—no manual IP addresses or port forwarding. When you switch Wi-Fi networks, your group reconnects and restores your screen arrangement automatically.

### How much does Elephant Walk cost, and how many devices are included?

Elephant Walk is a **$9.90 USD one-time purchase** (taxes shown at checkout), with **no subscription** and free lifetime updates. One license covers **unlimited devices** for one person (household sharing is allowed on an honor basis). Before buying, you get a **full-featured 1-day free trial** with no card required—the clock starts the first time your cursor crosses into another device.

### Why is it closed-source, and how can I verify it does not upload my keystrokes?

Elephant Walk is independently built and funded through one-time licenses, so the application itself is closed-source. To earn trust through verifiable facts rather than promises, we document every network endpoint and exact steps to inspect traffic with Wireshark, `tcpdump`, Little Snitch, or LuLu on our [Security & encryption](https://ew.4ier.icu/en/security/) page. If open-source auditability is mandatory for your environment, we explicitly recommend Deskflow on our [Compare](https://ew.4ier.icu/en/compare/) page.

### Does Elephant Walk work offline?

Yes. Once activated, daily keyboard, mouse, and clipboard sharing runs strictly peer-to-peer on your local network without internet access. Internet connectivity is only used for sign-in, license activation, updates, and periodic license sync when online.

### What is the refund policy?

In addition to the free 1-day trial, all orders are processed by Paddle.com (Merchant of Record) and honor regional cancellation and statutory withdrawal rights (such as 7 days unconditional in China, South Korea, Brazil, and Canada, and 14 days in the EU/UK). If an unresolved technical fault prevents Elephant Walk from working on a supported system, email `hello@4ier.icu` for troubleshooting or a full refund. Full details are in the [Refund policy](https://ew.4ier.icu/en/refunds/).
