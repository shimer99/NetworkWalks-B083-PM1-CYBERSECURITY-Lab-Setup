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

![VirtualBox home screen](screenshots/01-virtualbox-home.png)

### Step 2. Import Kali Linux

The Kali Linux 2026.2 (Rolling) x64 virtual machine image was imported into VirtualBox, using an 80.09 GB SATA virtual disk. Default Kali credentials (kali / kali) were used for first login.

![Kali VM details](screenshots/02-kali-vm-details.png)
