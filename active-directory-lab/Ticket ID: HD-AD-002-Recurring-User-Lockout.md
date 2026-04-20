# Ticket ID: HD-AD-002

## User Information
- Name: Camille Spencer
- Department: IT
- Date Reported: April 20, 2026

---

## Issue Summary
User account is repeatedly getting locked out shortly after being unlocked.  
User is unable to maintain stable access to the domain despite correct password usage.

---

## Environment
- Domain: Equinox.local  
- Directory Service: Active Directory Domain Services (AD DS)  
- Client OS: Windows 10 (Domain-joined workstation)  
- Devices Involved:
  - Laptop (primary workstation)
  - Mobile device (email sync enabled)

---

## Troubleshooting Steps
- Verified account lockout status in Active Directory Users and Computers (ADUC)  
- Reviewed Event Viewer logs on Domain Controller  
- Identified repeated account lockout events (Event ID 4740)  
- Checked for multiple authentication sources using the same account  
- Reviewed stored credentials on client machine  

---

## Resolution
- Identified outdated cached credentials on secondary device (mobile/email client)  
- Cleared saved credentials from Credential Manager on workstation  
- Updated password on all connected devices  
- Forced sign-out from all active sessions  
- Monitored account after unlock for reoccurrence  

---

## Root Cause
Recurring lockouts were caused by **outdated stored credentials on a secondary device**, which continuously attempted authentication using an old password, triggering the domain lockout policy.

---

## Status
Resolved
