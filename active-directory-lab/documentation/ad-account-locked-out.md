# Active Directory – Account Lockout Troubleshooting Guide

## Overview
Account lockout occurs when a user exceeds the maximum number of failed login attempts defined in the domain security policy. This is enforced by Active Directory to prevent unauthorized access.

---

## Symptoms
- User cannot log in to domain account  
- Error message: “The referenced account is currently locked out”  
- Login attempts fail even with correct password  
- Account status shows “Locked Out” in ADUC  

---

## Environment
- Domain: Equinox.local  
- Service: Active Directory Domain Services (AD DS)  
- Tools:
  - Active Directory Users and Computers (ADUC)
  - Event Viewer (Security Logs)

---

## Root Cause
- Multiple incorrect password attempts  
- Cached credentials on devices or services  
- Mobile devices using outdated passwords  
- Password entered incorrectly repeatedly by user  

---

## Resolution Steps

### 1. Identify the Locked Account
- Open **Active Directory Users and Computers**
- Search for user: Pierre Price
- Confirm account status shows **Locked Out**

---

### 2. Unlock the Account
- Right-click user account  
- Select **Unlock Account**  
- Click OK to confirm changes  

---

### 3. Verify Authentication
- Ask user to log in again using correct credentials  
- Confirm successful login  

---

## Verification
- User successfully logs in to domain workstation  
- No further lockout messages appear  
- Event Viewer shows successful logon after unlock  

---

## Common Scenarios
- Incorrect password entered multiple times  
- User changed password but device still uses old credentials  
- Email/mobile sync using outdated password  
- Background services using stored credentials  

---

## Advanced Troubleshooting
- Check Event Viewer:
  - Event ID **4740** → Account locked out event  
  - Event ID **4625** → Failed login attempts  
- Identify source machine causing lockout  
- Use tools like:
  - LockoutStatus.exe (if available in lab)

---

## Prevention
- Educate users on password changes across devices  
- Clear cached credentials after password reset  
- Monitor repeated failed login attempts  
- Implement account lockout policy with balanced threshold (e.g., 5 attempts)

---

## References
- Active Directory Users and Computers (ADUC)  
- Windows Event Viewer Security Logs  
- Microsoft Account Lockout Policy Documentation  
