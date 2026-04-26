# Design, Build, and Secure a Small Network (Physical Mode)

## Project Overview
This project involved the end-to-end design and physical deployment of a multi-subnet network within Cisco Packet Tracer's Physical Mode. Unlike standard logical labs, this required manual hardware racking, power management, and out-of-band management via console cabling. The project demonstrates proficiency in subnetting design, physical layer connectivity, and network hardening.

## Environments and Technologies Used
* **Cisco Packet Tracer (Physical Mode)**: Used for realistic hardware racking and cabling.
* **Cisco IOS CLI**: For device configuration (Routers & Switches).
* **IPv4 Subnetting (VLSM)**: Designed a custom addressing scheme to optimize address space.
* **SSH Protocol**: Implemented for secure remote management.
* **Network Security**: Applied password encryption and console hardening.

## Physical Implementation 
<img width="449" height="470" alt="image" src="https://github.com/user-attachments/assets/c773e47c-12ea-4597-bf26-445175e41f56" /><img width="686" height="449" alt="image" src="https://github.com/user-attachments/assets/45bd050f-81ed-41d6-a77c-7408216324c0" />
**Physical Infrastructure Details**:
* **Rack Mounting**: 1U Cisco 4321 Integrated Services Router and two 1U Cisco 2960 Catalyst Switches mounted in a standard 19-inch rack.
* **Power Management**: All network nodes are integrated into a centralized Power Distribution Unit (PDU) for surge protection and power redundancy.
* **Cabling Standards**: * Data Plane: Copper Straight-Through (Green Cables) cabling utilized for Router-to-Switch uplinks and Host-to-Switch access links.
* **Management Plane**: RJ-45 to RS-232 Roll-Over (Console/Blue Cable) cabling used for out-of-band configuration and monitoring via PC0.

## Objectives
1. **Physical Hardware Deployment**: Manually rack and power one Cisco 4321 router and two Cisco 2960 switches.
2. **Layer 1 Connectivity**: Establish data links using Copper Straight-Through cables and management links using Roll-Over (Console) cables.
3. **Subnet Design**: Partition a 192.168.10.0/24 network into two /25 subnets to support separate broadcast domains.
4. **Network Hardening**: Configure SSH, encrypted secrets, and banner warnings to secure the infrastructure.

## Addressing Table (Custom Design)
<img width="574" height="389" alt="image" src="https://github.com/user-attachments/assets/014eeb3c-31d3-47e6-b929-681e477ec26f" />

## Configuration & Implementation Steps
* **Step 1**: Physical Layer & Out-of-Band Management
Action: Racked devices in a standard telecommunications closet layout. Connected PC0 to the Router’s Console port using an RS-232 to RJ-45 Roll-Over cable.
* **Troubleshooting**: Identified and corrected a terminal configuration mismatch (Parity settings) to establish a clean CLI session.

* **Step 2**: Interface Configuration & Subnetting
Logic: Divided the class C block into two subnets.
Action: Enabled GigabitEthernet interfaces and assigned gateway addresses.
<img width="511" height="343" alt="image" src="https://github.com/user-attachments/assets/b78ec5eb-f73b-464c-ab23-74948a4ff06b" />

* **Step 3**: Security Hardening (SSH & Encryption)
* **Action**: Moved management from insecure console access to encrypted SSH.
* **Commands**:
* Generated 1024-bit RSA keys `crpyto key generate rsa`.
* Configured `transport input` ssh on VTY lines.
* Enabled `service password-encryption` to protect sensitive data in the configuration file.

## Verification & Connectivity Tests
<img width="558" height="276" alt="image" src="https://github.com/user-attachments/assets/dcf34ff2-0163-474e-8210-96203c866ce3" />
* **Reflection**: This lab reinforced the importance of Layer 1 troubleshooting. In physical Mode, connectivity issues are often hardware-related (power, cable type, or port choice) rather than just configuration errors. Documenting the cabling map was essential for maitaining order in the multi-switch enviroment.

## Techincal Veriication & Verification Artifacts
The following sections provice documented proof of the network's operational status across the Physial, Data and Management planes.

1. **Layer 3 Routing & Subnet Integrity**

This output confirms that the Cisco 4321 router is correctly processing the VLSM design and recognizes both the `192.168.10.0/25` and `192.168.10.128/25` segments.


2. **Interface Operational Status**

Verification that all physical links are "Up/Up" and assigned to the correct gateway interfaces.

3. **Deep Dive: Configuration & Security (Expand to View)****
**SSH Management Status****
Confirms that the RSA key pair (1024-bit) was successfully generated and the SSH version 1.99/2.0 is active for secure remote management.

**Full Device Configuration**
The complete `running-config` showing `service password-encryption`, `enable secret`, and `line vty` security implementations.


4. **End-to-End Connectivity Proof (ICMP)**
This screenshot/snippet demonstrates a successful ping from **PC0** in Subnet A to **PC1** in Subnet B, proving the router is successfully moving traffic between the two broadcast domains.
