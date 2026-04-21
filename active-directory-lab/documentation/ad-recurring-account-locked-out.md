# Active Directory – Recurring Account Lockout Troubleshooting

## Overview
Recurring account lockout occurs when a user account is repeatedly locked after being unlocked. This typically indicates continuous authentication attempts using outdated credentials from a device or service.

---

## Symptoms

- Account locks again shortly after being unlocked  
- User experiences intermittent login success  
- Event ID 4740 appears multiple times in Event Viewer  

![Lockout Error](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-002-Locked-Out.png?raw=true)

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

![Event 4740](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-002-Event-Viewer-Locked-Out-Result.png?raw=true)

---

### 2. Analyze Lockout Details

- Open Event ID 4740 details  
- Review available event fields such as:
  - Target User Name  
  - Target Domain Name  
  - Computer (Domain Controller)

![Caller Computer](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-002-Computer-Name.png?raw=true)

> Note: In this lab environment, the **Caller Computer Name field is not present**.  
> The source of the lockout was determined through controlled testing using a single domain-joined client machine.  
>  
> In real-world environments, the **Caller Computer Name** field is used to identify the exact device causing the lockout, which may include multiple systems.

---

### 3. Analyze Failed Login Attempts

- Look for Event ID **4625**  
- Confirm repeated failed authentication attempts  

![Failed Login](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-002-Event-Viewer-Login-Attempts.png?raw=true)

---

## Resolution Steps (Lab Implementation)

### 1. Simulate Recurring Lockout

- Log in using correct credentials  
- Change password in ADUC  
- Attempt login using old password multiple times  

![Failed Attempts](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-002-Failed-Login.png?raw=true)

---

### 2. Unlock and Correct Authentication

- Unlock account in ADUC  
- Log in using updated password  
- Ensure correct credentials are used consistently  

![Unlock Account](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-002-Logging-In.png?raw=true)

---

### 3. Verify Stability

- Monitor Event Viewer logs  
- Confirm no new lockout events occur  
- Validate successful authentication without interruption  

---

## Resolution (Real-World Scenario)

If multiple devices are identified as sources of authentication attempts:

- Identify affected systems  
- Remove cached or stored credentials  
- Update passwords on all devices  
- Sign out active sessions if necessary  

---

## Verification

- No new Event ID 4740 entries observed  
- User account remains unlocked  
- Successful login persists without interruption  

---

## Common Scenarios

- User changed password but system still uses old credentials  
- Background authentication using outdated password  
- Repeated login attempts with incorrect credentials  

---

## Prevention

- Ensure credentials are updated after password changes  
- Monitor lockout events regularly  
- Educate users on proper credential usage  

---

## References

- Active Directory Users and Computers (ADUC)  
- Windows Event Viewer  
