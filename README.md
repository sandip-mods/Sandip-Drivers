<p align="center">
  <img src="app/src/main/res/drawable/ic_app_logo.png" width="160" height="160" alt="Sandip Driver's Logo" />
</p>

<h1 align="center">⚡ SANDIP DRIVER'S — Kernel Driver Manager</h1>

<p align="center">
  <a href="https://github.com/your-username/sandip-drivers/releases/latest">
    <img src="https://img.shields.io/github/v/release/your-username/sandip-drivers?style=for-the-badge&color=blue&logo=github&label=Latest%20Release" alt="Latest Release" />
  </a>
  <a href="https://github.com/your-username/sandip-drivers/releases/latest">
    <img src="https://img.shields.io/badge/Download-APK-success?style=for-the-badge&logo=android&logoColor=white" alt="Download APK" />
  </a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android-green.svg?style=for-the-badge&logo=android" alt="Platform" />
  <img src="https://img.shields.io/badge/Language-Kotlin-purple.svg?style=for-the-badge&logo=kotlin" alt="Language" />
  <img src="https://img.shields.io/badge/UI-Jetpack%20Compose-blue.svg?style=for-the-badge&logo=jetpackcompose" alt="Jetpack Compose" />
  <img src="https://img.shields.io/badge/Design-Material%203-pink.svg?style=for-the-badge&logo=materialdesign" alt="Material 3" />
  <img src="https://img.shields.io/badge/Root-Required-red.svg?style=for-the-badge&logo=android" alt="Root Required" />
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge" alt="License" />
</p>

**SANDIP DRIVER'S** is a modern, high-performance Android Kernel Driver Manager & Loader application built with **Kotlin** and **Jetpack Compose (Material 3)**. It allows rooted Android devices to inspect kernel architecture, detect compatible kernel modules (`.ko`), execute driver payloads, and monitor real-time execution logs through a custom terminal interface.

---

## 🚀 Latest Release

