# 📊 Network Traffic Analysis Report – testphp.vulnweb.com

## 🧪 Overview

This report provides an in-depth analysis of network traffic captured while interacting with the intentionally vulnerable site [http://testphp.vulnweb.com](http://testphp.vulnweb.com). The goal is to identify and understand key network protocols using **Wireshark** on **Kali Linux**.

Captured traffic reveals how common protocols like **DNS**, **TCP**, **HTTP**, **ARP**, and **TLS** work together to deliver a complete web session.

---

## 1. 🎯 Traffic Capture Process

###  Live Capture Setup

To ensure that traffic between the browser and the target site was captured, Wireshark was launched and actively monitoring the network interface (`eth0`) while submitting form data on `testphp.vulnweb.com`.

📸 **Screenshot:**

![](https://github.com/deepthiii33/Elavate_Labs_task-5/blob/main/screenshots/before_capture.png)

### ✅ After Capturing Traffic

After interacting with `testphp.vulnweb.com`, the capture was stopped. This screenshot shows the populated packet list after browsing activity.

📸 **Screenshot:** 

![After Capture](https://github.com/deepthiii33/Elavate_Labs_task-5/blob/main/screenshots/after_capture.png)

---

## 2. 📈 Protocol Hierarchy Breakdown

The protocol hierarchy view in Wireshark summarizes all observed protocols and their data volume:

- **Major Protocols:** IPv4, TCP, HTTP, TLS, DNS
- **Supporting Protocols:** ARP, UDP

📸 **Screenshot:** 

![](https://github.com/deepthiii33/Elavate_Labs_task-5/blob/main/screenshots/protocol_hierarchy.png)

---

## 3. 🌐 DNS – Domain Name Resolution

DNS packets show the resolution process of `testphp.vulnweb.com` into an IP address prior to any HTTP request.

📸 **Screenshot:** 

![](https://github.com/deepthiii33/Elavate_Labs_task-5/blob/main/screenshots/dns_example.png)

---

## 4. 🔌 TCP – Connection Establishment (3-Way Handshake)

Using the filter `tcp.flags.syn == 1`, we observe the initial **SYN** packets that start the TCP 3-way handshake:

1. **SYN** – Client initiates connection
2. **SYN, ACK** – Server responds
3. **ACK** – Client confirms

📸 **Screenshot:** 

![](https://github.com/deepthiii33/Elavate_Labs_task-5/blob/main/screenshots/tcp_handshake.png)

---

## 5. 📡 ARP – Address Resolution Protocol

ARP packets reveal MAC address resolution on the local network, necessary before sending IP packets to the gateway or other devices.

📸 **Screenshot:** 

![](https://github.com/deepthiii33/Elavate_Labs_task-5/blob/main/screenshots/arp_traffic.png)

---

## 6. 📄 HTTP – Web Communication

### 🔍 HTTP GET Request

A typical HTTP GET request is captured when the browser fetches data from the target site.

📸 **Screenshot:** 

![](https://github.com/deepthiii33/Elavate_Labs_task-5/blob/main/screenshots/http_get.png)

### 📨 HTTP POST Request

An HTTP POST request was captured, likely from a form submission or login activity on the site.

📸 **Screenshot:** 

![](https://github.com/deepthiii33/Elavate_Labs_task-5/blob/main/screenshots/http_post.png)

---

## 7. 🔐 TLS – Encrypted HTTPS Traffic

Though the handshake isn't fully visible, **TLS Application Data** packets indicate encrypted communication over TCP port 443.

📸 **Screenshot:** 

![](https://github.com/deepthiii33/Elavate_Labs_task-5/blob/main/screenshots/tls_enc_data.png)

---

## 8. 🧠 Protocols Identified

| Protocol | Function |
|----------|----------|
| **ARP**  | Resolves MAC address from IP on local network |
| **DNS**  | Resolves domain names to IP addresses |
| **TCP**  | Establishes reliable connection |
| **HTTP** | Retrieves web content via GET/POST |
| **TLS**  | Encrypts communication (HTTPS) |
| **IPv4** | Routes packets over the network |
| **UDP**  | Used in DNS queries and local discovery |

---

## ✅ Conclusion

This analysis demonstrates how various protocols coordinate to support web browsing:

- ARP and DNS handle network setup and name resolution.
- TCP ensures reliable delivery.
- HTTP and TLS deliver and secure web content.

Wireshark’s filtering and visualization tools made it easy to observe each protocol’s role.

---

*Conducted using Kali Linux and Wireshark. Target: testphp.vulnweb.com — an authorized testing environment.*
