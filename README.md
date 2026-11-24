# Active Directory & Enterprise IAM Lab

**Windows Server 2025 | Active Directory | PowerShell | IAM | Group Policy | VirtualBox**

## Project Overview

This project involves building and securing a simulated enterprise Windows environment using Windows Server 2025 and Active Directory Domain Services (AD DS).

The lab is designed to demonstrate practical skills in centralized identity management, user and group administration, domain authentication, access control, security policy enforcement, and PowerShell automation.

The environment simulates an organization with multiple business departments and more than 1,000 fictional employee accounts.

## Technologies & Tools

- **Operating Systems:** Windows Server 2025, Windows 11
- **Virtualization:** Oracle VirtualBox
- **Directory Services:** Active Directory Domain Services (AD DS)
- **Networking:** DNS, Virtual Networking, Static IP Configuration
- **Automation:** PowerShell, CSV
- **Administration:** Active Directory Users and Computers (ADUC), DNS Manager, Group Policy Management Console (GPMC)
- **Security:** Identity and Access Management (IAM), Kerberos, Group Policy, NTFS Permissions, Role-Based Access Control (RBAC)

## Project Components

### 1. Enterprise Infrastructure

- Deploy and configure a Windows Server 2025 domain controller.
- Establish the `adlab.local` Active Directory domain.
- Configure DNS and isolated virtual networking.
- Assign static IP addresses and configure domain name resolution.
- Integrate a Windows 11 client into the domain.

### 2. Identity & Access Management

- Design departmental Organizational Units (OUs).
- Automate provisioning of 1,000+ fictional employee accounts using PowerShell.
- Organize users into departmental security groups.
- Implement role-based access control and least-privilege principles.
- Demonstrate user account administration and lifecycle management.

### 3. Security Policies & Access Control

- Create and configure Group Policy Objects (GPOs).
- Implement password and account lockout policies.
- Apply workstation security restrictions and selected software controls.
- Configure NTFS permissions for departmental resources.
- Validate authentication, authorization, and departmental access restrictions.

### 4. Security Analysis

- Develop an enterprise asset inventory and classification framework.
- Classify assets according to sensitivity and business criticality.
- Identify Active Directory and identity-related security threats.
- Evaluate compromised account and excessive privilege scenarios.
- Document potential attack paths, business impact, and recommended mitigations.

### 5. Testing & Validation

- Verify network connectivity and DNS resolution.
- Validate domain authentication from the Windows 11 client.
- Confirm Group Policy application and enforcement.
- Test departmental security group memberships and resource permissions.
- Evaluate authorized and unauthorized access scenarios.
- Document test results, identified issues, and corrective actions.

## Repository Structure

```text
active-directory-homelab/
│
├── README.md
│
├── documentation/
│   ├── project-overview.md
│   ├── infrastructure-blueprint.md
│   ├── network-configuration.md
│   ├── active-directory-configuration.md
│   ├── identity-and-access-management.md
│   ├── group-policy.md
│   └── testing-and-validation.md
│
├── scripts/
│   ├── create-organizational-units.ps1
│   ├── create-users.ps1
│   ├── manage-user-accounts.ps1
│   └── configure-security-groups.ps1
│
├── data/
│   └── sample-employees.csv
│
├── screenshots/
│   ├── infrastructure/
│   ├── active-directory/
│   ├── group-policy/
│   └── testing/
│
└── reports/
    ├── asset-inventory.md
    ├── asset-classification.md
    ├── threat-assessment.md
    └── risk-mitigation.md
```

## Current Progress

**Status: In Progress**

**Completed:**
- Deployed Windows Server 2025 Standard Evaluation virtual machine.
- Installed Active Directory Domain Services.
- Promoted the server to a domain controller.
- Established the `adlab.local` domain.
- Created and organized the GitHub project repository.

**Upcoming:**
- Configure isolated VirtualBox networking and static IP addressing.
- Deploy and domain-join the Windows 11 client.
- Build the departmental Active Directory structure.
- Implement PowerShell-based identity provisioning.
- Configure security groups, access controls, and Group Policy.
- Complete asset classification, threat modeling, and security validation.

## Project Outcomes

Upon completion, this project will demonstrate:

- Enterprise-style Active Directory infrastructure deployment and administration.
- Automated identity provisioning and account management at scale.
- Centralized authentication and authorization.
- Departmental access controls and least-privilege implementation.
- Group Policy-based security enforcement.
- Practical identity threat assessment and security validation.

## Disclaimer

This is an isolated personal homelab developed for educational and professional portfolio purposes. It simulates selected enterprise identity and infrastructure security practices and does not represent a production enterprise deployment. All employee accounts and organizational data are fictional.
