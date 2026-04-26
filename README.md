# Design, Build, and Secure a Small Network (Physical Mode)

## Project Overview
This project involved the end-to-end design and physical deployment of a multi-subnet network within Cisco Packet Tracer's Physical Mode. Unlike standard logical labs, this required manual hardware racking, power management, and out-of-band management via console cabling. The project demonstrates proficiency in subnetting design, physical layer connectivity, and network hardening.

## Environments and Technologies Used
* Cisco Packet Tracer (Physical Mode): Used for realistic hardware racking and cabling.
* Cisco IOS CLI: For device configuration (Routers & Switches).
* IPv4 Subnetting (VLSM): Designed a custom addressing scheme to optimize address space.
* SSH Protocol: Implemented for secure remote management.
* Network Security: Applied password encryption and console hardening.

## Objectives
1. Physical Hardware Deployment: Manually rack and power one Cisco 4321 router and two Cisco 2960 switches.
2. Layer 1 Connectivity: Establish data links using Copper Straight-Through cables and management links using Roll-Over (Console) cables.
3. Subnet Design: Partition a 192.168.10.0/24 network into two /25 subnets to support separate broadcast domains.
4. Network Hardening: Configure SSH, encrypted secrets, and banner warnings to secure the infrastructure.

## Addressing tabl (Custom Design)
<img width="574" height="389" alt="image" src="https://github.com/user-attachments/assets/014eeb3c-31d3-47e6-b929-681e477ec26f" />

## Configuration & Implementation Steps
**Step 1**: Physical Layer & Out-of-Band Management
Action: Racked devices in a standard telecommunications closet layout. Connected PC0 to the Router’s Console port using an RS-232 to RJ-45 Roll-Over cable.
Troubleshooting: Identified and corrected a terminal configuration mismatch (Parity settings) to establish a clean CLI session.

Step 2: Interface Configuration & Subnetting
Logic: Divided the class C block into two subnets.
Action: Enabled GigabitEthernet interfaces and assigned gateway addresses.
