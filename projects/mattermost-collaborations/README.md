# Mattermost

A self-hosted team messaging platform deployed as an alternative to Slack, giving full control over data and communications.

## What it does

Mattermost provides a team chat interface with channels, direct messages, and file sharing. In my homelab, I use it to practice managing a communication platform and understand how enterprise chat tools are deployed and maintained internally.

## Setup overview

| Detail | Value |
|---|---|
| Platform | TrueNAS Scale |
| Deployment | Docker via Dockge |
| Database | PostgreSQL (separate container) |
| Storage | Persistent volume on 500 GB HDD |

## How I deployed it

1. Created a `docker-compose.yml` using the official Mattermost image alongside a PostgreSQL container
2. Configured environment variables for database credentials and site URL
3. Mounted persistent volumes for database data and Mattermost file uploads
4. Managed and monitored the containers through Dockge UI

## Challenges & how I solved them

- **Challenge:** Mattermost container failed to start because PostgreSQL wasn't ready yet
  **Fix:** Added `depends_on` with a health check in the Compose file so Mattermost waits for the DB

- **Challenge:** Uploaded files disappeared after restarting the container
  **Fix:** Mapped the `/mattermost/data` path to a named persistent volume

## What I learned

- How multi-container applications communicate over a shared Docker network
- How to manage database credentials securely using environment variables
- The importance of persistent volume mapping for stateful applications

## Screenshots

![Mattermost Dashboard](./screenshots/dashboard.png)
