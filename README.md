**Objective: To build a controlled environment to simulate attacks and monitor logs using Kali Linux and Windows 11.**

**Hardware Host:** MacBook Pro 2017 (Intel i7, 16GB RAM) 
**Hypervisor Choice:** Oracle VirtualBox 7.x

**Rationale:** While Parallels offers high performance for daily use, VirtualBox was selected for this lab to ensure seamless internal networking between the offensive (Kali) and defensive (Windows) nodes using a unified virtual switch.


**Lab Architecture**

**Hypervisor:** VirtualBox (Type 2)

**Internal Network:** NAT Network (Name: Security_Lab)

**Subnet:** 10.0.2.0/24

**Node A (Attacker):** Kali Linux (10.0.2.5) - I chose the installer image (ISO) over the pre-built image (the VM) specifically to perform a manual installation for system hardening and custom partitioning.

**Node B (Victim):** Windows 11 (10.0.2.10)

**Node C (SIEM/SOC):** Wazuh Manager (Running on Linux)
