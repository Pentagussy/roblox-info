# Content and Asset Directory Structure

Overview of the asset directories, compiled shaders, and network configuration files packaged with the client.

---

## 1. `shaders/`
Contains precompiled binary graphics shader packs for multiple graphics backends:

| Package File | Target Graphics API |
| :--- | :--- |
| `shaders_vulkan_desktop.pack` | **Vulkan** (modern cross-platform high-performance renderer) |
| `shaders_d3d11.pack` | **DirectX 11** (standard Windows graphics API) |
| `shaders_d3d10.pack` & `shaders_d3d10_1.pack` | **DirectX 10** (legacy graphics fallback) |
| `shaders_glsl3.pack` | **OpenGL 3.x / GLSL** (cross-platform desktop fallback) |

These files contain compiled GPU bytecode (vertex, pixel, and compute shaders) for rendering lighting, shadows, atmospheric fog, terrain deformation, and UI post-processing.

---

## 2. `ssl/`
* **`cacert.pem`**:
  * Mozilla's standard CA (Certificate Authority) certificate bundle.
  * Used by the internal HTTP client (`libcurl`) to establish secure, encrypted HTTPS/TLS connections to official backend servers, ensuring server identities cannot be spoofed.

---

## 3. `content/`
Standard client resources bundled with the installation:
* **`content/avatar/`**: Base R6 and R15 character rigs, dynamic head meshes (`headA.mesh` – `headL.mesh`), and default clothing textures.
* **`content/fonts/`**: TrueType and OpenType fonts used across the in-game UI (`Arimo`, `AmaticSC`, `Accanthis`).
* **`content/textures/`**: System cursors, tool icons, user interface widgets, and stock skybox assets.
* **`content/sounds/`**: Default UI sound effects and interaction audio.

---

## 4. `ExtraContent/`
* **`ExtraContent/LuaPackages/`**:
  * Pre-packaged Luau modules powering the Universal App.
  * Contains the core libraries for the in-game TopBar, PlayerList, Chat service, emote wheels, and purchase prompt interfaces.
* **`ExtraContent/translations/`**:
  * Localization tables for multi-language client interface text.

---

## 5. `PlatformContent/`
* **`PlatformContent/pc/textures/`**:
  * Platform-optimized texture dictionaries compressed specifically for desktop GPUs.
* **`PlatformContent/pc/terrain/`**:
  * High-resolution terrain material maps (grass, rock, water, sand).
* **`PlatformContent/pc/shared_compression_dictionaries/`**:
  * Zstandard / LZ4 compression dictionaries enabling compressed network packet transmission between client and server.
