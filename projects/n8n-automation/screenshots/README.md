## Screenshots

### Board - Sync workflow
![Board Sync](https://github.com/vladimirzeth/IT-Portfolio/blob/main/projects/n8n-automation/screenshots/SYNC-WORKFLOW.png)

The most complex workflow in the system. Triggered by a webhook from Mattermost when a `#sync` command is sent, it fetches all cards from the Mattermost Board, loops through each item, retrieves the block content and formats it, then checks Google Calendar for existing events. If the event already exists it updates it, if not it creates a new one — then posts a confirmation summary back to the Mattermost channel.

### Board - Update workflow
![Board Update](https://github.com/vladimirzeth/IT-Portfolio/blob/main/projects/n8n-automation/screenshots/UPDATE-WORKFLOW.png)

Handles updating existing cards on the Mattermost Board via webhook. Parses the incoming command, searches for the target card via HTTP, compares the current block content, applies a PATCH update to the card, deletes outdated blocks, and posts the updated content back — all in a single automated chain.

### Board - Delete workflow
![Board Delete](https://github.com/vladimirzeth/IT-Portfolio/blob/main/projects/n8n-automation/screenshots/DELETE-WORKFLOW.png)

A focused webhook-triggered workflow that receives a delete command from Mattermost, parses the card name, searches the board for the matching card via HTTP, and sends a DELETE request to remove it — keeping the board clean through a simple chat command.

### Task Creator workflow
![Task Creator](https://github.com/vladimirzeth/IT-Portfolio/blob/main/projects/n8n-automation/screenshots/TASK-CREATOR-WORKFLOW.png)

Receives a webhook trigger and uses JavaScript to parse the incoming task data. Branches based on an If condition — creates a new card on the Mattermost Board via HTTP POST if it's a new task, then merges both paths, aggregates the result, formats it with JavaScript, and sends a final confirmation request back to the channel.

### AI Agent Zane — Telegram assistant
![AI Agent Telegram](https://github.com/vladimirzeth/IT-Portfolio/blob/main/projects/n8n-automation/screenshots/AI-AGENT-TELEGRAM.png)

A personal AI assistant connected to Telegram. When a message arrives, it checks whether it is a voice message or text — if voice, it downloads the audio file and transcribes it using OpenAI's transcription API before processing. The message (text or transcribed) is passed into an AI Agent powered by an OpenAI Chat Model with simple memory for context. The agent has four tools available: Event Creator, Event Checker, Event Updater, and Event Terminator — allowing it to fully manage Google Calendar through natural conversation. Errors are caught and reported back to Telegram automatically.
