
# Architecture Overview

## Purpose

This document describes the architecture of the Active Directory lab environment deployed in Microsoft Azure. It outlines how resources are structured and how the services communicate within the network.

---

## VM Architecture

The lab environment consists of two virtual machines deployed within a single Azure Virtual Network:

- **Domain Controller (dc-1)**  
  - Windows Server  
  - Hosts Active Directory Domain Services (AD DS)  
  - Hosts DNS services  

- **Client Virtual Machine (client-1)**  
  - Windows 10 Pro  
  - Domain-joined workstation  

Both systems communicate exclusively over private IP addresses within the same virtual network.

---

## Network Architecture
 
- **Virtual Network:** ad-vnet  
- **Subnet:** Single subnet used for all virtual machines  

The Virtual Network provides isolated, internal connectivity similar to an on-prem corporate network. No internal directory or authentication traffic traverses the public internet.

---

## DNS and Authentication Flow

1. The client virtual machine uses the Domain Controller as its primary DNS server.
2. DNS queries for domain resources are resolved by the Domain Controller.
3. Authentication requests (Kerberos, LDAP) are processed by Active Directory on the Domain Controller.
4. Group Policy and domain services are delivered over the same private network.

A static private IP address is assigned to the Domain Controller to ensure DNS reliability and consistent client configuration.

---

## Security

- All virtual machines are isolated within a private Azure Virtual Network.
- Public access is used only for administrative access (e.g., RDP).
- Windows Defender Firewall was temporarily disabled on the Domain Controller for lab setup purposes.
- In production environments, firewall rules would be explicitly configured instead.

---

## Architecture Diagram

![[Pasted image 20260114174013.png]]

