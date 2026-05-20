---
title: "Hermes: a self-hosted AI API for builders"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: Hermes Agent
status: draft
author: TBD
word-target: 1800-2200
publishes-first: medium
cross-post: linkedin (7 days after)
track-a-link: "../track-a-opinion/Article-5_The-Verdict.md"
test-bed: ~/Documents/experiments/from-chatbot-to-personal-ai/vault
tested-on: macOS [FILL: version] Apple Silicon
hermes-version: [FILL: hermes --version output]
test-date: [FILL: date of setup session]
security-note: CVE-2026-7396 (path traversal in WeChat Work adapter). Critical warning about Claude API access — subscription does NOT work, API key required.
---

# Hermes: a self-hosted AI API for builders

*Hands-on setup of a self-hosted autonomous agent. Referenced in Article 5: The Verdict.*

---

## What Hermes Is (and What Makes It Different)

Hermes Agent is Nous Research's entry in this space [github.com/NousResearch/hermes-agent]. Nous Research is the lab behind the Hermes, Nomos, and Psyche model families — they have been working on the open-source model side of the stack for years before building the agent layer. 95,000+ GitHub stars since launching February 2026 [cite: github.com/NousResearch/hermes-agent].

The differentiator is the self-improvement loop. After you run Hermes on 20–30 complex tasks, it has built a library of procedures calibrated to your specific workflows. It writes down what worked, converts successful approaches into reusable skills, and automatically loads relevant ones when similar tasks come up again. The other tools in this series are static — the same agent on day 100 as on day 1. Hermes is not.

Whether that matters in practice depends entirely on how you use it. Running it occasionally to query your Obsidian vault will not build a meaningful skill library. Running it daily as an always-on agent on a VPS will. This distinction is worth naming before the setup steps.

Two clarifications before we continue:

**First, Obsidian is a first-class feature.** Hermes has native, documented Obsidian vault integration via an environment variable and a bundled skill [cite: hermes-agent.nousresearch.com/docs/user-guide/skills/bundled/note-taking]. This is the only tool in this series besides OpenClaw where the vault integration is first-party rather than a WebSocket plugin or a custom ingestion script.

**Second, Claude via a Claude Pro or Max subscription does not work with Hermes.** Anthropic blocked third-party tools from accessing Claude through subscription accounts as of April 2026 [FILL: verify exact date and cite source]. You need a pay-as-you-go API key from [console.anthropic.com](https://console.anthropic.com) — not a subscription. If you planned to use your existing Claude subscription here, it will not work. Groq, Gemini, OpenRouter, and others work fine and are free.

---

## Prerequisites

- macOS 12 or later. Tested on macOS [FILL: version] on Apple Silicon.
- Python 3.11 (specifically 3.11 — the installer handles this but verify: `python3 --version`).
- An AI provider API key. Free options: Groq (console.groq.com), Google Gemini (aistudio.google.com), OpenRouter (openrouter.ai). Paid options: OpenAI, Anthropic (API key, not subscription). This setup used [FILL: which provider].
- The test vault at `~/Documents/experiments/from-chatbot-to-personal-ai/vault`.

Hardware: Hermes is Python-based and runs on any modern laptop. Local model inference through Hermes is significantly slower than running the model directly — one documented case reported 1–2 tokens/s through Hermes vs. 45 tokens/s native [cite: community forums]. If response speed matters, use a cloud provider rather than Ollama here.

> **Windows** *(not tested — documentation only)*
>
> Native Windows support is described as "early beta" — installs and runs but not broadly tested. WSL2 is the recommended path.
>
> For WSL2: use the same Linux/macOS one-liner below from inside a WSL terminal.
>
> For native Windows: the installer unpacks a MinGit to `%LOCALAPPDATA%\hermes\git`, isolated from any system Git. This means if you have Git for Windows installed separately, they coexist without conflict.

---

## Installation

Hermes installs via a shell script. Same category of risk as NanoClaw's installer and ZeroClaw's bootstrap. Clone first, read the script, then run it.

```bash
git clone https://github.com/NousResearch/hermes-agent.git
cd hermes-agent
cat scripts/install.sh   # read it
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```

The installer handles: `uv`, Python 3.11, Node.js, `ripgrep`, `ffmpeg`, and a portable Git. No admin/root required.

[FILL: document what the installer outputs, how long it took, and whether it prompted for any configuration during the install. Note any dependency conflicts — Python version conflicts in particular are common on macOS where the system Python and Homebrew Python can interfere.]

**Configure your AI provider:**

```bash
hermes config set provider [FILL: groq|anthropic|openai|google]
hermes config set api-key YOUR_KEY
```

[FILL: verify correct config commands. Document where the API key is stored — likely `~/.hermes/.env` — and note the file permissions.]

**Configure the Obsidian vault:**

```bash
echo 'OBSIDIAN_VAULT_PATH=~/Documents/experiments/from-chatbot-to-personal-ai/vault' >> ~/.hermes/.env
```

[VERIFY: exact env var name and file path from hermes-agent.nousresearch.com/docs/user-guide/skills/bundled/note-taking]

Then load the Obsidian skill:

```bash
hermes skill enable obsidian
```

[VERIFY: exact command. The skill may be enabled by default or may require an explicit load step.]

**Verify the install:**

```bash
hermes --version
hermes status
```

[FILL: actual output. Note any warnings about provider configuration.]

---

## Connecting the Obsidian Vault

Hermes treats the vault as a local directory accessed through standard file tools — no WebSocket, no plugin, no database ingestion. Set `OBSIDIAN_VAULT_PATH` and load the Obsidian skill. The agent reads and writes markdown files directly.

[FILL: document any configuration that was not obvious from the docs. Things to check: whether Hermes respects the vault's `.obsidian/` config directory, whether it creates any index files in the vault (these would show up as untracked files in your vault's git history if you use one), and whether write operations work correctly on the test vault.]

