# Active Directory – Recurring Account Lockout Troubleshooting

## Overview
Recurring account lockout occurs when a user account is repeatedly locked after being unlocked. This typically indicates continuous authentication attempts using outdated or incorrect credentials.

> Note: This scenario was simulated in a controlled lab environment using stale credentials on a domain-joined client machine.

---

## Symptoms

- User account repeatedly locks after being unlocked  
- User experiences intermittent login access  
- Correct password works temporarily, then fails again  

![Account Lockout Error](../screenshots/recurring-lockout-error.png)

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
- Simulated stale credentials on client machine  
- Continuous failed login attempts triggering lockout policy  

---

## Resolution Steps

### 1. Confirm Account Lockout in ADUC

- Open **Active Directory Users and Computers**  
- Locate user: Camille Spencer  
- Verify account is locked  

![ADUC Locked Account](../screenshots/aduc-locked-account.png)

---

### 2. Review Security Logs on Domain Controller

- Open **Event Viewer**  
- Navigate to:  
  `Windows Logs → Security`  
- Identify:
  - Event ID **4740** (Account lockout)  
  - Event ID **4625** (Failed logon attempts)  

![Event Viewer Lockout](../screenshots/event-4740.png)

---

### 3. Simulate Recurring Lockout (Lab Setup)

- Log in using correct credentials  
- Change password in ADUC  
- Attempt login using old password multiple times  

![Failed Login Attempts](../screenshots/failed-login.png)

---

### 4. Clear Cached Credentials

- Open **Credential Manager**  
- Remove stored domain credentials  
- Re-enter updated password  

![Credential Manager](../screenshots/credential-manager.png)

---

### 5. Unlock and Test Account

- Unlock account in ADUC  
- Log in using updated credentials  
- Confirm stable access  

![Successful Login](../screenshots/success-login.png)

---

## Verification

- No new Event ID 4740 entries observed  
- User account remains unlocked  
- Successful login persists after multiple attempts  

---

## Common Scenarios

- User changed password but system still uses old credentials  
- Background authentication attempts using outdated password  
- Cached credentials not updated  

---

## Prevention

- Ensure all credentials are updated after password change  
- Clear cached credentials regularly  
- Monitor frequent lockout events in Event Viewer  

---

## References

- Active Directory Users and Computers (ADUC)  
- Windows Event Viewer  
