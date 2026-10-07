# ❓ FAQ

### What is the $250 credit, exactly?
A one-time compute credit that new **Docker Agentic Platform** signups get for Docker Cloud Sandboxes - 10× the standard $25. It's **one per user / account**, needs a credit card at signup, and the offer ends **October 31, 2026, 11:59 PM PT**. Claim it at https://www.docker.com/c/sbx-promo/.

### How far does $250 actually go?
Docker's own example, at the *Medium* tier (4 vCPU, 8 GB, **$0.28/hr**): **4 agents in parallel, 7 hours a day, for 30 days** - or about **3,500 fifteen-minute automated runs**. Plenty for a hackathon.

### What's a "sandbox"?
A cloud microVM with its own Linux kernel, Docker daemon, filesystem, and network stack. Your agent gets `sudo` inside it, fully isolated from your machine - and it keeps running after you close your laptop.

### Do I need Docker Desktop?
No. The `sbx` CLI runs standalone (`brew install docker/tap/sbx`). It works alongside Rancher Desktop too.

### I don't have a credit card / can't claim the credit. Can I still enter?
Yes. Build **locally** with the same `sbx` CLI - local entries are fully eligible. The only exception is the 💰 *Best Bang for the Buck* award, which is judged on cloud spend.

### Can I enter as a team?
Yes - **up to 3 people**. You can only be on one team.

### Can I use any AI agent?
Yes - Claude Code, Codex, Copilot, and Gemini all work out of the box (`sbx run claude|codex|copilot|gemini`). Use whichever fits your build.

### How do secrets work? (the 🔐 track)
You store API keys in your **host OS keychain** via `sbx secret set`. The sandbox proxy injects auth headers into outbound requests, so the **raw key never enters the sandbox**. That's what makes the *No Keys Allowed* track possible.

### Where do I submit?
In this repo's **[Issues tab](../../issues/new/choose)** → **🏆 Challenge Submission**. Details in [SUBMISSION.md](SUBMISSION.md).

### What are the deadlines?
- **Sat, Oct 10** - kickoff
- **Fri, Oct 30, 11:59 PM IST** - submissions close
- **Sat, Oct 31** - Demo Day & People's Choice voting
- **Sat, 21 Nov 2026** - Winners announced at the Collabnix Meetup, Bangalore

### What do winners get?
Winners are announced **on stage at the Collabnix Meetup in Bangalore on Sat, 21 Nov 2026**, get a slot to demo to the community, and take home **Docker swags and goodies** 🐳🎁.

### Where do I get help?
Collabnix **Slack** and **Discord**, or open a [Discussion](../../discussions) here.

### I'm brand new. Where do I start?
**[GETTING_STARTED.md](GETTING_STARTED.md)** - zero to your first cloud agent in about 10 minutes.
