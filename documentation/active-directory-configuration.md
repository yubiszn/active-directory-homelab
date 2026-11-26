# Active Directory Configuration

## Overview

This document outlines the deployment and configuration of Active Directory Domain Services (AD DS) within the homelab environment.

Windows Server 2025 was configured as the domain controller, providing centralized identity management, authentication, DNS integration, and directory services for the Windows 11 client.

The environment was designed to demonstrate Active Directory administration, organizational unit management, user provisioning, security group administration, and centralized account management.

## Environment

| **Component** | **Configuration** |
|---|---|
| Server Operating System | Windows Server 2025 Standard |
| Client Operating System | Windows 11 Pro |
| Domain Controller | `ADServer` |
| Client Computer | `ADClient` |
| Active Directory Domain | `adlab.local` |
| Server Fully Qualified Domain Name | `adserver.adlab.local` |
| DNS Server | `ADServer` |
| Virtualization Platform | Oracle VirtualBox |
| Virtual Network | `ADLab-Network` |

## Active Directory Domain Deployment

Installed Active Directory Domain Services on Windows Server 2025 and promoted the server to a domain controller.

Established the Active Directory forest and domain using the following configuration:

- Domain Name: `adlab.local`
- Domain Controller: `ADServer`
- Fully Qualified Domain Name: `adserver.adlab.local`
- DNS Integration: Enabled

Configured the Windows Server DNS environment to support domain name resolution and domain controller discovery.

The Active Directory domain provided centralized authentication and management of domain users, computers, and security policies.

## Organizational Unit Structure

Created Organizational Units (OUs) to organize domain accounts according to administrative responsibilities and departments.

The following organizational structure was established:

```text
adlab.local
├── Admin
├── IT
├── HR
├── Engineering
└── Accounting
```

| **Organizational Unit** | **Purpose** |
|---|---|
| Admin | Administrative account organization |
| IT | Information Technology department |
| HR | Human Resources department |
| Engineering | Engineering department |
| Accounting | Accounting department |

The organizational structure included:

- An administrative account for Ayub Ali.
- IT department accounts for Ayub Ali and Steve Rogers.
- A separate organizational unit for HR accounts.
- A separate organizational unit for Engineering accounts.
- A separate organizational unit for Accounting accounts.

Organized employee accounts within their respective departmental OUs and maintained a separate administrative OU.

This structure provided a foundation for organizing accounts and applying policies to specific groups of users or computers.

## User Account Management

Created domain user accounts within the Active Directory environment using Active Directory Users and Computers.

Used Marvel Cinematic Universe characters as sample employees to represent users across the different departments in the lab environment.

| **Employee** | **Username** | **Department** |
|---|---|---|
| Ayub Ali | `it.admin` | IT Administration |
| Steve Rogers | `it.user` | IT |
| Natasha Romanoff | `hr.user` | HR |
| Bruce Banner | `finance.user` | Accounting |
| Peter Parker | `engineering.user` | Engineering |

User account administration included:

- Creating individual domain user accounts.
- Assigning usernames and configuring account passwords.
- Configuring account password options.
- Organizing users into departmental OUs.
- Managing account membership in security groups.
- Centralizing account administration through Active Directory.

## Security Group Configuration

Created two domain security groups to organize domain access and administrative privileges.

| **Security Group** | **Membership / Purpose** |
|---|---|
| Domain Admin | Contains Ayub Ali's administrative account |
| Domain Users | Contains standard domain user accounts |

The `Domain Admin` group was used to distinguish the administrative account from standard domain users.

The `Domain Users` group provided the standard user membership structure for the environment.

Configured and reviewed group membership by:

- Adding Ayub Ali's administrative account to `Domain Admin`.
- Maintaining standard employee membership in `Domain Users`.
- Verifying group membership through the Member Of tab in Active Directory Users and Computers.
- Reviewing the configured security groups and their membership.

## Domain Client Integration

Configured the Windows 11 client to communicate with the domain controller through the `ADLab-Network` VirtualBox NAT Network.

