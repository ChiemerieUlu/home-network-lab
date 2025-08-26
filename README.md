# Isolated Home Network Lab: DHCP & Port Forwarding

## 📖 Project Overview

This project is a hands-on lab which demonstrates core networking concepts- **DHCP Reservation** and **Port Forwarding** conducted on a **physically isolated home network**. The goal was to successfully host and access a simple HTTP server from a client device within the network. The entire lab was performed on a network segment with no connection to the internet.

## 🎯 Learning Objectives

- [x] Understand and manage a router's administrative interface.
- [x] Explain the difference between dynamic and static IP addressing.
- [x] Implement a DHCP Reservation (Static Lease) for a specific device.
- [x] Configure a Port Forwarding rule to direct external traffic to an internal server.
- [x] Set up a basic HTTP server on a local machine.
- [x] Test and validate the entire network path from client to server.

## 🛠️ Technologies & Hardware Used

- **Router:** Huawei EchoLife HS8545M5 
- **Server:** Windows 10 Pro PC
- **Client:** iPhone XR
- **Software:** Python 3 (`http.server`), Command Prompt

## 🔧 Methodology & Steps

### Step 1: Network Isolation and Access
1. Physically disconnected the WAN/Internet cable from the Huawei router.
2. Connected the Windows 10 Pro PC to the router via Ethernet for stability.
3. Accessed the router's administration panel at `http://192.168.100.1`.

### Step 2: DHCP IP Reservation
The goal was to assign a permanent IP address to the server PC to ensure reliable port forwarding.
1. Located the PC's MAC address via `ipconfig /all` in Command Prompt.
2. Navigated to the **DHCP -> Static IP Configuration** section on the Huawei router.
3. Created a new binding for the server's MAC address to the static IP `192.168.100.50`.

### 3. Port Forwarding Rule
- Navigated to the **Forward Rules -> Port Mapping Configuration**  section in the Huawei router admin panel.
- Created a new rule:
  - **External Port:** `8080`
  - **Internal IP Address:** `192.168.100.50`
  - **Internal Port:** `80`
  - **Protocol:** `TCP`

### 4. HTTP Server Setup and Testing
- On the server machine (Windows PC), created a project directory and a simple `index.html` file.
- Opened Command Prompt as Administrator (required to use port 80 on Windows).
- Navigated to the directory and launched the HTTP server:
  ```bash
  python -m http.server 80
