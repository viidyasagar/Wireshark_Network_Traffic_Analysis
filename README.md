# Wireshark_Network_Traffic_Analysis
This project demonstrates how to capture and analyze live network traffic using **Wireshark** in **Kali Linux**. The goal is to observe and interpret DNS, TCP, and ICMP packets by generating live traffic through actions like ping and web browsing.

 **Project Goal:**
This project demonstrates how to perform real-time network traffic capture and deep protocol analysis using **Wireshark** on **Kali Linux**. The goal was to observe how network traffic behaves when common actions like `ping` or web browsing are performed.

⚙️ **Setup & Installation Steps:**

1. 🐧 OS: Kali Linux (VM with NAT)
2. 🛠️ Install Wireshark:

   ```bash
   sudo apt update
   sudo apt install wireshark -y
   sudo usermod -aG wireshark $USER
   ```
3. 🔁 Restart session (logout/login) to apply Wireshark group permissions.
4. 🚀 Launch Wireshark:

   ```bash
   wireshark &
   ```

---

🌐 **Traffic Generation:**

✅ In another terminal:

```bash
ping google.com
```

✅ Launched Firefox and visited:

```
http://example.com
```

---

🎥 **Capture Process:**

* Selected interface: `eth0`
* Started live capture
* Stopped after 1 minute
* Saved capture as `network-capture.pcap`

---

🔍 **Protocol Filters Used:**

* 📦 `dns` — to capture DNS queries/responses
* 🔁 `tcp` — to capture handshakes, retransmissions
* 📡 `icmp` — to capture echo requests/replies from ping

---

📸 **Captured Packet Analysis:**

### 1️⃣ DNS (Domain Name System)

* Queried `google.com`
* Received A (IPv4), AAAA (IPv6), and PTR records
* IP resolved: `142.250.192.110`
* 🔍 Captured both query and response packets

### 2️⃣ TCP (Transmission Control Protocol)

* Observed SYN → SYN-ACK → RST/ACK
* Multiple retransmissions and resets (RST)
* Ports involved: `57329`, `1515`, `41789`
* 💡 Connection issues detected, possibly blocked or dropped

### 3️⃣ ICMP (Ping Protocol)

* Continuous ping sent to `google.com`
* Alternating Echo Request and Echo Reply
* TTL = 64 and TTL = 128 showed hop count differences
* 🔁 Perfect round-trip behavior observed

---

📤 **Exported Files:**

* 🗂️ `network-capture.pcap` — complete packet dump
* 🖼️ Screenshots:

  * DNS queries
  * TCP handshakes
  * ICMP echo packets
  * Terminal commands & setup

---

📈 **Key Observations:**

* 🔹 DNS works as expected — both IPv4 & IPv6 resolutions seen
* 🔹 TCP connections show SYN flooding and reset packets
* 🔹 ICMP echo works flawlessly, replies received in sequence
* 🔹 Analysis reflects behavior of real-world network tools

---

📁 **Project Structure:**

```
wireshark-network-analysis/
├── README.md
├── network-capture.pcap
└── screenshots/
    ├── dns.png
    ├── tcp.png
    ├── icmp.png
    └── terminal-setup.png
```

---

🧠 **Conclusion:**

This project provided practical experience in live packet capturing, protocol-level traffic inspection, and network behavior analysis. Tools like Wireshark are essential in security analysis, threat hunting, and understanding how data moves across networks.

---

