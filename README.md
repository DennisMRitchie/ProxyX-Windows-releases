# ProxyX for Windows

![Platform](https://img.shields.io/badge/Platform-Windows%2011%20x64-0078D4?logo=windows&logoColor=white)
![Status](https://img.shields.io/badge/Status-alpha-orange)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

**A fast VPN/proxy client for Windows, powered by Xray-core.**

ProxyX for Windows is the desktop sibling of the [ProxyX Android app](https://github.com/DennisMRitchie/ProxyX-releases).
This repository hosts the **release builds**: download the latest archive from the
[Releases](../../releases) page.

> **Alpha software.** Expect rough edges. Please report problems in
> [Issues](../../issues).

---

## Features

- **Protocols:** VLESS, VMess, Trojan, Shadowsocks and Hysteria2, with REALITY / TLS
- **Two modes:** system proxy, or full-system **TUN** mode (Wintun adapter)
- **Subscriptions:** import and refresh server lists from a URL; add servers from `vless://`, `vmess://`, `trojan://` and `ss://` share links
- **Real ping:** measures latency through the proxy itself, not just TCP
- **DPI bypass:** built-in Xray TLS fragmentation; optional zapret2 engine with your own strategy
- **Tray icon, start with Windows, auto-connect**
- **Dark / light theme**, UI in English, Russian and German

Planned: per-app split tunneling.

---

## Install

1. Download `ProxyX-v<version>-win64.zip` from [Releases](../../releases).
2. (Optional) Check the file against `SHA256SUMS.txt`:
   `certutil -hashfile ProxyX-v<version>-win64.zip SHA256`
3. Unzip it to a folder of your choice. **Keep all files together**: `proxyx.exe` needs
   `xray.exe`, `tun2socks.exe` and `wintun.dll` next to it.
4. Run `proxyx.exe`. Windows asks for administrator rights (UAC); they are required to create
   the TUN adapter and routes.

The executable is **not code-signed**, so Windows SmartScreen may show a warning on first run
(click *More info*, then *Run anyway*). Antivirus products sometimes flag network tools like this
one; the SHA-256 checksums let you verify that the file is the one published here.

### Requirements

- Windows 11 x64 (primary target). Windows 10 with the WebView2 runtime should work but is not tested.
- WebView2 runtime (preinstalled on Windows 11).

### zapret2 (optional)

The DPI engine is not bundled. It needs the WinDivert driver, which antivirus software often
flags. If you want it, download the official
[zapret-win-bundle](https://github.com/bol-van/zapret-win-bundle) and place `winws2.exe`,
`cygwin1.dll`, `WinDivert.dll`, `WinDivert64.sys` and the `lua` folder in a `zapret` folder
next to `proxyx.exe`. Then pick *zapret2* in Settings, Bypass DPI, and paste a strategy found with
blockcheck2 for your network. A strategy that works on one provider may not work on another.

### Uninstall

Close ProxyX, delete its folder, and remove `%APPDATA%\ProxyX` if you also want to drop your
settings and server list.

---

## License

[MIT](LICENSE) © 2026 Konstantin Lychkov.

The release archive also contains third-party components under their own licenses:
Xray-core (MPL-2.0), tun2socks (MIT) and Wintun (WireGuard Prebuilt Binaries License).
See `THIRD-PARTY-NOTICES.md` inside the archive.

## Disclaimer

ProxyX is a general-purpose network tool. You are responsible for using it in accordance with the
laws of your country and the terms of the services you connect to.
