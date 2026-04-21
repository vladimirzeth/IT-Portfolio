# Ticket ID: HD-AD-005

## User Information
- Name: Mary Jane Anderson
- Department: Sales

## Issue Summary
User cannot access shared folder on network.

## Environment
- File Server: S01
- Shared Folder: \\FS01\Sales

## Troubleshooting Steps
- Verified NTFS permissions
- Checked share permissions
- Confirmed group membership

## Resolution
- Added user to Finance security group
- Verified access

## Root Cause
User not assigned correct permissions.

## Status
Resolved

---

## Documentation
- [Active Directory – Folder Permission Troubleshooting](../active-directory-lab/documentation/ad-folder-permission.md)
