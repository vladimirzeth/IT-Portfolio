# Ticket #MM-001 – Unable to Access Server Remotely

- Status: Resolved
- Priority: High
- Category: Network / Application

## Issue Description

The Mattermost server was accessible within the local network but could not be accessed remotely.

## Environment
 Platform: TrueNAS SCALE
 Service: Mattermost (Docker container)
 Remote Access: Tailscale

## Symptoms
Accessible locally via IP and port
Remote connection attempts fail

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

Successfully accessed Mattermost remotely.

## Lessons Learned

Always isolate whether the issue is network-related or application-related before troubleshooting deeper.
