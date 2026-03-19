![Version](https://img.shields.io/badge/Version-1.5_ADV-blue)
![Hardware](https://img.shields.io/badge/Hardware-Cardputer-orange)
![Platform](https://img.shields.io/badge/Platform-M5Stack-red)
![License](https://img.shields.io/badge/License-Proprietary-gray)
[![Boosty](https://img.shields.io/badge/Support-Boosty-orange)](https://boosty.to/zeloksa)

# 📡 Wi-Fi Radar ADV (V1.5)

**Radar V1.5 ADV** is an advanced, high-speed Wi-Fi tracking and spatial direction-finding tool specifically optimized for the **M5Stack Cardputer ADV**. It utilizes Active Probing and log-normal attenuation models to detect, track, and measure the distance to specific Wi-Fi targets in real-time.

> [!IMPORTANT]
> **Source Code Status:** This project is proprietary. The source code is private. 
> **Distribution:** Binary (`.bin`) only via the **Releases** tab.

---

## ⚡ Technical Highlights

* **Active Probing Engine (40 FPS):** Replaces traditional passive scanning. The radar aggressively sends `Probe Requests` directly to the target, forcing an instant response (even from Hidden networks). This drops channel scan time from 80ms down to **20ms**, providing lag-free, surgical tracking.
* **Mesh-Network Support:** Intelligently separates physical hardware. If a corporate building has 5 routers broadcasting the same "Office_WiFi" SSID, the radar will plot 5 distinct dots and automatically lock the Sonar onto the closest physical node.
* **Log-Normal Attenuation Math:** Converts raw RSSI signal strength into an approximate physical distance (in meters) using a real-time mathematical model.
* **Deep Scan Mode:** Dedicated 400ms/channel listening phase when opening the "WIFI NETS" list to guarantee 100% capture of all quiet, hidden, or low-frequency beaconing networks.
* **CRT Retro-Futurism UI:** A custom-built rendering engine featuring 3D perspective grids, hardware-accelerated scanlines, and neon glow effects for an authentic 80s tactical terminal aesthetic.

---

## 🛠 Installation
1. Go to the **[Releases]** tab on the right side of this GitHub repository.
2. Download the latest **V1.5 ADV `.bin`** file.
3. Flash it to your M5Stack Cardputer using **M5Burner** (via the local file option) or the official **Espressif ESP32 Download Tool**.

---

## 🕹 Controls
* **[ , / . ]**: Navigate menus and lists (Up/Down/Left/Right).
* **[ ENTER ]**: Select / Start Tracking.
* **[ ESC / \` ]**: Back / Exit to Main Menu.
* **[ [ / ] ]**: Adjust Screen Brightness (Step 25).
* **[ - / = ]**: Adjust Sonar Volume (10% increments).
* **[ C ]**: Force IMU Recalibration.

---

## 📖 Comprehensive User Manual

To achieve maximum accuracy with the direction-finding compass, you must understand how to hold the device and how the different scanning modes operate.

### 🧭 IMU Calibration & The "Body Shield" Technique
1. When prompted, place the Cardputer perfectly **FLAT** on a table and press `[ENTER]`. Do not touch it while the progress bar fills.
2. **Directional Tracking:** The ESP32-S3 uses an omnidirectional antenna. To make the radar "directional", you must **hold the Cardputer tightly against your chest**, looking down at the screen. Your physical body acts as an RF shield, blocking signals from behind you. As you turn your body, the radar plots signals in a 360-degree space based on your physical rotation.

### 🌐 WIFI NETS (Deep Scan)
This mode performs a deep analysis of the 2.4GHz spectrum.
* Networks without password protection are visibly tagged with **[OPEN]** in yellow.
* Selecting a network here will open the **NETWORK INFO** panel, showing MAC, exact RSSI, approximate distance, Channel, and Encryption type.
* Press `[ENTER]` on the Info screen to lock onto this target and enter Single Track mode.

### 🎯 TRACK TARGET (Single Target Mode)
This is the ultimate hunting mode. The Cardputer shuts down 12 of its 13 Wi-Fi channels and focuses 100% of its processing power on the specific channel of your target.
* **Geiger-Counter Sonar:** The device emits a beep. The closer you get to the target (the stronger the signal), the faster the beep interval.
* **Mute:** Press `[ENTER]` to quickly toggle the Sonar audio ON/OFF.
* **UI:** Distances and signal strengths are displayed in large, bold text specifically designed for readability while walking.

### 📡 MASS RADAR (General Mode)
Scans all 13 channels simultaneously, displaying every device in your vicinity.
* **Fast-Track Feature:** While in Mass Radar mode, press `[ENTER]` (the `[ENT] NETS` button). The device will instantly jump to the Wi-Fi list. If you select a network this way, it **bypasses the Info Screen** and instantly launches into TRACK TARGET mode for rapid engagement.

---

## 🆕 V1.5 ADV Changelog
* **Major Overhaul:** Transitioned from Passive Scanning to Active Probing.
* **UI/UX:** Added fully transparent HUD elements over a scrolling Raw Data Stream background.
* **Power Management:** Replaced generic battery reading with an Exponential Moving Average (EMA) mathematical filter. The battery percentage no longer jumps erratically under heavy CPU load.
* **Ergonomics:** Added direct hotkeys for Volume `[-/+]` and Brightness `[[/]]`.
* **Security Tags:** Open networks are now explicitly flagged in the list.

---

## 💬 Feedback & Suggestions
If you find a bug or have a suggestion for the next version:
1. Go to the **[Issues]** tab at the top of this repository.
2. Click **[New Issue]**.
3. Describe your problem or idea in detail.

---

## ☕ Support the Project
If this tool has been useful for your research, security audits, or hobbyist projects, consider supporting further development:
* **[https://boosty.to/zeloksa]**

---
*Developed by Engineer Zeloksa. Strictly optimized for Cardputer ADV.*
