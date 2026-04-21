# Active Directory – Shared Folder Access Issue

## Overview  
User was unable to access a shared network folder located at `\\FS01\Sales`. The issue was caused by incorrect security group assignment resulting in insufficient permissions to the shared resource.

---

## Symptoms  

- User cannot access `\\FS01\Sales` shared folder  
- Access denied error when attempting to open network path  
- No visible network connectivity issues  

![Access Denied](INSERT_IMAGE_LINK_HERE)

---

## Environment  

- File Server: S01  
- Shared Folder: \\FS01\Sales  
- Service: Windows File Sharing (SMB)  
- Tools:
  - Active Directory Users and Computers (ADUC)
  - File Server Permission Management
  - NTFS Permissions

---

## Root Cause  

User was not assigned to the correct security group required to access the shared folder. This resulted in missing NTFS and share-level permissions.

---

## Investigation Steps  

### 1. Verified Share Access  
- Attempted to access `\\FS01\Sales`  
- Confirmed access denied error  

---

### 2. Checked Share Permissions  
- Reviewed file server share permissions  
- Confirmed required groups exist but user was not included  

---

### 3. Checked NTFS Permissions  
- Reviewed folder security settings  
- Verified access restricted to specific security groups  

---

### 4. Verified Active Directory Group Membership  
- Opened Active Directory Users and Computers (ADUC)  
- Checked user account properties  
- Confirmed missing required security group  

---

## Resolution  

- Added user to the correct security group (Finance group)  
- Applied Active Directory changes  
- Forced policy refresh / user re-login  
- Verified successful access to shared folder  

---

## Resolution Outcome  

User successfully gained access to `\\FS01\Sales` after proper security group assignment.

---

## Verification  

- User can now access shared folder  
- No access denied errors observed  
- Permissions applied correctly and persist after re-login  

---

## Prevention  

- Ensure correct group assignment during onboarding  
- Regular audit of security group memberships  
- Maintain Role-Based Access Control (RBAC) structure  
- Monitor permission-related access issues proactively  

---

## Documentation  

- Ticket ID: HD-AD-005  
- Evidence Folder: `\\S01\IT-Documentation\HD-AD-005\`  
- Screenshots: Add your GitHub image links here  
