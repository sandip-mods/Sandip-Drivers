# ⚡ SANDIP DRIVER'S — Kernel Driver Manager

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

## 📌 Table of Contents
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
