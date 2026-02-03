# OpenClaw

<p align="center">
  <img src="https://raw.githubusercontent.com/usemanusai/OpenClaw/main/README-header.png" alt="OpenClaw" width="600">
</p>

**OpenClaw** is a powerful personal AI assistant with multi-platform support. This repository contains the full OpenClaw codebase pre-configured with **Google Antigravity** models and **Discord/Telegram** integration.

## ✨ Features

- **Multi-Model Support**: Access to 7 frontier AI models via Google Antigravity
- **Multi-Platform**: iOS, Android, macOS native apps + CLI
- **Channel Integrations**: Discord, Telegram, Slack, WhatsApp, Signal, Matrix, and more
- **Skills System**: Extensible skills for GitHub, Notion, Apple Notes, Spotify, and 50+ integrations
- **Voice Assistant**: Swabble voice assistant integration
- **Free Google Search**: Keyless search using Google Antigravity Auth plugin

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

## 🎮 Discord Control Capabilities

Send commands to your OpenClaw bot via Discord:

- **Search the web**: AI-powered answers with Google Search
- **Send messages**: Control Discord channels programmatically
- **React to messages**: Add reactions to any message
- **Create polls**: Run polls in channels
- **Manage threads**: Create and reply to threads
- **Pin messages**: Pin important messages
- **And more**: Member info, role info, channel info, voice status, events

### Example Commands (via Discord DM or mention)

```
"Search for the latest news about AI"
"Send a message to #general saying hello"
"Create a poll in #team asking about lunch options"
"React with 👍 to the last message in #announcements"
```

## 🚀 Quick Start

### 1. Installation

```bash
npm install -g openclaw
```

### 2. Configuration

1. Copy `openclaw.json.template` to `~/.openclaw/openclaw.json`
2. Configure your bot tokens:
   - **Telegram**: Update `botToken` in `channels.telegram`
   - **Discord**: Update `token` in `channels.discord`

### 3. Antigravity Authentication

Link your Google account to enable Gemini 3 models and free Google Search:

```bash
openclaw models auth login --provider google-antigravity
```

### 4. Run the Gateway

```bash
openclaw gateway run
```

## 📁 Project Structure

```
├── apps/                    # Native applications
│   ├── android/            # Android app
│   ├── ios/                # iOS app
│   └── macos/              # macOS app
├── extensions/             # Channel plugins
│   ├── discord/            # Discord integration
│   ├── telegram/           # Telegram integration
│   ├── slack/              # Slack integration
│   ├── whatsapp/           # WhatsApp integration
│   ├── signal/             # Signal integration
│   └── ...                 # 25+ more channels
├── skills/                 # AI skills
│   ├── discord/            # Discord actions
│   ├── github/             # GitHub integration
│   ├── notion/             # Notion integration
│   ├── coding-agent/       # Code generation
│   └── ...                 # 50+ more skills
├── src/                    # Core source code
├── docs/                   # Documentation
├── Swabble/                # Voice assistant
└── openclaw.json.template  # Configuration template
```

## 🔧 Discord Bot Setup

1. Go to the [Discord Developer Portal](https://discord.com/developers/applications)
2. Create a new application and add a Bot
3. Enable **Privileged Gateway Intents**:
   - `MESSAGE CONTENT INTENT`
   - `SERVER MEMBERS INTENT` (optional)
4. Copy the bot token to `channels.discord.token`
5. Invite the bot with these permissions:
   - Send Messages, Read Message History, Add Reactions
   - Manage Messages (for pins), Create Public Threads
   - Send Messages in Threads, Use External Emojis

## 💰 Cost

**$0** - This setup uses Google Antigravity which is available in free public preview. All 7 models and Google Search are included with generous rate limits.

## 📝 License

MIT

---

<p align="center">
  <b>Built with ❤️ for the AI community</b>
</p>
