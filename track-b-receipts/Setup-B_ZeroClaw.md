---
title: "ZeroClaw: a Rust rewrite, benchmarked honestly"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: ZeroClaw
status: draft
author: TBD
word-target: 1500-2000
publishes-first: medium
cross-post: linkedin (7 days after)
track-a-link: "../track-a-opinion/Article-5_The-Verdict.md"
test-bed: ~/Documents/experiments/from-chatbot-to-personal-ai/vault
tested-on: macOS [FILL: version, e.g. 15.4.1] Apple Silicon
zeroclaw-version: [FILL: zeroclaw --version output]
test-date: [FILL: date of setup session]
---

# ZeroClaw: a Rust rewrite, benchmarked honestly

*Hands-on setup and benchmark. Referenced in Article 5: The Verdict.*

---

## What ZeroClaw Is

ZeroClaw is a Rust rewrite of OpenClaw's core runtime. The project launched in early 2026, with the stated goal of preserving OpenClaw's feature scope while rebuilding the architecture for performance and resource efficiency [cite: zeroclaw-labs/zeroclaw README].

The headline numbers from the project README: sub-10ms startup time, 3.4MB binary, under 5MB RAM at rest [cite: zeroclaw-labs/zeroclaw README]. OpenClaw, built on Node.js, sits around 400MB RAM at idle [cite: ZeroClaw blog comparison post]. Whether those numbers matter depends on how you intend to run the agent. The section "What Sub-10ms Startup Means in Daily Use" gives the measured answer for this hardware.

Feature scope is identical to OpenClaw. Same channels, same providers, same config format. If you already have OpenClaw running, `zeroclaw migrate openclaw` handles the transition [cite: ZeroClaw docs]. What changed is everything underneath. This setup started from scratch rather than migrating, so the comparison is clean.

---

## Prerequisites

- macOS 12 or later. Tested on macOS [FILL: version] on Apple Silicon.
- An Obsidian vault set aside for testing — not your real one. ZeroClaw's default mode is `supervised`, which still requires approval for writes, but there is no reason to test autonomy modes against notes you care about.
- An AI provider: Ollama locally, or any of the free cloud options (Groq, Gemini, OpenRouter). See "Connecting the Obsidian Vault" for the full list. This setup tested [FILL: which provider].
- No Rust required if you use the prebuilt binary.

Hardware: the binary is 3.4MB. Everything else is the model. A Llama 3.2 3B pulls about 2GB via Ollama; the 70B variants run to 40GB+. Pick based on what your machine can actually run, not what the benchmark charts suggest.

**The test vault**

For this series, all six tools run against the same dedicated test vault, not a live personal vault. ZeroClaw's default autonomy mode (`supervised`) requires approval for write operations, but `full` mode can create and modify notes without prompting. Running any write-capable agent against real notes during initial configuration is not a risk worth taking.

The test vault lives at `~/Documents/experiments/from-chatbot-to-personal-ai/vault`. It contains seven notes across three folders: two project notes, three meeting notes from the same week, and two research files. That is enough content for the three test queries to produce meaningful results.

The three test queries this series uses are locked before any setup session. Every tool runs the same three:

1. What are the open blockers across my current projects?
2. What decisions and action items came out of my meetings this week?
3. Summarize what I know about AI tooling and what I still need to research.

---

## Installation

Three methods. Prebuilt binary is the fastest path. Cargo install is slower but you know exactly what compiled. The bootstrap script exists and should be skipped — more on that below.

**Method 1: Prebuilt binary**

