# OpenClaw Antigravity + Discord

This repository contains the optimized configuration for **OpenClaw**, a personal AI assistant. It is pre-configured to use **Google Antigravity** models via the **Antigravity Auth** plugin, enabling advanced capabilities like **Free Google Search** and access to multiple frontier AI models.

**Key Feature**: Control your AI agent via Discord commands, powered by Google Antigravity (free with Google Cloud subscription).

## ✨ Features

- **Multi-Model Support**: Access to 7 frontier AI models via Google Antigravity
- **Primary Model**: `google-antigravity/gemini-3-flash` (fast, efficient)
- **Fallback Models**: Gemini 3 Pro, Claude Sonnet 4.5
- **Authentication**: Keyless search using the Google Antigravity Auth plugin
- **Channels**: Pre-configured for **Telegram** and **Discord** bot integration
- **Tools**: Enabled `google-search` and `web_fetch` for comprehensive research
- **Discord Control**: Full Discord action support (messages, reactions, threads, polls, etc.)

## 🤖 Available Models

All models are available through Google Antigravity at **no additional cost** (with Antigravity Pro subscription):

| Model | Alias | Best For |
|-------|-------|----------|
| `google-antigravity/gemini-3-flash` | Gemini 3 Flash | Fast responses, UI generation, real-time interactions |
| `google-antigravity/gemini-3-pro` | Gemini 3 Pro | Complex reasoning, code generation, detailed analysis |
| `google-antigravity/gemini-3-pro-thinking` | Gemini 3 Pro (Thinking) | Deep reasoning with extended thinking |
| `google-antigravity/claude-sonnet-4-5` | Claude Sonnet 4.5 | Balanced speed/quality, concise responses |
| `google-antigravity/claude-sonnet-4-5-thinking` | Claude Sonnet 4.5 (Thinking) | Extended reasoning with Claude |
| `google-antigravity/claude-opus-4-5-thinking` | Claude Opus 4.5 (Thinking) | Most capable Claude model, complex tasks |
| `google-antigravity/gpt-oss` | GPT-OSS | OpenAI's open-source model (GPT-OSS-120B) |

### Switching Models

You can switch models in the config or via Discord command:
- Edit `agents.defaults.model.primary` in your config
- Or ask the bot: "Switch to Claude Opus for this task"

## 🎮 Discord Control Capabilities

Send commands to your OpenClaw bot via Discord and it will execute them using Google Antigravity:

- **Search the web**: Ask questions and get AI-powered answers with Google Search
- **Send messages**: Control Discord channels programmatically
- **React to messages**: Add reactions to any message
- **Create polls**: Run polls in channels
- **Manage threads**: Create and reply to threads
- **Pin messages**: Pin important messages
- **Search messages**: Search through channel history
- **And more**: Member info, role info, channel info, voice status, events

### Example Commands (via Discord DM or mention)

```
"Search for the latest news about AI"
"Send a message to #general saying hello"
"Create a poll in #team asking about lunch options"
"React with 👍 to the last message in #announcements"
"Pin the message about the release in #releases"
```

## 🚀 Setup Instructions

### 1. Installation

Ensure you have [Node.js](https://nodejs.org/) installed, then install OpenClaw globally:

```bash
npm install -g openclaw
```

### 2. Configuration

1. Copy the `openclaw.json.template` to your OpenClaw configuration directory (usually `~/.openclaw/openclaw.json` or `%USERPROFILE%\.openclaw\openclaw.json`).
2. Configure your bot tokens:
   - **Telegram**: Update `botToken` in `channels.telegram` with your Telegram Bot Token (from [@BotFather](https://t.me/BotFather))
   - **Discord**: Update `token` in `channels.discord` with your Discord Bot Token (from [Discord Developer Portal](https://discord.com/developers/applications))

#### Discord Bot Setup

1. Go to the [Discord Developer Portal](https://discord.com/developers/applications)
2. Create a new application and add a Bot
3. Enable the following **Privileged Gateway Intents**:
   - `MESSAGE CONTENT INTENT` (required to read messages)
   - `SERVER MEMBERS INTENT` (optional, for member info)
4. Copy the bot token and paste it into `channels.discord.token`
5. Invite the bot to your server using OAuth2 URL Generator with `bot` scope and these permissions:
   - Send Messages
   - Read Message History
   - Add Reactions
   - Manage Messages (for pins)
   - Create Public Threads
   - Send Messages in Threads
   - Use External Emojis

### 3. Antigravity Authentication

The most important step is to link your Google account to enable the **Gemini 3** models and the **Free Google Search tool**.

Run the following command:

```bash
openclaw models auth login --provider google-antigravity
```

Follow the browser prompts to sign in with your Google account. Once complete, your agent will have full search and reasoning capabilities.

### 4. Running the Gateway

Start the OpenClaw gateway to enable both Telegram and Discord bots:

```bash
openclaw gateway run
```

## 🔧 Channel Configuration

### Telegram Options

| Option | Description |
|--------|-------------|
| `botToken` | Your Telegram bot token |
| `dmPolicy` | `"pairing"` (require approval), `"allowlist"`, or `"open"` |
| `groupPolicy` | `"allowlist"` or `"open"` |
| `streamMode` | `"partial"` or `"full"` |

### Discord Options

| Option | Description |
|--------|-------------|
| `token` | Your Discord bot token |
| `dm.policy` | `"pairing"` (require approval), `"allowlist"`, or `"open"` |
| `dm.allowFrom` | Array of allowed Discord user IDs |
| `groupPolicy` | `"allowlist"` or `"open"` |
| `guilds` | Per-guild channel configuration |
| `actions.*` | Enable/disable specific Discord actions |

### Discord Actions Configuration

Control which Discord actions the bot can perform:

```json
{
  "channels": {
    "discord": {
      "actions": {
        "reactions": true,      // React to messages
        "messages": true,       // Send/edit/delete messages
        "threads": true,        // Create/manage threads
        "pins": true,           // Pin/unpin messages
        "search": true,         // Search messages
        "polls": true,          // Create polls
        "permissions": true,    // Check bot permissions
        "memberInfo": true,     // Get member info
        "roleInfo": true,       // Get role info
        "channelInfo": true,    // Get channel info
        "voiceStatus": true,    // Check voice status
        "events": true,         // List scheduled events
        "stickers": true,       // Send stickers
        "emojiUploads": false,  // Upload custom emojis (disabled by default)
        "stickerUploads": false,// Upload stickers (disabled by default)
        "roles": false,         // Add/remove roles (disabled by default)
        "channels": false,      // Create/edit/delete channels (disabled by default)
        "moderation": false     // Timeout/kick/ban (disabled by default)
      }
    }
  }
}
```

## 🛠 Project Structure

- `openclaw.json.template`: The core configuration file with optimized settings
- `extensions/discord/`: Discord channel plugin
- `extensions/telegram/`: Telegram channel plugin
- `extensions/google-antigravity-auth/`: Google Antigravity authentication plugin
- `skills/discord/`: Discord action skill (send messages, react, polls, etc.)

## 💰 Cost

**$0** - This setup uses Google Antigravity which is available in free public preview. All 7 models (Gemini 3 Pro/Flash, Claude Sonnet 4.5, Claude Opus 4.5, GPT-OSS) and Google Search are included with generous rate limits.

**Rate Limits**: Google provides "generous rate limits" that refresh periodically. Heavy multi-agent automation may consume quotas quickly. For higher limits, consider Google AI Pro or Ultra subscriptions.

## 📝 License

MIT
