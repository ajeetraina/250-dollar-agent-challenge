# 🚀 Getting Started

From zero to your first cloud agent in about 10 minutes.

---

## 1. Claim your $250 credit

1. Go to **https://www.docker.com/c/sbx-promo/**
2. Sign up for the **Docker Agentic Platform**.
3. Add a credit card (required by Docker at signup).
4. The **$250 one-time credit** is applied to your account (10× the standard $25).

> **Heads up**
> - One credit **per user / account**.
> - Offer ends **October 31, 2026, 11:59 PM PT** - claim early.
> - **No credit card / can't claim the credit?** You can still compete by running `sbx` locally. Skip to [the local path](#no-credit-card-build-locally).

---

## 2. Install the `sbx` CLI

**macOS** (Docker Desktop *not* required):
```bash
brew install docker/tap/sbx
```

**Windows:**
```powershell
winget install -h Docker.sbx
```

**Linux** (Ubuntu 22.04+): requires KVM - see the [official docs](https://docs.docker.com/ai/sandboxes/).

> Works alongside **Rancher Desktop** too - `sbx` runs standalone and doesn't need Docker Desktop.

---

## 3. Authenticate

```bash
sbx login
```

You'll pick a default **network policy**:

| Policy | Behavior |
|---|---|
| **Open** | All outbound traffic allowed |
| **Balanced** | Deny-by-default + common dev sites allowed *(recommended)* |
| **Locked Down** | Everything blocked unless you explicitly allow it |

You can change this later with `sbx policy set-default` or allow specific hosts with `sbx policy allow network <host>`.

---

## 4. Store your agent's credentials

Secrets are kept in your **host OS keychain**. The sandbox proxy injects auth headers into outbound requests - **raw key values never enter the sandbox** (this is the magic behind the 🔐 *No Keys Allowed* track).

```bash
sbx secret set -g anthropic                       # Claude  - paste your Anthropic API key
sbx secret set -g openai                          # Codex   - paste your OpenAI API key
sbx secret set -g github -t "$(gh auth token)"    # GitHub  - token from gh CLI
sbx secret set -g google                          # Gemini  - paste your Google API key
```

Using 1Password? Keep keys off disk entirely:
```bash
sbx secret set -g anthropic -t "$(op read -n 'op://Vault/Anthropic/api-key')"
```

> `-g` makes the secret **global** (all sandboxes). Global secrets only take effect at sandbox **creation**, so recreate a sandbox after changing one.

---

## 5. Run your first agent

```bash
cd ~/my-project
sbx run claude        # creates the sandbox + attaches, in one step
```

First run downloads the sandbox image (slow); later runs are cached. Pick your agent:

| Agent | Command | Credential |
|---|---|---|
| Claude Code | `sbx run claude` | `anthropic` (or OAuth) |
| Codex | `sbx run codex` | `openai` (required) |
| Copilot | `sbx run copilot` | `github` |
| Gemini | `sbx run gemini` | `google` (or interactive sign-in) |

Verify what's running:
```bash
sbx ls          # table: agent, status, ports, workspace
sbx             # interactive TUI dashboard
```

---

## 6. The workflows you'll actually use in the challenge

### Close your laptop - the work keeps going (🌙 Night Shift)
A sandbox is a cloud microVM. Start a long task, detach, and reconnect later:
```bash
sbx run claude --name nightshift ~/my-project
# ... later, from anywhere ...
sbx run nightshift          # reconnect to the same sandbox
sbx exec -d nightshift npm run long-task   # kick off a background command
```

### Run several agents at once (👥 The Crew)
Each sandbox is fully isolated - give every agent its own:
```bash
sbx run claude --name crew-a ~/project
sbx run claude --name crew-b ~/project
sbx run codex  --name crew-c ~/project
sbx ls          # watch them all
```

Keep each agent on its own git branch so they don't collide:
```bash
sbx run claude --branch feature-x     # creates a git worktree under .sbx/
```
> Add `.sbx/` to your `.gitignore`.

### Expose a service (for demos)
```bash
sbx ports my-sandbox --publish 8080:3000    # host:8080 → sandbox:3000
```
> Services inside the sandbox must bind to `0.0.0.0`, not `127.0.0.1`.

### Watch your spend
Track usage as you go so you can screenshot it for your submission (see 💰 *Best Bang for the Buck*). Check your Docker Agentic Platform dashboard for the running credit balance.

### 💰 Don't let a sandbox run up your credit while you sleep
A sandbox keeps billing while it's running, even idle. There's no built-in auto-stop timer, so stop them deliberately. A *stopped* sandbox preserves its state and doesn't burn compute.

```bash
# Best: tie the sandbox to the task - stop it the moment the job finishes
sbx exec -it nightshift bash -c './my-task.sh'; sbx stop nightshift

# Or a hard time cap. Keep the host awake, or it won't fire while asleep;
# on macOS, wrap the whole line with: caffeinate -i ...
( sleep 10800 && sbx stop nightshift ) &   # auto-stop after 3 hours

# Morning safety net: see what's still running, then stop it
sbx ls
sbx stop <name>
```

---

## No credit card? Build locally

The entire `sbx` CLI runs on your machine. You still get isolated microVM sandboxes - you just run them locally instead of burning cloud credit. Everything above works the same; local entries are fully eligible (though the 💰 *Best Bang for the Buck* award is judged on cloud spend).

---

## Housekeeping

```bash
sbx stop my-sandbox     # pause - state is preserved
sbx run  my-sandbox     # resume
sbx rm   my-sandbox     # permanent delete (and all its branch worktrees)
```

> **Security note:** agents have `sudo` *inside* the sandbox by design - the hypervisor boundary is the control. The one real residual risk is your **mounted workspace**: an agent can change git hooks, CI configs, and build scripts there. After a session, `git diff` and peek at `.git/hooks/`.

Full command reference: `sbx <command> --help` and the [official docs](https://docs.docker.com/ai/sandboxes/).

---

➡️ Next: pick a **[track](TRACKS.md)** and read the **[rules](RULES.md)**.