| Version | Status | Release Package | Download |
| :--- | :--- | :--- | :--- |
| **`v1.0`** | 🟢 Stable Release | `app-release.apk` | [📥 **Download APK**](https://github.com/your-username/sandip-drivers/releases/latest/download/app-release.apk) |

> 📌 **Note:** Make sure your device is **rooted** (via Magisk, KernelSU, or APatch) before installing the APK.

---

## 📌 Table of Contents
- [🚀 Latest Release](#-latest-release)
- [✨ Features](#-features)
- [📱 Screenshots & UI](#-screenshots--ui)
- [🧠 Architecture & Tech Stack](#-architecture--tech-stack)
- [⚡ Prerequisites](#-prerequisites)
- [📥 Installation & Setup](#-installation--setup)
- [🛠️ How to Add Custom Kernel Drivers](#️-how-to-add-custom-kernel-drivers)
- [⚙️ Building from Source](#️-building-from-source)
- [⚠️ Security & Disclaimer](#️-security--disclaimer)
- [📄 License](#-license)

---

## ✨ Features

### 🛡️ Core Functionality
- **Root Authorization Check (`su`):** Automatic root access detection via `su` shell commands.
- **Kernel & Device Diagnostics:** Real-time extraction of device model, Android version, SDK API level, and full Kernel version string.
- **Smart Driver Matching:** Scans packaged driver assets and automatically filters compatible drivers matching the device's kernel series.
- **One-Tap Driver Flashing / Loading:** Safely executes kernel module injection with status updates.
- **Integrated Live Terminal:** Embedded monospace log viewer displaying step-by-step kernel module operations, commands, and errors.
- **Quick Reboot Control:** Built-in system reboot dialog with root privileges for instant system restarts.

### 🎨 Design & Experience
- **100% Jetpack Compose UI:** Built with Material Design 3 guidelines.
- **Smooth Animations:** Custom screen slide transitions, staggered item entrances, loading indicator pulses, and shimmer text effects.
- **Haptic Feedback:** Tactile haptic feedback integration for button clicks, toggles, and status changes.
- **Customization Settings:**
  - Dynamic Appearance modes: **Light**, **Dark**, and **System Default**.
  - Toggle visibility of Terminal log card and Device Info card.
  - Haptic feedback toggle.

---

## 📱 Screenshots & UI

| Home Screen (Idle) | Driver Execution & Live Terminal | Settings & Theme Customization |
| :---: | :---: | :---: |
| *(Add Screenshot)* | *(Add Screenshot)* | *(Add Screenshot)* |

---

## 🧠 Architecture & Tech Stack

The app strictly follows **Modern Android Architecture (MVVM)** principles with reactive data streams:

```
┌─────────────────────────────────────────────────────────────┐
│                      UI Layer (Compose)                     │
│        MainActivity ── HomeScreen ── SettingsScreen         │
└──────────────────────────────┬──────────────────────────────┘
                               │ StateFlow / Events
┌──────────────────────────────▼──────────────────────────────┐
│                    ViewModel Layer                          │
│                     MainViewModel                           │
└──────────────────────────────┬──────────────────────────────┘
                               │ Coroutines / Dispatchers.IO
┌──────────────────────────────▼──────────────────────────────┐
│                    Data & Utility Layer                     │
│ ShellUtils │ DriverCompatibilityManager │ LogManager │ Prefs│
└─────────────────────────────────────────────────────────────┘
```

- **Language:** Kotlin 2.x
- **UI Framework:** Jetpack Compose + Material 3 (Compose BOM)
- **State Management:** `StateFlow` & `MutableStateFlow`
- **Asynchronous Processing:** Kotlin Coroutines (`Dispatchers.IO` & `viewModelScope`)
- **System Access:** Android Root Shell (`su` execution pipeline)
- **Min SDK:** `28` (Android 9.0 Pie)
- **Target SDK:** `37` (Android 15+)

---

## ⚡ Prerequisites

To use **SANDIP DRIVER'S**, your Android device must meet the following requirements:

1. **Rooted Device:** Magisk, KernelSU, or APatch with Superuser access granted.
2. **Android Version:** Android 9.0 (API Level 28) or higher.
3. **Compatible Kernel Module:** Custom `.ko` module targeting your kernel version string.

---

## 📥 Installation & Setup

1. **Download the APK:** Download the latest release from the [Releases](https://github.com/your-username/sandip-drivers/releases) section.
2. **Install APK:** Install the APK on your rooted device.
3. **Grant Root Access:** Upon launching the app, grant Superuser permissions when prompted by Magisk / KernelSU / APatch.
4. **Load Driver:** Select a compatible driver from the list and tap to load.

---

## 🛠️ How to Add Custom Kernel Drivers

You can bundle your custom kernel modules (`.ko`) into the application:

1. Place your pre-compiled `.ko` files in the `app/src/main/assets/drivers/` directory.
2. Name your driver files following your target kernel version (e.g., `driver_5.10.ko` or `module_android12.ko`).
3. Rebuild the APK. The `DriverCompatibilityManager` will automatically discover and list compatible modules based on the device's kernel series.

---

## ⚙️ Building from Source

### Prerequisites
- Android Studio Ladybug (2024.2+) or newer.
- JDK 17 / JDK 11 configured in Android Studio.
- Android SDK 35/37 installed.

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/sandip-drivers.git
   cd sandip-drivers
   ```
2. Open the project in **Android Studio**.
3. Build debug APK using Gradle CLI:
   ```bash
   ./gradlew assembleDebug
   ```
   Or generate release APK:
   ```bash
   ./gradlew assembleRelease
   ```
4. Output APK location:
   `app/build/outputs/apk/release/app-release.apk`

---

## ⚠️ Security & Disclaimer

> [!WARNING]
> **Kernel Module Execution Requires Root Privileges.**  
> Loading incompatible or corrupted kernel drivers can cause system instability, kernel panics, or bootloops. Always verify that your kernel modules match your exact kernel architecture and version. Use this tool at your own risk. The developer is not responsible for any bricked devices or data loss.

---

## 📄 License

```text
MIT License

Copyright (c) 2025 Sandip Sah

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
