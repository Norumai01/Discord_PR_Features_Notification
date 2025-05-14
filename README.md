# Test Update Workflow with Discord Notifications

## Overview
This project implements a workflow for tracking test updates with automatic Discord notifications. When pull requests are merged into the main branch, a notification is sent to a Discord channel with details about the update.

## Setting Up the Discord Notification Workflow

### Prerequisites
- GitHub account
- Discord server with permissions to create webhooks
- Basic understanding of Git and GitHub

### Discord Webhook Setup
1. In your Discord server, go to the channel where you want to receive notifications
2. Click the gear icon (Edit Channel)
3. Go to "Integrations" > "Webhooks" > "Create Webhook"
4. Name your webhook (e.g., "GitHub Updates")
5. Copy the webhook URL

### GitHub Repository Setup
1. In your GitHub repository, go to "Settings" > "Secrets and variables" > "Actions"
2. Create a new repository secret:
    - Name: `DISCORD_WEBHOOK`
    - Value: [Paste your Discord webhook URL]

## Using the Workflow

### Creating Effective Pull Requests
1. Create a pull request to merge your branch into main
2. Use the provided PR template (`.github/pull_request_template.md`)
3. Fill out the template with your changes:
    - Use checkboxes `- [x]` for completed items
    - Use unchecked boxes `- [ ]` for incomplete items
    - List your additions, modifications, and removals

Example PR description:
```
**Descriptive title here**

**Addition (Add or remove as needed)**
- [x] Add feature X
- [x] Add documentation for Y

**Modification (Add or remove as needed)**
- Change layout in Z

**Remove (Add or remove as needed)**
- [ ] Remove deprecated function
```

### Pull Request Merging and Notification
1. When your PR is approved and merged to main, the GitHub Action will automatically:
    - Trigger the `discord_notification.yml` workflow
    - Send a formatted notification to your Discord channel
    - Include PR details, changes made, and author information

## How the Discord Notification Works
The Discord notification workflow:
- Triggers when PRs are merged to the main branch
- Converts PR template checkboxes to ✅ and ❌ emojis
- Creates a formatted Discord embed with:
    - Title and description from the PR
    - PR description as formatted text
    - Author information
    - Statistics about files changed, additions, and deletions
    - Link to the PR

### Screenshot Demo
![Screenshot-Demo](/assets/Screenshot_demo.png "Screenshot Demo")


## Project Structure
- `.github/workflows/discord_notification.yml` - GitHub Action for Discord notifications
- `.github/pull_request_template.md` - Template for standardized PRs

## Troubleshooting
- If notifications aren't working:
    1. Check that the `DISCORD_WEBHOOK` secret is correctly set
    2. Verify webhook URL is valid in Discord
    3. Ensure that PRs are being merged (not just closed)
    4. Check Action logs in GitHub for any errors

