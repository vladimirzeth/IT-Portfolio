# Ticket ID: HD-005
## User Information
- Name: Home Lab Admin
- Role: System Administrator
- Platform: Mattermost
## Assigned To
- Infrastructure Admin
---
## Environment
- OS: TrueNAS SCALE
- Platform: Mattermost (Docker)
- Automation Tool: n8n
- Integration: Google Calendar API
- UI Layer: Custom HTML Web Interface
- Network: Local Network + Cloudflare Tunnel

---
## Issue Summary
Mattermost mobile application does not support Boards functionality, preventing users from creating, updating, deleting, or syncing tasks and calendar events on mobile devices.

---
## Business Impact
- Users unable to manage tasks or events from mobile
- No native Google Calendar integration from Mattermost Boards
- Manual event syncing required as temporary workaround
- Workflow disruption for mobile-dependent users
---
## Category
- Integration / Automation
- Application Limitation
---
## Priority
- Level: High
- Impact: Core task and calendar management unavailable on mobile
- Urgency: High - affects daily team workflow
---
## Initial Diagnosis
- Confirmed Mattermost mobile app does not render Boards interface
- Tested event creation workflow on mobile vs desktop — desktop functional, mobile not
- Confirmed absence of native Google Calendar integration from Boards
- Server-side Boards data intact — limitation is client-side only
- API-based automation identified as the appropriate resolution path
---
## Troubleshooting Steps
1. Verified Mattermost mobile app feature limitations — Boards not supported on mobile client
2. Tested event creation workflow on mobile vs desktop to reproduce and document the gap
3. Confirmed no native Google Calendar integration exists within Mattermost Boards
4. Evaluated possible API-based integration approaches
5. Implemented automation prototype using n8n as the middleware layer
6. Built custom HTML web interface for full CRUD task operations
7. Configured Mattermost bot to generate secure, time-limited links (30-minute expiry) via slash command
8. Connected full pipeline: Mattermost Board → n8n Workflow → Google Calendar API
9. Validated end-to-end on both mobile browser and desktop
---
## Tools / Commands Used
- Mattermost Slash Commands (custom bot configuration)
- n8n Workflow Automation
- Google Calendar API
- HTML/CSS (custom web interface)
- Cloudflare Tunnel (secure external access)
---
## Resolution
Implemented an n8n-based automation workflow with a custom HTML web interface to enable full task management and Google Calendar synchronization. The solution bypasses mobile client limitations by providing a secure, browser-accessible interface triggered via Mattermost slash command.

**Solution Architecture:**
**Implemented Features:**
- Create Task - title, status, committee assignment, date, assigned users, description
- Update Task - search and modify existing task details
- Delete Task - remove tasks via web interface
- View Tasks - filter and view tasks by date range
- Sync to Google Calendar - synchronize selected tasks to calendar

**Verification:**
- Events successfully created and reflected in Google Calendar
- Updates and deletions correctly synced
- Workflow accessible via mobile browser
- Mattermost Board data properly mapped to calendar events
---
## Root Cause & User Explanation
The Mattermost mobile application does not support Boards at the client level, and no native Google Calendar integration exists. Rather than waiting for an upstream fix, a custom automation layer was built to bridge the gap - enabling full task management through a secure web interface accessible from any device including mobile.

For full implementation walkthrough and screenshots, see: [Implementation Details](./MM-001-Implementation.md)

---
## Time to Resolution
- ~3–5 hours (design, development, and validation)
## Status
Closed
---
## Lessons Learned
- Mobile feature limitations in collaboration tools can disrupt workflows but can be effectively bridged through API-driven automation
- n8n is a practical middleware for integrating services that lack native mobile support
- Secure, time-limited links are an effective way to expose internal tools without permanent external access
- Web-based UI layers provide a reliable workaround when mobile clients lack feature parity with desktop
---
## Evidence / Screenshots

### Mattermost Mobile — Board Feature Not Available
<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-mobile.png?raw=true" width="300"/>

### Mattermost Web Interface — Board Functionality
<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web.png?raw=true" width="500"/>
<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-board.png?raw=true" width="500"/>
