<p align="center">
  <img src="assets/wincore11-logo.png" width="128" alt="WinCore 11 Logo">
</p>

<h1 align="center">WinCore 11</h1>

<p align="center">
  <b>A cleaner, faster Windows 11 — without compromising what matters.</b>
</p>

<p align="center">
  <img src="assets/no-ai-slop.jpg" width="1000">
</p>

<p align="center">

[![Download autounattend.xml](https://img.shields.io/badge/⬇%20Download-autounattend.xml-107C10?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/WinCore11/WinCore11-Build/releases/latest/download/autounattend.xml)
[![Version v1.0.0 (Latest)](https://img.shields.io/badge/Version-1.0.0%20Latest-0078D4?style=for-the-badge&logo=github&logoColor=white)](https://github.com/WinCore11/WinCore11-Build/releases/latest)

</p>

---

## 🖼️ Before / After

| Stock Windows 11 | WinCore 11 Edition |
|------------------|-------------------|
| <img src="assets/win11-orijinal.jpg" width="500"> | <img src="assets/win11-wincore11-edition.jpg" width="500"> |

---

## What is WinCore 11?

WinCore 11 is an `autounattend.xml` answer file that fully automates your Windows 11 installation. No ISO modifications, no third-party tools, no shady executables — just Microsoft's own [Answer File](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/update-windows-settings-and-scripts-create-your-own-answer-file-sxs?view=windows-11) technology doing the heavy lifting.

Place it on your USB drive and boot. You'll still select your language, Windows edition, and target disk — then setup takes over. All optimizations, tweaks, and bloatware removal happen automatically in the background. At the end you'll set up your local account name and password, and you're in. No Microsoft account, no junk, no manual configuration.

> [!NOTE]
> WinCore 11 is built around one philosophy: **maximum performance without sacrificing usability.** Xbox and Minecraft compatibility, touchscreen support, Microsoft Store, and biometric login are deliberately preserved. This is not a "nuke everything" script.

> [!NOTE]
> After installation you will find an **Install Winhance** shortcut on your desktop. [Winhance](https://github.com/memstechtips/Winhance) is the excellent tool by memstechtips that WinCore 11 is built on top of. Installing it gives you a GUI to further customize your Windows settings. It is completely optional.

---

## ⚙️ What Does It Do?

### Core Optimizations

- **Bypasses Windows 11 hardware requirements** — TPM, Secure Boot, CPU and RAM checks skipped.
- **No Microsoft account required** — Local account setup only, no forced sign-in.
- **Full privacy** — All telemetry, tracking, and advertising IDs completely disabled.
- **Winhance Power Plan** — Applied automatically for peak sustained performance.
- **Bloatware removed** — Copilot, OneDrive, sponsored apps, and background junk gone.
- **Smart Windows Updates** — Auto-updates disabled; you get notified when updates are available, you decide when to install.
- **Dark Mode** — Enabled by default. Start Menu pins cleared.
- **Clean Explorer** — Classic right-click context menu, file extensions visible, nav pane decluttered.

### WinCore 11 Exclusive Changes

#### 🌐 Network & Latency
| # | Change | Detail |
|---|--------|--------|
| 1 | **TcpAckFrequency** | Set to `1` — disables Nagle's algorithm, reduces network latency |
| 2 | **TCPNoDelay** | Enabled — packets sent immediately without buffering |
| 3 | **TcpDelAckTicks** | Set to `0` — delayed ACK timer removed for consistent low-latency response |
| 4 | **Network Throttling Disabled** | `NetworkThrottlingIndex` set to `4294967295` — removes artificial bandwidth cap |

#### ⚡ Performance & System
| # | Change | Detail |
|---|--------|--------|
| 5 | **SystemResponsiveness Restored** | Registry key set to 20 - Windows 11 default value. |
| 6 | **Smart Power Throttling** | Battery-aware: disabled on desktops via WMI check, left untouched on laptops |
| 7 | **Faster Shutdown** | Page file clear on shutdown disabled — no functional benefit, only slows shutdown |
| 8 | **Smart SysMain & Prefetcher** | Services left at Automatic — Windows natively detects SSDs vs HDDs and optimizes caching behavior with zero manual WMI scripting required |
| 9 | **Win32PrioritySeparation** | Set to `38` — adjusts CPU scheduling to favor active foreground applications |
| 10 | **HiberbootEnabled Correct Path** | Applied to `CurrentControlSet` (active) instead of `ControlSet001` (backup) — ensures the setting actually takes effect |

#### 🔒 Security & Stability
| # | Change | Detail |
|---|--------|--------|
| 11 | **UAC Genuinely Re-enabled** | LUA restored at end of setup AND `ConsentPromptBehaviorAdmin` set to `5` with `PromptOnSecureDesktop = 1` — the "allow this app to make changes" popup works properly and securely |
| 12 | **Touch & Biometrics Active** | WbioSrvc and TabletInputService left running — required for fingerprint login and touch input |
| 13 | **Driver Updates Preserved** | `ExcludeWUDriversInQualityUpdate` removed — GPU, WiFi, Bluetooth and other hardware drivers continue to receive updates through Windows Update |
| 14 | **Office & Microsoft App Updates Preserved** | `AllowMUUpdateService` removed — security patches for Office and Microsoft apps continue to arrive through Windows Update |
| 15 | **Disk Health Monitoring Preserved** | Autochk Proxy scheduled task left enabled — Windows continues to quietly monitor disk health and warn of issues before data loss occurs |
| 16 | **ProtectYourPC** | Set to `3` during OOBE to manually control and strictly enforce security settings instead of relying on default OOBE configurations |

#### 🎮 Gaming & Apps
| # | Change | Detail |
|---|--------|--------|
| 17 | **Xbox & Gaming Apps Kept** | GamingApp, XboxApp, TCUI and related packages preserved for out-of-box gaming compatibility |
| 18 | **Microsoft Store Kept** | Store retained — required for app updates, drivers, and modern app delivery |
| 19 | **Essential Apps Kept** | Mail & Calendar, Alarms & Clock, Camera, Paint retained — no offline alternative ships with Windows |
| 20 | **Windows Photos Kept** | Modern Photos app preserved — no functional replacement exists in stripped setups |
| 21 | **Edge Retained** | EdgeRemoval script omitted — removal breaks with every Windows update anyway |
| 22 | **XblAuthManager** | Set to Manual start — triggers on demand to preserve Xbox compatibility while saving idle resources |
| 23 | **NVIDIA-Only Tweaks Gated** | `EnableGR535` registry key only applied when an NVIDIA GPU is detected via WMI — AMD and Intel users no longer get orphaned NVIDIA registry entries |

#### 🖥️ UI & Desktop
| # | Change | Detail |
|---|--------|--------|
| 24 | **Start Menu Centered** | `TaskbarAl = 1` — preserves Windows 11 default layout, avoids taskbar rendering issues |
| 25 | **Taskbar Icon Size Default** | `TaskbarSmallIcons` removed — unsupported on Win11, causes rendering glitches with no performance gain |
| 26 | **System Tray Unchanged** | Overflow behavior left at default — avoids forcing all icons visible and cluttering the bar |
| 27 | **Default UI Animations** | Visual effects and animations left untouched — Win11 animations run on the GPU, disabling them degrades the UX with no CPU benefit |
| 28 | **File Explorer Default** | Launches to "This PC" for all users, applied via DefaultUser hive |
| 29 | **IsEducationEnvironment Removed** | Redundant education flag stripped — `HideRecommendedSection` already cleanly hides the Recommended section without side effects |
| 30 | **Home Network Profile** | `NetworkLocation` set to `Home` instead of `Work` — enables network discovery, file sharing, and visibility of other home devices like phones and smart TVs |

#### 🖱️ Input
| # | Change | Detail |
|---|--------|--------|
| 31 | **Mouse Acceleration Fully Disabled** | All three required values set: `MouseSpeed = 0`, `MouseThreshold1 = 0`, `MouseThreshold2 = 0` — equivalent to unchecking "Enhance pointer precision" in Control Panel, which is what competitive gamers expect |

#### 🔔 Notifications & Background
| # | Change | Detail |
|---|--------|--------|
| 32 | **Selective Notification Blocking** | Only Microsoft promotional notifications blocked — important system notifications like Windows Defender alerts, battery warnings, and app toasts (WhatsApp, Spotify) remain fully functional |
| 33 | **Sleep & Lock Kept** | Start Menu power options and Win+L retained — removing them breaks expected UX |

---

## 📋 Requirements

- A **licensed copy of Windows 11** (Home or Pro)
- A **bootable Windows 11 USB drive** (created with [Rufus](https://rufus.ie) or [Ventoy](https://ventoy.net))
- At least **8 GB** USB drive
- A PC with **internet access** after installation (for drivers and updates)

> [!IMPORTANT]
> Hardware requirement bypasses (TPM, Secure Boot) are included. However, installing on unsupported hardware means you take full responsibility for update compatibility going forward.

---

## 🚀 Usage

> [!IMPORTANT]
> The file **must** be named exactly `autounattend.xml`. Any other name will be silently ignored by the Windows installer.

1. Download `autounattend.xml` using the button above.
2. Place it at the **root** of your bootable Windows 11 USB drive.
3. Boot from the USB and proceed with installation as normal.
4. Setup will handle everything automatically. No prompts, no choices — just a clean install.

---

## ❓ FAQ

**Does this work with Windows 10?**
No. WinCore 11 is built specifically for Windows 11. Some tweaks are incompatible with Windows 10 and may cause unexpected behavior.

**Will I still receive Windows Updates?**
Yes. Automatic updates are disabled but you will be notified when updates are available. You can install them manually at any time through Windows Update settings.

**Is this safe to use?**
WinCore 11 uses only Microsoft's official answer file mechanism — no third-party tools, no modified ISOs, no injected executables. You can inspect every line of the XML yourself.

**Does this work with Windows 11 Home and Pro?**
Yes. Both editions are supported. The file presents all available editions during setup so you can choose.

**Can I use this on a laptop?**
Yes. Power throttling settings are battery-aware and will not affect laptop battery life. SysMain and Prefetcher are also preserved automatically if an HDD is detected.

**Does it remove Microsoft Edge?**
No. Edge removal breaks with every major Windows update and causes system instability in some configurations. Edge is kept but you are free to install and use any browser you prefer.

**Will Xbox and Game Pass still work?**
Yes. All Xbox-related components are preserved specifically for this reason.

**What is the Winhance shortcut on my desktop?**
After installation you will find an "Install Winhance" shortcut. [Winhance](https://github.com/memstechtips/Winhance) is a powerful Windows customization tool by memstechtips that WinCore 11 is built on top of. It is completely optional — click it if you want a GUI to further tweak your system, or ignore it.

**Will my mouse acceleration be disabled?**
Yes, all three required registry values are set to fully disable mouse acceleration — equivalent to unchecking "Enhance pointer precision" in Control Panel.

---

## ⚠️ Disclaimer

WinCore 11 is an independent, community-built project and is not affiliated with, endorsed by, or supported by Microsoft Corporation.

By using this file you acknowledge that:
- You own a valid Windows license.
- You understand that bypassing hardware requirements may affect eligibility for future Windows updates.
- The authors of WinCore 11 are not responsible for any data loss, system instability, or damage resulting from use of this file.
- All changes are applied at your own risk.

Always back up your data before a fresh installation.

---

## 🙏 Acknowledgements

Built on top of the outstanding work by **[memstechtips](https://github.com/memstechtips)** and the **[UnattendedWinstall](https://github.com/memstechtips/UnattendedWinstall)** project. WinCore 11 extends that foundation with compatibility fixes, hardware-aware optimizations, security corrections, and a usability-first philosophy.
