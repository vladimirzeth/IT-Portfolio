# Ticket ID: HD-001

## User Information
- Name: John Doe
- Department: Engineering Department
- Date Reported: April 10, 2026

## Assigned To
- Help Desk Technician

---

## Issue Summary

A container entered a restart loop and failed to start properly after deployment.

---
## Category
-	Software / Containerization
---

## Priority
- Priority: High
- Impact: Main service unavailable

---

## Initial Diagnosis
-	Container observed in continuous restart loop
-	Service endpoint inaccessible via mapped port
---

## Troubleshooting Steps
1.	Checked container logs using 'docker logs'
2.	Reviewed container configuration and port mappings
3.	Identified that the configured port was already in use
4.	Selected an available port for reassignment

## Tools / Commands Used
- 'docker logs <container_id>'
- 'docker ps'

---

## Resolution
Updated the container port mapping to an available port and successfully restarted the container, restoring service availability.

---

## User Communication
The issue was caused by a port conflict due to duplicate port usage by another service. The configuration was corrected, and the service is now operational.

---

## Timne to Resolution
- ~15 minutes

## Status
Closed

---

## Lessons Learned
Port conflicts are common in containerized environments and should always be checked during deployment.
