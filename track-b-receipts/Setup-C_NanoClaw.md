---
title: "NanoClaw: reading 4,000 lines of agent code in a day"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: NanoClaw
status: draft
author: TBD
word-target: 1500-2000
publishes-first: medium
cross-post: linkedin (7 days after)
track-a-link: "../track-a-opinion/Article-5_The-Verdict.md"
test-bed: ~/Documents/experiments/from-chatbot-to-personal-ai/vault
tested-on: macOS [FILL: version] Apple Silicon
nanoclaw-version: [FILL: from repo commit hash at time of setup]
test-date: [FILL: date of setup session]
security-note: CVE-2026-7875 (CVSS 8.8) unpatched at time of research. Check repo security advisories before running.
---

# NanoClaw: reading 4,000 lines of agent code in a day

*Hands-on setup and code walkthrough. Referenced in Article 5: The Verdict.*

---

## What NanoClaw Is

The name on the box says "security-first." The pitch is the line count: roughly 4,000 lines of Node.js across about 15 source files [cite: github.com/nanocoai/nanoclaw], small enough that a human or an AI agent can read the entire thing in a single day. That is not a performance claim. It is a design constraint — you are supposed to fork this, read it, and own what you deploy.

This puts NanoClaw in a different category from OpenClaw or ZeroClaw. It is not a product you configure. It is a codebase you adopt. Every new capability lives on a separate branch. Pull requests adding features are explicitly not merged — the architecture is intentionally frozen so your fork stays auditable. The intended workflow is: clone, read, extend using Claude Code, run.

Three things to establish before the setup steps:

First, NanoClaw is not a fork of OpenClaw. They are independent projects. The names are similar; the architectures are not.

Second, NanoClaw is tightly coupled to Anthropic. It ships with the Anthropic Agent SDK as its primary inference layer. Running non-Claude models requires custom work that is not in scope for this article.

Third, NanoClaw runs each agent group inside an isolated Linux container via Docker. This is the security story. Whether it holds is addressed in "Security Notes."

---

## Prerequisites

