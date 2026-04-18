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
After system reboot, the Cloudflared tunnel Docker container does not start automatically. This results in DNS resolution failure and HTTP 404 errors when attempting to access hosted services externally through the Cloudflare domain.

---

## Business Impact
- External services become inaccessible after system reboot
- Cloudflare DNS routing fails due to inactive tunnel
- Users experience HTTP 404 errors when accessing services via domain
- Manual intervention required after every system restart to restore connectivity

---

## Initial Diagnosis
- Verified system after reboot and confirmed Cloudflared tunnel was not running
- Checked Docker containers using: `sudo docker ps -a`
- Identified that the Cloudflared container was not running after restart
- Confirmed DNS requests failed due to inactive tunnel connection
- Manual container execution restored external access temporarily

---

## Troubleshooting Steps
1. Checked Docker container status using `docker ps -a`
2. Confirmed Cloudflared tunnel container was not auto-starting after reboot
3. Verified TrueNAS ini/Shutdown Scripts configuration
4. Checked script path: `/home/truenas_admin/start-cloudflaretunnel.sh`
5. Confirmed script execution works manually when triggered
6. Identified missing/failed automatic startup during boot process 

---

## Root Cause
The Cloudflared Docker container was not configured to automatically start after system reboot. Because of this, the tunnel service remained inactive until manually started.

Additionally, the Init/Shutdown script was required to enforce container startup during the TrueNAS SCALE boot sequence.

---

## Resolution
Configured and validated an Init/Shutdown script in TrueNAS SCALE to start Cloudflared tunnel at **Post Init stage**:

```bash
sudo bash /home/truenas_admin/start-cloudflaretunnel.sh
```
---

## Time to Resolution
- ~30 - 45 minutes (including diagnosis and validation)

## Status
Resolved

---

## Lessons Learned
- Docker containers in TrueNAS SCALE do not always persist auto-start behavior after reboot unless explicitly configured
- Verifying container status using docker ps -a is critical for identifying post-reboot service failures
- Init/Shutdown Scripts are effective for enforcing service startup during boot sequence when native Docker restart policies are unreliable
- Post-reboot validation is necessary to ensure external services (DNS/tunnels) are fully operational
- Automating critical infrastructure services reduces downtime and eliminates dependency on manual recovery steps

---

## Evidence / Screenshots

**Init/Shutdown Script**

![Upgrade Failure](https://github.com/vladimirzeth/IT-Portfolio/blob/main/helpdesk-tickets/screenshots/hd-04-Init-Shutdown-Script.png?raw=true)
