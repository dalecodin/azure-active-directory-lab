# Azure VM Setup

## Overview

This document describes the initial Azure infrastructure setup for an Active Directory lab environment. The objective of this was to setup the Azure resources, deploy the virtual machines, and prepare the Domain Controller for DNS and directory services. This establishes the foundation required for subsequent Active Directory configuration.

---

## Resource Group Configuration

An Azure Resource Group was created to group and manage all resources used with this lab. Using a single resource group provides centralized management, simplifies access control, and allows the environment to be easily modified or deleted as a unit.

---

## Virtual Network Configuration

An Azure Virtual Network (VNet) was created to enable private communication between virtual machines. The virtual network simulates an internal network and ensures that all directory, DNS, and authentication traffic remains isolated within Azure’s private networking.

All virtual machines deployed in this lab were placed within this VNet to ensure consistent and reliable connectivity.


![[Pasted image 20260114093410.png]]

---

## Domain Controller Virtual Machine Deployment

A Windows Server virtual machine was deployed to serve as the Domain Controller. During creation, the virtual machine was connected to the custom Virtual Network in the Networking tab to ensure correct subnet placement and private IP assignment.

![[Pasted image 20260114093537.png]]

This system will host Active Directory Domain Services and DNS, making it a dependency for all domain operations.

---

## Client Virtual Machine Deployment

A second virtual machine was deployed using Windows 10 Pro to act as a domain client. This system was connected to the same Virtual Network as the Domain Controller to allow direct communication over private IP addresses.

Placing both systems in the same VNet ensures the client can resolve domain resources and authenticate without relying on public networking.

---

## Domain Controller IP Address Configuration

Because the Domain Controller will function as the DNS server for the environment, its private IP address must remain consistent. To prevent DNS resolution and authentication issues, the Domain Controller’s private IP address was changed from dynamic to static.

This configuration was performed by accessing the virtual machine’s network interface settings in Azure and modifying the IP allocation method.

![[Pasted image 20260114094045.png]]

![[Pasted image 20260114094056.png]]

---

## Firewall Configuration

After configuring the static IP address, the Domain Controller was accessed via Remote Desktop. Windows Defender Firewall was temporarily disabled for the Domain, Private, and Public profiles.

![[Pasted image 20260114094421.png]]

This was done to prevent Active Directory and DNS traffic from being blocked during the lab setup. In real environments, firewall rules would be explicitly configured rather than disabling the firewall entirely.

---

## Client DNS Configuration

The client virtual machine was configured to use the Domain Controller as its DNS server. This was done by modifying the client’s network interface DNS settings, disabling inheritance from the Virtual Network, and specifying the Domain Controller’s private IP address.

![[Pasted image 20260114094502.png]]

This ensures all domain name resolution and authentication requests are directed to the Domain Controller.

---

## Outcome

At the completion of this phase:

- All Azure resources are contained within a single Resource Group
- Both virtual machines are connected to the same Virtual Network
- The Domain Controller has a static private IP address
- The client is configured to use the Domain Controller for DNS
- The environment is prepared for Active Directory Domain Services installation