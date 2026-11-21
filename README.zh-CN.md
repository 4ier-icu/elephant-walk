# 大象漫步（Elephant Walk）

**一套键鼠，走过你桌上的每块屏——纯局域网、TLS 1.3 加密的四端跨屏键鼠共享软件（软 KVM）。**

[中文官网](https://ew.4ier.icu/zh/) · [English README](README.md) · [安装说明](https://ew.4ier.icu/zh/install/) · [平台兼容矩阵](docs/compatibility.md) · [安全与加密](docs/zh/security.md) · [软件对比](docs/zh/compare.md) · [常见问题](docs/zh/faq.md) · [更新记录](docs/zh/changelog.md)

> 本仓库为**大象漫步（Elephant Walk）**的公开文档中心、版本更新记录与公开 Issue 反馈入口（主程序为闭源商业软件，$9.90 一次买断，提供 1 天完整免费试用且无需绑卡）。

---

## 核心特性

- **四端同一个应用**：
  - **macOS**：Apple 芯片（M1 及以上），macOS 13+
  - **Windows**：Windows 10 / 11（免安装便携 x64 `.exe` 与 ARM64）
  - **Linux**：64 位 **GNOME、KDE、X11、niri**（原生支持 Wayland 与 X11）
  - **Android**：Android 11+ 手机与平板（首次无线调试引导授权；**免 Root、免 Shizuku、不申请无障碍服务、无常驻通知**）
  - *不支持*：iOS / iPadOS、Intel 芯片 Mac
- **局域网零配对自发现**：同 Wi-Fi 打开即自动发现并重连，无需手填 IP 和端口。
- **真实物理毫米排列**：按桌面实际比例排布屏幕（12 毫米吸附、0.5 毫米接触容差），安卓平板横竖屏旋转时按邻居接缝自动贴边重锚，不重置回左上角。
- **双向文字与图片剪贴板**：电脑与安卓手机/平板之间直接复制粘贴文字和图片，不依赖聊天软件中转。
- **简单买断制**：**$9.90 美元一次买断**，一人购买不限设备、同住家人可共用、终身免费更新、无订阅；先提供 1 天完整免费试用（鼠标首次跨屏时开始计时）。

---

## 安全与局域网加密

你的键盘输入、鼠标轨迹、手势、剪贴板内容和屏幕排列**全部只在局域网内点对点加密直连，绝不经过云端**：

- **控制与剪贴板通道（TCP）**：强制 **TLS 1.3** 双向证书认证（mTLS），每次握手校验对端 **Ed25519** 公钥 SHA-256 指纹。
- **高频指针通道（UDP）**：基于已认证 TLS 1.3 会话导出双向独立密钥，采用 **AES-256-GCM** 加密与严格单调 64 位防重放序号。
- **零行为遥测**：应用本体不含任何行为统计或埋点。

完整架构与 Wireshark / Little Snitch 自己抓包验证方法见：[安全与加密说明](https://ew.4ier.icu/zh/security/)。

---

## 问题反馈与联系

- 请直接在本仓库提交 [Issue](https://github.com/4ier-icu/elephant-walk/issues)，注明操作系统与桌面环境（例如 macOS 15、Ubuntu GNOME Wayland、niri、Windows 11、Android 14）及复现步骤。
- 邮件联系与安全反馈：**hello@4ier.icu**
- 开发者主页：**[四叶虫·4ier (https://4ier.icu/)](https://4ier.icu/)**
