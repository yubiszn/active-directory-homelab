
# Infrastructure Blueprint
## Active Directory & Enterprise Identity Security Lab

## 1. Infrastructure Overview

This document outlines the architecture of a simulated enterprise Windows environment built using Oracle VirtualBox, Windows Server 2025, and Windows 11.

The infrastructure is designed to provide a controlled environment for implementing and testing enterprise directory services, centralized authentication, identity management, network services, and security controls.

The environment consists of a Windows Server 2025 domain controller and a Windows 11 client workstation operating within a virtualized lab environment.

## 2. Virtualization Environment

| Component | Configuration |
|---|---|
| Virtualization Platform | Oracle VirtualBox 7.2.22 |
| Host Operating System | Windows 11 |
| Server Operating System | Windows Server 2025 Standard Evaluation |
| Client Operating System | Windows 11 |
| Virtualization Type | Hardware-assisted virtualization |

## 3. Virtual Machine Architecture

The lab consists of two primary virtual machines.

### 3.1 Domain Controller — ADServer

| Component | Configuration |
|---|---|
| Hostname | ADServer |
| Operating System | Windows Server 2025 Standard Evaluation |
| Primary Role | Active Directory Domain Controller |
| Directory Services | Active Directory Domain Services (AD DS) |
| Domain | adlab.local |
| Additional Services | DNS |

**Responsibilities:**
- Provide centralized directory services.
- Authenticate domain users and computers.
- Maintain Active Directory objects and directory information.
- Provide DNS services for domain name resolution.
- Centrally manage users, groups, and security policies.

### 3.2 Client Workstation — ADClient

| Component | Planned Configuration |
|---|---|
| Hostname | ADClient |
| Operating System | Windows 11 |
| Primary Role | Domain-joined client workstation |
| Domain | adlab.local |

**Responsibilities:**
- Connect to the Active Directory domain.
- Authenticate using domain accounts.
- Receive centralized Group Policy configurations.
- Access authorized network resources.
- Provide a workstation for testing authentication and access controls.

## 4. Active Directory Architecture

The Active Directory environment uses the following domain:

| Component | Configuration |
|---|---|
| Domain Name | adlab.local |
| Domain Controller | ADServer |
| Directory Service | Active Directory Domain Services |
| Authentication Protocol | Kerberos |
| Name Resolution | DNS |

The domain will provide centralized identity and access management for the simulated organization.

Departmental Organizational Units, security groups, user accounts, and access controls will be implemented during the identity and access management phase.

## 5. Network Architecture

The virtual machines will operate within a network configuration designed to support communication between the domain controller and client workstation.

| Component | Planned Configuration |
|---|---|
| Virtual Network | To be finalized during network implementation |
| Domain Controller | ADServer |
| Client Workstation | ADClient |
| Network Addressing | Static IPv4 |
| Name Resolution | DNS provided by ADServer |

### 5.1 IP Addressing

The final IP addressing scheme will be documented after the network configuration is implemented and verified.

| Setting | ADServer | ADClient |
|---|---|---|
| IPv4 Address | Pending verification | Pending configuration |
| Subnet Mask | Pending verification | Pending configuration |
| Default Gateway | Pending verification | Pending configuration |
| Preferred DNS | 127.0.0.1 (planned) | ADServer IP (planned) |

### 5.2 Network Configuration Considerations

- Configure consistent network connectivity between both virtual machines.
- Assign static IPv4 addresses where appropriate.
- Configure the domain controller as the DNS server for domain clients.
- Verify domain name resolution and connectivity.
- Ensure the client can locate and communicate with the domain controller.

## 6. Infrastructure Architecture Diagram

```text
             VirtualBox Environment
                      |
          +-----------+-----------+
          |                       |
     ADServer                 ADClient
 Windows Server 2025          Windows 11
          |                       |
       AD DS                     Domain
        DNS                    Workstation
          |                       |
          +------ adlab.local ----+
```

## 7. Implementation Status

### Completed

- Deployed Windows Server 2025 Standard Evaluation virtual machine.
- Installed Active Directory Domain Services.
- Promoted ADServer to a domain controller.
- Established the adlab.local domain.
- Created the GitHub project repository.

### In Progress

- Infrastructure architecture documentation.
- Static IP and DNS configuration.
- VirtualBox network configuration.
- Windows 11 client deployment and domain integration.

### Planned

- Departmental Organizational Unit design.
- Automated provisioning of 1,000+ fictional employee accounts using PowerShell.
- Security group configuration and role-based access control.
- Group Policy implementation and security hardening.
- NTFS permissions and departmental resource access controls.
- Asset classification and threat modeling.
- Infrastructure testing and validation.

## 8. Scope and Limitations

This infrastructure is an isolated educational homelab designed to simulate selected enterprise Windows infrastructure and identity security practices.

All employee accounts and organizational information will be fictional. The environment is intended for technical learning, experimentation, and professional portfolio demonstration rather than production deployment.
