# Cybersecurity-Lab-Setup
Week 1 Cybersecurity Lab setup using VirtualBox and Kali Linux 


## Overview

This project documents the setup of a local cybersecurity testing laboratory using VirtualBox and Kali Linux.

The purpose of the lab is to create an isolated environment where cybersecurity, networking, and penetration-testing concepts can be practiced safely on authorized virtual machines.

## Lab Objectives

- Set up a VirtualBox-based cybersecurity lab.
- Configure a dedicated NAT Network.
- Deploy Kali Linux as the primary security testing machine.
- Configure  NAT network for the lab.
- Configure network connectivity for the kali virtual machine.
- Assign IP address to the kali VM.
- Enable Internet connectivity for the lab
- Configure shared clipboard and file transfer functionality
- Take VM snapshots for recovery.
- Create a controlled environment for future cybersecurity exercises.

## Lab Environment

| Component | Configuration |
|---|---|
| Host OS | Windows 10 |
| Virtualization | Oracle VirtualBox |
| Attacking/Testing OS | Kali Linux |
| Lab Network | 10.0.0.0/24 |
| NAT Network | CyberLab |
| Kali IP | 10.0.0.2/24 |
| DNS IP | 8.8.8.8 |

## Network Topology

![image alt](https://github.com/Sama-41/Cybersecurity-Lab-Setup/blob/b62d8ef8dc9aed3b604ed25278c8720ad245cd9e/Screenshot%20(29).png)


 

## Lab Setup Procedure

# Step 1: Install 7-Zip

7-Zip was installed to allow extraction of the Kali Linux virtual machine files, which were provided in a compressed ".7z" archive.

Tool Used: 7-Zip
# Step 2: Install VirtualBox
VitualBox was installed as a hypervisor which is used to manage virtual machines

# Step 3: Configure the NAT Network

A separate NAT Network was created in VirtualBox to provide network connectivity between the virtual machines while keeping the lab environment isolated.

Network Configuration:

- Network Name: "NatNetwork"
- IPv4 Network: "10.0.0.0/24"
- DHCP: Enabled
- IPv6: Disabled
  ![image alt](https://github.com/Sama-41/Cybersecurity-Lab-Setup/blob/main/Screenshot-%202.png?raw=true)


# Step 4: Import Kali Linux

The Kali Linux virtual machine was obtained from the official Kali Linux source and then imported into VirtualBox for use in the lab environment.

After importing the VM, its network interface was configured to connect to the previously created NAT Network.

Network Adapter Configuration:

- Adapter: Adapter 1
- Connection Type: NAT Network
- Network: "NatNetwork"
- Adapter Type: Intel PRO/1000 MT Desktop
![image alt]()
  




















                    
                      