The vault path defaults to `~/Documents/Obsidian Vault` if the env var is not set [VERIFY]. Make sure the env var is pointing at the test vault, not a production vault.

---

## The Same Test Queries

**Query 1:** What are the open blockers across my current projects?

**Result:**
[FILL: verbatim output.]

---

**Query 2:** What decisions and action items came out of my meetings this week?

**Result:**
[FILL: verbatim output.]

---

**Query 3:** Summarize what I know about AI tooling and what I still need to research.

**Result:**
[FILL: verbatim output.]

---

## What Hermes Enables That Other Tools in This Series Cannot

The self-improvement loop is the obvious differentiator, but it takes time to observe. After [FILL: N] sessions, these are the skills Hermes wrote based on the vault queries:

[FILL: list any skills Hermes automatically created. Note the location where skills are stored — likely `~/.hermes/skills/` or similar — and describe what one of them looks like. If the skill library did not grow meaningfully in the test sessions, say so. The self-improvement story only works if it actually happened.]

The Skills Hub at [agentskills.io](https://agentskills.io) allows community-contributed skills to be installed. [FILL: note any skills from the Hub that were relevant to vault/notes use cases and whether they worked.]

---

## When to Choose Hermes

Hermes makes sense when the agent is always on and you are patient enough to let the skill library develop. Running it for three vault queries and closing the laptop is not the use case.

The VPS deployment pattern is the real intended setup: a cheap instance ($5–15/month), a low-cost model API (Groq free tier, DeepSeek), and Hermes running continuously. After a month, the agent has learned your workflows. [FILL: if the test ran long enough to observe any self-improvement, document it concretely here.]

OpenClaw is the better starting point if you want a personal assistant that works on day one without a ramp-up period. Hermes is the better starting point if you are building a system you intend to run for months.

---

## What Surprised Us

[FILL after testing: specific observations. Known candidates: the local model speed issue (1–2 tokens/s) if Ollama was tested, the Anthropic subscription block if you tried it, anything about how the skill-writing works mechanically.]

---

## What Did Not Work

[FILL after testing: honest account. Documented issues include: Telegram gateway token overhead [FILL: check if this is resolved in current version], and the Anthropic subscription access block if you encountered it.]

---

## Security Notes

**CVE-2026-7396:** Path traversal vulnerability in the WeChat Work (Wecom) platform adapter, `gateway/platforms/wecom.py` [cite: radar.offseq.com/threat/cve-2026-7396]. Allows remote attackers to read arbitrary files via manipulated file paths. No privileges required, no user interaction required. The exploit is publicly available.

The good news: this only affects the WeChat Work integration. If you are not connecting Hermes to Wecom, the CVE is not in your attack surface. [FILL: verify whether the current version has a patch — check github.com/NousResearch/hermes-agent/security/advisories.]

**The local model caveat on speed:** If you tested Hermes with Ollama and found response times of 1–2 tokens/s, this is not the model being slow — it is overhead in Hermes's inference routing layer. The same model running directly in LMStudio or Ollama's CLI should be dramatically faster [cite: community reports]. This is a known issue [FILL: check if there is an open GitHub issue for this]. Practically, it means Hermes with local models is not suitable for conversational use; it is only viable with cloud API providers where network latency already sets the floor.

**API key storage:** Check where Hermes stores your API key. If it is in `~/.hermes/.env` in plaintext, note the file permissions. `chmod 600 ~/.hermes/.env` if they are not already 600.

**The skill-writing mechanism:** Hermes writes skills based on what worked. A sufficiently clever prompt injection could potentially cause it to write a skill that encodes malicious behavior. This is a theoretical risk that has not been documented as an exploit, but it is worth knowing when a self-modifying agent is running against your notes.

---

## Resource Usage

| Metric | Value |
|---|---|
| Memory at rest | [FILL] |
| Memory during vault query | [FILL] |
| Response time with cloud provider | [FILL] |
| Response time with Ollama (tokens/s) | [FILL] |
| Disk footprint | [FILL] |

---

*Status: Draft. The self-improvement sections require multiple sessions to fill meaningfully. Plan more than one sitting for this article.*

---

## Three Takes

**[Author A]:**

**[Author B]:**

**[Author C]:**

---

## LinkedIn Post

<!-- 3–5 specific observations. End with "Full setup notes on Medium [link]."
     The Claude subscription block is the most immediately useful finding for most readers —
     lead with that if it came up during setup. -->
