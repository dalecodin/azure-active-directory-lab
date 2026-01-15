# Active Directory Setup

## Overview

This section documents the installation and configuration of **Active Directory Domain Services (AD DS)** on the Windows Server virtual machine designated as the Domain Controller. The objective was to install the required server roles, promote the server to a Domain Controller, and establish a new Active Directory forest and domain.

---

## AD DS Role Installation

While connected to the Domain Controller, **Server Manager** was used to configure the local server. From Server Manager, the **Add Roles and Features** wizard was launched to install the required server roles.

![[Pasted image 20260114113945.png]]

During the role selection phase, **Active Directory Domain Services** was selected. All required dependencies were added as part of the installation process. This role provides the core directory, authentication, and authorization services required for a Windows domain environment.

![[Pasted image 20260114113953.png]]

The installation was completed successfully before proceeding to domain configuration.

---

## Domain Controller Promotion

After the AD DS role installation, Server Manager was used to promote the server to a Domain Controller. The post-deployment notification in Server Manager was selected to begin the promotion.

![[Pasted image 20260114114022.png]]

During deployment configuration, the option to **add a new forest** was selected. This was chosen because this environment represents a new domain with no existing Active Directory infrastructure. A root domain name was specified (`mydomain.com`) to establish the domain namespace.

![[Pasted image 20260114114030.png]]

---

## DNS Configuration Options

During the DNS configuration stage, the option to **create DNS delegation** was left unchecked. DNS delegation is only required when integrating with an existing DNS infrastructure, which is not present in this lab environment. Because the Domain Controller is hosting DNS for a new forest, delegation is not needed.

![[Pasted image 20260114114055.png]]

---

## Installation Completion

The Active Directory Domain Services configuration wizard was completed using default settings where appropriate. Once configuration finished, the server automatically restarted to apply changes and bring Active Directory services online.

---

## Post-Installation Configuration

At this stage, a domain administrator user account was created within Active Directory.

![[Pasted image 20260114114122.png]]

Creating a dedicated administrative account allows domain management tasks to be performed without relying on default or built-in accounts. This aligns with administrative best practices.
