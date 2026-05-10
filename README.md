# Zync — Pro Multi-Camera Audio Sync for DaVinci Resolve

> **Automatic, frame-accurate audio synchronization for DaVinci Resolve.**
> No clapper boards. No manual nudging. Just sync.

---

## ✨ Features

- 🎙️ **Multi-source sync** — Match any camera or recorder audio to a master track automatically
- 🎯 **Frame-accurate alignment** — Sub-frame precision using waveform cross-correlation
- 📼 **VFR & RAW support** — Handles Variable Frame Rate media, R3D, BRAW, and more
- 🔀 **Sample rate drift correction** — Compensates for long-recording drift between devices
- 🎬 **DaVinci timeline builder** — Creates a fully assembled multicam timeline in one click
- 🌍 **English & Spanish UI** — Fully localized interface

---

## ⬇️ Download

Head to the **[Releases page](https://github.com/eresunperro/zyncvideo/releases)** and download the file for your OS.

---

## 🍎 macOS Installation

> **Requires:** DaVinci Resolve 18 or 19 with **External Scripting** enabled.

1. Download `Zync_App_Mac.zip` from the Releases page.
2. Unzip it — you'll get `Zync.app`.
3. **Right-click → Open** the first time (macOS Gatekeeper requires this once).
4. Keep DaVinci Resolve open in the background and click **Sync**!

---

## 🪟 Windows Installation

> **Requires:** DaVinci Resolve 18 or 19 with **External Scripting** enabled. No Python installation needed — it's bundled inside the app.

1. Download `Zync.exe` from the Releases page.
2. Double-click `Zync.exe` to launch — no installation needed.
3. If Windows Defender shows a warning, click **More info → Run anyway**.
4. Keep DaVinci Resolve open in the background and click **Sync**!

---

## ⚙️ Enable External Scripting in DaVinci Resolve

Zync connects to DaVinci Resolve via its built-in scripting API. You need to enable it once:

1. Open DaVinci Resolve.
2. Go to **DaVinci Resolve → Preferences** (Mac) or **Edit → Preferences** (Windows).
3. Click the **General** tab.
4. Set **External scripting using** to **Local**.
5. Restart DaVinci Resolve.

---

## 🛠️ Troubleshooting

| Problem | Fix |
|---|---|
| "Cannot connect to DaVinci" | Make sure DaVinci Resolve is open and External Scripting is set to **Local** |
| App won't open on Mac | Right-click → Open instead of double-clicking |
| Windows Defender warning | Click **More info → Run anyway** — this is normal for unsigned apps |
| No timelines appear | Open a project in DaVinci Resolve first |

---

## 📋 System Requirements

| | Mac | Windows |
|---|---|---|
| **OS** | macOS 12+ | Windows 10/11 |
| **DaVinci Resolve** | 18 or 19 | 18 or 19 |
| **Python** | Not required (bundled) | Not required (bundled) |
| **RAM** | 8 GB+ | 8 GB+ |

---

*This repository is used exclusively for distributing compiled public releases of Zync. Source code is proprietary.*
