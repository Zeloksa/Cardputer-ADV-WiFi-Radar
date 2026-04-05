![Version](https://img.shields.io/badge/Version-2.0_ADV-blue)
![Hardware](https://img.shields.io/badge/Hardware-Cardputer-orange)
![Platform](https://img.shields.io/badge/Platform-M5Stack-red)
![License](https://img.shields.io/badge/License-Proprietary-gray)
[![Boosty](https://img.shields.io/badge/Support-Boosty-orange)](https://boosty.to/zeloksa)

# 📡 Wi-Fi & BLE Radar ADV (V2.0)

**Wi-Fi & BLE Radar ADV V2.0** is an advanced, high-speed tracking and spatial direction-finding tool specifically optimized for the **M5Stack Cardputer ADV**. This version introduces a completely independent Bluetooth Low Energy (BLE) engine alongside the upgraded Wi-Fi tracking system.

> [!IMPORTANT]
> **Source Code Status:** This project is proprietary. The source code is private. 
> **Distribution:** Binary (`.bin`) only via the **Releases** tab.

---

## ⚡ V2.0 Technical Highlights

* **Dual-Radio Management:** Implements strict antenna sharing logic. The firmware isolatedly handles Wi-Fi and BLE states to prevent radio coexistence interference, ensuring surgical precision in tracking.
* **Anti-Tracking Bypass (Phone/Watch Detection):** Modern mobile devices use randomized MAC addresses to hide. Our V2.0 engine parses IEEE address types on the fly to identify and tag randomized targets like iPhones and Android smartphones.
* **Embedded OUI Database:** Includes an internal vendor lookup table to instantly resolve the manufacturer of detected devices (Apple, Xiaomi, Garmin, Huami/Mi-Band, etc.) directly on the radar screen.
* **Background TDM Scanning:** The Device List uses Asynchronous Time-Division Multiplexing. The radio module automatically toggles between Wi-Fi and BLE every 3 seconds, keeping the lists updated in real-time without freezing the UI.
* **Visual Stability Engine:** Integrated UI Throttling prevents "text shaking" in high-density areas. While data is captured at 60Hz, visual sorting is updated every 1.2s for optimal tactical readability.

---

## ⚠️ Important Limitations (Must Read)

Before using the BLE Radar, please understand the physical and cryptographic limits of the hardware:

1. **Bluetooth Low Energy (BLE) ONLY:** The ESP32-S3 chip inside the Cardputer lacks the hardware to scan for "Bluetooth Classic" (BR/EDR). 
   * **What it CAN see:** Modern smartphones, Smartwatches (Mi Band, Apple Watch, Garmin), IoT sensors, BLE Beacons, and modern Smart TVs.
   * **What it CANNOT see:** Old wireless headphones, legacy car stereos, old game controllers (PS3/PS4), or basic Bluetooth speakers.
2. **MAC Randomization is NOT a Bug:** If you see a massive list of devices named `Phone(Rnd)` or `Priv.(Rnd)` that seem to disappear and reappear, **this is not a flaw in the firmware**. Modern Apple iOS and Android devices use cryptographic MAC Randomization to actively prevent tracking by changing their MAC addresses every 10-15 minutes. The radar is working perfectly—you are just witnessing modern cyber-security in action.

---

## 🛠 Installation
### Method 1: M5Burner (Recommended)
1. Open **M5Burner**.
2. Search for `Wi-Fi & BLE Radar ADV` or `Zeloksa`.
3. Select version **V2.0**.
4. Burn to your M5Stack Cardputer.

### Method 2: Manual Flashing
1. Go to the **[Releases]** tab of this repository.
2. Download the **`merged.bin`** (full 8MB flash dump) or the standard app bin.
3. Flash to your Cardputer using **M5Burner** (Local File) or **esptool**.

---

## 🕹 Controls
* **[ , / . ]**: Scroll lists Up/Down.
* **[ ; / / ]**: Switch active columns (Wi-Fi / BLE) in the Device List.
* **[ ENTER ]**: Select target / Toggle Sonar Mute.
* **[ ESC / \` ]**: Back to Menu / Exit mode.
* **[ [ / ] ]**: Screen Brightness control.
* **[ - / = ]**: Sonar Volume control.
* **[ C ]**: Trigger manual IMU Recalibration.

---

## 📖 Operational Guide

### 🧭 IMU & Radio Warm-up
When starting a scan, place the device **FLAT** on a table. During calibration, the radio chip initiates a background warm-up sequence to eliminate initial scan latency (Cold Start), ensuring targets appear instantly once the radar screen loads.

### 📋 DEVICE LIST (Dynamic Discovery)
This mode lists every signal in your vicinity.
* **Persistent Memory:** Devices are never deleted from the list during the session, allowing you to track targets that have moved out of range.
* **Security Tags:** Open Wi-Fi networks are highlighted with a yellow **[OPEN]** tag (turning Red when selected).
* **Smart Navigation:** Entering the list from the Radar screen enables "Fast-Lock"—selecting a target instantly bypasses the info screen and starts tracking.

### 🎯 TRACK TARGET (Single Mode)
Locks onto a specific MAC address. In BLE mode, the device provides distance estimation based on log-normal path loss models calibrated for portable electronics. The sonar beep frequency increases as you approach the physical source.

---

## 🆕 Wi-Fi & BLE Radar ADV (V2.0) Changelog
* **Added:** Independent BLE Radar mode with vendor resolution.
* **Added:** Dual-column "Device List" with background multiplexed scanning.
* **Improved:** Eliminated the 2-second "blind period" after calibration via async radio warm-up.
* **Improved:** Redesigned all UI icons and color-coded menus (Green/Yellow/Blue).
* **Fixed:** Resolved the "bouncing list" issue caused by RSSI fluctuations.
* **Fixed:** Cursor and scroll position now reset to top when entering lists.

---

## ☕ Support the Project
Support the development of advanced tools for the Cardputer ecosystem:
* **[https://boosty.to/zeloksa]**

---
*Developed by Engineer Zeloksa. Strictly optimized for Cardputer ADV.*