Configured static IPv4 addressing on both the server and client to establish consistent network communication.

**Virtual Network Configuration**

| **Setting** | **Value** |
|---|---|
| Network Name | `ADLab-Network` |
| Network Type | NAT Network |
| Network Subnet | `10.0.2.0/24` |
| DHCP | Enabled |

**Domain Controller Network Configuration**

| **Setting** | **Value** |
|---|---|
| Computer Name | `ADServer` |
| IPv4 Address | `10.0.2.15` |
| Subnet Mask | `255.255.255.0` |
| Default Gateway | `10.0.2.2` |
| Preferred DNS | `127.0.0.1` |
| IP Assignment | Manual |
| DNS Assignment | Manual |

**Windows 11 Client Network Configuration**

| **Setting** | **Value** |
|---|---|
| Computer Name | `ADClient` |
| IPv4 Address | `10.0.2.3` |
| Subnet Mask | `255.255.255.0` |
| Default Gateway | `10.0.2.2` |
| Preferred DNS | `10.0.2.15` |
| IP Assignment | Manual |
| DNS Assignment | Manual |

Configured the client to use the domain controller's IP address as its preferred DNS server.

### Network and DNS Validation

Performed connectivity and DNS tests to verify communication between `ADClient` and `ADServer`.

Validation included:

- Reviewing the client network configuration using `ipconfig /all`.
- Pinging the domain controller at `10.0.2.15`.
- Confirming four successful replies with 0% packet loss.
- Querying `adlab.local` using `nslookup`.
- Retrieving domain DNS information.
- Querying the LDAP service record to verify domain controller discovery.

Executed the following command to query the LDAP SRV record:

```powershell
nslookup -type=SRV _ldap._tcp.dc._msdcs.adlab.local
```

**Verified LDAP Service Information**

| **Setting** | **Result** |
|---|---|
| Service | LDAP |
| Protocol | TCP |
| Port | 389 |
| Domain Controller | `adserver.adlab.local` |
| IP Address | `10.0.2.15` |

The DNS lookup initially returned timeout messages before successfully resolving the domain and LDAP service records.

These tests confirmed that the Windows 11 client could communicate with the domain controller, resolve the Active Directory domain, and locate the domain controller through LDAP service records.

## Active Directory Administration Tools

Used the following Windows administrative tools to manage and maintain the Active Directory environment:

- **Active Directory Users and Computers:** Managed domain users, organizational units, and security groups.
- **DNS Manager:** Managed DNS zones and domain records.
- **Group Policy Management:** Accessed the interface for creating and managing Group Policy Objects.
- **Active Directory Domains and Trusts:** Accessed domain and trust configuration.
- **PowerShell:** Supported account creation, directory administration, and automation.

## PowerShell Administration

Maintained PowerShell scripts in the project repository to support repeatable Active Directory administration.

The project included scripts for:

| **Script** | **Purpose** |
|---|---|
| `create-organizational-units.ps1` | Created the departmental and administrative organizational units. |
| `create-users.ps1` | Created user accounts using employee data. |
| `manage-user-accounts.ps1` | Managed existing domain user accounts. |
| `configure-security-groups.ps1` | Configured domain security groups and membership. |

Organized the scripts to demonstrate repeatable administration and reduce reliance on manual account management.

## Project Evidence

Captured screenshots documenting the Windows Server infrastructure, Active Directory configuration, security groups, and client connectivity.

Organized the screenshots into `screenshots/infrastructure/`, `screenshots/active-directory/`, and `screenshots/testing/`.

## Summary

Deployed an Active Directory environment using Windows Server 2025 and established `adlab.local` as the domain.

Configured the domain controller, DNS environment, organizational units, employee accounts, and security groups to demonstrate centralized identity and account management.

Integrated a Windows 11 client into the lab network and verified server-to-client connectivity, domain DNS resolution, and LDAP service discovery.

The completed configuration provided a foundation for demonstrating enterprise directory administration, user provisioning, security group management, network services, and Group Policy administration.
