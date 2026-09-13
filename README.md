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

  
![image alt](https://github.com/Sama-41/Cybersecurity-Lab-Setup/blob/main/Screenshot_3.png?raw=true)

# Step 5: Configure Kali Linux Network
Start the Kali Linux virtual machine and inspect its network configuration.

The laboratory uses a private IPv4 configuration similar to:

IP address: 10.0.0.2
Subnet mask: 255.255.255.0
Default gateway: 10.0.0.1
DNS server: 8.8.8.8

The exact procedure for entering these values may depend on the version of Kali Linux and the network-management software being used.
After making the configuration changes, reconnect the network or restart the relevant networking service if necessary.
A consistent IP address makes the machine easier to identify when completing later laboratory exercises.

![image alt](https://github.com/Sama-41/Cybersecurity-Lab-Setup/blob/main/Screenshot_4.png?raw=true)

# Step 6 – Create a Baseline Snapshot
Once Kali Linux has been configured and tested, create a VirtualBox snapshot.

Give the snapshot a descriptive name, such as:

Clean Kali - Network Setup

This snapshot represents the working state of the laboratory immediately after the initial setup.

If a later experiment modifies the operating system or networking configuration, the VM can be returned to this known-good state instead of rebuilding the environment from the beginning.
  



# Testing and verifying the Laboratory
After completing the configuration, several checks were performed.

#### I. Check the IP Configuration
Open a terminal in Kali Linux and run:

ip a

Checked that the expected network interface was an IPv4 address belonging to the laboratory subnet.

For the reference configuration, the address was similar to:

10.0.0.2/24

#### II. Test the Virtual Gateway
Test communication with the virtual gateway:

ping 10.0.0.1

Successful replies indicated that Kali can communicate with the NAT Network gateway.

#### III. Test External Connectivity
Next, test connectivity to an external IP address:

ping 8.8.8.8

If replies are received, the virtual machine has external IP connectivity.

#### IV. Test DNS
IP connectivity alone does not prove that DNS is functioning. Test name resolution with:

nslookup networkwalks.com

A successful response indicates that the configured DNS service can resolve the requested domain.

#### V. Confirm Nmap Installation
Check whether Nmap is installed and available:

nmap --version

The command should return information about the installed Nmap version.

#### VI. Test the Snapshot
Finally, verified that the VirtualBox snapshot could be restored.

After restoring the baseline snapshot, run:

ip a

Confirmed that the machine had returned to the expected laboratory configuration.

# Troubleshooting

### Loss of Connectivity After Setting a Static Address
A static IPv4 configuration can occasionally result in connectivity problems depending on the Kali Linux network-management configuration.

One configuration adjustment documented in the reference laboratory is:

sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0

After making a change, reconnect the network and test connectivity again.

The connection name may not be "Wired connection 1" on every installation. Therefore, identifying the actual NetworkManager connection name on the system before applying an nmcli command.

### Virtualization or VT-x Error
If VirtualBox reports that hardware virtualization is unavailable, check whether virtualization support is enabled in the computer's firmware.

A typical procedure is:

Shut down or restart the computer.
Enter the BIOS/UEFI configuration screen.
Locate the processor or virtualization settings.
Enable Intel VT-x or the corresponding hardware virtualization feature.
Save the firmware settings.
Restart the computer.
Open VirtualBox and start the Kali Linux VM again.
The exact BIOS/UEFI menu names differ between computer manufacturers.

# Final Verification
Before considering the laboratory complete, the following were verified:

VirtualBox launched normally.
Kali Linux started without virtualization errors.
Kali is connected to the correct NAT Network.
The Kali machine had the expected IPv4 configuration.
The gateway responded to ping.
External IP connectivity works.
DNS resolution worked.
Nmap is available.
A clean VM snapshot was created.
The snapshot can be restored successfully.


# Security Considerations
The laboratory should remain in a controlled environment for cybersecurity education.

Security tools such as network scanners and penetration-testing software should only be used against systems that you own or have explicit permission to test. Keeping practice targets inside the dedicated virtual network helps reduce the possibility of unintentionally interacting with unrelated systems.

The snapshot should also be maintained as a clean recovery point before performing experiments that could alter the virtual machine.

# Lessons Learnt
1. The completed laboratory provided a foundation for future cybersecurity exercises. VirtualBox supplies the virtualization layer, while Kali Linux provides the security-testing environment.

2. The NAT Network allows multiple virtual machines to communicate within a controlled network, making it suitable for future exercises involving reconnaissance, vulnerability assessment, packet analysis, and other authorized security-testing activities.

3. Creating a clean snapshot at the end of the setup is particularly useful because it provides a known working state to which the Kali machine can be returned after experimental changes.

4. I learnt how to configure and verify IPv4 addressing, subnet mask, Default gateway and DNS statically. 

5. The strongest approach is to supplement this procedure with your own screenshots, commands actually executed, test results, problems encountered, and observations rather than presenting the source repository's text as your own.



# Tools
- 7-zip: https://7-zip.org/download.html
- VirtualBox: https://virtualbox.org/wiki/downloads
- Kali Linux: https://kali.org/get-kali












                    
                      
