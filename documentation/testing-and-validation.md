# Testing and Validation

## Overview

Performed network connectivity and DNS validation to verify communication between the Windows 11 client and the Windows Server 2025 domain controller.

Testing confirmed successful client-to-server communication, domain name resolution, and LDAP service record discovery.

## Network Connectivity Testing

Tested connectivity between `ADClient` and `ADServer` using the Windows `ping` command.

**Command:**

```powershell
ping 10.0.2.15
```

**Results:**

| Test | Result |
|---|---|
| Destination | `ADServer` |
| IP Address | `10.0.2.15` |
| Packets Sent | 4 |
| Packets Received | 4 |
| Packet Loss | 0% |

Confirmed successful communication between the Windows 11 client and the domain controller.

## DNS Resolution Testing

Used `nslookup` to verify that the client could resolve the Active Directory domain.

**Command:**

```powershell
nslookup adlab.local
```

Verified that the domain resolved to the domain controller's IP address, `10.0.2.15`.

The initial DNS queries returned timeout messages before successfully resolving the domain.

## LDAP Service Record Testing

Queried the Active Directory LDAP service record to verify domain controller discovery through DNS.

**Command:**

```powershell
nslookup -type=SRV _ldap._tcp.dc._msdcs.adlab.local
```

**Results:**

| Setting | Result |
|---|---|
| Service | LDAP |
| Protocol | TCP |
| Port | 389 |
| Domain Controller | `adserver.adlab.local` |
| IP Address | `10.0.2.15` |

Successfully retrieved the LDAP service record and resolved the domain controller address.

## Group Policy Testing

Group Policy validation was included in the lab plan to verify policy application and workstation behavior.

Testing covered:

- Password requirements and account lockout behavior.
- Department drive mapping.
- Desktop wallpaper enforcement.
- Control Panel and PC Settings restrictions.
- USB storage restrictions.

Documented the final test results after configuring and applying each GPO.

## Project Evidence

Captured screenshots documenting client network configuration, connectivity, and DNS resolution.

Organized the testing evidence in `screenshots/testing/`.
