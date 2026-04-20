# Ticket ID: HD-AD-004

## User Information
- Name: Pierre Price
- Department: IT
- Date Reported: April 20, 2026

---

## Issue Summary
User reported being unable to log in to the domain due to account lockout.  
System displayed an error indicating that the account has been locked due to multiple failed login attempts.

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
- Verified user account status in ADUC  
- Checked for account lockout state  
- Reviewed Domain Controller Security logs  
- Confirmed multiple failed authentication attempts  

---

## Resolution
- Located user account: **Pierre Price** in Active Directory  
- Confirmed account was in a locked state  
- Right-clicked account → Selected **Unlock Account**  
- Instructed user to retry login with correct credentials  
- Verified successful authentication after unlock  

---

## Root Cause
Account was locked due to multiple failed login attempts exceeding the domain lockout threshold policy.

---

## Status
Resolved

---

## Documentation

- [Active Directory – Account Locked Out Troubleshooting](../active-directory-lab/documentation/ad-account-locked-out.md)
