
# 📡 Wireshark Network Traffic Analysis

This project demonstrates how to use **Wireshark** to analyze network traffic and detect common cybersecurity threats such as port scanning, plain-text credential leaks, and suspicious HTTP requests. The goal is to help aspiring SOC analysts practice packet inspection and threat detection in a virtual lab environment using Kali Linux and public or simulated traffic.

---

## 📁 Project Structure

```
wireshark-network-analysis/
├── README.md
├── screenshots/
│   ├── capturing.png
│   ├── port_scanning.png
│   ├── http_login_data.png
│   ├── installation_of_wireshark.png
│   ├── wireshark_fin_button.png
│   └── wireshark.png
└── captures/
    └── my_capture.pcapng
```

---

## 🛠 Tools Used

- **Wireshark** – Network protocol analyzer
- **Nmap** – To simulate port scans
- **Firefox** – To browse insecure HTTP pages (like httpforever.com)
- **Kali Linux** – Virtual testing environment
- **VirtualBox** – Virtual machine host

---

## 🎯 Objectives

- Capture live traffic using Wireshark
- Simulate suspicious activities (HTTP browsing, scanning)
- Analyze and detect threats using filters
- Document findings with screenshots

---

## 🧪 Steps Performed

### 1. Installed Wireshark on Kali Linux
```bash
sudo apt update && sudo apt install wireshark -y
```
🔹 Screenshot: `installation_of_wireshark.png`

---

### 2. Started Wireshark and Began Capturing
- Interface: `eth0`
- Clicked the blue **Start Capturing** button.
🔹 Screenshot: `wireshark_fin_button.png`

---

### 3. Visited Insecure HTTP Website
- Website: [httpforever.com](http://httpforever.com)
- Purpose: To generate unencrypted web traffic
🔹 Screenshot: `http_login_data.png`

---

### 4. Simulated Port Scanning
```bash
nmap -sS <target-ip>
```
- Captured SYN packets
- Filter used:
```wireshark
tcp.flags.syn == 1 and tcp.flags.ack == 0
```
🔹 Screenshot: `port_scanning.png`

---

### 5. Applied Filters in Wireshark

#### ✅ For HTTP logins:
```wireshark
http.request.method == "POST"
```

#### ✅ For Port Scanning:
```wireshark
tcp.flags.syn == 1 and tcp.flags.ack == 0
```

#### ✅ For suspicious URIs:
```wireshark
http.request.uri contains ".exe"
```

---

## 🖼️ Screenshots

All screenshots are saved under the `screenshots/` folder for each activity:
- Traffic capture
- Filtered results
- Tool interfaces

---

## ✅ Key Findings

| Threat | Evidence |
|--------|----------|
| Unencrypted HTTP | Found browsing to `httpforever.com` using HTTP |
| Port Scanning | Detected large number of SYN packets with no ACKs |
| Login Credentials | HTTP POST captured in plaintext |

---

## 🧠 What I Learned

- How to analyze .pcap files using Wireshark
- How to detect early-stage threats like port scans
- How to recognize insecure data transmission patterns

---

## 📌 Notes

- This lab was performed in a closed environment.
- Only simulated attacks were performed for educational purposes.
- Ideal for SOC Analyst (L1) resume and GitHub portfolio.
