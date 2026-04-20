# Active Directory – Recurring Account Lockout Troubleshooting Guide

## Overview
Recurring account lockout occurs when a user account is repeatedly locked shortly after being unlocked. This indicates that an external device or service is continuously attempting authentication with incorrect credentials.

---

## Symptoms
- User account repeatedly locks after being unlocked  
- User reports intermittent login failures  
- Password works temporarily then stops working again  
- Event ID 4740 appears frequently in logs  

---

## Environment
- Domain: Equinox.local  
- Service: Active Directory Domain Services (AD DS)  
- Tools:
  - Active Directory Users and Computers (ADUC)
  - Event Viewer (Security Logs)
  - Credential Manager

---

## Root Cause
Recurring lockouts are typically caused by:
- Cached credentials on secondary devices  
- Mobile devices using outdated passwords  
- Email clients (Outlook, mobile mail apps)  
- Mapped network drives with old credentials  
- Scheduled tasks or services using stored credentials  

---

## Resolution Steps

### 1. Identify Source of Lockout
- Open Event Viewer on Domain Controller  
- Navigate to:  
  `Windows Logs → Security`  
- Look for:
  - Event ID **4740**
- Check **Caller Computer Name** (source device)

---

### 2. Remove Cached Credentials
- Open **Credential Manager** on affected workstation  
- Remove outdated credentials  
- Re-enter correct domain password  

---

### 3. Update All Devices
- Update password on:
  - Mobile devices  
  - Email clients (Outlook, etc.)  
  - Secondary PCs or laptops  

---

### 4. Verify Resolution
- Unlock user account in ADUC  
- Monitor for new lockout events  
- Confirm stable login across all devices  

---

## Verification
- No new Event ID 4740 entries after fix  
- User account remains active  
- Successful login from all devices  
- No repeated lockout within monitoring period  

---

## Common Scenarios
- User changed password but mobile device not updated  
- Outlook still using old cached password  
- VPN client using outdated credentials  
- Background service running under user account  

---

## Advanced Troubleshooting
- Use **Event Viewer → Security Logs** to trace lockout source  
- Identify pattern of repeated authentication attempts  
- Check services running under user credentials  
- Use tools (if available in lab):
  - LockoutStatus.exe  
  - PowerShell AD queries  

---

## Prevention
- Educate users to update all devices after password change  
- Enforce periodic credential refresh  
- Remove unused device sessions from account  
- Monitor frequent lockout accounts proactively  

---

## References
- Active Directory Users and Computers (ADUC)  
- Windows Event Viewer  
- Microsoft Account Lockout Troubleshooting Guide  
