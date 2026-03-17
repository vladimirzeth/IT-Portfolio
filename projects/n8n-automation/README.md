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

- **Challenge:** Devices on the network were not automatically using Pi-hole as their DNS server after deployment
  **Fix:** Logged into the home router's DHCP settings and set the server's local IP as the primary DNS server, so all connected devices receive it automatically

- **Challenge:** Some devices were bypassing Pi-hole by using hardcoded DNS servers (e.g. 8.8.8.8)
  **Fix:** Added a firewall rule on the router to intercept and redirect all outbound DNS traffic on port 53 to Pi-hole, forcing every device to use it regardless of their configured DNS

## What I learned

- How event-driven automation works using webhooks and triggers
- How to secure a self-hosted web UI behind authentication
- Practical understanding of how tools like Zapier work under the hood

## Screenshots

![n8n Workflow Editor](./screenshots/workflow.png)
