# OpenClaw: Your Terminal That Texts Back 🦞

---

## Slide 1: Title

# OpenClaw

### The self-hosted AI gateway that lives on your machine

**Moritz Sontheimer** | April 22, 2026

---

## Slide 2: The Problem

### What if your terminal could message back?

- AI coding agents are powerful... but stuck in the terminal
- Need to be at your keyboard to use them
- What if you could message your dev machine from anywhere?

**The gap:** Access without being at the machine

---

## Slide 3: What is OpenClaw?

### OpenClaw = Self-hosted AI gateway

- **Runs locally** — on your machine or server
- **Multi-channel** — WhatsApp, Telegram, Discord, iMessage
- **Agent-native** — built for coding agents with tool use
- **Your data, your rules** — no hosted service dependency

```
Chat apps → OpenClaw Gateway → AI Agent → Your tools
```

---

## Slide 4: Why Techies Should Care

### 4 Key Benefits

1. **Self-hosted = Control**
   - No API key leaks, no vendor lock-in
   - Your data never leaves your machine

2. **Workflow Integration**
   - Trigger scripts, automation, CI/CD from chat
   - `/build`, `/deploy`, `/test` — done

3. **Multi-agent Routing**
   - Different agents for different contexts
   - Work agent | Personal agent | Project agents

4. **Mobile Dev Machine**
   - Your phone → remote dev environment
   - Run commands, check logs, push code

---

## Slide 5: Live Demo 1 - Research

### "Show me the latest OpenClaw features"

**(DEMO TIME - Live command)**

```
web_search: "OpenClaw AI agent features 2026"
web_fetch: First result → summarize
```

---

## Slide 6: Live Demo 2 - Git Workflow

### "Add a feature, commit, push — from chat"

**(DEMO TIME - Live command)**

1. Write a new file
2. `git add .`
3. `git commit -m "Add feature"`
4. `git push`

---

## Slide 7: Live Demo 3 - Cron Jobs

### "This runs on a schedule"

**(DEMO TIME - Trigger on command)**

Cron jobs can:
- Send reminders
- Trigger builds
- Run periodic checks
- Fire any automation

```
schedule: every 1 hour
→ systemEvent delivered to chat
```

---

## Slide 8: Architecture

### How it works

```
┌─────────────────────────────────────┐
│     Chat Apps (WA, TG, Discord)       │
└─────────────────┬───────────────────┘
                  │
              [Gateway]
                  │
        ┌─────────┼─────────┐
        ▼         ▼         ▼
   [Sessions]  [Tools]  [Channels]
        │
        ▼
   [Coding Agent] → Shell, Git, Browser, etc.
```

- Single Gateway process
- Channel plugins
- Isolated sessions per sender

---

## Slide 9: Security

### Control from the start

- **Allowlists** — restrict who can access
- **Mention rules** — group chat control
- **Tokens** — per-channel API keys
- **Local-only** — your data never leaves

```json
{
  "channels": {
    "telegram": {
      "allowFrom": ["your-id"]
    }
  }
}
```

---

## Slide 10: Get Started

### One-liner install

```bash
npm install -g openclaw@latest
openclaw onboard
openclaw gateway
```

### Links

- Docs: https://docs.openclaw.ai
- GitHub: https://github.com/openclaw/openclaw
- Discord: https://discord.gg/clawd

---

## Slide 11: Call to Action

### Try it now

1. `npm install -g openclaw@latest`
2. `openclaw onboard`
3. Message your gateway

**Your terminal just learned to text back.**

---

## Slide 12: Q&A

### Questions?

- Docs: docs.openclaw.ai
- GitHub: github.com/openclaw/openclaw
- Find me: @bausparfuchs

_Live demo powered by Clawdia 🦞_