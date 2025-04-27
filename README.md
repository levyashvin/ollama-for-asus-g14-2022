# Running Ollama on AMD GPU (gfx10xx Series) — Setup Guide

This guide explains how to set up **Ollama** to use an AMD discrete GPU (like RX6700S, **gfx1032** for G14 2022).

---

## Steps

### 1. Find your GPU

- Open:
`%localappdata%\Ollama\server.log`

- Look for the `gpu_type` field — you want **gfx10xx** (example: `gfx1032` for G14 2022).
- **Important**:  
- There are 2 GPUs — integrated and discrete. **GPU 0** was the discrete GPU for me (you want to run it on your dGPU).
- Open **Task Manager** (`Ctrl + Shift + Esc`), go to the **Performance** tab and check the GPU type if you aren't sure.

---

### 2. Backup Current Install

- Go to:
`C:\Users%username%.ollama`

- Make a **copy** of the `.ollama` folder and **rename** it with `_backup` at the end.
- *(Optional but recommended)*: Create a **Windows System Restore Point**.

---

### 3. Download OllamaSetup.exe

- Download from: [Ollama for AMD Releases](https://github.com/likelovewant/ollama-for-amd/releases)
- Close Ollama if it’s running (system tray → Task Manager).
- Run the installer.  
*(It’s unsigned — click "More Info" → "Run Anyway")*.
- After installation, check the **hidden system tray** to close the Ollama service that is running.

---

### 4. Install ROCm Libraries

- Go to: [ROCmLibs Latest Release](https://github.com/likelovewant/ROCmLibs-for-gfx1103-AMD780M-APU/releases)
- Download the latest version (e.g., **0.6.2.4** currently).
- Find your gfx version's zip file and download it.
- Some GPUs have **multiple versions** — read carefully before downloading.

> **If the link isn't working**:
> - Visit the [Ollama for AMD Wiki](https://github.com/likelovewant/ollama-for-amd/wiki).
> - Navigate to the **Demo Release Version** section.
> - Find the ROCm libraries for your version (e.g., `rocm.gfx1035.for.hip.sdk.6.1.2.7z`).

---

### 5. Replace ROCm Libraries

- Extract the `.7z` file.  
You should find:
  - A `rocblas.dll` file.
  - A `library` folder.
- Navigate to:
`%localappdata%\Programs\Ollama\lib\ollama`

- Locate the current `rocblas.dll`:
- It may be in the main folder or inside a subfolder like `rocm`.
- **Backup** the original files (rename them with `.old` or `_old` if you wish).
- **Copy**:
  - `rocblas.dll`
  - `library` folder (usually inside `rocm\rocblas\`).

> *Folder structure may vary slightly from guide references.*

---

### 6. Final Steps

- This is a **brief overview** — it's recommended to **read the Wiki** for any changes or updates.
- **Important**:
- **Do not update Ollama normally** via the app.
- Always manually re-download and reinstall
- Automatic updater is available [byronleeee's releases](https://github.com/ByronLeeeee/Ollama-For-AMD-Installer).
- **Issues?**
- Open an issue on the [likelovewant GitHub page](https://github.com/likelovewant/ollama-for-amd/issues).
- **Restoring Models**:
- If you backed up `.ollama`, you can restore previous models by copying back the `models` folder.
- **Test GPU Usage**:
- Start with a small model.
- Monitor GPU usage via **Task Manager**.
- *Note*: If the model is too large, some load might fall back to the CPU.

---

## 🔗 Links and References

- [Ollama for AMD GitHub](https://github.com/likelovewant/ollama-for-amd/)
- [ROCm Libraries for AMD GPUs](https://github.com/likelovewant/ROCmLibs-for-gfx1103-AMD780M-APU/releases)
- [Ollama for AMD Wiki](https://github.com/likelovewant/ollama-for-amd/wiki)
- [Troubleshooting AMD ROCm on Windows](https://docs.msty.app/troubleshooting/amd-rocm-windows-issues)
- [YouTube Walkthrough (Outdated)](https://www.youtube.com/watch?v=G-kpvlvKM1g)
