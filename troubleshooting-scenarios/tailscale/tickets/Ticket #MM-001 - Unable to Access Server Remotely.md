# Ticket #NV-001 – Unable to Access Server Remotely

- **Status**: Resolved
- **Priority**: High
- **Category**: Network / Application

## Issue Description

The Navidrome server was accessible within the local network but could not be accessed remotely.

## Environment
 - **Platform**: TrueNAS SCALE
 - **Service**: Navidrome (Docker container)
 - **Remote Access**: Tailscale

## Symptoms
- Accessible locally via IP and port
- Remote connection attempts fail

## Troubleshooting Process
1. Verified container is running
2. Checked exposed ports
3. Tested local connectivity
4. Verified VPN connection status
5. Reviewed firewall/network settings
   
## Root Cause

VPN connection was not properly routing traffic to the server.

## Resolution

Reconnected VPN client and ensured proper network routing.

## Verification

Successfully accessed Navidrome remotely.

## Lessons Learned

Always isolate whether the issue is network-related or application-related before troubleshooting deeper.


# SCREENSHOTS
## Navidrome Service Connection Issue

![Navidrome Timeout](screenshots/navidrome.png)

This screenshot shows a connection timeout error encountered while attempting to access the Navidrome media server hosted within the local network.

The error indicates that the service was not responding on the specified IP address and port, suggesting a potential issue with container status, port configuration, or network accessibility.

This scenario was used to troubleshoot service availability, verify container health, and diagnose network-related issues within the homelab environment.

