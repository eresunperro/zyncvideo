# Zync — Professional Multi-Camera Audio Sync

> **Automatic, frame-accurate multilayer audio synchronization for DaVinci Resolve**

---

## 🎯 Why Zync?

| Benefit | Impact |
|---------|--------|
| **Save Hours Per Day** | Automated sync eliminates manual audio alignment — sync 10+ cameras in minutes |
| **Frame-Accurate Results** | Sub-frame precision using AI waveform analysis |
| **Enterprise-Ready** | Handles VFR, RAW, and long-form multi-day recordings with drift correction |
| **Seamless Integration** | Native DaVinci Resolve extension — no external apps or context switching |

---

## ⚡ Key Features

✨ **Multi-source synchronization** — Any camera or recorder to master track  
🎯 **Frame-accurate alignment** — Waveform cross-correlation with <1 frame error  
📼 **Professional media support** — VFR, R3D, BRAW, iPhone MOV  
🔀 **Drift correction** — Handles long recordings with sample rate drift  
🎬 **Timeline assembly** — Multi-cam timeline built automatically  
🌍 **Bilingual UI** — Full English & Spanish support  

---

## 📥 Quick Install

**DaVinci Resolve 18+ (macOS)**

```bash
# 1. Download
curl -O https://github.com/perritodev/zyncvideo/releases/download/v1.0.3/Zync-DaVinci-Installer.pkg

# 2. Install
sudo installer -pkg Zync-DaVinci-Installer.pkg -target /

# 3. Restart DaVinci Resolve

# 4. Launch
# Workspace → Workflow Integrations → Zync
```

**That's it.** Python dependencies install automatically.

---

## ✅ Requirements

- DaVinci Resolve 18 or later
- macOS 12+
- 8 GB RAM
- External Scripting enabled (one-time setup, see below)

---

## 🎬 How to Use

### Step 1: Open Zync in DaVinci Resolve
1. Create or open a DaVinci Resolve project
2. Import your camera clips and master audio file into the Media Pool
3. Go to **Workspace → Workflow Integrations → Zync**

### Step 2: Select Your Media
- **Camera Timelines:** Zync lists all timelines in your project. Check the boxes next to each camera timeline you want to sync
  - *Note: Each camera should be in its own timeline for Zync to detect it*
- **Master Audio:** Zync lists audio files from your Media Pool. Select your primary audio track, or click **Browse** to choose a file from disk (must be 40+ seconds)
- **Output Timeline Name:** Give your synced timeline a name (e.g., "SYNC_MULTICAM")

### Step 3: Click Sync
- Zync analyzes the audio waveforms and automatically aligns all clips to your master
- Progress appears in the log window
- Once complete, a new timeline is created with all clips synced

### Step 4: Review & Edit
- New timeline appears in your project automatically
- All clips are positioned frame-accurately to match the master audio
- Make any fine adjustments in the timeline if needed

**That's it.** Your multicam timeline is ready to edit.

---

## 💡 Tips

- **Master audio should be at least 40 seconds long** for reliable sync
- **All clips must overlap with the master audio** (even partially)
- **Handles long recordings:** Works with hours of footage, including drift correction
- **Multiple masters:** Run Zync multiple times with different master files if needed

---

## ⚙️ Enable External Scripting (One-Time Setup)

1. Open DaVinci Resolve → **Preferences**
2. Go to **General** tab
3. Set **External scripting using** to **Local**
4. Restart DaVinci Resolve

---

## 🛠️ Troubleshooting

| Issue | Fix |
|-------|-----|
| Extension doesn't appear in menu | Restart DaVinci Resolve completely |
| "Cannot connect to DaVinci" | Verify External Scripting is set to **Local** in Preferences |
| Master audio won't sync | Ensure master audio is 40+ seconds long and overlaps with camera clips |
| Installer fails | Run: `sudo installer -pkg Zync-DaVinci-Installer.pkg -target /` |

---

## 📊 Performance

- **Typical 10-camera sync:** 2-5 minutes
- **Accuracy:** Sub-frame (better than ±1 frame)
- **Processing:** Local (no cloud upload)
- **Supported duration:** Hours to days per recording session

---

## 📈 Latest Release

### v1.0.3 — May 18, 2026

**✅ What's Fixed**
- iPhone MOV files with embedded audio now sync perfectly
- Improved audio extraction for all video formats
- Better error detection and reporting

**🔧 For Teams**
- Professional-grade multi-camera synchronization
- Supports enterprise workflows (long form, VFR, RAW)
- Bilingual interface (EN/ES)

**🔗 Get Started**
- [Download Zync](https://github.com/perritodev/zyncvideo/releases)
- [Full Release Notes](https://github.com/perritodev/zyncvideo/releases/tag/v1.0.3)

---

## 📞 Support

For installation help or feature requests:
- **GitHub Issues:** [Report a bug](https://github.com/perritodev/zyncvideo/issues)

---

*Professional multi-camera audio synchronization for DaVinci Resolve*
