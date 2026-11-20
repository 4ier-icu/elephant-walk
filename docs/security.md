# Security & Encryption

Elephant Walk is a local-network software KVM. Because any keyboard, mouse, and clipboard sharing tool requires deep operating system permissions, this page documents the exact encryption protocols, network boundaries, platform permissions, and how you can independently verify its behavior.

## 1. Local Network Encryption (Direct Peer-to-Peer, No Cloud Relay)

Your keystrokes, mouse movements, touchpad gestures, clipboard text and images, and screen layouts **stay strictly on your local network** and travel directly between your trusted devices. They are never routed through or uploaded to any cloud server.

| Channel | Implemented Cryptography & Authentication |
| --- | --- |
| **Control & clipboard lane (TCP)** | Enforces **TLS 1.3** with **mutual certificate authentication (mTLS)**. Each device generates its own local **Ed25519** key pair and self-signed X.509 certificate. Every handshake verifies the peer's **SHA-256 public-key fingerprint** (certificate pinning) and binds the protocol version, lane, and device group via ALPN. |
| **High-frequency pointer datagrams (UDP)** | Never sent in plaintext and never uses static keys. After the authenticated TLS 1.3 session is established, independent 256-bit send and receive keys are derived via standard TLS `ExportKeyingMaterial` (`EXPORTER-elephant-motion-v1`). Packets are encrypted with **AES-256-GCM** using strictly monotonic 64-bit nonces to reject replayed or forged packets. Keys expire immediately when the connection closes. |
| **Account isolation gate** | When signed in, peer handshakes verify account certificates so devices belonging to another account on the same Wi-Fi (such as an office or shared network) are rejected. |

## 2. What Traffic Leaves Your Local Network?

The Elephant Walk app contains **zero behavioral analytics, tracking, or telemetry**. It only contacts the internet over HTTPS for licensing and updates:

- **Sign-in, trial, and license verification (`license.4ier.icu`, hosted on Cloudflare)**: Email sign-in codes, one-way local device digests used to prevent repeated trials after uninstall, license activation, and a 30-day revocation/refund sync check. Original hardware serials, device names, screen layouts, keystrokes, and clipboard contents are **never uploaded**. Full details are in the [Privacy policy](https://ew.4ier.icu/en/privacy/).
- **Downloads and updates (`download.4ier.icu`)**: Checking for new releases and downloading installers.
- **Payments and transactional emails**: Payments are handled by **Paddle.com** (Merchant of Record); verification and license emails are delivered via **Resend**.

**Works offline**: Once activated, your devices continue sharing keyboard, mouse, and clipboard even without an internet connection; online access is only needed for initial activation and periodic license status checks.

## 3. Least-Privilege Platform Permissions

- **macOS (Apple silicon, macOS 13+)**: Requests Local Network (peer discovery), Accessibility, and Input Monitoring (capturing and injecting keyboard/mouse input across screens).
- **Windows (Windows 10 / 11)**: Portable `ElephantWalk.exe` with no installer or administrator rights required for normal use; only requires allowing local Private network access in Windows Firewall. Because Elephant Walk does not yet have a Microsoft-recognized commercial code-signing certificate, Windows SmartScreen may show a warning on first launch.
- **Linux (64-bit, GNOME / KDE / X11 / niri)**: Installs into your user directory (`~/.local/share/elephant-walk`). The install script asks for your local password once only if you want lock-screen virtual input via `uinput`, and **never** adds your account to the `input` group that reads physical keyboards. If you decline, desktop sharing after unlock still works normally.
- **Android (Android 11+)**: Uses a one-time setup via Developer options and Wireless debugging to authorize local input injection and background bidirectional clipboard sync. **No root, no Shizuku, no accessibility service, and no notification permission required.**

## 4. How to Verify Network Behavior Yourself

Elephant Walk is closed-source commercial software, so you do not have to take these claims on faith—you can verify them directly:

1. **Inspect outbound connections**: Run Little Snitch or LuLu on macOS, or monitor sockets with `ss` / firewall logs on Linux and Windows. While typing, moving the cursor across screens, and copying text or images, verify that no packets are sent to any external internet host.
2. **Inspect LAN packets**: Capture local traffic between two paired devices with Wireshark or `tcpdump`. Control and clipboard connections negotiate TLS 1.3, and UDP motion packets (header prefix `EWM1`) carry authenticated AES-256-GCM ciphertext—no plaintext keystrokes or clipboard data appear on the wire.

## 5. Developer & Security Contact

Elephant Walk is developed and maintained by independent developer **Fourier · 4ier (Fu Yang)**. To report a security issue or ask about the architecture, email [hello@4ier.icu](mailto:hello@4ier.icu) or open an issue on the [public GitHub repository](https://github.com/41er1cu/elephant-walk).
