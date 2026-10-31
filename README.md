Secure Campus Network Using Cisco Packet Tracer
A mini project demonstrating how to configure and secure a small campus network using Cisco Packet Tracer and Cisco IOS commands.

📌 Project Overview
This project simulates a small university department network with one router, two switches, and six PCs. The router connects two separate IP networks and enables communication between them. Security configurations help protect network devices from unauthorized access.

The project covers router and switch configuration, console and privileged EXEC security, SSH remote access, password encryption, switch port security using sticky MAC addresses, and network connectivity testing.

🎯 Objectives
Build a small campus network in Cisco Packet Tracer.
Configure IP addresses and default gateways.
Enable communication between two different IP networks through a router.
Secure console and privileged EXEC access.
Configure SSH for secure remote device management.
Enable password encryption in device configurations.
Apply sticky MAC address port security on access ports.
Disable unused switch ports.
Verify connectivity and security using Cisco IOS commands.
🧰 Tools and Technologies
Cisco Packet Tracer
Cisco IOS CLI
Router: Cisco 1941
Switches: Cisco 2960
End devices: 6 PCs
Protocols and features: IPv4, ICMP (ping), SSH version 2, port security, sticky MAC learning
🖧 Network Topology
The topology contains two networks:

Network 1: 192.168.10.0/24 — S1 connects PC1, PC2, and PC3.
Network 2: 192.168.20.0/24 — S2 connects PC4, PC5, and PC6.
Router R1 connects the two networks and acts as their default gateway.
Physical Connections
Device/Interface	Connected To
R1 G0/0	S1 G0/1
R1 G0/1	S2 G0/1
S1 Fa0/1	PC1
S1 Fa0/2	PC2
S1 Fa0/3	PC3
S2 Fa0/1	PC4
S2 Fa0/2	PC5
S2 Fa0/3	PC6
Use Copper Straight-Through cables for the connections listed above.

🌐 IP Addressing Plan
Subnet mask for both networks: 255.255.255.0 (/24).

Device	Interface	IP Address	Default Gateway
R1	G0/0	192.168.10.1	—
R1	G0/1	192.168.20.1	—
S1	VLAN 1	192.168.10.2	192.168.10.1
S2	VLAN 1	192.168.20.2	192.168.20.1
PC1	NIC	192.168.10.10	192.168.10.1
PC2	NIC	192.168.10.11	192.168.10.1
PC3	NIC	192.168.10.12	192.168.10.1
PC4	NIC	192.168.20.10	192.168.20.1
PC5	NIC	192.168.20.11	192.168.20.1
PC6	NIC	192.168.20.12	192.168.20.1
🔐 Security Features Implemented
1. Console and Privileged EXEC Security
Console passwords protect direct console access, while enable secret protects privileged EXEC mode.

2. Password Encryption
The service password-encryption command obfuscates plaintext line passwords in the configuration. It is basic protection, not strong encryption; use enable secret for privileged access.

3. Secure Remote Access with SSH
SSH version 2 is configured for remote administration. A local administrator account is used for authentication, and VTY lines are configured to accept SSH rather than Telnet.

4. Switch Port Security
Port security is enabled on PC-facing access ports Fa0/1–Fa0/3 on both switches. Each port allows one secure MAC address and uses sticky MAC learning. The violation action is shutdown, which disables the port when a security violation occurs.

5. Disable Unused Ports
Unused switch ports Fa0/4–Fa0/24 are shut down to reduce the risk of unauthorized devices connecting through them.

Security note: The accompanying project document contains example lab passwords. Do not reuse these credentials in real networks or publish real credentials in a public repository. Replace any lab credentials before sharing configuration files.

⚙️ Configuration Summary
The project documentation includes step-by-step Cisco IOS configuration for:

Router hostname and GigabitEthernet IP addresses
Router console password and enable secret
Password encryption
SSH domain name, local user, RSA keys, SSH version 2, and VTY access
Switch management IP addresses and default gateways
Switch console and SSH configuration
Sticky MAC port security on access ports
Shutdown of unused ports
Saving configuration to startup configuration
The exact commands and screenshots are documented in the project PDF.

🧪 Testing and Verification
The following checks are used to verify the network and security configuration.

Connectivity Tests
From PC1, open Desktop → Command Prompt and run:

ping 192.168.10.1
ping 192.168.20.10
ping 192.168.20.11
ping 192.168.20.12
The first command checks connectivity to the local router gateway. The remaining commands test communication with PCs on the second network.

SSH Tests
Examples from the project:

ssh -l admin 192.168.10.2
ssh -l admin 192.168.10.1
From PC4, test the S2 management address:

ssh -l admin 192.168.20.2
Enter the configured lab account credentials when prompted.

Port Security Verification
Run these commands on a switch:

show port-security
show port-security address
show port-security interface fastEthernet 0/1
show mac address-table
Check that port security is enabled, the maximum secure MAC address count is one, sticky MAC learning is active, and the violation mode is shutdown.

Demonstrating a Port Security Violation
Connect the expected PC to a secured port and generate traffic so the switch learns its MAC address.
Disconnect that PC and connect a different device to the same port.
Check the port-security status and interface state.
If the port is shut down, restore it after the test using the appropriate interface commands.
Observed results recorded in the project: gateway and inter-network ping tests succeeded, SSH access was tested, port security was enabled on both switches, and an unauthorized-device test caused the secured link to show a red/down state. The project also records unused ports as administratively down.

📂 Project Files
Suggested repository structure:

Secure-Campus-Network/
├── README.md
├── CiscoMiniProject1.pdf
└── SecureCampus.pkt
README.md — project overview and setup guide.
CiscoMiniProject1.pdf — detailed practical documentation, commands, screenshots, and test results.
SecureCampus.pkt — Packet Tracer simulation file, if included in the repository.
Only include the .pkt file if you have it available and are permitted to share it.

🚀 How to Run the Project
Install and open Cisco Packet Tracer.
Open the project .pkt file, if included. Otherwise, recreate the topology using one Cisco 1941 router, two Cisco 2960 switches, and six PCs.
Connect the devices according to the physical connection table.
Configure IP addresses, subnet masks, and default gateways according to the addressing plan.
Apply the router and switch configurations described in the PDF.
Test connectivity with ping.
Test SSH access and verify port security using the listed commands.
Save the Packet Tracer file and device configurations.
📚 Learning Outcomes
Understanding IPv4 addressing and default gateways
Connecting two IP networks through a router
Configuring Cisco routers and switches using the CLI
Using SSH for secure remote administration
Applying switch port security and sticky MAC learning
Testing connectivity and verifying security controls
✅ Conclusion
This mini project demonstrates how to build and secure a small campus network using Cisco Packet Tracer. It combines inter-network connectivity with console protection, privileged EXEC security, SSH remote administration, password obfuscation, sticky MAC port security, and shutdown of unused ports. These controls provide a practical introduction to basic network configuration and security.
document : Secure_Campus_Network_Mini_Project_Report_Teal
