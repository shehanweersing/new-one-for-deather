<div align="center">
  
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=40&pause=1000&color=33CA7F&center=true&vCenter=true&width=600&lines=ESP8266+WiFi+Deauther;Understand+WiFi+Security;Test+Your+Own+Networks" alt="Typing SVG" />

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Hardware](https://img.shields.io/badge/Hardware-ESP8266-blue.svg)](https://en.wikipedia.org/wiki/ESP8266)
[![Firmware](https://img.shields.io/badge/Firmware-SpacehuhnTech-brightgreen.svg)](https://github.com/SpacehuhnTech/esp8266_deauther)
[![Educational Purposes](https://img.shields.io/badge/Purpose-Educational-red.svg)]()

**An educational project to understand WiFi security and the 802.11 deauthentication vulnerability.**

</div>

---

> [!CAUTION]
> ## ⚠️ Disclaimer
> **This project is intended for educational purposes and testing on your OWN networks only.**
> Using this tool on networks you do not own or have permission to test is **illegal** and constitutes a Denial of Service (DoS) attack. The author takes no responsibility for any misuse of this information.

---

## 🧐 What is this?

This project uses an **ESP8266** development board (NodeMCU) to run the open-source [Deauther firmware](https://github.com/SpacehuhnTech/esp8266_deauther) created by Spacehuhn.

### Jammer vs. Deauther
Many people confuse this tool with a "WiFi Jammer," but it is actually a **Deauthentication Tool**.
- 🚫 **Jammer:** Creates physical noise on the 2.4GHz spectrum to block all signals (Highly Illegal).
- 🔓 **Deauther:** Sends specific, unencrypted WiFi management packets (frames) that instruct a device to disconnect from a router.

This tool demonstrates a critical flaw in the older 802.11 WiFi standard where these "management frames" are completely unencrypted, allowing anyone to spoof them.

## ⚡ How It Works

The attack exploits the lack of encryption in management frames on older WiFi networks in four simple steps:

1. **📡 Scan:** The ESP8266 listens for nearby WiFi access points and connected clients.
2. **🎭 Spoof:** It mimics the MAC address of the target router.
3. **💥 Attack:** It sends a "Deauthentication Frame" to the target device (client).
4. **🔌 Result:** The client believes the legitimate router sent the request and disconnects immediately.

## 🛠️ Hardware Requirements

| Component | Description |
| :--- | :--- |
| **Microcontroller** | NodeMCU (ESP8266) or Wemos D1 Mini |
| **Cable** | Micro-USB Data Cable (Must support data transfer) |
| **Computer** | Windows / macOS / Linux PC (for flashing) |

## 📥 Installation Guide

Follow these steps to replicate this project:

### 1. Install Drivers
Ensure your computer can communicate with the ESP8266. You will likely need one of these drivers depending on your board's serial chip:
- **[CP2102](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers)** (Commonly used on square chips)
- **[CH340](https://sparks.gogo.co.nz/ch340.html)** (Commonly used on rectangular chips)

### 2. Flashing the Firmware
The easiest method is using the Web Installer:
1. Connect your ESP8266 to your PC via USB.
2. Navigate to **[esp.deauther.com](https://esp.deauther.com)** using a Web Serial compatible browser (like Chrome or Edge).
3. Click **Connect** and select the correct COM port for your board.
4. Click **Install Deauther** and wait for the process to complete.

## 🎮 Usage Instructions

1. **Power up** the ESP8266.
2. Connect your phone or PC to the new WiFi network named **`pwned`** (Default Password: `deauther`).
3. Open a web browser and navigate to `http://192.168.4.1`.
4. Go to the **Scan** tab to look for access points and stations.
5. **Select** your own test network from the list.
6. Navigate to the **Attack** tab and click **Start** on the "Deauth" attack.

## 📸 Interface Previews

Here is a look at the web interface in action:

<details>
<summary>Click to view screenshots</summary>

<br>

![Scan Interface](https://github.com/user-attachments/assets/a999de02-861b-48c6-a5fb-abfc7104c0d7)

![Target Selection](https://github.com/user-attachments/assets/dc8766a9-ac8d-419b-ab31-bc0a269d68f7)

![Attack Interface](https://github.com/user-attachments/assets/5f09cadd-a329-462f-aec6-4cf1aac5eca8)

</details>

## 🛡️ How to Protect Yourself

The definitive way to stop this attack is to use the **802.11w** standard (Protected Management Frames or PMF).
- Most modern routers (WPA3) enforce this feature, but it is often disabled by default on WPA2 routers to maintain compatibility with older devices.
- When **802.11w is enabled**, the device will ignore fake disconnect packets because they lack the proper cryptographic signature from the router.

## 👏 Credits & Acknowledgments

- **Firmware Creator:** [SpacehuhnTech](https://github.com/SpacehuhnTech) for the amazing open-source ESP8266 Deauther project.
- **Documentation:** Your Name / GitHub Handle

---

<p align="center">
  <i>Created for educational exploration of cybersecurity concepts.</i>
</p>
