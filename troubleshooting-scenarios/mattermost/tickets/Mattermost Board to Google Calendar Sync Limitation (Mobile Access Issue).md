# Ticket #MM-001 – Mattermost Board to Google Calendar Sync Limitation (Mobile Access Issue)
- **Status**: Resolved (via Automation Workaround)
- **Priority**: High
- **Category**: Integration / Automation

## Issue Description
Users are unable to create, update, delete, or sync calendar events from the Mattermost Board when using the mobile application. The mobile version of Mattermost does not support Board functionality, resulting in a workflow limitation for event management on-the-go.

## Environment
- **Platform**: Mattermost (Desktop + Mobile)
- **Automation** Tool: n8n
- **Integration**: Google Calendar API
- **UI Layer**: Custom HTML Web Interface
- **Data Source**: Mattermost Board



## Symptoms
- Mattermost mobile app does not display Board feature
- Users cannot create or manage events via mobile
- No direct Google Calendar integration from Board
- Manual event syncing required prior to fix


  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-mobile.png?raw=true" width="500" height="750"/>



## Troubleshooting Process

1. Verified Mattermost mobile app feature limitations (Board not supported)
2. Tested event creation workflow on mobile vs desktop
3. Confirmed absence of native Google Calendar integration
4. Evaluated possible API-based integration approaches
5. Implemented automation prototype using n8n
6. Built HTML-based web UI for CRUD operations
7. Connected Mattermost Board → n8n workflow → Google Calendar API

**Figure: Mattermost Web Interface and Board Functionality**

  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web.png?raw=true" width="500"/>
  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-board.png?raw=true" width="500"/>



## Root Cause
Mattermost mobile application does not support Board functionality, and there is no native integration between Mattermost Boards and Google Calendar.

## Resolution
Implemented an automation workflow using n8n combined with a custom HTML web interface to enable full task management (Create, Update, Delete, View, Sync) and integration with Google Calendar.

This solution bypasses the limitation of the Mattermost mobile application by providing a browser-accessible interface with secure, time-limited access.
- Create event
- Update event
- Delete event
- Sync events to Google Calendar

### HTML WEB VERSION
**Slash Command Trigger**
- Initiates the workflow using a custom Mattermost slash command, allowing users to request access to the task management interface.
  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-slash-command.png?raw=true" width="500"/>

**Secure Link via Bot (Expires in 30 Minutes)**
- The slash command triggers a bot that sends a time-limited access link (valid for 30 minutes) to ensure secure interaction with the system.
  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-slash-url.png?raw=true" width="500"/>

**HTML Web UI Dashboard**
- Upon accessing the link, users are redirected to a custom-built HTML interface where they can manage tasks through Create, Update, View, Delete, and Sync functionalities.
  
  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-webUI.png?raw=true" width="500"/>

**Create Task**
  Users can create tasks by:
  - Entering a task title
  - Selecting status via dropdown
  - Assigning committees through checkboxes
  - Setting date
  - Assigning responsible individuals
  - Adding task descriptions

  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web-create.png?raw=true" width="500"/>

**Update Task**
- Users can search for an existing task by title and modify its details, enabling flexible task management and updates.
  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web-Update.png?raw=true" width="500"/>

**Delete Task**
- Allows users to remove tasks by simply searching for the task title and confirming deletion.
  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web-delete.png?raw=true" width="500"/>

**View Tasks**
- Users can filter and view tasks within a selected date range by specifying a start and end date.
  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web-view.png?raw=true" width="500"/>

**Sync to Google Calendar**
- Enables synchronization of tasks to Google Calendar based on a selected time range, ensuring alignment between Mattermost Boards and calendar events.
  
  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web-sync.png?raw=true" width="500"/>



This bridges the gap between Mattermost Boards and Google Calendar, allowing full event management even on mobile devices through a web-based interface.

## Verification
- Events successfully created and reflected in Google Calendar
- Updates and deletions correctly synced
- Workflow accessible via mobile browser
- Mattermost Board data properly mapped to calendar events

## Lessons Learned
Mobile feature limitations in collaboration tools can significantly disrupt workflows, but API-driven automation (e.g., n8n + Google Calendar API) can effectively bridge missing native functionality. Web-based UI layers are a practical workaround when mobile clients lack feature parity.
