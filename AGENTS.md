# AGENTS.md — From Chatbot to Personal AI

This file is the canonical instruction file for this project, read completely at session start. `CLAUDE.md` and `GEMINI.md` are one-line pointers to this file — no content lives there.

---

## Project Overview

A two-track LinkedIn/Medium article series testing six open-source personal AI tools against the same Obsidian vault with the same three queries. Author: Deepak Sharma. Honest verdicts.

- **Track A** — opinion articles, LinkedIn-first (`track-a-opinion/`, 5 articles)
- **Track B** — setup receipts, Medium-first (`track-b-receipts/`, 6 setup posts)
- **Test vault** — `~/Documents/experiments/from-chatbot-to-personal-ai/vault/` (7 synthetic notes, never the real vault)
- **Session notes** — `session-notes/` in this repo

**Related, but separate:** personal, non-publishing use of these same tools (real vault, real repos, no locked format) lives in the vault at `02-Projects/AI-Agents-Lab/`, code at `~/Documents/GitProjects/lab/`. That track isn't gated by this one's sequence or its synthetic-vault rule, and vice versa.

**Open question (as of 2026-07-12):** Is this six-tool list still current, and does the series concept itself still fit, after ~2 months idle? Not yet decided — revisit before resuming Track B.

*(No Tech Stack / Coding Standards / Git Workflow / Testing Rules sections — this is a writing project, not a code project. Everything specific to it is below.)*

---

## Project-Specific

### The Six Tools

