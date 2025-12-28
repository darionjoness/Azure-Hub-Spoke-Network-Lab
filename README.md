# Azure Hub-and-Spoke Network with Linux NVA

## Overview
This project demonstrates a hub-and-spoke network topology in Azure using a Linux-based Network Virtual Appliance (NVA) to route traffic between isolated spoke VNets.

The lab focuses on core AZ-104 networking concepts including:
- Virtual Networks
- VNet Peering
- User Defined Routes (UDRs)
- Network Security Groups (NSGs)
- Linux IP forwarding

## Architecture
- Hub VNet contains a Linux NVA
- Two spoke VNets each contain a virtual machine
- All spoke-to-spoke traffic is routed through the NVA using UDRs

## Network Design

Component - CIDR 
Hub VNet - 10.0.0.0/16
NVA Subnet - 10.0.1.0/24 
Spoke 1 VNet - 10.1.0.0/16 
Spoke 2 VNet - 10.2.0.0/16 

## Key Configuration Steps
1. Created hub and spoke VNets
2. Peered spoke VNets to hub VNet
3. Deployed Linux NVA in hub and enabled IP forwarding
4. Created UDRs on spoke subnets pointing traffic to NVA
5. Configured NSGs to allow ICMP and SSH
6. Verified private IP connectivity between spokes

## Validation
- Successfully pinged Spoke 2 VM from Spoke 1 VM using private IPs
- Verified routing paths using UDRs and Linux routing tables

Screenshots are available in the /screenshots directory.

## Lessons Learned
- Azure does not automatically route traffic between peered VNets
- UDRs are required to force traffic through an NVA
- Linux IP forwarding must be enabled for routing to function

## Skills Demonstrated
- Azure Networking (AZ-104)
- Linux Networking
- Routing and Traffic Control
