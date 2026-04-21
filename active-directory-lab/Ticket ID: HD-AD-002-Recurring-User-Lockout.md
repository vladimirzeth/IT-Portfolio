# Ticket ID: HD-AD-002

## User Information
- Name: Camille Spencer
- Department: IT
- Date Reported: April 20, 2026

---

## Issue Summary
User account repeatedly locks out shortly after being unlocked.  
User reports intermittent access to domain resources despite using correct credentials.

---

## Environment
- Domain: Equinox.local  
- Directory Service: Active Directory Domain Services (AD DS)  
- Client OS: Windows 10 (Domain-joined workstation)  
- Tools Used:
  - Active Directory Users and Computers (ADUC)
  - Event Viewer (Domain Controller)

---

## Troubleshooting Steps
- Verified account lockout status in ADUC  
- Reviewed Security logs on Domain Controller  
- Identified multiple lockout events (Event ID 4740)  
- Observed repeated failed logon attempts (Event ID 4625)  
- Simulated stale credential usage on client machine  

---

## Resolution
- Reset user password in Active Directory  
- Cleared cached/stored credentials on client machine  
- Re-authenticated user with updated credentials  
- Monitored account for further lockout events  

---

## Root Cause
Recurring lockouts were caused by repeated authentication attempts using outdated credentials on the client machine, simulating a secondary device or service.

---

## Status
Resolved

---

## Documentation

- [Active Directory – Recurring Account Lockout Troubleshooting](../active-directory-lab/documentation/ad-recurring-lockout.md)
