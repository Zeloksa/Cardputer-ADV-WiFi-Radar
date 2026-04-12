![Version](https://img.shields.io/badge/Version-3.0_ADV-blue)
![Hardware](https://img.shields.io/badge/Hardware-Cardputer-orange)
![Platform](https://img.shields.io/badge/Platform-M5Stack-red)
![License](https://img.shields.io/badge/License-Proprietary-gray)
[![Boosty](https://img.shields.io/badge/Support-Boosty-orange)](https://boosty.to/zeloksa)

# 📡 Wi-Fi & BLE Radar ADV (V3.0)

**Wi-Fi & BLE Radar ADV V3.0** is an advanced, high-speed tracking, spatial direction-finding, and spectrum analysis tool strictly optimized for the **M5Stack Cardputer ADV**. This version transforms the device into a professional diagnostic suite by introducing a full-fledged Wi-Fi Spectrum Analyzer and intelligent UI state management.

> [!IMPORTANT]
> **Source Code Status:** This project is proprietary. The source code is private. 
> **Distribution:** Binary (`.bin`) only via the **Releases** tab.

---

## ⚡ V3.0 Technical Highlights

* **Professional Spectrum Analyzer:** A real-time 2.4GHz Wi-Fi channel monitor featuring True Peak Hold and Interference Arcs mapping to visually detect Co-Channel (CCI) and Adjacent Channel (ACI) interference.
* **Smart Channel Advisor:** The radar mathematically calculates interference scores across all 13 channels based on signal power and channel overlap, dynamically recommending the absolute best (cleanest) channel for your home router.
* **Target Name Lock (DPI Protection):** Deep Packet Inspection (DPI) parsing is now strictly locked during target tracking. This prevents dynamic Bluetooth payload fragmentation (e.g., a phone suddenly broadcasting a Microsoft Swift Pair packet) from altering the target's name mid-pursuit.
* **Anti-Tracking Bypass & OUI Database:** Instantly resolves the manufacturer of detected devices (Apple, Xiaomi, Garmin, Huami/Mi-Band, etc.) and parses IEEE address types on the fly to identify randomized targets.
* **Dual-Radio Management:** Implements strict antenna sharing logic. The firmware isolatedly handles Wi-Fi and BLE states to prevent radio coexistence interference, ensuring surgical precision in tracking.

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
3. Select version **V3.0**.
4. Burn to your M5Stack Cardputer.

### Method 2: Manual Flashing
1. Go to the **[Releases]** tab of this repository.
2. Download the **`merged.bin`** (full 8MB flash dump) or the standard app bin.
3. Flash to your Cardputer using **M5Burner** (Local File) or **esptool**.

---

## 🕹 Controls
* **[ ; / . ]**: Scroll lists Up/Down.
* **[ , / / ]**: Switch active columns (Wi-Fi / BLE) in the Device List OR Toggle Bar/Arc Mode in CH Analyzer.
* **[ ENTER ]**: Select target / Toggle Sonar Mute.
* **[ ESC / \` ]**: Back to Menu / Exit mode.
* **[ [ / ] ]**: Screen Brightness control.
* **[ - / = ]**: Sonar Volume control.
* **[ C ]**: Trigger manual IMU Recalibration.

---

## 📖 Operational Guide

### 🧭 IMU & Tactical Warm-up
When starting a scan, place the device **FLAT** on a table. Once calibrated, the radar features a new **tactical 360° rotation HUD overlay**. The system will prompt you to rotate your body to capture all surrounding networks. The prompt automatically dismisses once a full 180-degree sweep is detected via the IMU.

### 📊 CH ANALYZER (Spectrum Analyzer)
A professional diagnostic mode for the 2.4GHz band. 
* **True Peak Hold:** Networks are permanently accumulated in memory during the session to show the *real* channel congestion, even if a router temporarily stops broadcasting.
* **Dual Visualization:** Use the `< / >` keys to switch between standard **Density Bars** and **Spectral Arcs**. Arcs visually demonstrate how a router on channel 6 creates physical noise on channels 4, 5, 7, and 8. Arc peaks are smartly labeled with the network's SSID.
* **Grade & Advice:** The top-left corner dynamically displays the mathematically cleanest channel (e.g., `BEST CH: 11 [95% A]`), evaluating both CCI and ACI penalties. The purity grading scale is:
  * **(A) 90-100%:** 🟢 Ideal / Crystal clear.
  * **(B) 75-89%:** 🍏 Good.
  * **(C) 60-74%:** 🟡 Acceptable.
  * **(D) 40-59%:** 🟠 Poor (Expect connection lag).
  * **(F) <40%:** 🔴 Dead zone (Avoid using this channel).

### 📋 DEVICE LIST (Dynamic Discovery)
This mode lists every signal in your vicinity using background multiplexed scanning.
* **Stale Data Management:** If a device stops broadcasting for more than 15 seconds, it receives an **`[OFF]`** tag and is intelligently pushed to the bottom of the list, keeping your active targets at the top.
* **Security Tags:** Open Wi-Fi networks are highlighted with a yellow **[OPEN]** tag.

### 🎯 TRACK TARGET (Single Mode)
Locks onto a specific MAC address. The device provides distance estimation (`~Xm`) based on log-normal path loss models. The sonar beep frequency increases as you approach the physical source.

---

## 🆕 Wi-Fi & BLE Radar ADV (V3.0) Changelog
* **Added:** Professional **CH ANALYZER** (Spectrum Analyzer) with True Peak Hold.
* **Added:** **Smart Channel Advisor** that calculates CCI/ACI interference and grades channel purity (A to F).
* **Added:** **Spectral Arcs** visualization mode to physically map overlapping 2.4GHz Wi-Fi frequencies.
* **Added:** Tactical **360° Rotation HUD** animation upon entering Radar mode.
* **Added:** **`[OFF]`** status tags for inactive networks, combined with smart list sorting (active devices always stay on top).
* **Added:** Distance estimation (`~Xm`) is now available in the Wi-Fi Radar mode.
* **Fixed:** **Target Name Lock** implemented. Prevents BLE payload fragmentation from overwriting a locked target's name mid-scan.
* **Fixed:** Resolved the memory wipe issue. Navigating from Radar to the Device List now seamlessly transfers all scanned targets without resetting.
* **Improved:** Highly optimized UI overlapping and bounding boxes for a cleaner, professional look on the 240x135 screen.

---

## ☕ Support the Project
Support the development of advanced diagnostic tools for the Cardputer ecosystem:
* **[https://boosty.to/zeloksa]**

---
*Developed by Engineer Zeloksa. Strictly optimized for Cardputer ADV.*
