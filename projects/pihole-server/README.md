# Pi-hole

A network-wide DNS sinkhole that blocks ads and trackers for every device on the local network without installing anything on individual devices.

## What it does

Pi-hole acts as the primary DNS server for the home network. When any device makes a DNS request, Pi-hole checks it against blocklists and either resolves it or drops it if it matches a known ad or tracker domain. This protects all devices including phones, smart TVs, and IoT devices at the network level.

## Setup overview

| Detail | Value |
|---|---|
| Platform | TrueNAS Scale |
| Deployment | Docker via Dockge |
| Role | Primary DNS server for home network |

## How I deployed it

1. Deployed Pi-hole using the official Docker image with a static IP assigned to the container
2. Configured the home router to use the server's IP as its primary DNS server
3. Imported community blocklists via the Pi-hole web admin panel
4. Set up the web UI for monitoring query logs and blocked domains

## Challenges & how I solved them

- **Challenge:** Port 53 conflict the host OS was already using it for local DNS
  **Fix:** Disabled the host's `systemd-resolved` stub listener and reassigned port 53 to the Pi-hole container

- **Challenge:** All DNS stopped working when the Pi-hole container went down
  **Fix:** Configured a secondary DNS fallback on the router so the network stays functional during maintenance

## What I learned

- How DNS resolution works at the network level
- How to configure a router to delegate DNS to a custom server
- The difference between DNS-level blocking vs browser-level ad blocking
- How to read and interpret DNS query logs for troubleshooting

## Screenshots

![Pi-hole Dashboard](./screenshots/dashboard.png)
