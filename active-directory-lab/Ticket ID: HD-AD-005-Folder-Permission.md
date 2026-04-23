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
- NTFS permissions (File Server)
- Share permissions (File Server)
- AD group membership (ADUC)

## Resolution
- Added user to Sales_Team group
- Verified access

## Root Cause
User not assigned correct permissions.

## Status
Resolved

---

## Documentation
- [Active Directory – Folder Permission Troubleshooting](../active-directory-lab/documentation/ad-folder-permission.md)
