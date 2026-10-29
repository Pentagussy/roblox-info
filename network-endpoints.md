# Network Endpoints & Content Delivery

Publicly documented cloud infrastructure and APIs used by the desktop client.

---

## 1. Asset Delivery Pipeline
* **`https://assetdelivery.roblox.com/`**:
  * The primary CDN gateway for dynamic user-generated content (3D meshes, user models, audio files, and place assets).
  * Requests are resolved by unique numeric Asset IDs (e.g. `/v1/asset/?id=<assetId>`).
* **`https://setup.rbxcdn.com/`**:
  * The global content distribution network hosting official version binaries, ZIP archives, and channel deployment manifests.

---

## 2. Configuration & FastFlags (FFlags)
* **`https://clientsettingscdn.roblox.com/`**:
  * Provides client version resolution and dynamic feature flags.
  * FastFlags allow engine developers to remotely enable or disable features, balance memory pools, and tune rendering settings without requiring a client binary update.

---

## 3. Real-Time Telemetry & Diagnostics
* **`https://client-telemetry.roblox.com/`**:
  * Collects anonymous performance metrics (frame rates, network ping, memory consumption) to monitor client health across various hardware configurations.
* **`https://ecsv2.roblox.com/`**:
  * Event ingestion endpoint used for session telemetry and analytical logging.
