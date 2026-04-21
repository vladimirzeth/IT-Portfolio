# Active Directory – Shared Folder Access Issue

## Overview  
User was unable to access a shared network folder located at `\\FS01\Sales`. The issue was caused by missing group membership required for access permissions.

---

## Symptoms  

- User cannot access `\\FS01\Sales` shared folder  
- Access denied error when attempting to open network path  
- No network connectivity issues observed  

![Access Denied](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-005-File-Access-Denied.png?raw=true)

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

User was not included in the required security group that has permission to access the shared folder.

---

## Investigation Steps  

### 1. Verified Access Denial  
- User attempted to access `\\FS01\Sales`  
- Confirmed access was denied  

---

### 2. Checked Shared Folder Properties in Active Directory / File Server  
- Reviewed shared folder permission settings  
- Identified permitted security groups for access

  ![Permitted Lists](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-005-Permitted-Lists.png?raw=true)

---

### 3. Verified User Group Membership  
- Checked if user is part of authorized access groups  
- Confirmed user is not included in required group

  ![User Member of](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-005-Acct-Member-Of.png?raw=true)
  
---

## Resolution Steps  

### 1. Confirm Access Rejection  
- Verified that the user was denied access to the shared folder

---

### 2. Review Shared Permissions  
- Checked shared folder properties and security settings  
- Identified allowed groups for access control  

---

### 3. Validate Group Membership  
- Confirmed that the user is not part of the permitted group list  

---

### 4. Add User to Correct Security Group  
- IT added the user to the **Sales_Team** security group

  ![Adding To Group](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-005-Adding-Group.png?raw=true)

  ![Added](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-005-Added.png?raw=true)

---

### 5. Verify Access After Changes  
- User re-logged in / refreshed session  
- Confirmed successful access to `\\FS01\Sales`

  ![User Access the Folder Successfully](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-005-Success-Passthrough.png?raw=true)

---

## Resolution Outcome  

User gained successful access to the shared folder after being added to the correct security group.

---

## Verification  

- User can now access shared folder  
- No access denied errors observed  
- Permissions applied successfully after group update  

---

## Prevention  

- Ensure proper group assignment during onboarding  
- Regular review of security group memberships  
- Implement Role-Based Access Control (RBAC) best practices  
- Monitor access-related issues proactively  
