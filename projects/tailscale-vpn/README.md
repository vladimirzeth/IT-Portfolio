# Tailscale VPN

A zero-config VPN built on WireGuard that creates a private encrypted network between my devices, allowing secure remote access to all homelab services without exposing any ports to the internet.

## What it does

Tailscale assigns each enrolled device a private IP address on a virtual network (called a tailnet). This means I can access Mattermost, n8n, Pi-hole, and the TrueNAS dashboard from anywhere — phone, laptop, remote machine — as if I were on the local network, with no open firewall ports.

## Setup overview

| Detail | Value |
|---|---|
| Platform | TrueNAS Scale |
| Deployment | Docker via Dockge |
| Protocol | WireGuard (managed by Tailscale) |
| Access | All homelab services reachable via Tailscale IP |

## How I deployed it

1. Deployed the Tailscale container with the official image
2. Authenticated the container to my Tailscale account using an auth key
3. Enabled subnet routing so the container advertises the local network to other Tailscale devices
4. Enrolled personal devices (laptop, phone) into the tailnet for remote access

## Why Tailscale over port forwarding

Port forwarding exposes services directly to the public internet, which creates significant attack surface. Tailscale keeps everything private — no ports are open on the router, and access is gated by device authentication. This is a zero-trust approach to remote access.

## Challenges & how I solved them

- **Challenge:** Subnet routes weren't being advertised after container restart
  **Fix:** Added `--advertise-routes` to the container startup flags and approved the routes in the Tailscale admin console

- **Challenge:** Other containers couldn't be reached via Tailscale IP
  **Fix:** Configured the Tailscale container with `network_mode: host` so it could properly route traffic across the local network

## What I learned

- How WireGuard establishes encrypted peer-to-peer tunnels
- The concept of zero-trust networking and why it's preferred over VPN port exposure
- How subnet routing works to make an entire LAN reachable through a single VPN node

## Screenshots

![Tailscale Admin Console](./screenshots/admin-console.png)
