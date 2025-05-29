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

