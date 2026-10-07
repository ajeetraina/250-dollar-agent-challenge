# 🏁 Tracks

Pick **one** track. Each has its own winner. Any project can also compete for the [special awards](#-special-awards).

Not sure what to build? Each track below has starter ideas, and [`examples/`](examples/) has more.

---

## 🌙 Night Shift

**An agent that does real work while your laptop is closed.**

The headline feature of Cloud Sandboxes: each one is a microVM with its own kernel in the cloud, so it keeps running after you detach. Build something that takes real time and show it finishing on its own.

**Starter ideas**
- A 2 AM on-call responder that triages an alert, gathers logs, and drafts a fix PR.
- An overnight dependency-upgrade bot that bumps, builds, tests, and opens PRs.
- A long-running data crawl + cleanup that would tie up your machine for hours.
- A nightly "repo gardener" that fixes lint, updates docs, and files issues.

**What judges look for:** the task genuinely runs unattended; you can show it continuing after you disconnect (`sbx stop` / reconnect, or a background `sbx exec -d`).

---

## 🔐 No Keys Allowed

**Uses real APIs, but the agent never sees your tokens.**

Docker's proxy injects auth headers into outbound requests - raw credential values never enter the sandbox. Build something that hits real, authenticated APIs while proving the agent never had the secret.

**Starter ideas**
- An agent that manages GitHub (issues, PRs, releases) via a proxied token.
- A deploy agent that calls a cloud provider API without the key ever landing in the VM.
- A data agent that queries a paid API and shows the key is absent inside the sandbox.

**What judges look for:** a clear demonstration that the credential is **not** present inside the sandbox (e.g. `env` has no raw key, policy logs show proxied calls) while the API calls still succeed.

---

## 🔌 Tool Master

**Connects MCP servers to do something genuinely useful.**

Wire your agent to one or more [Model Context Protocol](https://modelcontextprotocol.io) servers and build a workflow that would be clumsy or impossible without them.

**Starter ideas**
- An agent that reads your calendar + email (via MCP) and prepares your day.
- A research agent chaining a web-search MCP with a docs/notes MCP.
- A DB-admin agent using a database MCP to investigate and fix a slow query.
- A multi-tool pipeline: filesystem + browser + API MCPs working together.

**What judges look for:** meaningful use of MCP tools (not a toy), and a clear story of which servers are wired and why.

---

## 👥 The Crew

**Several agents in parallel, each in its own sandbox.**

Split a problem across multiple isolated sandboxes and have them work at once - fan-out, divide-and-conquer, or specialist roles.

**Starter ideas**
- A "team" (architect, implementer, reviewer) each in its own sandbox on the same repo via branch mode.
- Parallel bug-hunters sweeping different modules, then a synthesizer.
- A fan-out migration: one agent per service/package, all running simultaneously.
- Competing solvers that each attempt the task; you pick the best.

**What judges look for:** real parallelism (show `sbx ls` with multiple sandboxes live), isolation between agents, and a result that benefits from the fan-out.

---

## 🧰 Kit Maker

**Ships as a kit others can run with a single command.**

Package your build so anyone can reproduce it with one command. Think reusable template, bootstrap script, or a custom sandbox image.

**Starter ideas**
- A custom `sbx` template (`sbx save` / custom Dockerfile) preloaded for a domain.
- A one-command bootstrap: `./run.sh` that sets secrets, policy, and launches the agent.
- A reusable "agent recipe" repo others can fork and run immediately.

**What judges look for:** someone else can run it end-to-end from your README with a single command, on a fresh machine.

---

## ✨ Special awards

Any track qualifies for these:

- 💰 **Best Bang for the Buck** - most impressive result per dollar of credit spent. *(Include your spend screenshot - this is judged on cloud spend.)*
- ✍️ **Best Build Log** - the write-up others will actually learn from and repeat.
- 🙌 **People's Choice** - voted by the community on Demo Day.

---

➡️ Ready? Read the **[rules](RULES.md)**, then **[submit](SUBMISSION.md)**.
