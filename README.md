# task9-EL-

![Nmap Version](https://img.shields.io/badge/Tool-Nmap-blue.svg)
![Security-Level](https://img.shields.io/badge/Task-Reconnaissance-green.svg)

## 📋 Project Overview
This repository contains the documentation and methodology for a **Network Vulnerability Scan**. The goal was to identify live hosts, discover open ports, fingerprint services, and analyze security risks using **Nmap**.

## 🛠 Tools Used
* **Nmap:** Primary tool for network discovery and security auditing.
* **NSE (Nmap Scripting Engine):** Used for automated vulnerability detection.
* **Masscan (Optional):** Used for high-speed initial network sweeps.

## 🚀 Step-by-Step Implementation

### 1. Host Discovery
Scanned the local subnet to identify active devices.
```bash
sudo nmap -sn 192.168.1.0/24 -oN discovery.txt

### 2. Port & Service Enumeration
Identified open ports and probed services for version information.
```Bash
sudo nmap -sV -p 1-65535 -T4 192.168.1.50

### 3. Operating System Fingerprinting
Determined the target's OS to understand the environment.
```Bash
sudo nmap -O 192.168.1.50

### 4. Vulnerability Assessment
Executed NSE scripts to check for known exploits (CVEs).
```Bash
sudo nmap --script vuln 192.168.1.50 -oA scan_results

📊 Findings & Analysis
Target IP      Open Ports   Detected Service   Risk Level      Vulnerability/Notes
192.168.1.50  22, 80, 445   SSH, Apache, SMB   Critical       SMBv1 detected (EternalBlue risk)
192.168.1.55   8080         HTTP-Proxy         Medium         Outdated Apache Tomcat version
