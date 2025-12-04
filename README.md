<p align="center">
  <img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

# Network Security Groups (NSGs) & Traffic Inspection Between Azure Virtual Machines  
This project demonstrates how to analyze network traffic between two Azure virtual machines using **Wireshark**, and how **Network Security Groups (NSGs)** influence network communication.  

This is core knowledge for IT Support, Help Desk, Cybersecurity, and System Administration roles, as it teaches:

- How network protocols operate  
- How to inspect packets  
- How firewall rules affect traffic  
- How to troubleshoot connectivity issues  

---

# 🧰 **Technologies & Tools Used**
- Microsoft Azure (Virtual Machines)
- Remote Desktop Protocol (RDP)
- Command Line Interface (Windows & Linux)
- Wireshark (Protocol Analyzer)
- Network Protocols: **ICMP, SSH, DNS, DHCP, HTTP/S, RDP**
- Azure Network Security Groups (NSGs)

---

# 💻 **Operating Systems Used**
- **Windows 10 (21H2)** — Traffic inspection host  
- **Ubuntu Server 20.04** — Linux target system  

---

# 🌐 **Project Overview**
In this lab:

- Two Azure VMs (Windows + Linux) are created in the same **Virtual Network (VNet)**.
- Wireshark is installed on the Windows VM to analyze traffic.
- The Linux VM is used as a target for pings, SSH sessions, and DNS lookups.
- NSGs are modified to block and allow specific traffic types.
  
This mirrors real-world troubleshooting scenarios where support teams diagnose connection failures and validate firewall rules.

---

# 🛠️ **Step-by-Step Actions & Observations**

---

## 🔹 Step 1 — Create Two Azure VMs in the Same Virtual Network
- **Windows 10 VM** → Used to generate and capture traffic with Wireshark  
- **Ubuntu 20.04 VM** → Target for network tests  
- Both machines: **2 vCPUs**, same VNet  

Install Wireshark on the Windows VM:  
👉 https://www.wireshark.org/download.html  

Filter Wireshark for ICMP packets.

<br/>

<img src="https://i.imgur.com/IIUShxp.png" width="80%" alt="ICMP Ping"/>

---

## 🔹 Step 2 — Capture ICMP Traffic (Ping)
ICMP is a diagnostic protocol used for network testing.

Using Windows:


Wireshark displays:

- Echo Request (ping)
- Echo Reply (response from Linux VM)

You can inspect each packet to view payload and metadata.

<br/>

<img src="https://i.imgur.com/GLxSIG3.png" width="80%" alt="Inspect ICMP"/>

---

## 🔹 Step 3 — Block & Allow ICMP Using NSGs

Next, run a continuous ping:


Modify the Linux VM’s **Network Security Group**:

- **Block ICMP inbound** → Ping fails  
- **Allow ICMP inbound** → Ping succeeds  

This demonstrates how firewall rules instantly impact communication.

<br/>

<img src="https://i.imgur.com/5vXO75R.png" width="80%" alt="ICMP blocked"/>
<img src="https://i.imgur.com/Asl80tN.png" width="80%" alt="ICMP allowed"/>

---

## 🔹 Step 4 — Capture SSH Traffic
SSH allows secure remote access to Linux systems.

On Windows, filter Wireshark for:


Then connect to the Linux server:


Wireshark captures encrypted SSH packets immediately.

<br/>

<img src="https://i.imgur.com/zteR41r.png" width="80%" alt="SSH traffic"/>

---

## 🔹 Step 5 — Capture DHCP Traffic  
DHCP (ports 67/68) assigns IP addresses on networks.

Renew the IP address on Windows:


Wireshark will capture DHCP Discover, Offer, Request, and ACK messages.

<br/>

<img src="https://i.imgur.com/vU8fpQf.png" width="80%" alt="DHCP traffic"/>

---

## 🔹 Step 6 — Capture DNS Traffic  
DNS (port 53) translates domain names to IP addresses.

Run:


Wireshark shows DNS queries and responses between the Windows VM and its DNS server.

<br/>

<img src="https://i.imgur.com/VMcwmsO.png" width="80%" alt="DNS traffic"/>

---

## 🔹 Step 7 — Inspect RDP Traffic  
RDP uses port **3389** — and since you're connected via RDP to the VM, traffic constantly flows.

Filtering for **tcp.port == 3389** or selecting the RDP protocol in Wireshark shows this activity clearly.

<br/>

<img src="https://i.imgur.com/VxXGv6X.png" width="80%" alt="RDP traffic"/>

---

# 🎯 **Skills Demonstrated**

### 🔍 Network Analysis  
- Capturing ICMP, SSH, RDP, DNS, DHCP traffic  
- Understanding packet structure & metadata  
- Recognizing protocol behavior under different conditions  

### 🔐 Firewall & Security  
- Creating and modifying NSGs  
- Blocking/allowing inbound traffic  
- Real-time testing of firewall rule effects  

### 🧩 Troubleshooting  
- Diagnosing connection issues  
- Confirming communication paths  
- Validating whether problems are OS-level or network-level  

### 💻 System Administration  
- Using SSH and RDP to manage remote servers  
- Renewing IPs, inspecting DNS settings  
- Interpreting protocol behavior for debugging  

---

# 🏁 **Summary**

This project provides hands-on experience with:

- Azure networking  
- Traffic inspection  
- Network protocol behavior  
- Firewall rule testing  
- Diagnostic troubleshooting  

These skills directly apply to:

- **IT Support Specialist**  
- **Help Desk Technician**  
- **Network Support Technician**  
- **System Administrator (Junior)**  
- **Cybersecurity Analyst (Entry)**  

Understanding packet flow and firewall behavior is essential for modern IT environments — this project proves you can analyze and diagnose network traffic just like a real support engineer.

