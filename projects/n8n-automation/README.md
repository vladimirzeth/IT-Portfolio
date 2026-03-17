# n8n Automation

A self-hosted workflow automation tool, similar to Zapier, used to build automated pipelines between services without relying on cloud platforms.

## What it does

n8n allows building automation workflows using a visual node-based editor. I use it to automate repetitive tasks in my homelab — for example, triggering notifications or connecting services together without manual intervention.

## Setup overview

| Detail | Value |
|---|---|
| Platform | TrueNAS Scale |
| Deployment | Docker via Dockge |
| Storage | Persistent volume for workflow data |

## How I deployed it

1. Created a `docker-compose.yml` using the official `n8nio/n8n` image
2. Set environment variables for timezone and basic authentication
3. Mounted a persistent volume to `/home/node/.n8n` so workflows survive restarts
4. Accessed the visual editor via browser on port 5678

## Example workflow

Built a workflow that monitors a webhook trigger and sends a notification — demonstrating how n8n can connect services and react to events automatically.

## Challenges & how I solved them

- **Challenge:** Workflows were lost after container restart
  **Fix:** Properly mapped the `.n8n` data directory to a named Docker volume

- **Challenge:** n8n was accessible from outside the local network without authentication
  **Fix:** Enabled basic auth via environment variables and restricted access through Tailscale

## What I learned

- How event-driven automation works using webhooks and triggers
- How to secure a self-hosted web UI behind authentication
- Practical understanding of how tools like Zapier work under the hood

## Screenshots

![n8n Workflow Editor](./screenshots/workflow.png)
