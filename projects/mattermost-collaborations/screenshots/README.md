## Screenshots

### Channel view with n8n automation
![Mattermost Channel](https://github.com/vladimirzeth/IT-Portfolio/blob/main/projects/mattermost-collaborations/screenshots/MATTERMOST-SCREENSHOT.png)

The `Board - Update / Sync` channel shows a bot (`zane_taskmanager`) automatically syncing Mattermost board tasks to Google Calendar. This bot is powered by an n8n automation workflow running on my self-hosted n8n server — triggered by a `#sync` command typed in the channel, the n8n workflow picks it up via webhook, processes the board data, and confirms each synced calendar entry back in the channel in real time.

### Boards — task management
![Mattermost Board](https://github.com/vladimirzeth/IT-Portfolio/blob/main/projects/mattermost-collaborations/screenshots/MATTERMOST-BOARD.png)

Mattermost Boards used as a personal task manager with custom properties: Status, Priority, Due Date, Area, Effort, and Recurring. Organized into energy-based categories (Today, Low Energy, Deadlines, Waiting, Backlogs). The board data is what the n8n automation reads and syncs to Google Calendar when the `#sync` command is triggered.
