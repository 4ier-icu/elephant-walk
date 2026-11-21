# Security Policy

## Reporting a Vulnerability

If you discover a security issue in **Elephant Walk**, please report it privately by email:

- **Email**: [hello@4ier.icu](mailto:hello@4ier.icu)

Please include:
- Affected OS / desktop environment and Elephant Walk version
- Steps to reproduce or packet/log observations
- Expected vs. actual security impact

We acknowledge reports promptly and coordinate fixes before public disclosure.

## Security Architecture Summary

Elephant Walk is designed as a **local-only, peer-to-peer** software KVM:

- **Zero cloud relay**: Keystrokes, mouse movements, touchpad gestures, clipboard text/images, and screen arrangements stay strictly on your local network and travel directly between trusted peers.
- **Control & clipboard lane (TCP)**: Enforces **TLS 1.3** with mutual certificate authentication (**mTLS**), local **Ed25519** device keys, and strict **SHA-256 public-key fingerprint pinning** on every handshake, plus ALPN group/lane binding.
- **Pointer motion datagrams (UDP)**: Derives independent directional 256-bit keys from the authenticated TLS 1.3 session via `ExportKeyingMaterial` and encrypts packets with **AES-256-GCM** using strictly monotonic 64-bit nonces to prevent replay or forgery.
- **Account isolation**: Signed-in accounts verify account certificates on connection so devices from other accounts on the same LAN are rejected.
- **Zero in-app telemetry**: No behavioral analytics or usage tracking.

Full technical specification and independent Wireshark / Little Snitch verification steps:
- English: [docs/security.md](docs/security.md) ([online](https://ew.4ier.icu/en/security/))
- 简体中文: [docs/zh/security.md](docs/zh/security.md) ([在线阅读](https://ew.4ier.icu/zh/security/))
