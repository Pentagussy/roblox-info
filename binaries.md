# Executables and Dynamic Link Libraries (DLLs)

Overview of the binaries installed in the client directory and their publicly documented roles.

---

## 1. `RobloxPlayerBeta.exe`
* **File Type:** 64-bit Windows PE GUI Executable (`x86-64`)
* **Role:** The primary process executable launched by the bootstrapper, web browser protocol handlers (`roblox-player://`), or command-line arguments.
* **Responsibilities:**
  * Initializes the process environment and Windows thread settings.
  * Handles standard command-line parameters (join tokens, authentication tickets, place IDs).
  * Dynamically loads `RobloxPlayerBeta.dll` and calls its exported `run()` routine.

---

## 2. `RobloxPlayerBeta.dll`
* **File Type:** 64-bit Windows Dynamic Link Library (`x86-64`)
* **Exported Symbols:** `run`
* **Role:** The core game engine shared library containing the application logic.
* **Responsibilities:**
  * **Rendering Engine:** Graphics pipelines supporting Vulkan, DirectX 11, and OpenGL.
  * **Luau Runtime:** Roblox's open-source Lua-based scripting engine and bytecode VM.
  * **Physics Engine:** Rigid body mechanics, collisions, constraints, and world simulation.
  * **Replication Subsystem:** Client-server state synchronization, interpolation, and UDP networking.
  * **Audio Subsystem:** 3D positional audio and sound mixing powered by FMOD.

---

## 3. `RobloxCrashHandler.exe`
* **File Type:** 64-bit Windows Executable (`x86-64`)
* **Implementation:** **Google Crashpad** (open-source crash reporting system developed by Google for Chromium).
* **Role:** Out-of-process crash monitoring and telemetry.
* **Responsibilities:**
  * Runs independently or monitors the main player process via inter-process communication (IPC).
  * If the player crashes or encounters an unhandled exception, Crashpad captures process state, register dumps, and stack traces into standard `.dmp` minidump files.
  * Sends telemetry crash dumps to the error reporting backend to assist developers in tracking game stability.

---

## 4. `WebView2Loader.dll`
* **File Type:** 64-bit Windows Dynamic Link Library (`x86-64`)
* **Provider:** Microsoft Corporation (part of the Microsoft Edge WebView2 SDK).
* **Role:** Embedded Chromium Web Browser Loader.
* **Responsibilities:**
  * Locates the installed Microsoft Edge WebView2 runtime on the host machine.
  * Embeds modern Chromium-based web views directly inside the desktop client for secure account authentication, in-game web views, and payment gateways.

---

## 5. `WebView2RuntimeInstaller/MicrosoftEdgeWebview2Setup.exe`
* **File Type:** 32-bit/64-bit Windows Executable
* **Provider:** Microsoft Corporation
* **Role:** Evergreen Runtime Bootstrapper.
* **Responsibilities:**
  * Executed silently by the installer if a compatible Microsoft Edge WebView2 runtime is not already present on the Windows system.
