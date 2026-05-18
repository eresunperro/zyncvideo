# ⚠️ Zync for Adobe Premiere Pro — End of Life Notice

## Status: Not Viable
**The Zync Premiere Pro extension is no longer viable and is not recommended for use.**

---

## Why Premiere Pro Support Was Discontinued

### Adobe Phased Out CEP Extensions
- **Beta Premiere Pro (2024+)**: No longer supports CEP extensions — Adobe has transitioned to UXP
- **Release Premiere Pro**: CEP support is legacy and deprecated
- Adobe's direction: All extensions must use UXP (Unified Extensibility Platform)

### UXP Cannot Support Zync's Core Architecture
Zync's audio synchronization algorithm fundamentally requires:
- ❌ **Python subprocess execution** — UXP has no subprocess support
- ❌ **librosa/scipy libraries** — UXP cannot load native Python modules
- ❌ **Background processes** — UXP kills processes when extension closes
- ❌ **Complex file I/O** — UXP restricts file access to user-selected files only

Rewriting Zync for pure JavaScript would eliminate the sophisticated waveform correlation algorithms that make Zync work.

---

## Recommendation
**Use Zync with DaVinci Resolve instead:**
- ✅ Full feature support
- ✅ Multi-camera audio sync with frame accuracy
- ✅ Automatic timeline creation
- ✅ Available in releases: `Zync-DaVinci-Installer.pkg`

---

## Files in This Repository

| File | Status | Notes |
|------|--------|-------|
| `Zync-DaVinci-Installer.pkg` | ✅ Active | Download and use this |
| `Zync-Premiere-Installer.pkg` | ❌ Deprecated | Does not work with Beta or modern Release builds |
| `PREMIERE_INSTALLER_FIX_SUMMARY.md` | ℹ️ Historical | Documents the CEP attempt (for reference only) |
| `CEP_VS_UXP_ANALYSIS.md` | ℹ️ Technical | Detailed analysis of why UXP won't work |

---

**Last Updated**: May 17, 2026  
**Decision**: CEP extension project archived due to platform lifecycle change
