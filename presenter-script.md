# OpenClaw Talk — Presenter Script
## Moritz Sontheimer | April 22, 2026

---

## Slide 1: Title (~30 sec)

**Hook opener:**
> "In the movie Her, Samantha wasn't an app. She lived inside the OS — always there, everywhere, through any screen."

Pause for effect. Let that sink in.

> "That movie came out in 2013. For over a decade, we thought this was science fiction. Then, eight weeks ago, something changed."

**Transition:** "Let me show you what changed — and why it matters for developers like us."

---

## Slide 1b: Her Movie Clip (~1-2 min)

**While video plays:** Let the clip run. Don't explain yet.

**After clip:**
> "The movie predicted it. OpenClaw builds it. Not a full Samantha — but the foundation. A persistent, context-aware AI agent that lives on your machine, accessible from anywhere, through any chat app you already use."

---

## Slide 2: The Problem (~1 min)

**Say:**
> "Here's what we deal with every day. AI coding agents are incredibly powerful — but they're stuck in the terminal. You're at your keyboard, you're at your laptop. What if you're on a flight? What if it's 3am and your production server is on fire?"

**Click through:**
- AI agents are powerful... but stuck in the terminal
- Need to be at your keyboard to use them
- What if you could message your dev machine from anywhere?

**Transition:** "This is the gap OpenClaw fills."

---

## Slide 3: What is OpenClaw? (~1 min)

**Say:**
> "OpenClaw is a self-hosted AI gateway. Think of it as the layer between your chat apps and your AI agent — running locally on your machine, 24/7, ready when you are."

**Quick demo moment (optional):** Pull up your phone, send a message to your gateway, show the response appearing.

**Key points:**
- Runs locally — on your machine or server
- Multi-channel — WhatsApp, Telegram, Discord, iMessage
- Agent-native — built for coding agents with tool use
- Your data, your rules — no hosted dependency

---

## Slide 4: Why Techies Should Care (~1 min)

**Say:**
> "Four reasons this matters for developers like us."

**Go through table:**
1. **Self-hosted = Control** — No API key leaks. No vendor lock-in. Your data never leaves your machine.
2. **Workflow Integration** — Trigger scripts, CI/CD, builds from chat. `/build`, `/deploy`, `/test` — done.
3. **Multi-agent Routing** — Different agents for different contexts. Work agent, personal agent, project agents.
4. **Mobile Dev Machine** — Your phone becomes a remote dev environment. Run commands, check logs, push code.

**Transition:** "But don't just take my word for it..."

---

## Slide 5: The Buzz (~1 min)

**Say:**
> "In just eight weeks, OpenClaw went from zero to 180,000 GitHub stars. Yes — that vertical line is real. It became one of the fastest-growing open-source projects in history."

**Point to the chart:**
> "This is from star-history.com. The blue line is React. The yellow is Vue. The pink is Linux. The green is Next.js. And the red vertical line is OpenClaw."

**Mention:**
> "Peter Steinberger, the creator, went from a weekend WhatsApp relay script to 700+ people at ClawCon in SF. Ashton Kutcher was there asking for demos. Andrej Karpathy called it 'the most incredible sci-fi takeoff-adjacent thing I've seen.'"

**Deep dive source:** "If you want the full technical breakdown, Paolo from Axiom wrote an incredible architecture deep-dive — link is in the resources slide and I'll share it at the end."

---

## Slides 6-8: Live Demos (~5-8 min total)

**Demo 1: Research (~2 min)**
> "Let me show you something real. I'm going to ask OpenClaw to research the latest OpenClaw features — live."

*(Do the web search demo)*

> "No browser. No copy-paste. Just a message, and I get the answer."

---

**Demo 2: Git Workflow (~2 min)**
> "Now let's do something I couldn't do from my phone before. I'm going to add a feature, commit it, and push — right from here."

*(Do the git demo)*

> "Perfect for that 3am on-call moment when you need to push a hotfix but don't want to open your laptop."

---

**Demo 3: Cron Jobs (~2 min)**
> "Finally — this isn't just reactive. OpenClaw can run on a schedule. Reminders, periodic checks, automation. Set it and forget it."

