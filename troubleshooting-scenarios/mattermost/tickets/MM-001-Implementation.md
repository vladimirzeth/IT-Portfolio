# MM-001 – System Implementation Details (Mattermost to Google Calendar Sync)

## Overview
This document provides a detailed walkthrough of the implemented solution used to overcome the Mattermost mobile limitation and enable full task and calendar management.

---

## Mobile vs Web Context

### 📱 Mobile Limitation (Mattermost App)
The Mattermost mobile application does not support Board functionality, preventing users from managing tasks directly.

<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-mobile.png?raw=true" width="300"/>

---

### 💻 Web Functionality (Mattermost Desktop)
The Board feature is fully accessible on the web/desktop version of Mattermost.

<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web.png?raw=true" width="500"/>
<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-board.png?raw=true" width="500"/>

---

## System Workflow

Mattermost Slash Command → Bot → Secure URL → HTML UI → n8n Workflow → Google Calendar API

---

## Step-by-Step Implementation

### ⚡ 1. Slash Command Trigger
Users initiate the workflow using a custom Mattermost slash command.

<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-slash-command.png?raw=true" width="500"/>

---

### 🔐 2. Secure Link via Bot (Expires in 30 Minutes)
A bot responds with a time-limited URL (valid for 30 minutes), ensuring secure access.

<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-slash-url.png?raw=true" width="500"/>

---

### 🌐 3. HTML Web Interface
Users are redirected to a custom-built interface that enables full task management.

<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-webUI.png?raw=true" width="500"/>

---

## Core Functionalities

### ➕ Create Task
Users can:
- Enter task title  
- Select status via dropdown  
- Assign committees through checkboxes  
- Set date  
- Assign responsible individuals  
- Add task descriptions  

<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web-create.png?raw=true" width="500"/>

---

### ✏️ Update Task
Users can search for an existing task by title and modify its details.

<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web-Update.png?raw=true" width="500"/>

---

### ❌ Delete Task
Users can remove tasks by searching the task title and confirming deletion.

<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web-delete.png?raw=true" width="500"/>

---

### 👁️ View Tasks
Users can filter and view tasks within a selected date range.

<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web-view.png?raw=true" width="500"/>

---

### 🔄 Sync to Google Calendar
Tasks are synchronized to Google Calendar based on a selected time range.

<img src="https://github.com/vladimirzeth/IT-Portfolio/blob/main/troubleshooting-scenarios/mattermost/tickets/screenshots/mattermost-web-sync.png?raw=true" width="500"/>

---

## Summary
This solution bridges the gap between Mattermost Boards and Google Calendar by introducing an automated workflow and a secure web interface, enabling full task management even on mobile devices where native support is unavailable.