Download the macOS ARM64 binary from the [ZeroClaw GitHub Releases page](https://github.com/zeroclaw-labs/zeroclaw/releases). The binary for Apple Silicon is named `zeroclaw-macos-arm64` [VERIFY: confirm exact filename on releases page].

Before running it, verify the checksum against the release page:

```bash
shasum -a 256 zeroclaw-macos-arm64
```

Compare the output against the SHA-256 listed on the release page for that version. If the checksums do not match, stop. Do not run the binary. See "Security Notes" for why this step matters.

Once verified:

```bash
chmod +x zeroclaw-macos-arm64
sudo mv zeroclaw-macos-arm64 /usr/local/bin/zeroclaw
```

macOS will likely block the binary on first run with a Gatekeeper warning. After you have verified the checksum, remove the quarantine flag:

```bash
xattr -d com.apple.quarantine /usr/local/bin/zeroclaw
```

This is safe to run after verification. Not before.

**Method 2: Cargo**

If you prefer to build from the published crate and want the source-level transparency that provides:

```bash
# Install Rust if not present
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"

# Build and install ZeroClaw
cargo install zeroclaw
```

`cargo install` compiles from source. On Apple Silicon this took [FILL: actual compile time] minutes. The resulting binary is placed at `~/.cargo/bin/zeroclaw`.

**Method 3: Bootstrap script (not used)**

ZeroClaw publishes a one-step install:

```bash
curl -fsSL https://raw.githubusercontent.com/zeroclaw-labs/zeroclaw/main/scripts/bootstrap.sh | bash
```

Not used here. Convenient, yes. Also the textbook supply chain attack vector. Piping a remote script into bash means you have no idea what runs before it runs. For a tool that will have access to your notes and messaging accounts, that feels like the wrong place to save 30 seconds. Use Method 1 or 2.

> **Windows** *(not tested — steps below are based on documentation only, not a live session)*
>
> Download the Windows x64 binary (`zeroclaw-windows-x86_64.exe`) from the [GitHub Releases page](https://github.com/zeroclaw-labs/zeroclaw/releases) [VERIFY: exact filename].
>
> Verify the checksum in PowerShell before running it:
> ```powershell
> Get-FileHash zeroclaw-windows-x86_64.exe -Algorithm SHA256
> ```
> Compare against the SHA-256 on the release page. If they don't match, stop.
>
> Move the binary somewhere on your PATH, e.g.:
> ```powershell
> Move-Item zeroclaw-windows-x86_64.exe C:\Windows\System32\zeroclaw.exe
> ```
> Or add a custom folder to your PATH instead of dumping things in System32.
>
> Windows Defender SmartScreen may block the binary on first run since it's not from a signed publisher. If you have verified the checksum, you can bypass the warning. If you have not verified it, do not bypass it.
>
> For cargo install on Windows, get Rust via [rustup.rs](https://rustup.rs) — the Windows installer handles everything including the MSVC build tools.
>
> Vault path: replace `~/Documents/experiments/from-chatbot-to-personal-ai/vault` with `$env:USERPROFILE\Documents\experiments\from-chatbot-to-personal-ai\vault` in any config.

---

**Verify the install:**

```bash
zeroclaw --version
```

Expected output: `zeroclaw [FILL: version string]`

[FILL: note any unexpected output or errors encountered here]

---

## Connecting the Obsidian Vault

Run the interactive onboarding wizard:

```bash
zeroclaw onboard --interactive
```

The wizard walks through four configuration steps:

1. **AI provider** — ZeroClaw supports 22+ providers [VERIFY]. Options that cost nothing: Ollama (local, private), Groq (key from console.groq.com, no card), Google Gemini (key from aistudio.google.com, no card), OpenRouter free tier (key from openrouter.ai). Paid options with better quality on complex queries: Anthropic Claude, OpenAI. [FILL: which provider was configured first, any prompts that were unclear, whether the provider list in the wizard matched the docs]

2. **Vault path** — Point ZeroClaw at the test vault:
   ```
   /Users/[your-username]/Documents/experiments/from-chatbot-to-personal-ai/vault
   ```
   [FILL: exact prompt text from the wizard, any path format requirements noticed]

3. **Autonomy mode** — Three options: `readonly`, `supervised`, `full`. Choose `supervised` for initial setup. In supervised mode, ZeroClaw requests approval before any operation that modifies files or sends messages. [FILL: confirm this is presented as a choice during onboarding or if it requires manual config]

4. **Channels** — ZeroClaw asks which messaging channels to connect. Skip all channels for initial vault testing. They can be added later. [FILL: confirm this can be skipped cleanly]

Config is written to `~/.zeroclaw/config.toml` [VERIFY: actual path]. [FILL: note anything about the config format that was not obvious, any values you had to look up]

**What differs from OpenClaw's vault configuration:**

[FILL after Setup-A is complete: document whether ZeroClaw's vault config format is identical to OpenClaw's, or what changed. Either answer is useful to readers migrating between tools.]

---

## The Same Test Queries

The same three queries run against every tool in this series. Results are recorded verbatim.

**Query 1:** What are the open blockers across my current projects?

**Result:**
[FILL: paste ZeroClaw's actual response here, verbatim. Do not summarize.]

---

**Query 2:** What decisions and action items came out of my meetings this week?

**Result:**
[FILL: paste ZeroClaw's actual response here, verbatim.]

---

**Query 3:** Summarize what I know about AI tooling and what I still need to research.

**Result:**
[FILL: paste ZeroClaw's actual response here, verbatim.]

---

## Performance Comparison vs OpenClaw

Measured on [FILL: hardware, e.g. MacBook Pro M3 16GB]. Timing via `time` command. Memory via Activity Monitor.

| Metric | ZeroClaw | OpenClaw |
|---|---|---|
| Startup time | [FILL] | [after Setup-A] |
| Response time (query 1) | [FILL] | [after Setup-A] |
| Response time (query 2) | [FILL] | [after Setup-A] |
| Memory at rest | [FILL] | [after Setup-A] |
| Memory under load | [FILL] | [after Setup-A] |
| Binary/install size | [FILL] | [after Setup-A] |

[FILL: OpenClaw numbers after Setup-A is complete. ZeroClaw numbers from this session.]

---

## What "Sub-10ms Startup, 3.4MB Binary" Means in Daily Use

[FILL after testing: answer the specific question of whether the startup advantage is noticeable in practice on this hardware. If ZeroClaw runs as a background daemon, startup time is irrelevant. If it is invoked per query, it matters. Document which mode was used and what was actually perceptible vs what only showed up in measurements.]

---

## What Surprised Us

[FILL after testing: two or three specific technical observations. Not general impressions. The format from the other setup posts: one paragraph per observation, specific enough that a reader could reproduce or check it.]

---

## What Did Not Work

[FILL after testing: honest account of failures encountered and whether they were resolved. If a step in the Installation or Vault Connection sections above was wrong, correct it there AND document what actually happened here.]

---

## Security Notes

ZeroClaw has no disclosed CVEs as of [FILL: setup date]. That is partly a function of Rust's memory model and partly a function of ZeroClaw being newer and less widely audited than OpenClaw. Both things are true simultaneously, and the distinction matters.

**What Rust eliminates by design:** buffer overflows, use-after-free errors, and data races. The Rust compiler enforces memory safety at compile time. This eliminates the vulnerability classes responsible for the majority of the 138 CVEs disclosed in OpenClaw's first five months of public auditing [cite: jgamblin/OpenClawCVEs]. A Rust rewrite does not inherit them.

**What Rust does not eliminate:** logic errors, authorization failures, injection vulnerabilities, and supply chain attacks. ZeroClaw uses `unsafe` blocks for FFI and performance-critical paths [cite: ZeroClaw source, grep for `unsafe`]. Code in `unsafe` blocks bypasses Rust's memory safety guarantees and requires the same manual auditing you would do in C. The project runs `cargo-audit` in CI and claims 85%+ fuzz coverage [cite: ZeroClaw README], but no independent third-party audit has been published as of this writing.

**The bootstrap script risk:** ZeroClaw's one-step `curl | bash` installer is convenient. It is also the canonical supply chain attack vector. A compromised bootstrap script — whether through a DNS hijack, a CDN compromise, or a repository takeover — runs with your user permissions before you can inspect it. Verify the binary checksum instead (see Installation).

**Practical checklist for this setup:**

- Use `supervised` autonomy mode during initial configuration. Not `full`.
- Verify the binary checksum before running it.
- Use the test vault, not your real vault.
- Decide before connecting an AI provider whether your queries should leave your hardware. Ollama keeps everything local. The Anthropic and OpenAI paths do not.
- Back up your test vault before connecting ZeroClaw in `full` mode, even if the vault is synthetic.

**Comparison to OpenClaw's CVE history:** OpenClaw has three critical disclosures relevant to local self-hosted setups. CVE-2026-32922 (CVSS 9.9) is a privilege escalation in the token rotation function [cite: armosec.io]. CVE-2026-25253 (CVSS 8.8) is a one-click RCE via cross-site WebSocket hijacking [cite: oasis.security]. CVE-2026-33579 (CVSS 8.6) is an incorrect authorization flaw [cite: blink.new]. ZeroClaw's Rust architecture does not inherit the memory-based vulnerabilities, but a WebSocket hijacking vulnerability is a logic error — Rust provides no protection against it. [FILL: check ZeroClaw's WebSocket implementation when Setup-A is done and note whether the same attack surface exists.]

---

## Who This Is Actually For

ZeroClaw's performance advantages are real. Whether they are relevant depends on where you are running the agent.

**Where the binary size and startup speed matter:** resource-constrained hardware (a Raspberry Pi 4, a VPS with 512MB RAM), edge deployment where startup latency is billable, and environments where a 400MB Node.js process is not acceptable — a shared server, an embedded system, a device with 1GB total RAM.

**Where they do not matter:** a MacBook with 16GB or more, a desktop development machine, any environment where the model weights dwarf the runtime footprint. ZeroClaw's 5MB idle memory is 80x lower than OpenClaw's 400MB, but both are invisible next to a 4GB Ollama model.

[FILL after testing: add any specific observations about where ZeroClaw fell short for personal assistant use that OpenClaw handles better. Missing features, rough edges in the Obsidian integration, anything that made the day-to-day experience noticeably worse than the spec sheet suggests.]

---

*Status: Draft. Installation and vault sections written before testing. Fill in all [FILL] markers during and after the setup session. Correct any instructions that do not match reality.*

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
