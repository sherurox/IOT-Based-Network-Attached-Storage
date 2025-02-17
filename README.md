# 🚀 IoT-Based Network Attached Storage (IoT-NAS)

## 📌 Overview
With the exponential rise of **Internet of Things (IoT) devices**, efficient data **storage, management, and security** have become critical. This project presents an **IoT-Based Network Attached Storage (IoT-NAS)** system using a **Raspberry Pi 4** and **OpenMediaVault** to build a **scalable, decentralized, and secure** storage solution for IoT-generated data.

This repository provides **step-by-step instructions** to:
1. Install and configure **Raspberry Pi OS**.
2. Install and set up **OpenMediaVault (OMV)** on your Raspberry Pi.
3. Configure network-attached storage with **multiple storage devices** (HDD, SSD, USB drives).
4. Evaluate **performance** and **security** of the IoT-NAS.
5. Showcase **future enhancements** (edge computing, AI-based storage, etc.).

---

## 📝 Table of Contents
1. [Introduction](#introduction)
2. [Key Features](#key-features)
3. [System Architecture](#system-architecture)
4. [Required Components](#required-components)
5. [Installation Guide](#installation-guide)
   - [Step 1: Install Raspberry Pi OS](#step-1-install-raspberry-pi-os)
   - [Step 2: Install OpenMediaVault via Script](#step-2-install-openmediavault-via-script)
   - [Step 3: Access OMV Web Interface](#step-3-access-omv-web-interface)
   - [Step 4: Configure Storage in OMV](#step-4-configure-storage-in-omv)
   - [Step 5: Create Shared Folders](#step-5-create-shared-folders)
   - [Step 6: Allocate Storage Space](#step-6-allocate-storage-space)
   - [Step 7: Set Up Network Shares](#step-7-set-up-network-shares)
6. [Performance Evaluation](#performance-evaluation)
7. [Security Measures](#security-measures)
8. [Future Enhancements](#future-enhancements)
9. [Contributing](#contributing)
10. [License](#license)
11. [Contact & Support](#contact--support)

---

## 🔍 Introduction
Traditional **cloud storage** and **centralized data centers** often fail to keep pace with the **massive data demands** of IoT devices. High latency, security risks, and limited scalability can hinder IoT data management.

This project **merges IoT with NAS**, providing:
- **Low-cost** deployment using **Raspberry Pi 4**.
- **Scalable** and **decentralized** data storage.
- **Enhanced security** through **encryption** and **role-based access**.
- **Optimized performance** with **compression** and **deduplication**.

---

## 🌟 Key Features
- **Decentralized NAS Architecture**: Distributes and replicates data across various drives.
- **Raspberry Pi 4-Based NAS**: Cost-effective, low power consumption, and easy to set up.
- **Multiple Storage Options**: Integrates HDDs, SSDs, USB flash drives, SD cards, etc.
- **OpenMediaVault Integration**: Web-based interface for easy NAS administration.
- **Security Measures**: Encryption, SSH, role-based access control, and robust backups.
- **Performance Optimization**: Utilizes deduplication, compression, and caching for higher throughput.
- **Cross-Platform Compatibility**: Supports SMB/CIFS, enabling access from Windows, macOS, Linux, iOS, and Android.

---

## 🏗 System Architecture
A **distributed storage model** is used to manage data from IoT devices:

[ IoT Devices ] --> [ Raspberry Pi 4 Running OMV ] --> [ HDD, SSD, USB, SD ] ↑ [ Security & Access Control ]

---


1. **IoT Devices** generate and send data to the Raspberry Pi.
2. **Raspberry Pi 4** (the NAS server) handles data processing, security, and management.
3. **Storage Devices** (HDD/SSD/USB/SD) store the incoming data.
4. **OpenMediaVault** provides a user-friendly web interface for administration.
5. **SMB/CIFS** or other protocols allow network-based file sharing.

---

## 🛠 Required Components
- **Raspberry Pi 4 Model B** (any RAM variant).
- **Type-C Power Supply** for Raspberry Pi 4.
- **microSD Card** (≥ 8 GB) for Raspberry Pi OS.
- **1 TB HDD**, **480 GB SSD**, or other drives (optional but recommended for higher storage).
- **Ethernet Cable** (or Wi-Fi) for network connectivity.
- **OpenMediaVault** (OMV) installed on Raspberry Pi.
- **Keyboard, Mouse, HDMI Monitor** (for initial setup, if needed).

---

## 📌 Installation Guide

### **Step 1: Install Raspberry Pi OS**
1. **Download** the latest Raspberry Pi OS from the [official website](https://www.raspberrypi.org/software/).
2. **Format** the microSD card using [SD Card Formatter](https://www.sdcard.org/downloads/formatter/).
3. **Flash** the OS image using [balenaEtcher](https://www.balena.io/etcher/).
4. **Insert** the microSD into the Raspberry Pi 4 and **power** it on.
5. **Optional**: Set up SSH headlessly by placing an empty `ssh` file in the `/boot` partition.  

---

### **Step 2: Install OpenMediaVault via Script**
1. **Open a terminal** on the Raspberry Pi (via SSH or locally).
2. **Run** this command to download and execute the OMV installation script:
   ```bash
   wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install \
   | sudo bash
3. Wait for the installation to complete (it may take several minutes).
4. The system will reboot automatically once done.


### **Step 3: Access OMV Web Interface**
1. Find the IP address of your Raspberry Pi (e.g., via ifconfig or your router’s DHCP list).
2. Open a browser on a PC or laptop on the same network.
3. Navigate to http://<RaspberryPi_IP_Address>/.
4. Log in using default credentials: <br>
Username: admin<br>
Password: admin<br>
5. Immediately change the default admin password under System > General Settings for security.

