# OpenClaw Talk - Speaker Notes

---

## Slide 1: Title

**"OpenClaw: Your Terminal That Texts Back"**

**Time:** 1 min

**Key points:**
- Welcome everyone, thanks for coming
- Quick intro: I'm Moritz, I work with AI agents, been tinkering with OpenClaw for a bit
- Today: Show you what OpenClaw is, why it matters, live demos

**Delivery:**
- Keep it casual, friendly
- Set expectation: this is a demo-heavy talk
- Hit: "By the end, you'll have a running instance and your terminal will be able to text you back"

---

## Slide 2: The Problem

**"What if your terminal could message back?"**

**Time:** 2 min

**Key points:**
- Hook: "How many of you have used an AI coding agent? Cursor, Claude, Copilot?"
- "Great tools... but they're stuck in your terminal"
- "Need to be at your keyboard, your machine"
- "Problem: Access != Aware"
- Show the gap: Phone has notification → can't act. Terminal has action → can't reach.

**Demo / Story:**
- "I was on the train, got a GitHub notification, wanted to check. No laptop. Terminal is far away."
- "What if I could just message my machine and have it do the thing?"

**Delivery:**
- Rhetorical questions work well here
- Build the pain point before the solution

---

## Slide 3: What is OpenClaw?

**"Self-hosted AI gateway"**

**Time:** 3 min

**Key points:**
- Definition: "OpenClaw is a gateway that connects chat apps to AI coding agents"
- It's not a hosted service — it runs on YOUR machine
- Multi-channel: "WhatsApp, Telegram, Discord, iMessage — pick your poison"
- Agent-native: "Built for agents with tool use, sessions, memory"
- Key phrase: "Your data, your rules"

**Technical:**
- Single Gateway process
- Node 22+ required
- Config at `~/.openclaw/openclaw.json`
- Works with any agent (Pi, Claude, etc.)

**Delivery:**
- Walk through the diagram slowly
- Point to each piece: chat → gateway → agent → tools

---

## Slide 4: Why Techies Should Care

**4 Key Benefits**

**Time:** 5 min

**Key points:**

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
- "Agent per project? Sure."

### 4. Mobile Dev Machine
- "Your phone becomes a remote dev environment"
- "Run commands, check logs, push code"
- "Pair a node — get camera, location, screen"
- "From anywhere → your machine, your tools"

**Delivery:**
- This is the "why should I care" slide
- Pause after each benefit, let it land
- Personal anecdotes work: "I use it to check my servers from bed"

---

## Slide 5: Live Demo 1 - Research

**"Show me the latest OpenClaw features"**

**Time:** 4 min

**Setup:**
- Before slide: "Let's see this in action"
- We'll do research live — no slides needed

**What to do:**
1. Say to chat: "Search for recent OpenClaw features"
2. Show web_search result
3. Click into one result with web_fetch
4. Summarize what we found

**Key messages:**
- "This is a real conversation - not pre-recorded"
- "I didn't open a browser, didn't copy-paste"
- "Just messaged, got result"

**Troubleshooting:**
- Have backup: pre-fetched result ready if demo fails

**Delivery:**
- Make it feel casual: "Let me ask my assistant"
- Narrate what you're doing: "I'm just sending a message..."
- Point at the response: "Here's what came back"

---

## Slide 6: Live Demo 2 - Git Workflow

**"Add a feature, commit, push"**

**Time:** 5 min

**Setup:**
- Repo already exists: `/data/workspace/openclaw-demo-repo/`
- Before this slide, make sure I'm connected

**What to do:**
1. Create a new file: `echo "New feature" > feature.txt`
2. Git add: `git add .`
3. Commit: `git commit -m "Add feature from chat"`
4. Show the commit in git log
5. (Skip actual push — no remote set up. Just show the commit locally.)

**Key messages:**
- "I just wrote code... from my phone"
- "That's my repo over there — it's real"
- "You could do this from anywhere"

**Delivery:**
- Make it slow, let the audience absorb it
- "This file didn't exist until I just created it... via chat"
- Show the file exists: `ls` or `cat`

---

## Slide 7: Live Demo 3 - Cron Jobs

**"This runs on a schedule"**

**Time:** 3 min

**Setup:**
- Cron job already created: fires every hour, waiting

**What to do:**
1. Explain: "I pre-set a cron job earlier — it fires every hour"
2. Say trigger command: "Now"
3. Show the system event fires in chat

**Key messages:**
- "Cron isn't just for servers — it's for YOU"
- "Reminders, builds, checks — any automation"
- "Schedule it once, forget about it"

**Delivery:**
- Make it a reveal: "I've actually had this ready since before the talk"
- "Let me trigger it now... ready?"
- Show the message popping in

---

## Slide 8: Architecture

**"How it works"**

**Time:** 3 min

**Key points:**
- Diagram walk-through
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

**"Control from the start"**

**Time:** 2 min

**Key points:**
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

**"One-liner install"**

**Time:** 2 min

**Key points:**
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

## Slide 11: Call to Action

**"Your terminal just learned to text back"**

**Time:** 1 min

**Key points:**
- "Try it tonight"
- "Message your machine"
- "Make it work for YOU"
- "Customize it, hack it, break it"

**Delivery:**
- End strong
- "Go install it, I'll be around for questions"
- "Your terminal is waiting for your message"

---

## Slide 12: Q&A

**"Questions?"**

**Time:** Open

**Logistics:**
- Mention: docs.openclaw.ai has everything
- Discord community is active
- Find me in the room or online

**Potential questions to prep for:**
- "Does it work on Windows?" → Yes, but CLI-focused, better on Mac/Linux
- "What agents does it support?" → Pi, Claude, any via config
- "Is it secure?" → Yes, local-only by default
- "Can I use it for business?" → Yes, self-hosted = your compliance

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
| Q&A   | ∞    |       |

**Total target: 25-30 min**