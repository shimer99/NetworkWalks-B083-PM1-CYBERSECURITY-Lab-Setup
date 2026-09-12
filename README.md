# NetworkWalks-B083-PM1-CYBERSECURITY-Lab-Setup
Building an isolated virtual lab for penetration testing and ethical hacking practice

# Project Overview

This project documents my setup of a virtual cybersecurity and penetration-testing lab using Oracle VirtualBox and Kali Linux 2026.2.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly, on an isolated internal network.

# Objectives
- Install and configure Oracle VirtualBox
- Import Kali Linux 2026.2 as a virtual machine
- Create a private NAT Network for the lab
- Configure network connectivity for the Kali VM
- Assign a consistent (static) IP address to the Kali VM
- Verify network connectivity and interface configuration
- Document the complete setup process

# Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing. It can be used for:

Network reconnaissance
Port scanning
Vulnerability assessment
Packet analysis
Security-tool experimentation

⚠️ Important: This lab must only be used for systems I own or have explicit permission to test.

# Lab Configuration

| Component | Configuration |
| :--- | :--- |
| Hypervisor | Oracle VirtualBox |
| Security OS | Kali Linux 2026.2 (Rolling), x64 |
| VM Disk | 80.09 GB (SATA) |
| Virtual Network | NAT Network — `NatNetwork` |
| Network Adapter | Intel PRO/1000 MT Desktop (82540EM) |
| MAC Address | 08:00:27:5A:87:BC |
| Promiscuous Mode | Deny |
| IPv4 Prefix (Net) | 10.0.0.0/24 |
| IPv6 Prefix (Net) | fd17:625c:f037:2::/64 |
| DHCP on Network | Enabled |
| Kali IP Address | 10.0.0.2/24 (static) |
| Default Gateway | 10.0.0.1 |
| DNS Server | 8.8.8.8 |

# Lab Setup Procedure
### Step 1. Install VirtualBox

Oracle VirtualBox was installed and launched as the hypervisor for the lab.

![VirtualBox home screen](https://github.com/shimer99/NetworkWalks-B083-PM1-CYBERSECURITY-Lab-Setup/blob/main/Screenshot%202026-09-09%20015309.png?raw=true)

### Step 2. Import Kali Linux

The Kali Linux 2026.2 (Rolling) x64 virtual machine image was imported into VirtualBox, using an 80.09 GB SATA virtual disk. Default Kali credentials (kali / kali) were used for first login.

![Kali VM details](https://github.com/shimer99/NetworkWalks-B083-PM1-CYBERSECURITY-Lab-Setup/blob/main/Screenshot%202026-09-09%20015608.png?raw=true)

### Step 3. Create the NAT Network

A dedicated NAT Network named **NatNetwork** was created in VirtualBox with the following configuration:

```text
Network Name: NatNetwork
IPv4 Prefix:  10.0.0.0/24
IPv6 Prefix:  fd17:625c:f037:2::/64
DHCP:         Enabled
```

![NAT Network configuration](https://github.com/shimer99/NetworkWalks-B083-PM1-CYBERSECURITY-Lab-Setup/blob/main/Screenshot%202026-09-09%20020232.png?raw=true)

A NAT Network was chosen (rather than a plain NAT adapter) because it allows multiple VMs attached to the same network to communicate with each other while still having outbound internet access — which will support adding target VMs to this lab later.

### Step 4. Attach the Kali VM to the NAT Network

The Kali VM's network adapter was configured as follows:

Adapter 1
Attached to:   NAT Network
Network:       NatNetwork
Adapter Type:  Intel PRO/1000 MT Desktop (82540EM)
Promiscuous Mode: Deny
MAC Address:   08:00:27:5A:87:BC

![Kali VM network adapter settings](https://github.com/shimer99/NetworkWalks-B083-PM1-CYBERSECURITY-Lab-Setup/blob/main/Screenshot%202026-09-09%20020320.png?raw=true)

### Step 5. Boot the Kali VM

The VM was powered on and booted successfully into Kali Linux via GRUB.

![Kali VM booting](https://github.com/shimer99/NetworkWalks-B083-PM1-CYBERSECURITY-Lab-Setup/blob/main/Screenshot%202026-09-09%20020409.png?raw=true)

### Step 6. Configure a Static IP on Kali

The Kali network connection was manually configured with a static IPv4 address to keep the machine consistently addressable within the lab:

Method:    Manual
Address:   10.0.0.2
Netmask:   24 (255.255.255.0)
Gateway:   10.0.0.1
DNS:       8.8.8.8

![Kali static IP configuration](https://github.com/shimer99/NetworkWalks-B083-PM1-CYBERSECURITY-Lab-Setup/blob/main/Screenshot%202026-09-09%20022214.png?raw=true)

# Lab Verification

The network configuration was verified using ifconfig inside the Kali VM:

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
      inet 10.0.0.2  netmask 255.255.255.0  broadcast 10.0.0.255
      inet6 fe80::d3c0:263c:d612:d72c  prefixlen 64  scopeid 0x20<link>
      ether 08:00:27:5a:87:bc  txqueuelen 1000  (Ethernet)
      RX packets 2  bytes 650 (650.0 B)
      TX packets 23  bytes 2828 (2.7 KiB)

![ifconfig output confirming static IP](screenshots/07-ifconfig-verification.png)

This confirms the Kali VM is correctly assigned the static IP 10.0.0.2/24 with the expected MAC address, matching the NAT Network configuration.

Test	Command	Result
Check IP address	ifconfig	✅ 10.0.0.2/24 assigned to eth0
<!-- Add ping/gateway/internet/DNS/nmap results here once tested, e.g.: | Test gateway | `ping 10.0.0.1` | | | Test internet | `ping 8.8.8.8` | | | Test DNS resolution | `nslookup kali.org` | | -->

# Problems Encountered & Solutions
<!-- Add any issues you ran into during setup, e.g. VT-x errors, NIC not detected, DNS not resolving, etc. -->
# What I Learned
<!-- Your own reflections on NAT Networks, VirtualBox networking, static IP config, etc. -->
# Security & Ethical Use

This lab is intended strictly for educational purposes, on systems I own or am authorized to test.

# Tools & Resources
VirtualBox: https://virtualbox.org/wiki/Downloads
Kali Linux: https://kali.org/get-kali
# Acknowledgments

Documentation structure referenced from waqaskarimccie's Cybersecurity Lab Setup README.

# Author

[Your Name]

LinkedIn: <your link>
