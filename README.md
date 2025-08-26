# Isolated Home Network Lab: DHCP & Port Forwarding

## 📖 Project Overview

This project is a hands-on lab conducted on a **physically isolated home network** (no internet connection). The goal was to configure core networking concepts—**DHCP Reservation** and **Port Forwarding**—to successfully host and access a simple HTTP server from a client device within the network.

## 🎯 Learning Objectives

- [x] Understand and manage a router's administrative interface.
- [x] Explain the difference between dynamic and static IP addressing.
- [x] Implement a DHCP Reservation (Static Lease) for a specific device.
- [x] Configure a Port Forwarding rule to direct external traffic to an internal server.
- [x] Set up a basic HTTP server on a local machine.
- [x] Test and validate the entire network path from client to server.

## 🛠️ Technologies & Hardware Used

- **Router:** Airtel 4G Smartbox
- **Server:** Windows 10 Pro PC
- **Client:** iPhone XR
- **Software:** Python 3 (`http.server`), Command Prompt

## 🔧 Methodology & Steps

### 1. Lab Setup
- Disconnected the router's WAN/Internet cable to create a closed, safe lab environment.
- Connected the server (Windows 10 PC) to the router via Wi-Fi.
- Connected a client device (iPhone XR) to the router's Wi-Fi.

### 2. DHCP Reservation
- Accessed the Airtel router's admin panel at `http://192.168.0.1`.
- Located the DHCP Client List (often under "Connected Devices" or "LAN Settings") to find the server's MAC address and current dynamic IP.
- Created a DHCP Reservation rule, binding the server's MAC address to a static IP: `192.168.0.50`.
- Renewed the DHCP lease on the server (`ipconfig /release` followed by `ipconfig /renew`) and verified the new static IP was assigned using `ipconfig`.

### 3. Port Forwarding
- Navigated to the **Port Forwarding** or **NAT** section in the Airtel router admin panel.
- Created a new rule:
  - **External Port:** `8080`
  - **Internal IP Address:** `192.168.0.50`
  - **Internal Port:** `80`
  - **Protocol:** `TCP`

### 4. HTTP Server Setup
- On the server machine (Windows PC), created a project directory and a simple `index.html` file.
- Opened Command Prompt as Administrator (required to use port 80 on Windows).
- Navigated to the directory and launched the HTTP server:
  ```bash
  python -m http.server 80