*(Trigger or show a scheduled cron)*

---

## Slide 9: System Architecture (~2 min)

**Say:**
> "Quick architecture overview. Your messages come in through a Channel Adapter — Telegram, WhatsApp, whatever you use. They hit the Gateway Control Plane — that's the brain that manages everything."

**Walk through the layers:**
- Gateway manages access control and sessions
- Agent Runtime does the reasoning
- Tools executor runs bash, browser, file ops, cron
- Everything is isolated per session, per user

**Transition:** "But the real power is extensibility..."

---

## Slide 10: Extensibility through Plugins (~1-2 min)

**Say:**
> "OpenClaw is designed to be extended without touching core code. Four plugin types:"

- **Channel plugins** — Add Teams, Matrix, Mattermost, anything
- **Memory plugins** — Vector stores, knowledge graphs instead of default SQLite
- **Tool plugins** — Custom capabilities beyond bash/browser
- **Provider plugins** — Bring your own LLM, self-hosted models

**Key point:** "Discovery-based. Drop a plugin with an `openclaw.extensions` field in package.json, and it hot-loads automatically."

---

## Slide 11: Security (~1 min)

**Say:**
> "Security isn't an afterthought — it's built in from day one."

- **Allowlists** — Restrict who can access
- **Mention rules** — Group chat control
- **Tokens** — Per-channel API keys
- **Local-only** — Your data never leaves

**Example config shown:** "This is what it looks like. Simple, explicit, secure."

---

## Slide 12: System Prompt Architecture (~2 min)

**Say:**
> "Here's how OpenClaw builds context for the model. This diagram shows the prompt assembly pipeline."

**Walk through inputs:**
- **Workspace files** — AGENTS.md, SOUL.md, TOOLS.md define who the agent is
- **Dynamic context** — Session history, skills, memory search
- **Tool definitions** — What the agent can do
- **Base system** — Core instructions

**Key:** "All of this gets assembled into the final prompt that goes to the model. That's why it 'remembers' who you are, what your workspace looks like, and how to use your tools."

---

## Slide 13: Meet Pi (~1-2 min)

**Say:**
> "Now let me introduce you to the agent behind all of this — Pi."

**Key points:**
- **Built by Infellip** — the core AI runtime that powers OpenClaw
- **Agent-native design** — tools, memory, reasoning — not a chatbot wrapper
- **Persistent context** — remembers your workspace across sessions
- **Multi-model support** — Claude, GPT, local models, any OpenAI-compatible API

**The mic drop line:**
> "This is what makes OpenClaw different from a chatbot. It's not responding to messages — it's an agent that acts."

**Fun fact to share:**
> "Pi stands for Personal Intelligence. Your agent, your context, your tools."

**Transition:** "Let's trace how a message actually flows through this system..."

---

## Slide 14: End-to-End Message Flow (~2 min)

**Say:**
> "Let's trace a message all the way through. This is the full flow — from you hitting send to getting a response."

**Walk through:**
1. User sends message → Channel Adapter → Gateway
2. Access Control validates permissions (<10ms)
3. Session Manager loads context
4. Agent Runtime builds the prompt
5. Model processes (200-500ms to first token)
6. Tool Executor runs tools if needed (bash <100ms, browser 1-3s)
7. Response streams back

**Key insight:** "Most steps are under 100ms. The bottleneck is always model inference and browser automation."

---

## Slide 15: Latency Breakdown (~1 min)

**Quick table walkthrough:**

| Step | Latency |
|------|---------|
| Access Control | <10ms |
| Session Load | <50ms |
| Prompt Assembly | <100ms |
| First Token | 200-500ms |
| Tool: Bash | <100ms |
| Tool: Browser | 1-3s |

**Takeaway:** "Use bash tools over browser when possible. The model is rarely the bottleneck — it's the tools."

---

## Slide 16: Multi-Agent Routing (~1-2 min)

**Say:**
> "One of the most powerful features: multi-agent routing. Different channels can go to different agents with different configs."

**Show the diagram:**
- WhatsApp → main session (Claude Opus)
- Discord group → Discord bot agent (Claude Sonnet)
- Telegram → support agent (GPT-4o)

