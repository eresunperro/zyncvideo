# CEP vs UXP for Zync Premiere Pro Integration

## Current Status
- **CEP extension** (just rebuilt with fixes):
  - ✓ Manifest corrected (removed invalid DispatchInfo)
  - ✓ CSInterface library loader added
  - ✓ HTML/JS script paths fixed
  - ✓ Python backend ready (Flask on localhost:18765)
  - ✓ Installation completes successfully

## Fundamental Platform Requirements for Zync

### What Zync Needs:
1. **Audio waveform analysis** using librosa/scipy (Python scientific libraries)
2. **Cross-platform file access** to read multiple audio files
3. **Subprocess execution** to run Python audio processing
4. **Complex mathematical operations** (FFT, correlation, synchronization algorithms)
5. **Persistent background process** for real-time audio sync

---

## Platform Comparison

### CEP (Common Extensibility Platform) ✓
- **Strengths**:
  - Can spawn Node.js subprocess
  - Can execute Python scripts via subprocess
  - Full file system access (with sandbox restrictions)
  - Can use all Premiere's APIs
  - Supports both HTML/JS UI + native code
  - Persistent background processes possible
  - Mature, well-documented

- **Zync Compatibility**: ✅ FULLY COMPATIBLE
  - Can run the Flask backend
  - Can use librosa/scipy for audio analysis
  - Can handle multi-file workflows
  - Can maintain background audio processor

### UXP (Unified Extensibility Platform) ✗
- **Strengths**:
  - Newer Adobe direction
  - Better sandboxing security
  - Modern JavaScript framework support
  - Appears in Extensions menu reliably

- **Critical Limitations**:
  - ❌ **NO subprocess execution** - Cannot run Python
  - ❌ **NO native module loading** - Cannot use librosa/scipy
  - ❌ **Severely restricted file I/O** - Can only access user-selected files
  - ❌ **JavaScript-only** - Would need to rewrite audio analysis in JavaScript (impractical)
  - ❌ **No persistent background processes** - Killed when extension closes
  - ❌ **Performance limited** - JavaScript audio processing is magnitudes slower than Python/librosa

- **Zync Compatibility**: ❌ NOT VIABLE
  - Would lose all audio processing capability
  - Audio sync algorithm requires librosa (scipy FFT, correlation functions)
  - Implementing real-time waveform analysis in pure JavaScript is not feasible
  - Would result in non-functional audio sync

---

## Why CEP Extension Might Not Be Showing

Potential issues (in order of likelihood):

1. **Extension not reloading after installation**
   - Solution: Force Premiere Pro to reload extensions
   - Mac: `~/Library/Application Support/Adobe/CEP/extensions/.allow_debugging`
   - Or: Complete Premiere restart

2. **CEP not enabled in Premiere Pro**
   - Some Premiere versions require CEP to be explicitly enabled
   - Check: Premiere Preferences → Security

3. **Manifest still has issues**
   - We fixed DispatchInfo, but may need to verify MainPath
   - Try enabling CEP debugging mode

4. **CSInterface.js not loading**
   - Adobe provides this in the Premiere installation
   - Path: `../../utils/CEPEngine.js` (relative to extension location)

5. **Extension directory permissions**
   - Installer runs as root, may need to fix ownership
   - Should be owned by current user, not root

---

## Recommended Next Steps

### Option A: Fix CEP Extension (RECOMMENDED) ✓
1. **Install updated CEP extension** (just pushed to releases)
2. **Test Premiere extension loading**:
   ```bash
   # Enable CEP debugging
   touch ~/Library/Application\ Support/Adobe/CEP/extensions/.allow_debugging
   
   # Force extension reload
   # Quit Premiere completely
   # Delete any cached extension data:
   rm -rf ~/Library/Caches/Adobe/CEP-extensions/
   
   # Restart Premiere Pro
   ```
3. **Check Window → Extensions menu** for "Zync" panel
4. **Check browser console** for JavaScript errors:
   - Premiere: Window → Extensions → Zync → Right-click → Inspect
5. **Monitor logs**:
   - `/tmp/zync_premiere_install.log` - Installation output
   - `/Library/Application Support/Adobe/CEP/extensions/com.zync.premiere/python/launch_audio_processor.sh` - Python backend logs

### Option B: Hybrid Approach (Fallback)
If CEP truly won't work:
1. Build a simple UXP UI extension (cosmetic only)
2. Keep Zync as separate desktop app for actual audio processing
3. UXP extension could launch the desktop app
4. **This is not ideal** - loses integration, creates more friction

---

## CEP Debugging Checklist

If extension still doesn't appear:

- [ ] Extension directory exists: `/Library/Application Support/Adobe/CEP/extensions/com.zync.premiere/`
- [ ] manifest.xml is valid XML (no parse errors)
- [ ] CSXS/manifest.xml has correct Extension Id: `com.zync.premiere`
- [ ] Type is "Panel"
- [ ] MainPath points to valid HTML file: `./index.html`
- [ ] index.html loads without JavaScript errors
- [ ] CSInterface library is accessible
- [ ] Premiere version meets minimum requirement (2023.0+)
- [ ] CEP is not disabled in Preferences
- [ ] No conflicting extensions with same Id

---

## Bottom Line

**CEP Extension is the right choice** for Zync's requirements. We just need to:
1. Verify the extension loads in Premiere
2. Fix any remaining manifest/initialization issues
3. Enable CEP debugging to see actual error messages

**UXP is not viable** because it cannot execute the Python audio analysis code that's core to Zync's functionality.

---

## Files Modified (Latest Build)

- **manifest.xml**: Removed invalid DispatchInfo section
- **index.html**: Added CSInterface.js loader, fixed script paths, added initialization hook
- **Zync-Premiere-Installer.pkg**: Rebuilt 2026-05-17 18:12 UTC

**Test this version first** before considering other approaches.
