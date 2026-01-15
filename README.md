# Azure Active Directory Lab

This repository documents the deployment of a basic **Active Directory Domain Services (AD DS)** environment in **Microsoft Azure**. The lab demonstrates how DNS, and client authentication components are configured inside a private virtual network.

The project is broken into phases, each documented in its own file.

---

## Lab Overview

The environment consists of:

- One **Windows Server** virtual machine acting as a Domain Controller
- One **Windows 10 Pro** virtual machine acting as a domain client
- A shared **Azure Virtual Network** for private communication
- Active Directory Domain Services with DNS

All systems communicate using private IP addresses within the same Azure VNet.

---

## Architecture

An overview of the environment, including DNS and authentication flow, is documented here:

- [`architecture-overview`](https://github.com/dalecodin/azure-active-directory-lab/blob/main/architecture-overview.md) 

This file explains how the Domain Controller and client interact and includes a network diagram.

---

## Lab Phases

### 1. Azure Infrastructure & VM Setup
- [`azure-vm-setup`](https://github.com/dalecodin/azure-active-directory-lab/blob/main/azure-vm-setup.md)

Covers:
- Resource Group creation
- Virtual Network configuration
- Windows Server and Windows 10 VM deployment
- Static private IP configuration for the Domain Controller
- DNS configuration and firewall considerations

---

### 2. Active Directory Setup
- [`active-directory-setup`](https://github.com/dalecodin/azure-active-directory-lab/blob/main/active-directory-setup.md)

Covers:
- Installation of Active Directory Domain Services
- Promotion of the server to a Domain Controller
- Creation of a new forest and root domain
- DNS configuration decisions
- Creation of a domain administrator account

---

### 3. Client Domain Join
- [`joining-clientvm-to-domain`](https://github.com/dalecodin/azure-active-directory-lab/blob/main/joining-clientvm-to-domain.md)

Covers:
- Joining the Windows 10 client to the domain
- Domain authentication using administrative credentials
- Verification of successful domain membership

---

## Technologies Used

- Microsoft Azure
- Azure Virtual Networks
- Windows Server
- Windows 10 Pro
- Active Directory Domain Services (AD DS)
- DNS
- Remote Desktop (RDP)

---

## Purpose

This lab was built to demonstrate practical understanding of:

- Azure virtual networking and VM deployment
- Active Directory and DNS dependencies
- Domain Controller configuration
- Client authentication and domain membership
- Basic enterprise identity architecture

---