**Key point:** "Each agent has its own workspace — its own AGENTS.md, SOUL.md, skills. Completely isolated. You can route by channel, by group, by user — however you want."

---

## Slide 17: Get Started (~1 min)

**Say:**
> "Ready to try it? Three commands. Five minutes."

```bash
npm install -g openclaw@latest
openclaw onboard
openclaw gateway
```

**Point to docs:** "Full docs at docs.openclaw.ai. Discord community is very active if you get stuck."

---

## Slide 18: What it Costs (~1 min)

**Say:**
> "Let's talk money. What's this going to cost you?"

| Component | Cost |
|-----------|------|
| OpenClaw | Free (self-hosted) |
| Infrastructure | ~€15/mo (Railway hobby) |
| Your machine | Already paid for |

**Key:** "OpenClaw itself is free. You bring your own API keys for the models. Hosting is cheap — or just run it on your existing dev machine."

---

## Slide 19: State Management (~1-2 min)

**Say:**
> "Quick look at how OpenClaw manages state. Everything lives in ~/.openclaw/"

**Walk through:**
- **Workspace** — AGENTS.md, SOUL.md, TOOLS.md, skills/
- **Config** — openclaw.json (overridden by env vars)
- **Credentials** — API keys, tokens
- **Sessions** — Conversation history
- **Memory** — SQLite databases for semantic search

**Key insight:** "Your workspace is just files. Git-trackable. Versionable. You can template it, share it, revert it."

---

## Slide 20: Resources (~1 min)

**Point through:**
- **Docs:** docs.openclaw.ai
- **GitHub:** github.com/openclaw/openclaw
- **Discord:** discord.gg/clawd
- **Skills marketplace:** clawhub.com

**Deep dive:** "Paolo's architecture breakdown — absolutely worth a read if you want the full technical picture."

---

## Slide 21: What's Next? (~1 min)

**Say:**
> "OpenClaw is growing fast — and there's more coming."

**Two paths:**
1. **Self-hosted (OpenClaw)** — Full control, bring your own API keys, free
2. **Hosted (NanoClaw)** — Zero config, pay per usage, managed for you

**Point to:** nanoclaw.dev — "Coming soon. If you want the power without the ops overhead, this is for you."

---

## Slide 22: Call to Action (~30 sec)

**Say:**
> "Your terminal just learned to text back. Try it tonight."

**Three steps:**
1. `npm install -g openclaw@latest`
2. `openclaw onboard`
3. Message your gateway

**Close with confidence:** "Five minutes. That's all it takes."

---

## Slide 23: Q&A

**Have your QR code ready, LinkedIn open.**

> "Let's connect. Questions?"

**Potential Q&A topics to prepare for:**

- **"Can it run on a Raspberry Pi?"** Yes — runs anywhere Node.js runs.
- **"How does it compare to ChatGPT Plugins?"** Local, self-controlled, no data leaving your machine.
- **"What models does it support?"** Any OpenAI-compatible API — OpenAI, Anthropic, local models, etc.
- **"Is it production-ready?"** It's open source and gaining traction fast. Check the GitHub for maturity.
- **"How do plugins work?"** They hook into the extension system via package.json — see the docs.

---

## Deep Dive Sources

**Architecture Deep-Dive (highly recommended):**
- https://ppaolo.substack.com/p/openclaw-system-architecture-overview

**Official Docs:**
- https://docs.openclaw.ai

**GitHub:**
- https://github.com/openclaw/openclaw

**Community:**
- Discord: https://discord.gg/clawd
- Skills: https://clawhub.com

**NanoClaw (Hosted version):**
- https://nanoclaw.dev/

---

## Tips for Delivery

1. **Pause after the Her quote** — let it land
2. **Live demos are your proof** — commit to them, even if they hiccup
3. **The latency slide is a mic drop** — "Most steps are under 100ms. The bottleneck is the model."
4. **The Buzz slide shows momentum** — social proof matters to techies
5. **End with confidence** — "Your terminal just learned to text back."

---

*Good luck! 🦞*
