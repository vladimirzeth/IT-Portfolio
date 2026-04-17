# Ticket ID: HD-003

## User Information
- Name: TrueNAS SCALE Admin
- Role: System Administrator
- Platform: TrueNAS SCALE

## Assigned To
- Infrastructure Admin

---

## Environment
- OS: TrueNAS Scale
- Platform: Nextcloud App
- Storage Path: `/mnt/<pool>/<dataset>/Nextcloud`

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
- Impact: Service disruption during upgrade process (Nextcloud temporarily inaccessible)
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
The PostgreSQL upgrade container failed because the database dataset had incorrect ownership. TrueNAS SCALE runs PostgreSQL under UID 999, and mismatched permissions prevented read/write access, causing the container to exit with error code 1 and blocking the upgrade process.

---

## Time to Resolution
- ~30 - 60 minutes (including diagnosis and validation)

## Status
Resolved

---

## Lessons Learned
- TrueNAS SCALE application upgrades are sensitive to dataset ownership and permissions
- PostgreSQL containers require UID 999 ownership for database directories
- Upgrade failures in dependent services can block entire application deployment
- App lifecycle logs are critical for diagnosing Helm and container startup issues
- Permission-related issues may present as database failures but originate from filesystem misconfiguration

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
