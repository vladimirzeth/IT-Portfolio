# Ticket ID: HD-AD-006

## User Information
- Name: John Reyes
- Department: IT Support

---

## Issue Summary
User cannot access domain resources due to DNS resolution failure.

---

## Environment
- Domain: Equinox.local
- Domain Controller: DC01
- Client: WS01

---

## Troubleshooting Steps
- Checked IP configuration
- Verified DNS settings
- Attempted domain resource access via hostname
- Performed nslookup test

---

## Resolution
- Updated DNS server to point to Domain Controller (DC01)
- Flushed DNS cache
- Restarted network adapter

---

## Root Cause
Client machine was using external DNS instead of internal Domain Controller DNS.

---

## Status
Resolved
