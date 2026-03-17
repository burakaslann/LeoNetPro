# LeoNet Pro v1.0 🦁

**Network Diagnostics & Internet Speed Test Desktop Application**

LeoNet Pro is a desktop network diagnostics and speed testing application for Windows 10/11. Speed testing, live ping monitoring, Wi-Fi scanning, advanced network diagnostics, iPerf3 throughput testing, and report export — all in a single interface with 6 themes and Turkish/English language support.

---

## Screenshots

![Ana Ekran](screenshots/LeoNetPro1.png)
![iPerf3 / LibreSpeed](screenshots/LeoNetPro2.png)
![Geçmiş](screenshots/LeoNetPro3.png)
![Tanılama](screenshots/LeoNetPro4.png)
![WiFi](screenshots/LeoNetPro5.png)
![Ayarlar](screenshots/LeoNetPro6.png)

---

## Download

👉 **[Download the latest release (LeoNetPro_Setup_v1.0.exe)](https://github.com/burakaslann/LeoNetPro/releases/latest)**

No Python or pip required. Just download and run the setup wizard.

---

## Features

### Speed Testing
- ⚡ **Internet Speed Test** — Speedtest CLI (Ookla) integration; download, upload and ping results
- 🌐 **iPerf3 Real Throughput Testing** — parallel streams, bandwidth cap, continuous traffic mode, live server log with `--logfile` polling
- 🖥️ **iPerf3 Server Mode** — built-in server with live log output, automatic port cleanup on restart
- 🚀 **LibreSpeed Test** — browser-based speed test, no external binary required
- ☁️ **Cloudflare Fallback Speed Test** — when Speedtest CLI is not installed, manual-only download/upload/ping measurement via Cloudflare's public endpoints (rate-limited, not used in scheduled tests)

### Network Diagnostics
- 📡 **Live Ping Monitor** — real-time graph, alert threshold, beep + tray notification on spike
- ⚠️ **Outage History** — automatic connection outage logging (start time, end time, duration)
- 🔬 **Packet Loss & Jitter** — 20-ping measurement, RFC 3550 compliant jitter calculation (inter-packet delay variation)
- 📏 **MTU Discovery** — binary search algorithm for precise Path MTU detection (576–1500), automatic interpretation (Ethernet/Wi-Fi, PPPoE, VPN, VLAN)
- 🫧 **Bufferbloat Test** — bidirectional (simultaneous download + upload load) latency measurement under load, A–F grading
- 🌍 **DNS Analysis** — latency comparison (Local, Cloudflare, Google, OpenDNS, Quad9), DNSSEC validation, DNS over HTTPS (DoH) availability, DNS over TLS (DoT) availability, DNS leak detection
- 🔌 **Gateway Ping** — automatic default gateway detection and latency measurement
- 🔢 **TTL Analysis** — remote OS fingerprinting, hop count estimation
- 🏆 **Network Quality Score** — 0–100 health score calculated from all diagnostic results

### Tools
- 🔍 **Ping Test** — 4-ping with average RTT extraction
- 🔗 **TCP Port Check** — connection test with open/closed/filtered status
- 📡 **UDP Port Check** — UDP probe with ICMP unreachable detection
- 🌐 **DNS Lookup** — forward + reverse resolution
- 🗺️ **Traceroute** — live hop-by-hop display with per-hop timeout

### Wi-Fi
- 📶 **Wi-Fi Scanner** — SSID list with signal (dBm), channel, band (2.4 / 5 / 6 GHz), security type + channel map

### Reporting & History
- 🔬 **TR-143 OCR Analysis** — automatic speed value extraction from screenshots via Tesseract OCR
- 📈 **Test History & Charts** — SQLite database, time-series graphs with theme-aware colors, QTableWidget with sortable columns
- 📁 **CSV Export** — full test history in Excel-compatible format
- 💾 **DB Export** — direct SQLite database export
- 📄 **PDF Report** — TR-143 compliant professional PDF report
- 📊 **Summary Report** — statistical overview (avg/max/min, pass/warn/fail rates)

### Alerts & Notifications
- 🔔 **Email Alerts** — automatic SMTP notification on speed test failure
- 🪝 **Webhook Alerts** — Slack / Teams / Discord / custom webhook support
- 🖥️ **System Tray** — run in background, tray notifications, right-click context menu

### Customization
- 🎨 **6 Themes** — Light, Dark Navy, Forest Green, Sunset Orange, Cherry Blossom, Midnight Black
- 🇹🇷 🇬🇧 **Turkish / English** — instant language switch, no restart required
- ⏱️ **Auto Test** — scheduled speed test every N minutes (requires Speedtest CLI)
- 🔊 **Sound Effects** — click and alert sounds with mute toggle
- 📐 **Mini Widget** — floating mini speed display

---

## Getting Started

### 1. Download Setup

Go to [Releases](https://github.com/burakaslann/LeoNetPro/releases) and download `LeoNetPro_Setup_v1.0.exe`.

Run the setup wizard — iPerf3 and Tesseract OCR are included as optional components.

### 2. Install Speedtest CLI ⚠️

> **Required for internet speed testing and scheduled tests**
>
> LeoNet Pro uses **Ookla's Speedtest CLI**.
> This binary is **not bundled** with the application.
>
> Download: https://www.speedtest.net/apps/cli
>
> If Speedtest CLI is not found, a **Cloudflare-based fallback test** will be available for manual use only. Scheduled/automatic tests require Speedtest CLI.

### 3. Run

Double-click `LeoNet Pro` from the desktop shortcut or Start Menu.

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Ctrl+Enter` | Calculate TR-143 |
| `Ctrl+T` | Start / Stop Speed Test |
| `F5` | Reload Logs |
| `Ctrl+K` | Copy Result to Clipboard |
| `Ctrl+O` | OCR Screenshot Analysis |
| `Ctrl+P` | Generate PDF Report |
| `Ctrl+W` | Clear Form |
| `Ctrl+M` | Toggle Mini Widget |
| `Ctrl+D` | Go to Diagnostics Tab |
| `Ctrl+H` | Go to History Tab |
| `Ctrl+,` | Go to Settings Tab |
| `F11` | Cycle Themes (6 themes) |
| `Ctrl+Q` | Quit Application |

---

## Tabs

| # | Tab | Content |
|---|-----|---------|
| 0 | 🏠 Home | TR-143 calculator, OCR, speed test, live gauges, stopwatch |
| 1 | ⚡ iPerf3 / LibreSpeed | iPerf3 client & server, LibreSpeed, Ping/TCP Port/UDP Port/DNS/Traceroute |
| 2 | 📊 History | SQLite history table, trend charts, CSV/DB export, summary report |
| 3 | 🔬 Diagnostics | Live ping monitor, full network diagnostics, outage log, quality score |
| 4 | 📶 Wi-Fi | Scanner, 2.4/5/6 GHz channel map |
| 5 | ⚙️ Settings | Language, theme, email/webhook alerts, sound toggle |

---

## Network Diagnostics Details

| Test | Method | Details |
|------|--------|---------|
| Packet Loss | 20× ICMP ping | Percentage of lost packets |
| Jitter | RFC 3550 | Mean inter-packet delay variation |
| Avg. Ping | 20× ICMP | Average round-trip time |
| MTU Discovery | Binary search with DF bit | Precise Path MTU (576–1500 bytes) |
| Bufferbloat | Bidirectional load + ping | Simultaneous DL+UL traffic, A–F grade |
| DNS Latency | Raw UDP queries × 3 | Median latency for 5 DNS providers |
| DNSSEC | Cloudflare DoH AD flag | Authenticated Data validation check |
| DoH | HTTPS probe | DNS over HTTPS availability |
| DoT | TLS handshake on port 853 | DNS over TLS availability |
| DNS Leak | whoami.akamai.net | Resolver IP disclosure test |
| Gateway | Auto-detect + 5× ping | Default gateway latency |
| TTL/Hops | ICMP TTL analysis | Remote OS guess, hop count estimate |
| Interfaces | ipconfig /all | Full network adapter listing |

---

## Privacy & Network Usage

LeoNet Pro does **not** collect, transmit, or store any personal data on external servers. All test results are stored locally in a SQLite database on your computer.

Network connections are made **only** when you initiate a test:
- Speedtest CLI servers (Ookla) — when running a speed test
- Cloudflare CDN (`speed.cloudflare.com`) — fallback speed test only, manual trigger only, rate-limited (min. 30s between tests)
- Cloudflare CDN (`speed.cloudflare.com`) — temporary download/upload during bufferbloat diagnostic (single-use, user-initiated)
- Cloudflare DNS (`cloudflare-dns.com`) — DNSSEC/DoH/DoT check during diagnostics
- iPerf3 servers — user-specified addresses only
- ICMP/DNS/TCP/UDP — diagnostic probes to user-specified targets
- GitHub Releases API — optional update check

**No background network activity occurs without explicit user action.**

---

## System Requirements

- Windows 10 / 11 (64-bit)
- 700 MB disk space (after installation)
- 4 GB RAM (recommended)
- Internet connection (for speed testing)

---

## Third-Party Notices

**Speedtest CLI** — Ookla LLC. Binary not bundled with this software.
LeoNet Pro is not affiliated with, endorsed by, or sponsored by Ookla LLC.
Speedtest® is a registered trademark of Ookla LLC.
https://www.speedtest.net/apps/cli

**iPerf3** — BSD License. Copyright © The Board of Trustees of the University of Illinois.
https://iperf.fr

**LibreSpeed** — LGPL License. https://librespeed.org

**Tesseract OCR** — Apache License 2.0. Copyright © Google Inc.
https://github.com/tesseract-ocr/tesseract

**Cloudflare** — `speed.cloudflare.com` and `cloudflare-dns.com` endpoints are used solely as diagnostic and fallback speed measurement tools. This usage is manual-only, rate-limited, minimal in volume, and non-commercial. LeoNet Pro is not affiliated with, endorsed by, or sponsored by Cloudflare, Inc. Cloudflare® is a registered trademark of Cloudflare, Inc.

---

## Disclaimer

THIS SOFTWARE IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED. THE DEVELOPER ASSUMES NO LIABILITY FOR ANY DAMAGES ARISING FROM ITS USE. USERS ARE SOLELY RESPONSIBLE FOR COMPLIANCE WITH ALL APPLICABLE LAWS, REGULATIONS, AND THIRD-PARTY TERMS OF SERVICE. SEE [EULA.txt](EULA.txt) FOR FULL TERMS.

---

## License

Personal and educational use is free and unrestricted.
Commercial use is prohibited without prior written permission.

See [EULA.txt](EULA.txt) for full terms.

---

## Author

Developed by **Burak Aslan**

📧 GitHub: [github.com/burakaslann/LeoNetPro](https://github.com/burakaslann/LeoNetPro)
