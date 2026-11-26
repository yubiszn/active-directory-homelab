# Network Configuration

## Overview

This document outlines the network configuration for the Active Directory homelab. The environment uses Oracle VirtualBox with a NAT Network to provide network connectivity between the Windows Server 2025 domain controller and Windows 11 client.

The network is configured to allow communication between virtual machines, DNS resolution, and Active Directory services.

## Virtual Network Configuration

| Setting | Configuration |
|---|---|
| Virtualization Platform | Oracle VirtualBox |
| Network Type | NAT Network |
| Network Name | ADLab-Network |
| Network Address | 10.0.2.0/24 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 10.0.2.2 |
| DHCP | Enabled |

Both virtual machines are connected to the same NAT Network.

## IP Address Configuration

Static IPv4 addresses are configured on both virtual machines to maintain consistent network communication and DNS resolution.

### Windows Server 2025 – Domain Controller

| Setting | Configuration |
|---|---|
| Computer Name | ADServer |
| IP Address | 10.0.2.15 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 10.0.2.2 |
| Preferred DNS Server | 127.0.0.1 |
| IP Assignment | Manual |
| DNS Assignment | Manual |

The domain controller uses its loopback address (127.0.0.1) for DNS because it hosts the DNS service for the Active Directory domain.

### Windows 11 – Client

| Setting | Configuration |
|---|---|
| Computer Name | ADClient |
| IP Address | 10.0.2.3 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 10.0.2.2 |
| Preferred DNS Server | 10.0.2.15 |
| IP Assignment | Manual |
| DNS Assignment | Manual |

The Windows 11 client uses the domain controller as its preferred DNS server to locate Active Directory services and resolve domain records.

## DNS Configuration

DNS is hosted on ADServer and is responsible for resolving the Active Directory domain and locating domain controller services.

**Active Directory Domain:**
- Domain: `adlab.local`
- DNS Server: `10.0.2.15`
- Domain Controller: `ADServer`

The client uses the domain controller's DNS service to locate Active Directory resources.

### DNS Resolution Validation

The following tests were performed from the Windows 11 client:

**1. Ping the domain controller**

```powershell
ping 10.0.2.15
```

Result:
- 4 packets sent
- 4 packets received
- 0% packet loss

**2. Resolve the Active Directory domain**

```powershell
nslookup adlab.local
```

The domain successfully resolved to the domain controller's IP address.

**3. Locate the domain controller using an LDAP service record**

```powershell
nslookup -type=SRV _ldap._tcp.dc._msdcs.adlab.local
```

The DNS query returned the following service information:

- Service: LDAP
- Port: 389
- Target: adserver.adlab.local
- IP Address: 10.0.2.15

These records allow domain clients to locate the domain controller for Active Directory authentication and directory services.

## Network Validation

Network connectivity and DNS resolution were tested between the Windows 11 client and Windows Server 2025 domain controller.

Validation included:
- IPv4 connectivity between virtual machines.
- DNS resolution of `adlab.local`.
- LDAP service record resolution.
- Confirmation that the client uses the domain controller for DNS.

## Summary

The network environment provides connectivity between the Windows Server 2025 domain controller and Windows 11 client.

Static IP addressing, centralized DNS resolution, and successful LDAP service discovery establish the network foundation required for Active Directory authentication and domain management.
