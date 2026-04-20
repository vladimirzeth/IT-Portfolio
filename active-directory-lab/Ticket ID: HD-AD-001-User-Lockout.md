# Ticket ID: HD-AD-001

## User Information
- Name: Masha Trusova
- Department: Sales
- Date Reported: April 20, 2026

## Issue Summary
User unable to log in to domain account. Error indicates account is locked.

## Environment
- Domain: Equinox.local
- Device: Domain-joined workstation
- OS: Windows 10

## Troubleshooting Steps
- Checked account status in Active Directory Users and Computers (ADUC)
- Verified account lockout status
- Reviewed failed login attempts

## Resolution
- Unlocked user account in ADUC
- Advised user to re-enter correct password

## Root Cause
Multiple failed login attempts triggered account lockout policy.

## Status
Resolved
