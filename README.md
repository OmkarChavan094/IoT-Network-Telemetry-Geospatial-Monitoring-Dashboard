# 📡 IoT Network Telemetry & Geospatial Monitoring Dashboard

An end-to-end IoT telemetry analytics project tracking edge device communications, transmission pathways, and geographical telemetry across Navi Mumbai and Mumbai metropolitan regions.

---

## 📌 Project Overview

This project models and visualizes live-style telemetry from distributed ESP32-based edge nodes transmitting critical packets to centralized weather station gateways[cite: 3]. The Power BI dashboard monitors communication health, multi-hop routing protocol distribution (LoRa, WiFi, Bluetooth, UWB), message priority levels, and geospatial node distributions across urban clusters[cite: 2, 3].

---

## 📊 Dashboard Preview

![IoT Dashboard](dashboard_screenshot.jpg)

### Core Telemetry KPIs
* **Total Devices Monitored:** 30 registered active edge hardware nodes (wearables, sensors, and GPS trackers)[cite: 2, 3].
* **Total Message Volume:** 98 operational telemetry packets processed[cite: 2].
* **Gateway Stations:** 5 centralized weather station receivers (`WS-0001` through `WS-0005`)[cite: 2, 3].
* **High Priority Alerts:** Critical packet counts flagged for urgent routing[cite: 2, 3].

---

## 🔍 Key Architectural Insights

* **Geospatial Clustering:** Edge devices are deployed across key nodes spanning Navi Mumbai, Panvel Taluka, and eastern Mumbai corridors, mapped via Azure Maps integration[cite: 2].
* **Protocol Distribution:**
  * **LoRa (32.65%):** Primary long-range backhaul protocol for low-power sensors[cite: 2].
  * **WiFi (24.49%):** High-throughput data synchronization near regional base points[cite: 2].
  * **Bluetooth (21.43%) & UWB (21.43%):** Short-range, high-precision local mesh hops[cite: 2, 3].
* **Multi-Hop Transmission Paths:** Telemetry routing simulates real mesh topology, dynamically bouncing packets through 2 to 3 hops (e.g., `UWB ➔ LoRa ➔ WiFi ➔ Internet`) before hitting destination weather gateways[cite: 3].

---

## 📁 Dataset Schema (`iot_devices_30.json`)

The system processes structured JSON device payloads containing hardware signatures, coordinates, and network paths[cite: 3]:

| Field | Type | Description |
| :--- | :--- | :--- |
| `message_id` | String | Unique packet transmission identifier (`MSG-XXXXXXX`)[cite: 2, 3] |
| `source.device_id` | String | Originating edge node ID (`WB-0001` to `WB-0030`)[cite: 2, 3] |
| `source.device_type` | String | Category: `wearable`, `sensor`, or `tracker`[cite: 2, 3] |
| `source.hardware_id` | String | Hardware chip identifier (e.g., ESP32 variants)[cite: 3] |
| `destination.device_id` | String | Target gateway weather station (`WS-0001` to `WS-0005`)[cite: 3] |
| `communication.current_method` | String | Protocol used (`LoRa`, `WiFi`, `Bluetooth`, `UWB`)[cite: 2, 3] |
| `communication.path` | List | Array showing full multi-hop transmission path[cite: 3] |
| `communication.hop_count` | Integer | Total network jumps required to reach destination[cite: 3] |
| `priority` | Integer | Alert severity level (1 = lowest, 5 = highest)[cite: 2, 3] |
| `location` | Object | Coordinates (`latitude`, `longitude`), accuracy radius, and fix source[cite: 3] |

---

## 🛠️ Tech Stack & Visual Tools

* **Data Engineering & Parsing:** Python (`pandas`, `json`), Microsoft Power Query
* **Business Intelligence & Mapping:** Microsoft Power BI Desktop (Azure Maps Visual, Donut Distribution, KPI Cards, Matrix Visual)[cite: 2]
* **IoT Protocols Modeled:** LoRaWAN, Ultra-Wideband (UWB), BLE, WiFi 802.11[cite: 2, 3]

---

## 🚀 Setup & Usage Instructions

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/OmkarChavan094/IoT-Network-Telemetry-Dashboard.git](https://github.com/OmkarChavan094/IoT-Network-Telemetry-Dashboard.git)
   cd IoT-Network-Telemetry-Dashboard
