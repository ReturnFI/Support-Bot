# Support Bot for Telegram

This is a Telegram support bot that runs on Cloudflare Workers. It allows users to send messages or photos, which are then forwarded to an admin. The admin can reply to users, block/unblock them, broadcast messages, and check user activity.

## ⚙️ Setup

### 💾 KV Namespace
Create a KV namespace named `RATE_LIMIT_KV` in Cloudflare Dashboard.

### 🔐 Environment Variables
Add these variables to your Worker:

| Variable | Description |
|----------|-------------|
| `BOT_TOKEN` | Your Telegram bot token from BotFather |
| `ADMIN_ID` | Your Telegram user ID (admin) |
| `RATE_LIMIT_KV` | The KV namespace binding |
| `SECRET_TOKEN` | A secret token for webhook security |
| `BOT_USER_LANGUAGE` | Language code ('EN' or 'FA') |

### 🌐 Setup Webhook
Set the webhook URL to your worker URL:
```
https://api.telegram.org/bot<BOT_TOKEN>/setWebhook?url=https://your-worker.your-subdomain.workers.dev&secret_token=<SECRET_TOKEN>
```

## 💬 Commands

| Command | Description |
|---------|-------------|
| `/reply <user_id> <message>` | Reply to a specific user |
| `/block <user_id>` | Block a user from using the bot |
| `/unblock <user_id>` | Unblock a previously blocked user |
| `/broadcast <message>` | Send a message to all active users |
| `/check` | Find and remove users who blocked the bot |

## ✨ Features

- **Two-way communication**: Users can send messages, admin can reply
- **Media support**: Send/receive photos and documents
- **User management**: Block/unblock problematic users
- **Broadcast messages**: Send announcements to all users
- **Multi-language support**: English and Persian interfaces
- **Rate limiting**: Prevents spam from users
- **Automatic cleanup**: Remove inactive users with `/check`

Just deploy the script to your Cloudflare Worker, set up variables and KV, and connect to Telegram via webhook.
