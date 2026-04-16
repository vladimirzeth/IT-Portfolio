# Ticket #MM-001 – Mattermost Board to Google Calendar Sync Limitation (Mobile Access Issue)

- **Status**: Resolved (via Automation Workaround)  
- **Priority**: High  
- **Category**: Integration / Automation  

---

## Issue Description
Users are unable to create, update, delete, or sync calendar events from the Mattermost Board when using the mobile application. The mobile version of Mattermost does not support Board functionality, resulting in a workflow limitation for event management on-the-go.

---

## Environment
- **Platform**: Mattermost (Desktop + Mobile)  
- **Automation Tool**: n8n  
- **Integration**: Google Calendar API  
- **UI Layer**: Custom HTML Web Interface  
- **Data Source**: Mattermost Board  

---

## Symptoms
- Mattermost mobile app does not display Board feature  
- Users cannot create or manage events via mobile  
- No direct Google Calendar integration from Board  
- Manual event syncing required prior to fix  

**Figure: Mattermost Mobile Application (Board Feature Not Available)**

  <img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-mobile.png?raw=true" width="500"/>

---

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


---

## Root Cause
Mattermost mobile application does not support Board functionality, and there is no native integration between Mattermost Boards and Google Calendar.

---

## Resolution
Implemented an automation workflow using n8n combined with a custom HTML web interface to enable full task management (Create, Update, Delete, View, Sync) and integration with Google Calendar.

This solution bypasses the limitation of the Mattermost mobile application by providing a browser-accessible interface with secure, time-limited access.

---

## Architecture Overview
The system follows this workflow:

Mattermost Slash Command → Bot → Secure URL → HTML UI → n8n Workflow → Google Calendar API

This design ensures secure, time-limited access and seamless synchronization between Mattermost and Google Calendar.

---

## Solution Walkthrough
The following section demonstrates how the system works end-to-end, including the mobile limitation and the implemented workaround.

---

## Implementation Details (HTML Web Interface)

### Mobile Limitation (Mattermost App)
The Mattermost mobile application does not support Board functionality, preventing users from managing tasks directly.

<img src="YOUR_MOBILE_SCREENSHOT_1" width="300"/>
<img src="YOUR_MOBILE_SCREENSHOT_2" width="300"/>

---

### ⚡ Slash Command Trigger
Users initiate the workflow using a custom Mattermost slash command.

<img src="YOUR_SLASH_COMMAND_IMAGE" width="500"/>

---

### 🔐 Secure Link via Bot (Expires in 30 Minutes)
A bot responds with a time-limited URL (valid for 30 minutes), ensuring secure access to the system.

<img src="YOUR_BOT_LINK_IMAGE" width="500"/>

---

### 🌐 HTML Web Interface
Users are redirected to a custom-built interface that allows full task management.

<img src="YOUR_WEB_UI_IMAGE_MAIN" width="500"/>

---

### ➕ Create Task
Users can:
- Enter task title  
- Select status via dropdown  
- Assign committees through checkboxes  
- Set date  
- Assign responsible individuals  
- Add task descriptions  

<img src="YOUR_CREATE_IMAGE" width="500"/>

---

### ✏️ Update Task
Users can search for an existing task by title and modify its details.

<img src="YOUR_UPDATE_IMAGE" width="500"/>

---

### ❌ Delete Task
Users can remove tasks by searching the task title and confirming deletion.

<img src="YOUR_DELETE_IMAGE" width="500"/>

---

### 👁️ View Tasks
Users can filter and view tasks within a selected date range.

<img src="YOUR_VIEW_IMAGE" width="500"/>

---

### 🔄 Sync to Google Calendar
Tasks are synchronized to Google Calendar based on a selected time range.

<img src="YOUR_SYNC_IMAGE" width="500"/>

---

## Verification
- Events successfully created and reflected in Google Calendar  
- Updates and deletions correctly synced  
- Workflow accessible via mobile browser  
- Mattermost Board data properly mapped to calendar events  

<img src="YOUR_GOOGLE_CALENDAR_SCREENSHOT" width="500"/>

---

## Lessons Learned
Mobile feature limitations in collaboration tools can significantly disrupt workflows, but API-driven automation (e.g., n8n + Google Calendar API) can effectively bridge missing native functionality. Web-based UI layers are a practical workaround when mobile clients lack feature parity.

## Lessons Learned
Mobile feature limitations in collaboration tools can significantly disrupt workflows, but API-driven automation (e.g., n8n + Google Calendar API) can effectively bridge missing native functionality. Web-based UI layers are a practical workaround when mobile clients lack feature parity.
