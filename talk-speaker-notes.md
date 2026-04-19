# OpenClaw Talk - Speaker Notes v2

---

## Slide 1: Title
**Time:** 1 min

**Talking points:**
- Welcome everyone, thanks for coming
- Quick intro: "I'm Moritz, I work with AI agents, been tinkering with OpenClaw"
- Today: What OpenClaw is, why it matters, live demos

**Delivery:**
- Keep it casual and friendly
- Set expectation: "This is a demo-heavy talk — bring questions"
- End intro with: "By the end, you'll have a running instance and your terminal will be able to text you back"

---

## Slide 2: The Problem
**Time:** 2 min

**Talking points:**
- Hook: "How many of you have used an AI coding agent? Cursor, Claude, Copilot?"
- "Great tools... but they're stuck in your terminal"
- "Need to be at your keyboard, your machine"
- "Problem: Access != Awareness"
- The pain: Phone has notification → can't act. Terminal has action → can't reach.

**Story:**
- "I was on the train, got a GitHub notification, wanted to check. No laptop. Terminal is far away."
- "What if I could just message my machine and have it do the thing?"

**Delivery:**
- Rhetorical questions work well here
- Build the pain point before the solution

---

## Slide 3: What is OpenClaw?
**Time:** 3 min

**Talking points:**
- Definition: "OpenClaw is a gateway that connects chat apps to AI coding agents"
- "It's not a hosted service — it runs on YOUR machine"
- "Multi-channel: WhatsApp, Telegram, Discord, iMessage — pick your poison"
- "Agent-native: built for agents with tool use, sessions, memory"
- Key phrase: "Your data, your rules"

**Technical:**
- Single Gateway process
- Node 22+ required
- Config at `~/.openclaw/openclaw.json`

**Delivery:**
- Walk through the diagram slowly
- Point to each piece: chat → gateway → agent → tools

---

## Slide 4: Why Techies Should Care
**Time:** 5 min

**Talking points:**

### 1. Self-hosted = Control
- "Your API keys never leave your machine"
- "No vendor lock-in, no hosted service going down"
- "You own the data, you own the infrastructure"

### 2. Workflow Integration
- "Trigger scripts from chat"
- Examples: `/build`, `/deploy`, `/test`
- "CI/CD from your pocket"
- "Perfect for on-call: message, get status"

### 3. Multi-agent Routing
- "Different agents for different contexts"
- "Work agent, personal agent, project-specific agents"
- "Isolated sessions — data doesn't leak between contexts"

### 4. Mobile Dev Machine
- "Your phone becomes a remote dev environment"
- "Run commands, check logs, push code"
- "Pair a node — get camera, location, screen"
- "From anywhere → your machine, your tools"

**Delivery:**
- Pause after each benefit, let it land
- Personal anecdotes work: "I use it to check my servers from bed"

---

## Slide 5: Live Demo 1 - Research
**Time:** 4 min

**What to say:**
- "Let's see this in action"
- "I'll do research live — not pre-recorded"
- "This is a real conversation with my assistant"

**Step by step:**
1. Open Telegram (or your chat app)
2. Type: "Search for the latest OpenClaw features"
3. Show the web_search result
4. Click into a result with web_fetch
5. Summarize what we found

**Key messages:**
- "This is a real conversation - not pre-recorded"
- "I didn't open a browser, didn't copy-paste"
- "Just messaged, got result"

**Troubleshooting:**
- Have backup: pre-fetched result ready if demo fails
- Don't panic if slow — narrate what you're doing

**Delivery:**
- Make it feel casual: "Let me ask my assistant"
- Point at the response: "Here's what came back"

---

## Slide 6: Live Demo 2 - Git Workflow
**Time:** 5 min

**Setup before demo:**
- Repo already exists and is linked

**What to say:**
- "Now let's do something more developer-focused"
- "I'll write some code... from my phone"

**Step by step:**
1. Create a new file: `echo "New feature" > feature.txt`
2. Git add: `git add .`
3. Commit: `git commit -m "Add feature from chat"`
4. Show the commit in git log
5. Push (if remote is set up)

**Key messages:**
- "I just wrote code... via chat"
- "That's my repo over there — it's real"
- "You could do this from anywhere"

**Delivery:**
- Make it slow, let the audience absorb it
- "This file didn't exist until I just created it... via chat"
- Show the file exists: `ls` or `cat`

---

## Slide 7: Live Demo 3 - Cron Jobs
**Time:** 3 min

**Setup:**
- Cron job already created before the talk

