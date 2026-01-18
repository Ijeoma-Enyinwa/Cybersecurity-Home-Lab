# Cybersecurity Home Lab & SOC Lab
## Developed by: Ijeoma Enyinwa

### 1. Project Overview
This project demonstrates the end-to-end deployment of an isolated cybersecurity lab. It features a manually configured **Kali Linux** offensive node, a **Windows 11** victim endpoint, and a **Wazuh SIEM** for real-time threat detection. 

The goal is to simulate real-world attacks (Red Team) and observe how they are logged and alerted within a Security Operations Center (Blue Team) environment.

---

### 2. Lab Architecture & Topology
I designed this lab using a **Type 2 Hypervisor** (VirtualBox) on an Intel-based macOS host. 



**Network Specifications:**
- **Hypervisor:** VirtualBox 7.x
- **Network Mode:** NAT Network (Isolated)
- **Subnet:** `10.0.2.0/24`
- **Gateway:** `10.0.2.1`


I configured a private **NAT Network** named `SecurityNatNetwork` with the CIDR `10.0.2.0/24`. This prevents any malicious traffic from "leaking" onto my physical home network.

<img width="1680" height="1050" alt="Screenshot 2026-01-18 at 6 47 45 PM" src="https://github.com/user-attachments/assets/4d2f60e1-f4de-4373-bcf4-61ed833709c2" />
Figure 1: Oracle VirtualBox Manager interface displaying the dual-node lab environment. Note the 'NAT Network' configuration with the name: "SecurityNatNetwork", ensuring the lab remains isolated from the host macOS network.


| Virtual Machine | Operating System | Role | IP Address | RAM | NOTES |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Kali-Red-Team** | Kali Linux 2024.x | Offensive / Pentesting | `10.0.2.5` | 2.5GB | I allocated 2560 MB (2.5GB) to the Kali node of RAM. Through baseline monitoring, I determined that the Xfce environment and the standard penetration testing suite maintained a low memory footprint. This allowed me to prioritise 6GB of RAM for the Windows 11 target to prevent service crashes during aggressive scanning, while maintaining a 5.5GB buffer for the host OS to prevent system crashes. |
| **Win11-Victim** | Windows 11 Pro | Defensive / Target | `10.0.2.10` | 6GB | **Hypervisor Selection Rationale** - Initially, Parallels Desktop was considered for the Windows 11 node. However, to ensure network isolation and parity between the offensive (Kali) and defensive (Windows) endpoints, the lab was standardised on **Oracle VirtualBox**. **Key Benefit:** This allowed for a unified 'NAT Network' adapter, preventing 'traffic leakage' to the host machine's physical network while allowing full inter-VM communication. |
| **Wazuh-Manager** | Ubuntu Server | SIEM / Log Analysis | `10.0.2.15` | 2GB | - |

---

