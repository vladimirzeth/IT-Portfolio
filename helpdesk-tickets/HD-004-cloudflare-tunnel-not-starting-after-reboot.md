# Ticket ID: HD-004

## User Information
- Name: TrueNAS SCALE Admin
- Role: System Administrator
- Platform: TrueNAS SCALE

---

## Environment
- OS: TrueNAS SCALE  
- Service: Cloudflared Tunnel (Cloudflare Zero Trust)  
- Startup Method: Init/Shutdown Script (Post Init)  
- Script Path: `/home/truenas_admin/start-cloudflaretunnel.sh`

---

## Issue Summary
After server reboot, the Cloudflared tunnel service does not start automatically, resulting in DNS resolution failure and HTTP 404 errors when attempting to access hosted services externally.

---

## Business Impact
- External services become inaccessible after system reboot  
- DNS routing fails due to inactive tunnel  
- Users experience 404 errors when accessing services via domain  
- Manual intervention required after every restart  

---

## Initial Diagnosis
- Verified that Cloudflared tunnel process was not running after reboot  
- Confirmed that init/shutdown script did not execute properly  
- DNS requests failed due to inactive tunnel connection  
- Services behind Cloudflare could not be resolved externally  

---

## Troubleshooting Steps
1. Checked TrueNAS Init/Shutdown Scripts configuration  
2. Verified script location and execution path:
   `/home/truenas_admin/start-cloudflaretunnel.sh`  
3. Confirmed script is set to run at **Post Init stage**  
4. Checked service logs after reboot for execution errors  
5. Verified tunnel manually starts successfully when executed manually  

---

## Root Cause
The Cloudflared tunnel was not automatically starting after reboot due to improper or unreliable execution of the init script during the TrueNAS SCALE boot sequence.

As a result, the DNS endpoint configured through Cloudflare was unreachable, causing external access failures and HTTP 404 responses.

---

## Resolution
Configured and validated an Init/Shutdown script in TrueNAS SCALE to start Cloudflared tunnel at **Post Init stage**:

```bash
sudo bash /home/truenas_admin/start-cloudflaretunnel.sh
