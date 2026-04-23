# Ticket ID: HD-AD-007

## User Information
- Name: Mark Santos
- Department: Finance

---

## Issue Summary
User is unable to establish a Remote Desktop (RDP) connection to a domain-joined workstation.

---

## Environment
- Domain: Equinox.local
- Domain Controller: DC01
- Client: WS01

---

## Troubleshooting Steps
- Verified network connectivity between client and target machine
- Checked Remote Desktop settings on target machine
- Reviewed Windows Firewall configuration
- Attempted RDP connection using hostname and IP address

---

## Resolution
- Enabled Remote Desktop on target machine
- Allowed RDP through Windows Firewall
- Verified user is part of Remote Desktop Users group

---

## Root Cause
Remote Desktop was disabled on the target machine and firewall rules were not allowing RDP connections.

---

## Status
Resolved

---

## Documentation
- [Active Directory – RDP Connection Failure](../active-directory-lab/documentation/ad-rdp-connection-failure.md)
