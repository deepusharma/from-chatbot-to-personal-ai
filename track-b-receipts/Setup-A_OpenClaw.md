---
title: "Setting up OpenClaw with an Obsidian vault and WhatsApp"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: OpenClaw
status: draft
author: TBD
word-target: 1800-2500
publishes-first: medium
cross-post: linkedin (7 days after)
track-a-link: "../track-a-opinion/Article-2_The-Reference.md"
test-bed: ~/Documents/experiments/from-chatbot-to-personal-ai/vault
tested-on: macOS 26.4.1 Apple Silicon
openclaw-version: [FILL: openclaw --version output]
node-version: v22.22.3
test-date: 2026-05-19
---

# Setting up OpenClaw with an Obsidian vault and WhatsApp

*The full setup notes behind Article 2: The Reference.*

---

## Prerequisites

- macOS 12 or later. Tested on macOS 26.4.1 on Apple Silicon.
- [Node.js](https://nodejs.org) v22.13 or later (pnpm 11 requires v22.13 minimum — v18 is not sufficient). Check: `node --version`. If missing or below v22: `brew install node@22` or via nvm: `nvm install 22 && nvm use 22`.
- [pnpm](https://pnpm.io): Check: `pnpm --version`. If missing: `npm install -g pnpm`. Verify after: `pnpm --version`. **nvm note:** pnpm installs per Node version. If you switched Node versions with nvm, run `npm install -g pnpm` again in the new version.
- Ollama, if you want local inference. Install from [ollama.com](https://ollama.com), verify with `ollama --version`. If you are using a cloud provider instead, skip this.
- A WhatsApp account on a phone you actually own. Not your partner's. The QR code method requires physical access to the phone at scan time. A secondary number is the smarter call here. See "Security Notes" for why that is not paranoia.
- The test vault at `~/Documents/experiments/from-chatbot-to-personal-ai/vault`. Do not point OpenClaw at your real vault on first setup. The write skills are real and the undo button is not.

**The test vault**

All six tools in this series run against the same dedicated vault. It lives at `~/Documents/experiments/from-chatbot-to-personal-ai/vault` and has seven notes: two project files with open blockers, three meeting notes from the same week, two research files. Enough for the three test queries to produce something meaningful without revealing anything you would miss if an agent accidentally rewrote it.

**The three test queries** — canonical source for all six setups:

1. What are the open blockers across my current projects?
2. What decisions and action items came out of my meetings this week?
3. Summarize what I know about AI tooling and what I still need to research.

Hardware: OpenClaw is a Node.js process. At idle it sits around 400MB RAM [cite: ZeroClaw blog comparison]. If that number is making you reconsider, the ZeroClaw article is Setup-B. Minimum recommended: 8GB RAM [VERIFY: openclaw docs]. Tested on [FILL: hardware, e.g. MacBook Pro M3 16GB].

---

## Installation

Two methods. The CLI installer is faster. Source is there if you want to see what you are actually running, which given the CVE history is not an unreasonable thing to want.

**Method 1: CLI installer**

```bash
npx openclaw-easy@latest
```

[VERIFY: this is the correct install command. Check docs.openclaw.ai/install for the current CLI command.]

The installer auto-detects your OS and Node version, downloads the current release, and runs a post-install configuration step. [FILL: document exactly what the installer outputs and asks. Note any steps that diverge from what the docs describe — those are the steps readers will need.]

**Method 2: From source**

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
pnpm install
```

[FILL: note actual output, any warnings, whether pnpm install threw errors. Record the exact openclaw version installed.]

**Verify the install:**

```bash
openclaw --version
```

Expected output: `openclaw [FILL: version string]`

[FILL: note if any errors appeared here, and what fixed them. Common macOS issues include Gatekeeper blocks and missing native dependencies.]

**Note on the hosted installer:** OpenClaw also offers a hosted installer at openclaw.ai [VERIFY: URL]. This was not used here. The docs are vague about whether it installs a cloud sync component alongside the local agent. For a setup claiming "zero cloud," that is not a great look. CLI or source install is the verifiable path.

---

> **Windows** *(not tested — steps below are based on documentation only, not a live session)*
>
> OpenClaw requires [Visual C++ Redistributables](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist) on Windows. If you get a missing DLL error on first run, install those first.
>
> Node.js: download the Windows installer from [nodejs.org](https://nodejs.org) or use `winget install OpenJS.NodeJS`.
>
> pnpm: `npm install -g pnpm` in PowerShell.
>
> CLI install (same command, run in PowerShell):
> ```powershell
> npx openclaw-easy@latest
> ```
>
> From source:
> ```powershell
> git clone https://github.com/openclaw/openclaw.git
> cd openclaw
> pnpm install
> ```
>
> Paths: replace `~/Documents/experiments/from-chatbot-to-personal-ai/vault` with `$env:USERPROFILE\Documents\experiments\from-chatbot-to-personal-ai\vault` in any config commands.
>
> Ollama has a native Windows installer at [ollama.com](https://ollama.com). The rest of the setup (vault connection, WhatsApp, AI provider config) should follow the same steps as macOS. If you hit Windows-specific issues, the OpenClaw Discord is the fastest place to get answers [VERIFY: Discord link in openclaw docs].

---

## Connecting the Obsidian Vault

OpenClaw connects to Obsidian via the **ObsidianClaw plugin**, which opens a local WebSocket server that OpenClaw reads from.

**Step 1: Install the ObsidianClaw plugin**

In Obsidian: Settings → Community Plugins → Browse → search "ObsidianClaw" → Install → Enable.

[VERIFY: exact plugin name in the community store. If it is not in the community store, it may require manual installation from the GitHub release.]

**Step 2: Configure the plugin**

The plugin settings show a WebSocket address: `ws://127.0.0.1:18789` [VERIFY: default port]. This is the address OpenClaw connects to.

[FILL: document the full plugin settings screen — what options are shown, which ones required changes, what the defaults were. Note whether the vault path needs to be configured in the plugin, in OpenClaw's config, or both.]

**Step 3: Point OpenClaw at the test vault**

```bash
openclaw config set vault ~/Documents/experiments/from-chatbot-to-personal-ai/vault
```

[VERIFY: this is the correct config command. If OpenClaw uses a config file instead, note the path and format.]

[FILL: note whether OpenClaw indexes the vault on connection — if yes, how long it took on the test vault (7 notes). Note any permission prompts macOS showed for folder access.]

**Step 4: Test the connection**

```bash
openclaw query "list my projects"
```

[FILL: record the actual output. If this failed, document what the error was and what fixed it.]

---

## Connecting WhatsApp

Two methods. WhatsApp Web (QR code) keeps everything local. The Business Cloud API is more stable but routes queries through Meta's servers, which makes "zero cloud" a bit of a stretch. This setup used the QR code method.

**WhatsApp Web (QR code method)**

```bash
openclaw channel add whatsapp
```

[VERIFY: correct command.]

OpenClaw will display a QR code in the terminal. Open WhatsApp on your phone → three-dot menu → Linked Devices → Link a Device → scan the QR code.

[FILL: note how long the QR code stayed valid, whether it required re-scanning, and whether the connection persisted after closing the terminal or required a background process to stay alive.]

**Stability:** The WhatsApp Web bridge works by running a headless browser session (via whatsapp-web.js [cite: github.com/pedroslopez/whatsapp-web.js]). [FILL: document actual stability over the test period — did the session drop, did it need to be re-authenticated, did WhatsApp flag the connection.]

**Security note on WhatsApp Web:** This method attaches OpenClaw to your personal WhatsApp account via the Linked Devices mechanism. Every incoming message on that number is readable by OpenClaw. Depending on config, those messages may be logged locally. Do not connect a primary number until you have checked what OpenClaw stores by default. A secondary SIM is the sane path here. 😅 See "Security Notes" for the full picture.

---

## Local Model vs API Setup

Five options tested, ranging from fully local (nothing leaves your machine) to free cloud APIs. Pick based on your privacy requirements and tolerance for sign-up flows.

---

**Option 1: Ollama (local, free, private)**

No API key. No data leaves your machine. The tradeoff is model quality at smaller sizes.

```bash
ollama serve
ollama pull llama3.2
```

[FILL: exact model used. Note pull size. Note whether openclaw auto-detected Ollama or required manual config.]

OpenClaw Easy auto-discovers installed Ollama models [VERIFY: source]. If auto-discovery did not work:

```bash
openclaw config set ai-provider ollama
openclaw config set ollama-model llama3.2
```

[FILL: verify correct config commands.]

---

**Option 2: Groq (free, fast, cloud)**

Groq's free tier gives you access to Llama 3.3 70B and Gemma 2 9B with genuinely fast inference. Get a key at [console.groq.com](https://console.groq.com). No credit card required.

```bash
openclaw config set ai-provider groq
openclaw config set groq-api-key YOUR_KEY
openclaw config set groq-model llama-3.3-70b-versatile
```

[VERIFY: openclaw supports groq as a named provider. If not, check whether it falls under a generic OpenAI-compatible endpoint config.]

Available free models at time of writing: `llama-3.3-70b-versatile`, `llama-3.1-8b-instant`, `gemma2-9b-it`. Rate limits apply but are generous for personal use.

---

**Option 3: Google Gemini (free tier, cloud)**

Google AI Studio gives free access to Gemini Flash. Get a key at [aistudio.google.com](https://aistudio.google.com). Again, no credit card.

```bash
openclaw config set ai-provider google
openclaw config set google-api-key YOUR_KEY
openclaw config set google-model gemini-2.0-flash
```

[VERIFY: openclaw's provider name for Gemini. May be `google`, `gemini`, or configured via OpenAI-compatible endpoint.]

Gemini Flash has a generous free quota. Gemini Pro has higher limits with billing enabled.

---

**Option 4: OpenRouter (free models, aggregator)**

OpenRouter aggregates dozens of providers and offers some models on a free tier. One key, many models. Get one at [openrouter.ai](https://openrouter.ai).

```bash
openclaw config set ai-provider openrouter
openclaw config set openrouter-api-key YOUR_KEY
openclaw config set openrouter-model google/gemma-3-27b-it:free
```

[VERIFY: openclaw's provider name for OpenRouter.]

Free models rotate. Check [openrouter.ai/models?filter=free](https://openrouter.ai/models?filter=free) for what is currently available at zero cost.

---

**Option 5: NVIDIA NIM (free credits, cloud)**

NVIDIA's inference platform includes free credits for hosted models including Llama 3.1 405B and DeepSeek. Get started at [build.nvidia.com](https://build.nvidia.com).

```bash
openclaw config set ai-provider nvidia
openclaw config set nvidia-api-key YOUR_KEY
openclaw config set nvidia-model meta/llama-3.1-405b-instruct
```

[VERIFY: openclaw's provider name for NVIDIA NIM. May require an OpenAI-compatible base URL: `https://integrate.api.nvidia.com/v1`.]

---

**Option 6: Anthropic Claude API (paid, highest quality)**

```bash
openclaw config set ai-provider anthropic
openclaw config set anthropic-api-key YOUR_KEY
```

[FILL: verify correct config commands. Note whether the API key is stored in plaintext in the config file. If yes, note the path and permissions.]

Not free, but noticeably better on complex multi-note synthesis queries.

---

**Quality comparison on the test queries:** [FILL: after running all three queries on at least two providers, note which ones showed the biggest quality difference and on which query type. The synthesis queries (blockers, decisions) tend to separate small local models from larger cloud ones faster than the summarization query.]

---

## The Test Queries

*This is the canonical source for all six tool setups. Other setup files reference back here for the query text.*

**Query 1:** What are the open blockers across my current projects?

**Result:**
[FILL: paste OpenClaw's actual response verbatim. Do not summarize. The comparison across all six tools depends on the real output text.]

---

**Query 2:** What decisions and action items came out of my meetings this week?

**Result:**
[FILL: paste actual response verbatim.]

---

**Query 3:** Summarize what I know about AI tooling and what I still need to research.

**Result:**
[FILL: paste actual response verbatim.]

---

## What Surprised Us

[FILL after testing: two or three specific technical observations a hobbyist reviewer would not make. Architecture decisions baked into the design, config assumptions, performance behaviors that diverged from the docs. One short paragraph per observation. This section feeds the "enterprise reframe" in Article 2.]

---

## What Did Not Work

[FILL after testing: honest account of failures and workarounds. If any step in the sections above was wrong, correct it there AND document what actually happened here.]

---

## Security Notes

The security situation with OpenClaw is not a minor caveat. It warrants a standalone section with specific citations.

**CVE volume:** One number before anything else: 138. That is the CVE count in OpenClaw's first five months of public auditing [cite: jgamblin/OpenClawCVEs]. An initial audit in January 2026 found 512 total vulnerabilities, eight classified as critical [cite: betterclaw.io/blog/openclaw-security-2026]. So I set it up anyway. What follows is what that actually means in practice, not a reason to close the tab.

A high CVE count reflects auditing activity as much as it reflects vulnerability. The attack surface is large because the feature scope is large — WhatsApp bridge, WebSocket server, file access, messaging across 15+ channels. Both things are true, and neither cancels the other out. The question for a self-hosted local setup is which CVEs actually affect you, and whether the version you install has patches for them.

**Specific advisories relevant to a local self-hosted setup:**

- **CVE-2026-32922 (CVSS 9.9):** Privilege escalation in the `device.token.rotate` function — newly minted tokens are not constrained to the caller's permission scope [cite: armosec.io/blog/cve-2026-32922]. Exploit requires authenticated access. On a local single-user setup, the practical risk is lower than the CVSS score implies, but this is still the first thing to check for a patch before deploying.

- **CVE-2026-25253 (CVSS 8.8):** One-click RCE via cross-site WebSocket hijacking [cite: oasis.security]. This is directly relevant to the ObsidianClaw setup in this article. The OpenClaw WebSocket server listens on `ws://127.0.0.1:18789`. Any webpage open in the same browser can send WebSocket requests to localhost if the browser is not configured to block it. Do not run OpenClaw with a browser open to untrusted sites. Check whether a patch for this specific CVE is included in the version you install [FILL: verify patch status at time of setup].

- **CVE-2026-33579 (CVSS 8.6):** Incorrect authorization (CWE-863) [cite: blink.new]. [FILL: check whether this affects the local-only configuration or only cloud/multi-user setups.]

**The WhatsApp Web bridge:** connecting OpenClaw to your personal WhatsApp account via whatsapp-web.js means OpenClaw can read all incoming messages on that number. This is how the integration works — it is not a vulnerability, it is the feature. The security question is: what does OpenClaw do with those messages by default? [FILL: check the default logging configuration and document it here. Note whether messages are stored locally, what the retention policy is, and how to disable logging if needed.]

**What was done for this setup:** [FILL: document the mitigations applied during this setup session — whether a patched version was used, which CVEs were checked, what was skipped and why.]

**Tracking CVE status:** The most current list is at [github.com/jgamblin/OpenClawCVEs](https://github.com/jgamblin/OpenClawCVEs). Check it against the version you install. Do not run an unpatched version of OpenClaw on a machine that handles sensitive data.

---

## Resource Usage

Measured on [FILL: hardware]. Memory via Activity Monitor. CPU via `top`.

| Metric | Value |
|---|---|
| Memory at rest | [FILL] |
| Memory during vault query | [FILL] |
| Memory during WhatsApp message processing | [FILL] |
| CPU at rest | [FILL] |
| CPU during inference (Ollama) | [FILL] |
| Disk footprint (install only, no model) | [FILL] |
| Disk footprint (install + Ollama model) | [FILL] |

[FILL: note whether resource usage scales with vault size. The test vault is small — 7 notes. A vault with 2,000+ notes may behave differently.]

---

## Setup Time

Elapsed time from zero to first successful WhatsApp query against the vault:

| Phase | Time |
|---|---|
| Node.js / pnpm install (if needed) | [FILL] |
| OpenClaw install | [FILL] |
| ObsidianClaw plugin install and config | [FILL] |
| WhatsApp QR scan and connection | [FILL] |
| Ollama model download | [FILL] |
| First successful vault query via WhatsApp | [FILL] |
| **Total** | **[FILL]** |

The Article 2 hook claims "20 minutes." [FILL: report the actual elapsed time. If it was 20 minutes, great. If it was 47 minutes because the WhatsApp QR code expired twice, say that instead. Update Article 2's hook to match reality, not ambition.]

---

*Status: Draft. All sections written before testing. Fill in all [FILL] markers during and after the setup session. Correct any instructions above that do not match what actually happens.*

---

## Three Takes

<!-- 2–3 sentences per co-author in their own voice.
     Anchor question: "What surprised me most about this tool."
     First-person is fine here. Voice rules still apply: no em dashes,
     no rhetorical questions, specific over generic. -->

**[Author A]:**

**[Author B]:**

**[Author C]:**

---

## LinkedIn Post

<!-- Short feed post driving to the Medium Article. Target ~200 words.
     Publish same day as the Medium Article.
     Main author publishes and tags the other two co-authors.
     Co-authors each repost with 3–4 bullets of their own take.

     WRITE: 3–5 specific observations from the setup — what was surprising,
     what differed from the docs, what a builder would want to know first.
     Not "we set up X." End with "Full setup notes on Medium [link]." -->
