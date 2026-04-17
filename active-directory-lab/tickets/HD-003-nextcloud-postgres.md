# Ticket ID: HD-003

## User Information
- Name: TrueNAS SCALE Admin (truenas_admin)
- Role: System Administrator
- Platform: TrueNAS SCALE

## Assigned To
- Infrastructure Admin

---

## Environment
- OS: TrueNAS Scale
- Platform: Nextcloud App
- Storage Path: `/mn/<pool>/<dataset>/Nextcloud`

---

## Issue Summary
Nextcloud application was stuck at 20% during upgrade process, failing to complete deployment due to PostgreSQL upgrade container error.

---

## Category
- Application Deployment
- Database (PostgreSQL)

---

## Priority
- Level: High 
- Impact: Servicie disruption during upgrade
- Urgency: Immediate access required for ongoing work  

---

## Initial Diagnosis
Logs indicated failure in the PostgreSQL upgrade container:
- postgres_upgrade-1 service didn't complete successfully: exit 1
- App stuck during compose `up` process
- Permissions mismatch suspected on PostgreSQL dataset

---

## Troubleshooting Steps
1. Reviewed app lifecycle logs:
`/var/log/app_lifecycle.log`
2. Identified PostgreSQL upgrade failure during startup
3. Checked container creation flow for Nextcloud stack
4. Identified possible permission issue on Postgres data directory
5. Applied filesystem permission correction

---

## Tools / Commands Used
- `chown -R 999:999 /mnt/Tank/Application_NextCloud/Postgresdata`

---

## Resolution
Fixed PostgreSQL permission issue by recursively setting correct ownership on the database dataset:
`chown -R 999:999 /mnt/Tank/Application_NextCloud/Postgresdata`
After correcting permissions, Nextcloud app successfully completed startup and upgrade process.

---

## Root Cause & User Explanation
The PostgreSQL update container failed because it did not have proper read/write permission on the database storage directory.
TrueNAS SACLE apps run PostgreSQQL under a specific internal user ID (UID 999). When the dataset ownership does not match this UID, the upgrade container exits with failure (**exit 1**), causing the entire Nextcloud app startup process to fail.

---

## Time to Resolution
- ~30 - 60 minutes (including diagnosis and valadation)

## Status
Resolved

---

## Lessons Learned
- TrueNAS SCALE app upgrades depend heavily on correct dataset ownership
- PostgreSQL containers require UID 999 ownership for database directories
- Failed upgrade containers can block entire app startup process
- Always check `/var/log/app_lifecycle.log` for Helm/app lifecycle failures
- Permission issues can appear as "database failure" but are actually lifesystem-related

---

## Evidence / Screenshots

### Before Fix
Got error in updating the Nextcloud
![Upgrade Failure](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/hd-003-error.png?raw=true)

Logs
![Logs](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/hd-003-logs.png?raw=true)


---

### After Fix
Logs After
![Logs After](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/hd-003-logs-after.png?raw=true)

Container running normally

![Running Container](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/hd-003-after.png?raw=true)
