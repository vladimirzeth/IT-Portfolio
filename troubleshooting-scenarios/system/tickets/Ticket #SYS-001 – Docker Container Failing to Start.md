# Ticket #SYS-001 – Docker Container Failing to Start

**Status:** Resolved  
**Priority:** High  
**Category:** System  

---

### Issue Description  
A container failed to start after deployment.

### Environment  
- Platform: TrueNAS SCALE  
- Container Runtime: Docker  
- Management Tool: Dockage

### Symptoms  
- Container stuck in restarting state  
- Service inaccessible  

### Troubleshooting Process  
1. Checked container logs  
2. Verified environment variables  
3. Reviewed container configuration  
4. Checked for port conflicts  

### Root Cause  
Port conflict with another running service.

### Resolution  
Changed port mapping and restarted the container.

### Verification  
Container started successfully and service became accessible.

### Lessons Learned  
Port conflicts are common in containerized environments and should always be checked during deployment.
