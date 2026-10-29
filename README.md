# Desktop Client Architecture Documentation

A reference documentation repository summarizing the file layout, binary components, asset directories, and network architecture of the desktop client installation.

---

## Repository Index

1. **[Binaries & DLLs (binaries.md)](binaries.md)**
   * Breakdown of executables and libraries (`RobloxPlayerBeta.exe`, `RobloxPlayerBeta.dll`, `RobloxCrashHandler.exe`, `WebView2Loader.dll`).
   * Explanations of their responsibilities, technologies used (Google Crashpad, Microsoft Edge WebView2, Luau VM, FMOD), and exported functions.

2. **[Content & Asset Structure (content-structure.md)](content-structure.md)**
   * Explanation of the `content/`, `ExtraContent/`, and `PlatformContent/` directory trees.
   * Details on compiled shader packs (`shaders_vulkan_desktop.pack`, `shaders_d3d11.pack`), character rigs, textures, and SSL certificate bundles.

3. **[Network Endpoints (network-endpoints.md)](network-endpoints.md)**
   * Public cloud infrastructure, Asset Delivery CDN endpoints, FastFlag (FFlag) configuration servers, and telemetry backends.

---

## Directory Summary

```text
version-<guid>/
├── RobloxPlayerBeta.exe             # Main launcher and host process
├── RobloxPlayerBeta.dll             # Core engine shared library (exports 'run')
├── RobloxCrashHandler.exe           # Google Crashpad crash reporting server
├── WebView2Loader.dll               # Microsoft Edge WebView2 loader
├── COPYRIGHT.txt                    # Open-source copyright notices
├── ssl/
│   └── cacert.pem                   # Mozilla TLS Root CA certificate bundle
├── shaders/                         # Precompiled GPU shader packs (Vulkan/DirectX)
├── content/                         # Avatars, fonts, sounds, base textures
├── ExtraContent/                    # Core Luau packages (in-game UI, chat)
├── PlatformContent/                 # Desktop-optimized texture and terrain maps
└── WebView2RuntimeInstaller/        # Standalone Microsoft WebView2 installer
```
