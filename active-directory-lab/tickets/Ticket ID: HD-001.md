# Ticket ID: HD-001

## User Information
- Name: John Doe
- Department: Engineering Department
- Date Reported: April 10, 2026

## Assigned To
- Help Desk Technician

---

## Environment
- OS: TrueNAS Scale
- Platform: Docker
- Service: Containerized Application

---

## Issue Summary

A container entered a restart loop and failed to start properly after deployment.

---
## Category
Software / Containerization
---

## Priority
- Level: High  
- Impact: Main service unavailable  
- Urgency: Immediate  

---

## Initial Diagnosis
-	Container observed in continuous restart loop
-	Service endpoint inaccessible via mapped port
-	Suspected configuration issue due to recent deployment changes
  
---

## Troubleshooting Steps
1.	Checked container logs using `docker logs`
2.	Reviewed container configuration and port mappings
3.	Identified that the configured port was already in use
4.	Selected an available port for reassignment

---

## Tools / Commands Used
- `docker logs <container_id>`
- `docker ps`

---

## Resolution
Updated the container port mapping to an available port and restarted the container, successfully restoring service availability.

---

## Root Cause & User Explanation
The issue was caused by a port conflict due to duplicate port usage by another service. The configuration was corrected, and the service is now operational.

---

## Time to Resolution
- ~15 minutes

## Status
Closed

---

## Lessons Learned
Port conflicts are common in containerized environments and should always be checked during deployment.
