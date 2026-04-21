# OpenClaw: Your Terminal That Texts Back 🦞

---

## Slide 1: Title

# OpenClaw

### *"In Her, Samantha wasn't an app. She lived inside the OS — always there, everywhere, through any screen."*

**Your Terminal That Texts Back**

**Moritz Sontheimer** | April 22, 2026

---

## Slide 1b: The Vision — Her (2013)

[Watch the clip](https://www.youtube.com/watch?v=dJTU48_yghs)

The movie predicted it. OpenClaw builds it.

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
## Slide 5: The Buzz

### Fastest growing open-source project? 👀

![Star History](images/star-history.jpg)

OpenClaw went from 0 to 180K GitHub stars in weeks. That's the vertical line. 😄

**Deep-dive by Paolo (Axiom):** https://ppaolo.substack.com/p/openclaw-system-architecture-overview

---

   - `/build`, `/deploy`, `/test` — done

3. **Multi-agent Routing**
   - Different agents for different contexts
   - Work agent | Personal agent | Project agents

4. **Mobile Dev Machine**
   - Your phone → remote dev environment
   - Run commands, check logs, push code

---

## Slide 6: Live Demo 1 - Research

### "Show me the latest OpenClaw features"

**(DEMO TIME - Live command)**

```
web_search: "OpenClaw AI agent features 2026"
web_fetch: First result → summarize
```

---

## Slide 7: Live Demo 2 - Git Workflow

### "Add a feature, commit, push — from chat"

**(DEMO TIME - Live command)**

1. Write a new file
2. `git add .`
3. `git commit -m "Add feature"`
4. `git push`

---

## Slide 8: Live Demo 3 - Cron Jobs

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

## Slide 9: System Architecture

![System Architecture](images/system-architecture.jpg)

- **Gateway** — single source of truth
- **Channel plugins** — each chat app
- **Sessions** — isolated per sender
- **Tools** — shell, git, browser, cron

---

## Slide 10: Extensibility through Plugins

![Plugin Architecture](images/plugins-architecture.jpg)

Extend without modifying core code:

- **Channel plugins** — Teams, Matrix, Mattermost
- **Memory plugins** — vector stores, knowledge graphs
- **Tool plugins** — custom capabilities beyond bash/browser
- **Provider plugins** — custom LLM providers, self-hosted models

Plugin discovery via `openclaw.extensions` in package.json, validated against TypeBox schemas, hot-loaded when configured.

---

## Slide 11: Security

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

## Slide 12: System Prompt Architecture

![System Prompt Architecture](images/system-prompt-arch.jpg)

How OpenClaw builds context for the model:

- **Workspace Files** — AGENTS.md, SOUL.md, TOOLS.md
- **Dynamic Context** — Session history, Skills, Memory search
- **Tool Definitions** — Built-in + Plugin tools
- **Base System** — Pi Agent core instructions

Final Prompt = System Prompt + Conversation History + User Message → Model Invocation

---

## Slide 13: Meet Pi — The Agent Behind It All

### The agent powering OpenClaw

**Built by Infellip** — the core AI runtime

- Agent-native design — tools, memory, reasoning
- Persistent context — remembers your workspace
- Multi-model support — Claude, GPT, local models

**Why it matters:** Pi is designed from the ground up for agentic workflows — tool use, memory search, session management, and streaming responses. This is what makes OpenClaw different from a chatbot — it's an agent that acts.

**Fun fact:** "Pi" = Personal Intelligence — your agent, your context, your tools.

---

## Slide 14: End-to-End Message Flow

![End-to-End Flow](images/end2end-flow.jpg)

From user message to response:

1. User → Channel Adapter → Gateway
2. Access Control validates permissions
3. Session Manager loads context
4. Agent Runtime builds prompt
5. Model API processes request
6. Tool Executor runs tools if needed
7. Session saves state
8. Response streams back to user

---

## Slide 15: Latency Breakdown

### Where the time goes

| Step | Latency |
|------|---------|
| Access Control | <10ms |
| Session Load | <50ms |
| Prompt Assembly | <100ms |
| First Token (Model) | 200-500ms |
| Tool: Bash | <100ms |
| Tool: Browser | 1-3s |

**Key:** Most steps are fast. Bottleneck = model inference + browser automation.

---

## Slide 16: Multi-Agent Routing

![Multi-Agent Routing](images/multi-agent-routing.jpg)

Different channels → different agents:

- **WhatsApp DM** → main session (Claude Opus)
- **Discord Group** → discord bot (Claude Sonnet)
- **Telegram DM** → support agent (GPT-4o)

Each agent has its own workspace (AGENTS.md, SOUL.md, skills), isolated sessions, route by channel/group/user.

---

## Slide 17: Get Started

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

## Slide 18: What it Costs

### Running your own AI gateway

| Component | Cost |
|-----------|------|
| **OpenClaw** | Free (self-hosted) |
| **Infrastructure** | ~€15/mo (Railway hobby) |
| **Your machine** | Already paid for |

- OpenClaw itself = free
- AI models = bring your own API key
- Hosting = cheap ($5-20/mo) or use your existing machine

---

## Slide 19: State Management

![State Management](images/state-management.jpg)

How OpenClaw stores persistent data:

- **Workspace** — AGENTS.md, SOUL.md, TOOLS.md, skills/
- **Config** — ~/.openclaw/openclaw.json
- **Credentials** — ~/.openclaw/credentials/
- **Sessions** — ~/.openclaw/sessions/
- **Memory** — ~/.openclaw/memory/*.db

---

## Slide 20: Resources

### Links & Plugins

- Docs: docs.openclaw.ai
- GitHub: github.com/openclaw/openclaw
- Discord: discord.gg/clawd
- Skills: clawhub.com

**Plugins:** WhatsApp, Signal, iMessage, Slack, Google Chat, Mattermost

**Deep-dive by Paolo (Axiom):** https://ppaolo.substack.com/p/openclaw-system-architecture-overview

---

## Slide 21: What's Next? (Outlook)

### OpenClaw is growing fast

**[nanoclaw.dev](https://nanoclaw.dev/)** — The hosted version (zero config)

**OpenClaw (Self-hosted):** Full control, bring your own API keys, free & open source

**NanoClaw (Hosted):** Zero config, pay per usage, managed by the team — coming soon

---

## Slide 22: Call to Action

### Try it now

1. `npm install -g openclaw@latest`
2. `openclaw onboard`
3. Message your gateway

**Your terminal just learned to text back.**

---

## Slide 23: Q&A

### Questions?

![LinkedIn QR](images/linkedin-qr.png)

**Let's connect!** — linkedin.com/in/moritzsontheimer

_Live demo powered by Clawdia 🦞_