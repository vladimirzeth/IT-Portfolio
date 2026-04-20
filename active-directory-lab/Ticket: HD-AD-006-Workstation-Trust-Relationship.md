# Ticket ID: HD-AD-006

## User Information
- Name: John Reyes
- Department: IT

## Issue Summary
User cannot log in. Error: "The trust relationship between this workstation and the primary domain failed."

## Environment
- Device: Domain-joined workstation

## Troubleshooting Steps
- Verified domain connectivity
- Checked computer account in AD

## Resolution
- Removed computer from domain
- Rejoined to domain

## Root Cause
Broken secure channel between workstation and domain controller.

## Status
Resolved
