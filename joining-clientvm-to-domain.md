# Client Virtual Machine Domain Join

## Overview

This section documents the process of joining the Windows client virtual machine to the Active Directory domain. The objective was to connect the client system into the domain so it can authenticate users and use directory and DNS services provided by the Domain Controller.

---

## Domain Join Process

The client system settings were accessed, and the **advanced system configuration** was opened through the *Rename this PC (advanced)* option. From the Computer Name settings, the option to change the system’s domain membership was selected.

The Active Directory domain name (`mydomain.com`) was entered to start the domain join process.

<img width="1593" height="965" alt="Pasted image 20260114151415" src="https://github.com/user-attachments/assets/62b0505d-500b-4b5b-86d4-8b2cf4d2eb78" />


---

## Authentication

During the domain join process, log-in of a domain account with administrative privileges were required. A domain administrator account was provided to authorize the client’s addition to the domain.

<img width="456" height="300" alt="Pasted image 20260114151503" src="https://github.com/user-attachments/assets/3f547083-8565-4471-b13b-299699f48670" />


---

## System Restart and Completion

After successful authentication, the client system prompted for a restart. The restart was required to apply domain membership changes and complete the join process.

Once restarted, the client became a member of the Active Directory domain and was able to authenticate against the Domain Controller.

---

## Outcome

At the completion of this phase:

- The client virtual machine was successfully joined to the domain
- Domain authentication was enabled on the client
- The system appeared in Active Directory Users and Computers
- The Active Directory environment was fully functional


