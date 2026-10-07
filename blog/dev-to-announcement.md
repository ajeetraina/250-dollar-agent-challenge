---
title: "What can you actually build with $250 of AI agents? (an open challenge)"
published: false
description: "Docker is handing new signups $250 in Cloud Sandbox credit. That's 4 AI agents running 7 hours a day for a month. Here's an open challenge to spend it well, and win Docker swag on stage in Bangalore."
tags: docker, ai, hackathon, devops
cover_image: https://raw.githubusercontent.com/ajeetraina/250-dollar-agent-challenge/main/assets/cover.png
canonical_url:
---

## $250 doesn't sound like much. Let's do the math.

For a coffee-sized number, here is what Docker's new **$250 Cloud Sandbox credit** actually buys you, priced at the *Medium* tier (4 vCPU, 8 GB, **$0.28/hr**):

- 🧑‍🤝‍🧑 **4 AI agents running in parallel, 7 hours a day, for 30 straight days**, or
- ⚡ **~3,500 fifteen-minute automated runs**

That is not a trial. That is a month of a small agent team working for you.

New **Docker Agentic Platform** signups get this one-time **$250 credit**, which is **10x** the standard $25. And we think the best way to find out what it's good for is to actually spend it, in public, together.

So the Collabnix community is running an open challenge: **claim the credit, build something real, and show us what an agent can do while you sleep.**

👉 **Everything lives here:** [github.com/ajeetraina/250-dollar-agent-challenge](https://github.com/ajeetraina/250-dollar-agent-challenge)

---

## Why cloud sandboxes change the game

Each Docker Cloud Sandbox is a **microVM with its own kernel**, running in the cloud. That one detail unlocks a few things that are awkward or impossible on your laptop:

- **Close your laptop, the work keeps going.** The sandbox lives in the cloud, so a long job keeps running after you disconnect.
- **Run several at once.** Each agent gets its own isolated sandbox. Fan out a problem across a whole crew.
- **Let the agent install anything.** Whatever it installs stays inside the sandbox, not on your machine.
- **The agent never sees your API keys.** A proxy injects auth headers into outbound requests, so your real tokens never enter the sandbox.

That last one is the part most people miss, and it's genuinely a big deal for running agents you don't fully trust yet.

---

## The challenge

Pick **one track**, build solo or in a team of up to 3, and write a build log anyone can follow.

| | Track | The challenge |
|---|---|---|
| 🌙 | **Night Shift** | An agent that does real work while your laptop is closed. |
| 🔐 | **No Keys Allowed** | Uses real APIs but never sees your tokens. |
| 🔌 | **Tool Master** | Connects MCP servers to do something genuinely useful. |
| 👥 | **The Crew** | Several agents in parallel, each in its own sandbox. |
| 🧰 | **Kit Maker** | Ships as a kit others can run with a single command. |

Plus three special awards any track can win: 💰 **Best Bang for the Buck**, ✍️ **Best Build Log**, and 🙌 **People's Choice**.

---

## Get started in about 10 minutes

```bash
# 1. Claim your $250 credit
#    https://www.docker.com/c/sbx-promo/

# 2. Install the sbx CLI (Docker Desktop NOT required)
brew install docker/tap/sbx          # macOS
# winget install -h Docker.sbx       # Windows

# 3. Authenticate and pick a network policy
sbx login

# 4. Store your agent credentials (stays in your OS keychain,
#    the proxy injects them, raw keys never enter the sandbox)
sbx secret set -g anthropic

# 5. Run your first agent in the cloud
cd ~/my-project
sbx run claude
```

Close your laptop. Come back later. Reconnect:

```bash
sbx run my-sandbox
```

That's the whole loop. Claude Code, Codex, Copilot, and Gemini all work out of the box.

> 💰 **Pro tip:** a sandbox keeps billing while it runs, even idle, and there's no built-in auto-stop timer. Stop it the moment your job is done so nothing runs up your credit overnight. The cleanest pattern ties the two together:
>
> ```bash
> sbx exec -it nightshift bash -c './my-task.sh'; sbx stop nightshift
> ```
>
> A stopped sandbox keeps its state and stops burning compute.

**No credit card?** You can still compete. The same `sbx` CLI runs locally, and local entries are fully welcome (the 💰 Best Bang for the Buck award is the only one judged on cloud spend).

---

## What you submit

Four things, by the deadline:

1. A **build log** (blog post or repo README) that lets anyone repeat your build.
2. A **2-minute demo video** (you record it and share the link, no live demo needed).
3. A **screenshot of your spend**.
4. The **[submission form](https://forms.gle/TFrsnDkbnZrrfoUW8)**.

Then the community votes on the recorded demos.

---

## The timeline

| When | What |
|---|---|
| **Sat, Oct 10** | Online kickoff: walkthrough & Q&A |
| **Oct 10 - Oct 31** | Build |
| **Sat, Oct 31, 11:59 PM IST** | Submissions close (last date to submit) |
| **Nov 1 - 14** | Judging & People's Choice voting on the recorded demos |
| **Sat, 21 Nov 2026** | 🎉 Winners announced on stage at the **Collabnix Meetup in Bangalore**, with **Docker swag and goodies** |

> ⏰ **Claim the credit early.** Docker's offer ends **Oct 31, 2026, 11:59 PM PT**. It's one credit per account, and a credit card is required at signup.

---

## Ready?

1. ⭐ **Star + read the repo:** [github.com/ajeetraina/250-dollar-agent-challenge](https://github.com/ajeetraina/250-dollar-agent-challenge)
2. 💳 **Claim your $250:** [docker.com/c/sbx-promo](https://www.docker.com/c/sbx-promo/)
3. 📝 **Submit when you're done:** [the submission form](https://forms.gle/TFrsnDkbnZrrfoUW8)

Come build in the open with us. Show the community what a month of agents can really do, and we'll see the winners on stage in Bangalore on 21 November.

*Built with ❤️ by the [Collabnix](https://collabnix.com) community. Powered by [Docker Sandboxes](https://docs.docker.com/ai/sandboxes/).*
