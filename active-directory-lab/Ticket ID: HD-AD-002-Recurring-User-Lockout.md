# Ticket ID: HD-AD-002

## User Information
- Name: Masha Trusova
- Department: Sales

## Issue Summary
User account repeatedly locks after being unlocked.

## Environment
- Domain: corp.local
- Multiple devices (laptop + mobile)

## Troubleshooting Steps
- Checked Event Viewer for lockout source
- Identified repeated authentication attempts
- Verified stored credentials

## Resolution
- Cleared cached credentials in Credential Manager
- Updated password on all devices
- Restarted workstation

## Root Cause
Stored outdated credentials on secondary device causing repeated failed logins.

## Status
Resolved
