# Cybersecurity-Lab-Setup
Week 1 Cybersecurity Lab setup using VirtualBox and Kali Linux 


#Overview
The purpose of this lab is to create an isolated environment, where cybersecurity, networking and penetration testing concepts can be practiced safely on  authorized virtual machines.


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

## Network Topology

```text
                    Internet
                       |
                 VirtualBox NAT
                       |
                  CyberLab
                10.0.0.0/24
                       |
                  Kali Linux
                   10.0.0.2
