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

<img width="415" alt="image" src="https://github.com/user-attachments/assets/48a54eaa-d76d-4d7f-a91b-5378d7513c90" />

---

1. **IoT Devices** generate and send data to the Raspberry Pi.
2. **Raspberry Pi 4** (the NAS server) handles data processing, security, and management.
3. **Storage Devices** (HDD/SSD/USB/SD) store the incoming data.
4. **OpenMediaVault** provides a user-friendly web interface for administration.
5. **SMB/CIFS** or other protocols allow network-based file sharing.

<img width="331" alt="image" src="https://github.com/user-attachments/assets/88ff2032-35e6-426a-b9c8-8b20d0e3533e" />


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

![image](https://github.com/user-attachments/assets/877c8aea-79f6-4209-b0db-ed04e2376037)

---

### **Step 3: Access OMV Web Interface**
1. Find the IP address of your Raspberry Pi (e.g., via ifconfig or your router’s DHCP list).
2. Open a browser on a PC or laptop on the same network.
3. Navigate to http://<RaspberryPi_IP_Address>/.
4. Log in using default credentials: <br>
Username: admin<br>
Password: admin<br>
5. Immediately change the default admin password under System > General Settings for security.

![image](https://github.com/user-attachments/assets/863ac0c1-2680-4a37-abc5-ff7c50e4aaba)


---

### **Step 4: Configure Storage in OMV**
1. Connect your external drives (HDD, SSD, USB, etc.) via USB.
2. In the OMV UI, go to Storage > Disks.
3. Select each disk and click “Wipe” if needed (erases existing data).
4. Create a File System: <br>
Navigate to Storage > File Systems.<br>
Click “Create”, select the disk, and choose a file system type (e.g., ext4).<br>
5. Mount the file system:<br>
After creation, select it and click “Mount”.<br>
Click “Apply” to confirm changes.<br>

![image](https://github.com/user-attachments/assets/d18f3469-7a7b-4201-b3ba-c18a666ecb9e)

---

### **Step 5: Create Shared Folders**
1. In OMV, go to Storage > Shared Folders.
2. Click “Add”.
3. Provide: <br>
A Name (e.g., Data, HDD1, etc.).<br>
A Path (auto-generated if you prefer).<br>
The File System you created in Step 4.<br>
4. Set Permissions (e.g., Read/Write for admin, etc.).
5. Repeat for each storage device (HDD, SSD, USB).

---

### **Step 6: Allocate Storage Space**
(Advanced Users Only)

By default, the entire disk space is available under each mounted file system.<br>
If you need precise control (quotas, partial allocations), you can configure:<br>
LVM (Logical Volume Manager) for more flexible partitioning.<br>
Quotas via Storage > File Systems > Quota in OMV to limit user space<br>

---

### **Step 7: Set Up Network Shares**
1. Enable SMB/CIFS:<br>
Go to Services > SMB/CIFS.<br>
Click “Enable” and “Save”.<br>
Adjust settings as required (workgroup name, etc.).<br>
2. Add SMB Shares:<br>
Under Services > SMB/CIFS > Shares, click “Add”.<br>
Select the Shared Folder created in Step 5.<br>
Adjust permissions and enable “Public” if you want open access on your LAN.<br>
3. Apply Config: Confirm and apply changes.<br>
4. Access from Other Devices:<br>
Windows: \\<RaspberryPi_IP_Address><br>
macOS/Linux: smb://<RaspberryPi_IP_Address>/<br>
5. (Optional): You can also configure FTP, NFS, or AFP if you have specific use cases.<br>

---

## 📊 Performance Evaluation

### **Speed Tests**
We tested the NAS setup by transferring a `1.2 GB .mkv` file and other sample data. Below are **observed vs. theoretical** speeds:

| **Storage Type**  | **Observed Speed (MBps)** | **Theoretical Speed (MBps)** |
|-------------------|---------------------------|------------------------------|
| **8 GB SD Card**  | 9 - 12                   | 50 - 70                      |
| **32 GB Pen Drive** | 10 - 15                  | 50 - 70                      |
| **1 TB HDD**      | 100 - 150                | 150 - 200                    |
| **480 GB SSD**    | 300 - 400                | 500 - 550                    |

#### **Key Observations**
1. **SSD outperforms HDD and USB drives** in both read/write speeds.
2. **Ethernet** improves transfer stability compared to Wi-Fi.
3. **Compression & Deduplication** can reduce storage usage and improve speeds.
4. **Integrated File Manager** (network-based) streamlines file access for users.

### **Mobile App Integration**
- An **iOS and Android** application can also be configured (using **SMB/CIFS** or specialized apps like **VNC**, **SSH**, or a custom front-end) to access the NAS on the go.

---

## 🔐 Security Measures
1. **Encryption**: Configure **AES-based** or **TLS** encryption for data at rest and in transit.
2. **Authentication**: Use **role-based** accounts and **strong passwords**.
3. **SSH**: Secure Shell access for admin tasks; disable root login if possible.
4. **Backup & Redundancy**:
   - Replicate data across multiple drives or off-site to **prevent single-point failures**.
5. **Compliance**: Align with **GDPR**, **HIPAA**, or IoT-specific privacy policies as needed.

---

## 🚀 Future Enhancements
1. **Edge Computing**: Process data locally to reduce latency for real-time IoT apps.
2. **AI-Based Predictive Storage**: Employ ML algorithms to optimize resource usage.
3. **Blockchain Security**: Integrate immutable ledgers to enhance data integrity.
4. **Advanced Remote Access**: Seamless multi-site replication and cloud integration.

---

## 🤝 Contributing
We welcome contributions! Please follow the steps below:
1. **Fork** this repository.
2. Create a new branch:
   ```bash
   git checkout -b feature/my-new-feature
3. Commit your changes:<br>
git commit -m "Add a new feature"
4. Push to the branch:<br>
git push origin feature/my-new-feature
5. Open a Pull Request and describe your changes for review.

---

## 📜 License
This project is licensed under the MIT License. See the LICENSE file for details.

---

## 📬 Contact & Support
Author: Shreyas Pradeepkumar Khandale
Affiliation: Watson College of Engineering & Applied Science, Binghamton University
Location: Binghamton, NY, USA

For questions or issues, please open a GitHub Issue or email the author directly.

---

## ⭐️ Final Notes
Star this repository if you found it helpful!
Feel free to share and fork to help others set up their own IoT-NAS.

---

### ✅ **Usage Instructions**
1. **Copy & Paste** the content above into a file named `README.md` in your GitHub repository.
2. **Commit** the file and **push it** to GitHub.
3. Your repository now contains **detailed performance evaluation, security measures, future enhancements, and contribution guidelines**.

🚀 **Your IoT-NAS project now has a complete and professional `README.md`!** 🚀


