- macOS 12 or later. Tested on macOS [FILL: version] on Apple Silicon.
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running. NanoClaw's container isolation model depends on it. Verify: `docker --version`.
- An Anthropic API key. NanoClaw calls the Anthropic Agent SDK directly. A Claude Pro or Max subscription does not work here — you need a key from [console.anthropic.com](https://console.anthropic.com). This distinction matters and comes up again in the Hermes article.
- The test vault at `~/Documents/experiments/from-chatbot-to-personal-ai/vault`. Same vault used across all six setups. See Setup-A for the structure.
- Node.js and pnpm. The install script handles these if missing, but verify first: `node --version`.

Hardware: no GPU required. NanoClaw runs on any modern laptop. The Docker containers are lightweight. The Anthropic API does the heavy inference lifting.

> **Windows** *(not tested — documentation only)*
>
> NanoClaw does not run natively on Windows. WSL2 with Docker Desktop is the only supported path.
>
> 1. Install Docker Desktop and enable WSL2 backend: Settings → Resources → WSL Integration.
> 2. Clone NanoClaw inside the WSL Linux filesystem (`~/nanoclaw`). Do NOT clone under `/mnt/c/` — the 9P bridge to Windows drives is 10–100x slower.
> 3. Run `bash nanoclaw.sh` from a WSL terminal.
>
> Do not install Docker Engine inside WSL separately alongside Docker Desktop. This causes conflicts that are not obvious to diagnose.

---

## Installation

NanoClaw installs via a single shell script that handles Node.js, pnpm, Docker, and the Anthropic credential step. Unlike ZeroClaw's bootstrap (which we skipped), NanoClaw's script is the only documented path — there is no binary or package manager alternative. Read the script before running it [VERIFY: github.com/nanocoai/nanoclaw/blob/main/nanoclaw.sh].

```bash
git clone https://github.com/nanocoai/nanoclaw.git
cd nanoclaw
cat nanoclaw.sh   # read it
bash nanoclaw.sh
```

Cloning first lets you inspect what runs. The script installs missing dependencies and prompts for your Anthropic API key. [FILL: document exactly what the script outputs, how it stores the API key, and whether the key is written to a file — if yes, note the path and permissions.]

**Verify the install:**

```bash
node --version   # should match what the script installed or required
docker ps        # confirm Docker is running
```

[FILL: note any errors, any dependency conflicts, any Docker permission issues on macOS (common when Docker Desktop hasn't been granted full disk access).]

---

## Connecting the Obsidian Vault

NanoClaw's container model changes how vault access works. Rather than a plugin or a config file pointing at a path, you define a mount allowlist — an explicit list of host directories the containers are permitted to access. This allowlist is stored outside the project root so containers cannot read it and cannot expand their own permissions.

The allowlist blocks sensitive paths by default: `.ssh`, `.aws`, `*.pem`, and similar. Your vault path needs to be explicitly added.

[FILL: document the exact allowlist config format — is it a file, an environment variable, or set during `bash nanoclaw.sh`? Note the path, the format, and any patterns that were blocked unexpectedly when accessing the test vault.]

The ObsidianClaw plugin [github.com/oscarhenrycollins/obsidianclaw] provides an in-vault chat interface and is compatible with NanoClaw. The WebSocket endpoint is the same as OpenClaw's (`ws://127.0.0.1:18789` [VERIFY]). If you have already installed it for Setup-A, it should work here without reconfiguration. [FILL: confirm or correct.]

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

## Reading the Code: Three Architecture Decisions Worth Stealing

This is the section that makes NanoClaw different from the other five setup posts. The codebase is small enough to read. Read it.

The three most instructive decisions are below. Each citation points to a specific file or area in the repo so you can verify directly.

**Decision 1:** [FILL: after reading the source. Focus on how the agent handles tool calling — the dispatch mechanism, how tools are registered, how errors surface. Cite the specific file and line range.]

**Decision 2:** [FILL: focus on context management — how NanoClaw handles the conversation window across turns, and what it does when context gets long. This is the area where small codebases make the most interesting trade-offs. Cite the file.]

**Decision 3:** [FILL: focus on the container isolation layer — how Docker containers are spawned per agent group, what the boundary is between host and container, and how permissions flow. Cite the file. This is directly relevant to CVE-2026-7875.]

---

## Two Decisions We Would Not Steal

Every design that makes NanoClaw auditable costs something elsewhere.

**Trade-off 1:** [FILL: identify one deliberate design choice made for minimalism that limits production use. Common candidates: no built-in retry logic, no skill ecosystem, no graceful degradation when the Anthropic API is unavailable. Cite the relevant code.]

**Trade-off 2:** [FILL: identify a second trade-off. The Anthropic-only inference coupling is the obvious candidate — note what it would take to add a second provider and whether that is realistic without breaking the auditable-codebase premise.]

---

## What Auditability Costs in Practice

Capabilities present in OpenClaw that NanoClaw dropped in service of the small-codebase constraint:

[FILL: list the specific features you attempted to use that were absent — multi-provider model selection, plugin ecosystem, WhatsApp Business API support, or whatever came up during the test session. One sentence per item: what it was, whether there is a workaround, and whether the workaround is something you would actually maintain.]

---

## What Surprised Us

[FILL after testing: two or three specific observations — what reading the source revealed that using the tool alone would not have shown. The interesting surprises in NanoClaw tend to be architectural: something the container model enables or prevents that is non-obvious from the surface.]

---

## What Did Not Work

[FILL after testing: honest account of failures. Common candidates for NanoClaw: Docker permission issues on macOS, the container not being able to reach the vault path until the allowlist was updated, or the Anthropic SDK hitting rate limits on longer vault queries.]

---

## Security Notes

NanoClaw markets itself as the "security-first" alternative. The CVE history deserves a closer look than that label suggests.

**CVE-2026-7875 (CVSS 8.8):** A host/container filesystem boundary escape [cite: redpacketsecurity.com/cve-alert-cve-2026-7875, thehackerwire.com/nanoclaw-container-escape]. A compromised or prompt-injected container can bypass directory restrictions during outbound attachment handling and outbox cleanup, enabling reads of arbitrary host files and in some scenarios recursive deletion of paths outside the intended sandbox. Requires initial access to a container or a successful prompt injection as a prerequisite.

As of the CVE's publication date, no patch had been issued [FILL: verify current patch status at github.com/nanocoai/nanoclaw/security/advisories before running].

The irony: the container isolation model that is NanoClaw's primary security feature is the attack surface for its first known CVE. The container boundary held in a narrow sense — the container was not deleted from the outside. But a prompt-injected agent inside the container could read host files it was not supposed to reach. Rust does not protect against logic errors, and neither does Docker.

**What the container model does protect against:** an agent that misbehaves cannot modify your system Python, cannot read your SSH keys (if the allowlist is configured correctly), and cannot install persistent processes outside its container. For a tool with write access to your notes and messaging channels, those guarantees matter.

**Practical checklist:**
- Check the repo security advisories before running: github.com/nanocoai/nanoclaw/security/advisories
- Verify the allowlist blocks `.ssh`, `.aws`, and `*.pem` paths — do not assume the defaults are correct for your machine layout
- Do not run NanoClaw with write access to your real Obsidian vault until CVE-2026-7875 has a patch. Use the test vault only.
- Review what the agent is permitted to send via WhatsApp or Telegram — the container boundary does not stop the agent from forwarding vault content through a messaging channel

---

## Resource Usage

| Metric | Value |
|---|---|
| Memory at rest (Node.js process) | [FILL] |
| Memory at rest (Docker containers) | [FILL] |
| Memory during vault query | [FILL] |
| CPU during Anthropic API inference | [FILL] |
| Disk footprint (install + containers) | [FILL] |

---

*Status: Draft. Fill in all [FILL] markers during and after the setup session. The code-reading sections require actually reading the source — budget an hour for this separate from the setup time.*

---

## Three Takes

**[Author A]:**

**[Author B]:**

**[Author C]:**

---

## LinkedIn Post

<!-- 3–5 specific observations from the setup and code read.
     End with "Full setup notes on Medium [link]."
     No "we set up X." No em dashes. One wry aside is fine. -->
