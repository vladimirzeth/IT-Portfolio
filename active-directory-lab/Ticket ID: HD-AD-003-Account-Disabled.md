# Ticket ID: HD-AD-003

## User Information
- Name: Anastasia Solyanik
- Department: IT
- Date Reported: April 20, 2026

---

## Issue Summary
User reported being unable to log in to the domain.  
Error indicated that the account was disabled in Active Directory.

---

## Environment
- Domain: Equinox.local
- Directory Service: Active Directory Domain Services (AD DS)
- OS: Windows 10 / Domain-joined workstation
- Tool Used: Active Directory Users and Computers (ADUC)

---

## Troubleshooting Steps
- Checked user account status in ADUC  
- Verified account is in **Disabled state**  
- Confirmed no password or lockout issues present  

---

## Resolution
- Navigated to Active Directory Users and Computers  
- Located user account: Anastasia Solyanik  
- Right-clicked account → Selected **Enable Account**  
- Confirmed account status changed to Active  

---

## Root Cause
Account was manually disabled by administrator (likely for administrative or security purposes).

---

## Status
Resolved

---

## Documentation

- [Active Directory – Account Disabled Troubleshooting](../active-directory-lab/documentation/ad-account-disabled.md)
