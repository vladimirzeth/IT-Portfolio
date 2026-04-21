# Ticket ID: HD-AD-004

## User Information
- Name: Melanie Cruz
- User Type: Temporary Staff
- Department: Operations
- Account Type: Active Directory Domain User

---

## Issue Summary
User reported inability to log in to the domain. Authentication failed despite correct credentials. Initial verification indicated that the account may have been disabled or expired in Active Directory.

---

## Environment
- Domain: Equinox.local
- Service: Active Directory Domain Services (AD DS)
- User Account Type: Temporary / Time-bound account
- Authentication Method: Windows Domain Login

---

## Troubleshooting Steps
- Verified user credentials and confirmed correct input from user
- Checked Active Directory Users and Computers (ADUC) for account status
- Reviewed account properties:
  - Account enabled status
  - Account expiration date
- Confirmed account was not locked due to failed login attempts
- Cross-checked group membership and policy restrictions
- Verified domain controller replication status (no issues found)

---

## Root Cause
The user account had reached its configured expiration date due to being a temporary staff account. Active Directory automatically disables authentication once the expiration date is reached.

---

## Resolution
- Extended the account expiration date in Active Directory Users and Computers (ADUC)
- Updated expiration date to align with revised contract period
- Verified successful login after modification
- Confirmed restored access with the user

---

## Status
Resolved

---

## Documentation (Link)
https://github.com/vladimirzeth/IT-Portfolio/tree/main/active-directory-lab/HD-AD-004