**What to say:**
- "Cron isn't just for servers — it's for YOU"
- "I pre-set a cron job earlier — it fires every hour"
- "Let me trigger it now... ready?"

**Step by step:**
1. Explain what cron jobs can do
2. Say the trigger command
3. Show the system event fires in chat

**Key messages:**
- "Reminders, builds, checks — any automation"
- "Schedule it once, forget about it"

**Delivery:**
- Make it a reveal: "I've had this ready since before the talk"
- "Let me trigger it now"
- Show the message popping in

---

## Slide 8: Architecture
**Time:** 3 min

**Talking points:**
- Walk through the diagram
- Gateway = single source of truth
- Channel plugins: each chat app
- Sessions: isolated per sender
- Tools: shell, git, browser, etc.

**Technical details:**
- Gateway runs as a service/daemon
- Config lives in `~/.openclaw/openclaw.json`
- Plugins for each channel
- Agent connects via RPC

**Delivery:**
- Reference back to demos: "Remember the git demo? That's the shell tool → gateway → agent"
- Don't over-engineer this slide
- One sentence per box

---

## Slide 9: Security
**Time:** 2 min

**Talking points:**
- Allowlists: "Only you can access"
- Mention rules: "In groups, need to @-mention me"
- Tokens: per-channel API keys
- Local-only: "Data never leaves"

**Code snippet:**
- Show a sample config piece
- `channels.telegram.allowFrom`

**Delivery:**
- Security is often an afterthought
- "OpenClaw puts it first"
- "Your gateway, your rules"

---

## Slide 10: Get Started
**Time:** 2 min

**Talking points:**
- Install: `npm install -g openclaw@latest`
- Onboard: `openclaw onboard`
- Start: `openclaw gateway`
- Done.

**Links:**
- Docs: https://docs.openclaw.ai
- GitHub: https://github.com/openclaw/openclaw
- Discord: https://discord.gg/clawd

**Delivery:**
- "Five minutes, literally"
- "I'll help anyone who wants to try it after"

---

## Slide 11: Resources
**Time:** 2 min

**Talking points:**
- Point to key resources
- Plugins ecosystem (clawhub.com)
- Multi-channel support

---

## Slide 12: Call to Action
**Time:** 1 min

**Talking points:**
- "Try it tonight"
- "Message your machine"
- "Make it work for YOU"
- "Customize it, hack it, break it"

**Delivery:**
- End strong
- "Go install it, I'll be around for questions"
- "Your terminal is waiting for your message"

---

## Demo Scripts (Detailed)

### Demo 1: Research
```
Command: "Search for recent OpenClaw releases on GitHub"

What happens:
1. web_search fires → finds latest releases
2. web_fetch pulls details from a result
3. I summarize the findings
```

### Demo 2: Git Workflow
```
Command: "Add a hello.txt file to the demo repo with 'Hello from OpenClaw' and commit it"

What happens:
1. File created in /data/workspace/openclaw-demo-repo/
2. git add .
3. git commit -m "Add hello.txt via chat"
4. git log shows the commit
```

### Demo 3: Cron Trigger
```
Command: "Fire the demo cron job now"

What happens:
1. cron run triggers the pre-set job
2. systemEvent delivered to chat
3. Message appears: "🔔 Demo cron fired!"
```

---

## Timing Summary

| Slide | Time | Total |
|-------|------|-------|
| 1-2   | 3 min | 3 min  |
| 3     | 3 min | 6 min  |
| 4     | 5 min | 11 min |
| 5     | 4 min | 15 min |
| 6     | 5 min | 20 min |
| 7     | 3 min | 23 min |
| 8     | 3 min | 26 min |
| 9     | 2 min | 28 min |
| 10    | 2 min | 30 min |
| 11    | 1 min | 31 min |
| 12    | 1 min | 32 min |

**Total target: 25-30 min** (Q&A adds more)

---

## Potential Q&A

**Q: Does it work on Windows?**
A: Yes, but CLI-focused. Best on Mac/Linux.

**Q: What agents does it support?**
A: Pi, Claude, any via config. Built-in support for MiniMax.

**Q: Is it secure?**
A: Yes, local-only by default. Token auth, allowlists.

**Q: Can I use it for business?**
A: Yes, self-hosted = your compliance.

**Q: What if my API key is exposed?**
A: It's on your machine — you control exposure. Unlike hosted services.

---

## Files in This Repo

- `README.md` — intro
- `presentation.html` — full slide deck (open in browser)
- `talk-slides.md` — raw slides (markdown)
- `talk-speaker-notes.md` — these notes