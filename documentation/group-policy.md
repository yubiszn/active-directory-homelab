# Group Policy Configuration

## Overview

Configured Group Policy within the `adlab.local` domain to strengthen account security, standardize workstation settings, manage department resources, and restrict unauthorized access to selected system features.

Created and configured five Group Policy Objects (GPOs):

1. Password Policy
2. Drive Mapping
3. Desktop Wallpaper
4. Restrict Control Panel
5. Disable USB Storage

## 1. Password Policy

Configured password and account lockout settings to strengthen domain account security.

The policy included:

- Minimum password length
- Password complexity requirements
- Password history
- Maximum password age
- Account lockout threshold
- Account lockout duration
- Reset account lockout counter

**GPO location:** `adlab.local` → `Computers` OU.

## 2. Drive Mapping

Configured department-based drive mapping to provide users with access to shared resources associated with their department.

Created shared folders for the following departments:

- IT
- HR
- Engineering
- Accounting

Configured folder sharing and access permissions, then created a GPO to automatically map the appropriate department drive when users signed in.

**Target OUs:** IT, HR, Engineering, and Accounting.

## 3. Desktop Wallpaper

Configured a desktop wallpaper policy to standardize the appearance of domain-user workstations.

- Selected a wallpaper image for the lab.
- Configured the desktop wallpaper setting through Group Policy.
- Applied the policy to domain users' desktops.

**Target OUs:** IT, HR, Engineering, and Accounting.

## 4. Restrict Control Panel

Configured a user restriction policy to prevent standard domain users from accessing Control Panel and Windows PC Settings.

- Enabled the policy that prohibits access to Control Panel and PC Settings.
- Applied the restriction to standard domain users.

**Target OUs:** IT, HR, Engineering, and Accounting.

## 5. Disable USB Storage

Configured removable-storage restrictions to prevent USB storage devices from being used on domain workstations.

- Configured removable-storage access settings.
- Enabled the restriction on USB storage devices.

**Target computer:** `ADClient`.

## 6. Group Policy Verification

Used the following commands on the Windows 11 client to refresh Group Policy and review the applied policies.

```powershell
gpupdate /force
gpresult /r
```

- `gpupdate /force` refreshed Group Policy settings.
- `gpresult /r` displayed the applied Group Policy Objects and policy information.

Validated the policies through the following tests:

| GPO | Validation |
|---|---|
| Password Policy | Tested password requirements and account lockout behavior using a separate test account. |
| Drive Mapping | Checked that the appropriate department drive appeared in File Explorer. |
| Desktop Wallpaper | Verified that the configured wallpaper appeared on the client desktop. |
| Restrict Control Panel | Tested whether a standard domain user could access Control Panel and PC Settings. |
| Disable USB Storage | Tested whether USB storage access was restricted on the client workstation. |

## 7. Project Evidence

Captured screenshots of the Group Policy configurations, policy application, and client-side testing.

Configuration evidence was organized in `screenshots/group-policy/`, while client testing evidence was organized in `screenshots/testing/`.

## 8. Documentation

Documented the Group Policy configuration, policy settings, target locations, and validation procedures as part of the Active Directory homelab project.
