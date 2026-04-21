# Active Directory – User Account Expiration Issue (HD-AD-004)

## Overview
User account expiration occurs when a configured Active Directory account reaches its defined expiration date. Once expired, the user is prevented from authenticating into the domain, even with correct credentials.

This lab simulates a real-world scenario where a temporary staff account becomes inaccessible due to expiration, and demonstrates the troubleshooting and resolution process using Active Directory tools.

---

## Symptoms

- User is unable to log in to domain-joined machine  
- Authentication fails despite correct credentials  
- No indication of incorrect password (account restriction behavior instead)  
- Account access suddenly stops working  

---

## Environment

- Domain: Equinox.local  
- Service: Active Directory Domain Services (AD DS)  
- Tools:
  - Active Directory Users and Computers (ADUC)
  - Windows 11 Domain-Joined Client VM
  - Server Manager (for AD verification)

---

## Root Cause

- The user account reached its configured expiration date in Active Directory  
- Expired accounts are automatically denied authentication by AD DS policies  

---

## Investigation Steps

### 1. Verify User Account in Active Directory

- Open **Active Directory Users and Computers (ADUC)**  
- Locate user account: Melanie Cruz  
- Check **Account tab → Account expires setting**

![Account Properties](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-004-Account-Properties.png?raw=true)

---

### 2. Check Expiration Status

- Confirm that the account expiration date has already passed  
- Validate that the account is still enabled (not disabled or locked)

---

### 3. Attempt Login from Windows 11 Client

- Use domain-joined Windows 11 VM  
- Attempt login using valid credentials  

### Result:
- Login fails due to expired account restriction  
- No successful authentication is possible until expiration is updated  

---

## Resolution Steps (Lab Implementation)

### 1. Extend Account Expiration

- Open ADUC  
- Navigate to user properties  
- Go to **Account tab**  
- Modify:
  - Set expiration date to future date OR select **Never expires**

![Extend Expiration](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-004-Extend-Expiration.png?raw=true)

---

### 2. Apply Changes

- Click Apply and OK  
- Ensure replication completes if multiple domain controllers are used  

---

### 3. Validate Access

- Return to Windows 11 client VM  
- Attempt login again using same credentials  

![Successful Login](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-004-Successful-Login.png?raw=true)

### Result:
- User successfully logs in to the domain  
- Access to system resources restored  

---

## Resolution (Real-World Scenario)

In production environments, account expiration issues are commonly resolved by:

- Verifying employment contract duration  
- Extending account validity based on HR confirmation  
- Ensuring temporary accounts follow lifecycle policies  
- Documenting all changes for audit compliance  

---

## Verification

- User successfully authenticates into domain-joined system  
- No login errors observed after modification  
- Active Directory reflects updated expiration settings  
- No further authentication restrictions detected  

---

## Prevention

- Regular review of temporary and contractor accounts  
- Implement account lifecycle management policies  
- Monitor expiring accounts using AD reports or scripts  
- Align account expiration with HR onboarding/offboarding processes  

---

## References

- Active Directory Users and Computers (ADUC)  
- Windows 11 Domain Authentication  
- Microsoft AD DS Account Management Documentation  
