# Active Directory – Account Disabled Troubleshooting

## Overview
This issue occurs when a user account in Active Directory has been disabled, preventing the user from authenticating to the domain. Disabled accounts are typically used for security control, employee offboarding, or administrative actions.

## Symptoms
-	User cannot log in to workstation or domain 
-	Error message: “Your account has been disabled. Please see your system administrator.” 
-	Login fails even with correct credentials

## Environment
- Domain: Equinox.local
- Directory Service: Active Directory Domain Services (AD DS)
- Tools:
	- Active Directory Users and Computers (ADUC)
	- Domain Controller (Windows Server 2022)

## Root Cause
-	Account was manually disabled by an administrator 
-	Account disabled due to security policy or suspicious activity 
-	User account deactivated during employee offboarding 
-	Bulk administrative action (e.g., script or group policy)

## Resolution
1.	Open Active Directory Users and Computers
   	![Users and Computers]("https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-003-AD-Users-and-Computers.png?raw=true")
3.	Navigate to the affected user account by using “Find” function in GUI
4.	Right-click the account
5.	Select “Enable Account”
6.	Confirm the account is now active

## Verification
-	User successfully logs in to domain workstation 
-	No error message appears during login 
-	Account status in ADUC shows as enabled 
-	Confirm user can access domain resources (shared folders, email, etc.)

## Common Scenarios
-	HR requested temporary account deactivation 
-	Administrator mistakenly disabled the account 
-	Security response to suspicious login attempts 
-	Inactive account cleanup policies


## Prevention
-	Implement clear procedures for account disable/enable requests 
-	Document all administrative actions on user accounts 
-	Use role-based access control (RBAC) to limit who can disable accounts 
-	Regularly audit disabled accounts

## References
-
