# Active Directory Configuration

## Overview

This document outlines the deployment and configuration of Active Directory Domain Services (AD DS) within the homelab environment.

Windows Server 2025 is configured as the domain controller, providing centralized identity management, authentication, DNS integration, and directory services for the Windows 11 client.

The environment is designed to demonstrate Active Directory administration, organizational unit management, user provisioning, and security group administration.

## Environment

| Component | Configuration |
|---|---|
| Server Operating System | Windows Server 2025 Standard |
| Client Operating System | Windows 11 |
| Domain Controller | ADServer |
| Client Computer | ADClient |
| Active Directory Domain | adlab.local |
| DNS Server | ADServer |
| Virtualization Platform | Oracle VirtualBox |

## Active Directory Domain Deployment

Active Directory Domain Services was installed on Windows Server 2025, and the server was promoted to a domain controller.

The domain was established using the following configuration:

- Domain Name: `adlab.local`
- Domain Controller: `ADServer`
- DNS Integration: Enabled

The Active Directory domain provides centralized authentication and management of domain users, computers, and security policies.

## Organizational Unit Structure

Organizational Units (OUs) were created to organize domain accounts according to administrative responsibilities and departments.

The following organizational structure was established:

| Organizational Unit | Purpose |
|---|---|
| Admin | Administrative account organization |
| IT | Information Technology department |
| HR | Human Resources department |
| Engineering | Engineering department |
| Accounting | Accounting department |

The organizational structure includes:
- An administrative account for Ayub Ali.
- IT department accounts for Ayub Ali and Steve.
- Separate organizational units for HR, Engineering, and Accounting.

This structure provides a foundation for organizing accounts and applying policies to specific groups of users or computers.

## User Account Management

User accounts were created within their respective organizational units using Active Directory Users and Computers.

The accounts represent employees across the different departments in the lab environment.

User account administration includes:
- Creating domain user accounts.
- Organizing users into departmental OUs.
- Managing account membership in security groups.
- Centralizing account administration through Active Directory.

## Security Group Configuration

Two security groups were created to organize domain access and administrative privileges.

| Security Group | Membership / Purpose |
|---|---|
| Domain Admin | Contains Ayub Ali's administrative account |
| Domain Users | Contains the domain user accounts |

The Domain Admin group is used to distinguish the administrative account from standard domain users.

The Domain Users group provides the standard user membership structure for the environment.

## Domain Client Integration

The Windows 11 client was configured to communicate with the domain controller through the `ADLab-Network` VirtualBox NAT Network.

The client uses the domain controller's IP address (10.0.2.15) as its preferred DNS server.

Network and DNS validation confirmed that the client could:
- Communicate with the domain controller.
- Resolve the `adlab.local` domain.
- Locate the domain controller through LDAP service records.

## Active Directory Administration Tools

The following Windows administrative tools are used to manage the environment:

- **Active Directory Users and Computers:** Manage domain users, organizational units, and security groups.
- **DNS Manager:** Manage DNS zones and domain records.
- **Group Policy Management:** Create and manage Group Policy Objects.
- **Active Directory Domains and Trusts:** Manage domain and trust configuration.
- **PowerShell:** Automate account creation and directory administration.

## PowerShell Administration

PowerShell scripts are maintained in the project repository to support Active Directory administration.

The project includes scripts for:

- Creating organizational units.
- Creating user accounts from employee data.
- Managing user accounts.
- Configuring security groups.

These scripts demonstrate repeatable administration and reduce the need for manual account management.

## Summary

The Active Directory environment establishes centralized identity and account management through Windows Server 2025.

The domain, departmental organizational units, user accounts, security groups, and Windows 11 client provide a foundation for demonstrating enterprise directory administration and access management.
