# Zync — Professional Multi-Camera Audio Sync

> **Automatic, frame-accurate audio synchronization for DaVinci Resolve.**  
> No clapper boards. No manual nudging. Just sync.

---

## ✨ Features

- 🎙️ **Multi-source sync** — Match any camera or recorder audio to a master track automatically
- 🎯 **Frame-accurate alignment** — Sub-frame precision using waveform cross-correlation (librosa)
- 📼 **VFR & RAW support** — Handles Variable Frame Rate media, R3D, BRAW, and more
- 🔀 **Sample rate drift correction** — Compensates for long-recording drift between devices
- 🎬 **DaVinci timeline builder** — Creates a fully assembled multicam timeline in one click
- 🌍 **English & Spanish UI** — Fully localized interface

---

## ⬇️ Installation

### 🎯 Recommended: DaVinci Resolve Workflow Integration

**For DaVinci Resolve 18+ (macOS/Apple Silicon)**

1. Download `Zync-DaVinci-Installer.pkg` from [Releases](https://github.com/perritodev/zyncvideo/releases)
2. Double-click to install (or `sudo installer -pkg Zync-DaVinci-Installer.pkg -target /`)
3. Python dependencies will be installed automatically
4. Restart DaVinci Resolve completely
5. Go to **Workspace → Workflow Integrations → Zync**

**Requirements:**
- DaVinci Resolve 18 or later
- External Scripting enabled (see below)
- Python 3.10-3.13 (will install if missing)
- macOS 12+ for installer method

---

### 🎬 Adobe Premiere Pro CEP Extension (macOS)

**For Adobe Premiere Pro 2023+ (macOS/Apple Silicon)**

1. Download `Zync-Premiere-Installer.pkg` from [Releases](https://github.com/perritodev/zyncvideo/releases)
2. Double-click to install
3. Restart Adobe Premiere Pro (all versions)
4. Open **Window → Extensions → Zync**

**Notes:**
- Audio processor runs in the background automatically
- Supports both Release and Beta Premiere Pro installations
- Python dependencies installed to system Python 3.11

---

### 🍎 Alternative: Standalone App (macOS)

1. Download `Zync_App_Mac.zip` from [Releases](https://github.com/perritodev/zyncvideo/releases)
2. Unzip it — you'll get `Zync.app`
3. **Right-click → Open** the first time (macOS Gatekeeper requires this once)
4. Keep DaVinci Resolve open and click **Sync**!

---

### 🪟 Alternative: Standalone App (Windows)

1. Download `Zync_Windows.zip` from [Releases](https://github.com/perritodev/zyncvideo/releases)
2. **Extract the zip** to any folder
3. Double-click **`install.bat`** (installs dependencies automatically)
4. Open DaVinci Resolve with your project
5. Launch: **Workspace → Workflow Integrations → Zync**

---

## ⚙️ Enable External Scripting in DaVinci Resolve

Zync needs this to communicate with DaVinci:

1. Open **DaVinci Resolve**
2. Go to **Preferences**:
   - **Mac:** DaVinci Resolve → Preferences
   - **Windows:** Edit → Preferences
3. Click **General** tab
4. Set **External scripting using** to **Local**
5. **Restart DaVinci Resolve**

---

## 🛠️ Troubleshooting

| Problem | Solution |
|---------|----------|
| "Cannot connect to DaVinci" | Make sure DaVinci Resolve is open and External Scripting is set to **Local** |
| iPhone MOV files don't sync (low confidence) | **[FIXED in latest release]** — Now uses librosa for robust audio extraction from MOV files |
| Waveform sync shows "no match found" | Make sure master audio file is at least 40+ seconds long and clips overlap with it |
| Installer fails on macOS | Try: `sudo installer -pkg Zync-DaVinci-Installer.pkg -target /` |
| App won't open on Mac | Right-click → Open instead of double-clicking |
| Windows Defender warning | Click **More info → Run anyway** (normal for unsigned apps) |
| No timelines appear | Open a project in DaVinci Resolve first |
| Extension doesn't appear in menu | Restart DaVinci Resolve completely, clear cache: `rm -rf ~/Library/Caches/Blackmagic` |
| Premiere Pro audio processor not starting | Restart Premiere Pro completely; check LaunchAgents: `~/Library/LaunchAgents/com.zync.premiere.audio-processor.plist` |

---

## 📋 System Requirements

| | macOS | Windows |
|---|---|---|
| **OS** | macOS 12+ | Windows 10/11 |
| **DaVinci Resolve** | 18+ | 18+ |
| **Python** | 3.10-3.13 (auto-installed) | 3.10-3.13 (auto-installed) |
| **RAM** | 8 GB+ | 8 GB+ |

---

## 📝 Notes

- **Source code:** Proprietary. This repository distributes compiled public releases only.
- **Support:** Check the troubleshooting section above
- **Updates:** Check [Releases](https://github.com/perritodev/zyncvideo/releases) for the latest version

---

## 📰 Release Notes

### v1.0.3 (May 18, 2026) — iPhone Audio Fix
- **Fixed**: iPhone MOV files with embedded audio now sync correctly via improved audio extraction
  - Now uses librosa's audioread backend first (more robust for MOV codec)
  - Falls back to FFmpeg if librosa unavailable
  - Validates extracted audio to detect degraded/silent extraction
- **Added**: Premiere Pro CEP extension installer (experimental)
- **Improved**: Audio validation to catch extraction failures early

### v1.0.2
- DaVinci Resolve Workflow Integration support
- Initial macOS and Windows standalone apps

---

**Latest Release:** [v1.0.3](https://github.com/perritodev/zyncvideo/releases/tag/v1.0.3)
