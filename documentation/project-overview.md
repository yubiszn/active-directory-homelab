# Project Overview
## Active Directory & Enterprise Identity Security Lab

## 1. Project Purpose

The purpose of this project is to design, deploy, administer, and secure a simulated enterprise Windows environment using Windows Server 2025 and Active Directory Domain Services (AD DS).

The lab replicates foundational enterprise IT infrastructure and identity management practices within an isolated virtual environment. It provides hands-on experience implementing centralized authentication, directory services, user administration, access controls, security policies, and administrative automation.

The environment will simulate an organization with multiple business departments and more than 1,000 fictional employee accounts.

## 2. Project Objectives

The primary objectives are to:

- Deploy and configure a Windows Server 2025 domain controller.
- Establish a centralized Active Directory domain and DNS infrastructure.
- Configure virtual networking and integrate a Windows 11 client.
- Design a departmental Organizational Unit (OU) structure.
- Automate large-scale user provisioning and account administration using PowerShell.
- Implement departmental security groups and role-based access controls.
- Apply centralized security policies through Group Policy.
- Configure and validate NTFS permissions for departmental resources.
- Evaluate identity-related security risks and document appropriate mitigations.
- Test and verify infrastructure functionality and security controls.

## 3. Technical Environment

The lab uses Oracle VirtualBox to host virtual machines on a Windows-based physical computer.

| Component | Planned Configuration |
|---|---|
| Virtualization Platform | Oracle VirtualBox 7.2 |
| Server Operating System | Windows Server 2025 Standard Evaluation |
| Client Operating System | Windows 11 |
| Domain Controller | ADServer |
| Active Directory Domain | adlab.local |
| Directory Services | Active Directory Domain Services |
| Name Resolution | DNS |
| Automation | PowerShell |
| Administrative Tools | ADUC, DNS Manager, GPMC |
| Network Architecture | Isolated VirtualBox Internal Network |

## 4. Planned Directory Architecture

The Active Directory environment will represent a fictional enterprise with the following departmental structure:

- IT
- Human Resources
- Finance
- Engineering

Each department will have its own Organizational Unit and associated security groups. User accounts will be organized according to departmental assignments and access requirements.

The directory structure will support centralized identity administration, group-based permissions, and delegated administrative organization.

## 5. Planned Infrastructure Architecture

The environment will consist of two primary virtual machines:

**ADServer**
- Runs Windows Server 2025.
- Functions as the Active Directory domain controller.
- Hosts Active Directory Domain Services and DNS.
- Provides centralized domain authentication and directory administration.
- Manages domain identities, groups, and security policies.

**ADClient**
- Runs Windows 11.
- Connects to the isolated lab network.
- Joins the `adlab.local` domain.
- Provides a client environment for authentication, policy application, and access-control testing.

The two virtual machines will communicate through a dedicated VirtualBox Internal Network.

## 6. Implementation Phases

### Phase 1 — Infrastructure Deployment
- Deploy Windows Server 2025 and Windows 11 virtual machines.
- Configure VirtualBox networking.
- Assign static IP addresses and DNS settings.
- Install and configure Active Directory Domain Services.
- Promote the server to a domain controller.
- Establish the `adlab.local` domain.
- Join the Windows 11 client to the domain.

### Phase 2 — Active Directory Administration
- Design departmental Organizational Units.
- Create departmental security groups.
- Develop PowerShell scripts for bulk user provisioning.
- Generate more than 1,000 fictional employee accounts.
- Organize accounts according to departmental structure.
- Implement account administration and lifecycle management.

### Phase 3 — Identity Security & Access Control
- Apply role-based access control.
- Configure least-privilege permissions.
- Implement departmental resource access restrictions.
- Configure NTFS permissions.
- Validate authorized and unauthorized access scenarios.

### Phase 4 — Group Policy & Security Hardening
- Create and configure Group Policy Objects.
- Implement password and account lockout policies.
- Apply workstation security restrictions.
- Configure selected software restrictions.
- Verify policy application on the Windows 11 client.

### Phase 5 — Asset Classification & Threat Modeling
- Develop an enterprise asset inventory.
- Classify assets by sensitivity and business criticality.
- Identify threats targeting Active Directory and identity infrastructure.
- Evaluate compromised account and excessive privilege scenarios.
- Document potential attack paths, business impact, and mitigations.

### Phase 6 — Testing & Validation
- Verify network connectivity and DNS resolution.
- Validate domain authentication.
- Test user and group permissions.
- Confirm Group Policy enforcement.
- Evaluate access-control effectiveness.
- Document test results and corrective actions.

## 7. Documentation & Evidence

The repository will maintain technical documentation and supporting evidence throughout implementation.

| Directory | Purpose |
|---|---|
| `documentation/` | Technical architecture, configuration, and implementation records |
| `scripts/` | PowerShell automation and administration scripts |
| `data/` | Fictional employee data used for provisioning |
| `screenshots/` | Visual evidence of configuration and testing |
| `reports/` | Asset classification, threat assessments, and security analysis |

Each major implementation milestone will be documented with its configuration details, relevant screenshots, and validation results.

## 8. Project Scope & Limitations

This project is a personal educational homelab designed to simulate selected enterprise identity and infrastructure security practices.

The environment is isolated using VirtualBox Internal Networking. It does not represent a production enterprise deployment, and all employee accounts and organizational data are fictional.

The project focuses on foundational Windows enterprise infrastructure, Active Directory administration, identity security, access control, automation, and security analysis.

## 9. Project Status

**Status:** In Progress

The initial Windows Server 2025 environment has been deployed, Active Directory Domain Services has been installed, and the server has been promoted to a domain controller for the `adlab.local` domain.

Further network configuration, Windows 11 client integration, identity administration, security controls, and validation will be documented as implementation progresses.
