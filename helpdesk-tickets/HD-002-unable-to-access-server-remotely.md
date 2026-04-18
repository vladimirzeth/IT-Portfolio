# Ticket ID: HD-002

## User Information
- Name: John Doe
- Department: Sales Department
- Date Reported: April 11, 2026

## Assigned To
- Help Desk Technician

---

## Environment
- OS: TrueNAS Scale
- Platform: Nextcloud (Docker)
- Network: Local Network + VPN (Tailscale)

---

## Issue Summary
The Nextcloud server was accessible within the local network but could not be accessed remotely.

---

## Category
Network / Remote Access

---

## Priority
- Level: High  
- Impact: Important files inaccessible to users from another building  
- Urgency: Immediate access required for ongoing work  

---

## Initial Diagnosis
- Server accessible locally via IP address and port  
- Remote connection attempts failed  
- VPN connection not properly routing traffic to the server  

---

## Troubleshooting Steps
1. Verified that the container was running  
2. Checked exposed ports and container configuration  
3. Confirmed local connectivity to the server  
4. Verified VPN connection status on client device  
5. Reviewed network routing and firewall settings  

---

## Tools / Commands Used
- `docker ps`  
- `ping`  
- Tailscale VPN client (connection status verification)

---

## Resolution
Reconnected the VPN client and ensured proper network routing, restoring remote access to the server.

---

## Root Cause & User Explanation
The issue occurred because the server was only accessible within the local network. Remote access requires a properly connected VPN to route traffic securely. Once the VPN connection was restored, users were able to access the server as if they were on the local network.

---

## Time to Resolution
- ~20 minutes

## Status
Closed

---

## Lessons Learned
Using a VPN is a secure way to enable remote access to internal services. Proper VPN connection and routing should always be verified when troubleshooting remote access issues.

---

## Evidence / Screenshots

### Before Fix
Nextcloud server was inaccessible
![Nextcloud Timeout](https://github.com/vladimirzeth/IT-Portfolio/blob/main/helpdesk-tickets/screenshots/hd-002-before-vpn.png?raw=true)

### VPN Connection (Tailscale)
![Tailscale](https://github.com/vladimirzeth/IT-Portfolio/blob/main/helpdesk-tickets/screenshots/hd-002-vpn-status.png?raw=true)

### After Fix
Container running normally
![Running Container](https://github.com/vladimirzeth/IT-Portfolio/blob/main/helpdesk-tickets/screenshots/hd-002-after-fix.png?raw=true)
