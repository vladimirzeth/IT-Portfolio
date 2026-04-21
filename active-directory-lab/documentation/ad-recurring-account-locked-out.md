# Active Directory – Recurring Account Lockout Troubleshooting

## Overview
Recurring account lockout occurs when a user account is repeatedly locked after being unlocked. This typically indicates continuous authentication attempts using outdated credentials from a device or service.

---

## Symptoms

- Account locks again shortly after being unlocked  
- User experiences intermittent login success  
- Event ID 4740 appears multiple times in Event Viewer  

![Lockout Error](../screenshots/recurring-lockout-error.png)

---

## Environment

- Domain: Equinox.local  
- Service: Active Directory Domain Services (AD DS)  
- Tools:
  - Active Directory Users and Computers (ADUC)
  - Event Viewer  

---

## Root Cause

- Repeated authentication attempts using outdated credentials  
- Continuous failed logon attempts triggering lockout policy  

---

## Investigation Steps

### 1. Check Account Lockout Event

- Open **Event Viewer** on Domain Controller  
- Navigate to:  
  `Windows Logs → Security`  
- Look for:
  - Event ID **4740** (Account lockout)

![Event 4740](../screenshots/event-4740.png)

---

### 2. Identify Source of Lockout

- Open Event ID 4740 details  
- Check **Caller Computer Name**

![Caller Computer](../screenshots/caller-computer.png)

> Note: In this lab setup, only one client machine is used, so the same computer name appears repeatedly.  
> In real environments, multiple devices may appear here.

---

### 3. Analyze Failed Login Attempts

- Look for Event ID **4625**  
- Confirm repeated failed authentication attempts  

![Failed Login](../screenshots/event-4625.png)

---

## Resolution Steps (Lab Implementation)

### 1. Simulate Recurring Lockout

- Log in using correct credentials  
- Change password in ADUC  
- Attempt login using old password multiple times  

![Failed Attempts](../screenshots/failed-login.png)

---

### 2. Unlock and Correct Authentication

- Unlock account in ADUC  
- Log in using updated password  

![Unlock Account](../screenshots/unlock-account.png)

---

### 3. Verify Stability

- Monitor Event Viewer logs  
- Confirm no new lockout events occur  

![Successful Login](../screenshots/success-login.png)

---

## Resolution (Real-World Scenario)

If multiple devices are identified in **Caller Computer Name**:

- Locate affected devices  
- Remove cached credentials  
- Update stored passwords on all devices  
- Sign out active sessions if necessary  

---

## Verification

- No new Event ID 4740 entries observed  
- User account remains unlocked  
- Successful login persists without interruption  

---

## Common Scenarios

- User changed password but another device still uses old credentials  
- Background authentication using outdated password  
- Multiple systems attempting login simultaneously  

---

## Prevention

- Ensure all devices are updated after password change  
- Monitor lockout events regularly  
- Educate users on credential management  

---

## References

- Active Directory Users and Computers (ADUC)  
- Windows Event Viewer  
