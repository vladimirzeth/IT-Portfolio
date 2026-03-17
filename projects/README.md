# Projects

This section contains documentation of the systems I have deployed and managed in my homelab environment.

## Architecture

![Homelab Architecture](./assets/architecture.png)

> All services run as Docker containers on TrueNAS Scale, managed through Dockge. Pi-hole handles network-wide DNS filtering, and Tailscale provides secure remote access without any open ports.

## Hardware

| Component | Spec |
|---|---|
| Machine | HP Thin Client T630 |
| RAM | 12 GB |
| Storage | 128 GB M.2 SSD (OS) + 500 GB HDD (data) |
| OS | TrueNAS Scale |
| Containers | Docker, managed via Dockge |

## Services

| Service | Purpose | Docs |
|---|---|---|
| Mattermost | Self-hosted team messaging | [View](./mattermost/) |
| n8n | Workflow automation | [View](./n8n-automation/) |
| Pi-hole | Network DNS + ad blocking | [View](./pihole/) |
| Tailscale VPN | Secure remote access | [View](./tailscale-vpn/) |

## Skills Demonstrated

Linux server administration · Docker & Compose · DNS & DHCP · VPN / WireGuard · Workflow automation · Low-power self-hosted infrastructure