| Tool | What it is | Key dependency | Critical CVE |
|---|---|---|---|
| OpenClaw | Reference implementation. Node.js. WhatsApp via whatsapp-web.js. Obsidian via ObsidianClaw plugin (WebSocket ws://127.0.0.1:18789). | None | CVE-2026-25253 (WebSocket hijacking), CVE-2026-32922 (CVSS 9.9 privilege escalation) |
| ZeroClaw | Rust rewrite of OpenClaw. 3.4MB binary, <5MB RAM, sub-10ms startup. Same feature scope, same config format. | None | 0 CVEs at research date |
| NanoClaw | Independent Node.js project (~4,000 lines). Docker container isolation per agent group. Designed to fork and read, not just run. Anthropic-only for now. | Docker | CVE-2026-7875 (CVSS 8.8, container escape, unpatched at research date) |
| memU | NOT an agent. A PostgreSQL + pgvector memory layer. memUBot is the agent wrapper. Requires custom ingestion for Obsidian (no native plugin). | PostgreSQL + pgvector | CVE-2026-25253 (auth token extraction, patched in 2026.1.29) |
| Hermes | Self-improving agent from Nous Research. Builds a skill library after 20-30 tasks. Anthropic subscriptions BLOCKED — needs API key from console.anthropic.com. | None | CVE-2026-7396 (path traversal in WeChat Work adapter only) |
| NemoClaw | NVIDIA wrapper FOR OpenClaw. NOT standalone — requires OpenClaw running underneath. Full stack needs DGX hardware + NVIDIA AI Enterprise license. API catalog path works without DGX but skips security controls. | OpenClaw | CVE-2026-24222 (CVSS 8.6, sandbox escape via prompt injection, fixed in v0.0.18) |

### The Three Test Queries

These are locked. Every tool runs against exactly these three, against `~/Documents/experiments/from-chatbot-to-personal-ai/vault/`.

1. What are the open blockers across my current projects?
2. What decisions and action items came out of my meetings this week?
3. Summarize what I know about AI tooling and what I still need to research.

### Article Status

All 11 articles drafted. All contain `[FILL]` markers that require real setup data.

| File | Status | Blocker |
|---|---|---|
| `track-a-opinion/Article-1_The-Map.md` | Draft complete | Verify star counts + CVE numbers before publish |
| `track-a-opinion/Article-2_The-Reference.md` | Draft structure only | Requires Setup-A session |
| `track-a-opinion/Article-3_The-Memory-Bet.md` | Draft structure only | Requires Setup-D session |
| `track-a-opinion/Article-4_The-Lock-In-Question.md` | Mostly complete | Verify "22% shadow AI" stat — DO NOT publish without source |
| `track-a-opinion/Article-5_The-Verdict.md` | Structure complete | Requires all 6 setups done |
| `track-b-receipts/Setup-A_OpenClaw.md` | Draft complete | Requires user to run setup + fill query outputs |
| `track-b-receipts/Setup-B_ZeroClaw.md` | Draft complete | Requires user to run setup + fill comparison cells |
| `track-b-receipts/Setup-C_NanoClaw.md` | Draft complete | Requires user to run setup |
| `track-b-receipts/Setup-D_memU.md` | Draft complete | Requires user to run setup; memU value is still unproven |
| `track-b-receipts/Setup-E_Hermes.md` | Draft complete | Requires user to run setup |
| `track-b-receipts/Setup-F_NemoClaw.md` | Draft complete | Requires user to run setup (API catalog path) |

**Open question:** Is memU worth including? Recommendation is to complete the other five setups first. If memU adds no measurable delta to the test queries after 3 sessions, cut it and note why in Article 5.

**Three Takes section in each article:** format needs a look before publish — one voice per article now, not necessarily three. Not yet decided; part of the broader series re-evaluation above.

### Voice Rules (Non-Negotiables)

Full rules in `Writing-Guidelines.md`. Kept in sync with the vault's `06-AI-Instructions/Voice-Writing.md` — check there if this ever looks stale. The hard stops:

- No em dashes. Ever. Split into two sentences.
- No rhetorical questions.
- Never open an article or LinkedIn post with "I."
- No scene-setters or warm-up openers. Substance in line one.
- Dry, self-deprecating humor at genuine punchlines only. One quip per article.
- Emojis sparingly — at the actual punchline, not for decoration.
- Don't stack short sentences as rhythm. Short = punchline, not beat.
- Validate before claiming. Every specific number needs a source.
- "Personal over preachy." Share the observation; let the reader draw the conclusion.

### [FILL] Protocol

`[FILL]` markers require real data from the actual setup sessions. Do not substitute plausible-sounding content. The credibility of this series rests on the comparison table being real. If a section cannot be filled without running the setup, leave it marked `[FILL]` and note what data is needed.

### Citation Discipline

Every specific number (star counts, CVE counts, benchmark figures, the "22% enterprises" claim) needs a sourced URL and an as-of date. Status tracked in `Citation-Tables.md`. Accuracy and relevance matter more than precision on fast-moving figures like star counts — don't get hung up on exact-to-the-day numbers, but don't state anything unsourced either. The "22% shadow AI" stat in Article 4 is unverified — that article cannot publish without a source.

### Publishing Order

Track B before Track A. Track A articles cite data that only exists after the setups are done. Recommended sequence: Setup-A → Article-2 → Setup-B → Setup-C → Setup-D (Article-3) → Setup-E → Setup-F (Article-4) → Article-5.

Article-1 (The Map) can publish first as it requires no setup data.

### Guided Setup Rule

When guiding Deepak through a setup session, always describe what each command does in one sentence before presenting the code block. Example:

> This checks which start scripts are available in the package:
> ```bash
> grep -E '"start"' package.json
> ```

Never give a bare command without context. Deepak runs all commands himself.

---

## Session Protocol

Uses the ai-config session protocol (see `ai-config/AGENTS.md` → "Session Protocol"). State file: `session-notes/Session-State.md`. Naming prefix: `FromChatbotToPersonalAI`.

**Extra steps on top of the template:**
- After each working session, update or create `session-notes/YYYY-MM-DD.md` — a dated log entry, in addition to `Session-State.md`.
- When a session gets a name, create that dated log file with the name as its first line and today's date as the timestamp.
