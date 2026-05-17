# From Chatbot to Personal AI — Series Outline

*Three enterprise AI practitioners. Six open-source personal AI agents. One Obsidian vault. Honest verdicts.*

---

## Status

Three co-authors confirmed. Partnership decisions (work split, voice editor, one-off vs recurring) to be agreed before drafting begins. This outline is the working brief.

---

## The Thesis

Four phases of how we relate to AI:

1. **LLMs** — You talk to AI. AI talks back. (ChatGPT, Claude, Gemini)
2. **Agentic Workflows** — Humans orchestrate AI through workflows. (LangChain, n8n, AutoGPT, enterprise agent platforms)
3. **Agents** — AI orchestrates itself within a defined task scope. Multi-agent systems sit here. (Devin, Copilot, custom agents)
4. **True Personal Assistants** — AI that knows YOU. Runs on YOUR hardware. Always on. Accessible anywhere. Not Siri. Not Alexa.

Apple Intelligence and Gemini Nano on-device are the proprietary mirror of Phase 4. OpenClaw and its ecosystem are the open-source counterpart and the first credible open-source proof that Phase 4 is here.

This series tests that proof. Same knowledge base (Obsidian vault). Same queries. Six tools. Honest verdicts.

---

## The Lens

We are engineers who build enterprise AI for a living. This series tests the open-source personal versions of what we ship to large organisations. That perspective does not appear elsewhere in coverage of this space.

Written in personal capacity. No employer affiliation, no product references, no proof-points beyond the experiment itself. The credibility is in the analysis.

---

## Series Metadata

| Field | Value |
|---|---|
| Series name (Track A) | From Chatbot to Personal AI |
| Series name (Track B) | From Chatbot to Personal AI: Field Notes |
| Track A primary platform | LinkedIn Articles |
| Track A secondary platform | Medium, canonical URL back to LinkedIn, published 7–14 days later |
| Track B primary platform | Medium |
| Track B secondary platform | This repo (configs and scripts) |
| Track A length | 700–1,000 words per article |
| Track B length | 1,500–2,500 words per setup post |
| Track A cadence | Roughly weekly, soft, with buffer built before launch |
| Track B cadence | When ready, no schedule pressure |
| Test bed | Single Obsidian vault, same queries across all hands-on work |
| Article drafts | `track-a-opinion/` |
| Setup post drafts | `track-b-receipts/` |

---

## Two-Track Structure

### Track A — Opinion (5 articles, LinkedIn primary)

| # | Working title | Type | Length | Lead role |
|---|---|---|---|---|
| 1 | The Map | Research and analysis, no setup | 800–1,000 words | Strategic framing |
| 2 | The Reference | OpenClaw verdict, what it proves | 700–1,000 words | Hands-on plus lens |
| 3 | The Memory Bet | memU as contrarian thesis on persistent memory | 700–1,000 words | Hands-on plus lens |
| 4 | The Lock-In Question | NemoClaw, shadow AI, NVIDIA's enterprise answer | 800–1,000 words | CISO/VP-Eng-targeted |
| 5 | The Verdict | Synthesis, framework, what kept running, 12-month view | 1,000–1,200 words | Strategic framing |

### Track B — Receipts (6 setup posts, Medium primary)

| # | Working title | Tool | Length |
|---|---|---|---|
| A | Setting up OpenClaw with an Obsidian vault and WhatsApp | OpenClaw | 1,800–2,500 |
| B | ZeroClaw: a Rust rewrite, benchmarked honestly | ZeroClaw | 1,500–2,000 |
| C | NanoClaw: reading 4,000 lines of agent code in a day | NanoClaw | 1,500–2,000 |
| D | memU: configuring persistent memory for a personal AI | memU | 1,800–2,200 |
| E | Hermes: a self-hosted AI API for builders | Hermes | 1,800–2,200 |
| F | NemoClaw via the NVIDIA API catalog (with DGX context) | NemoClaw | 1,500–2,000 |

---

## Article-Level Outlines (Track A)

### Article 1 — The Map

**Type:** Research and analysis, no setup required
**Hook:** The four-phase arc. OpenClaw's GitHub star count [cite] is a signal, not a product launch. Phase 4 has arrived.

**Sections:**
1. The four phases. Phase 2 vs 3 distinction made explicit: Phase 2 = humans orchestrate AI through workflows. Phase 3 = AI orchestrates itself within a defined task scope.
2. Why this is different from Siri, Alexa, ChatGPT. The "true personal assistant" distinction: runs on your hardware, knows your data, takes real action, model-agnostic.
3. The proprietary mirror: Apple Intelligence, Gemini Nano on-device. One paragraph placing them in Phase 4 as the closed counterpart. Bracket what this series covers vs what it does not.
4. The ecosystem map: OpenClaw, ZeroClaw, NanoClaw, memU, Hermes, NemoClaw. One paragraph each: what it is and who it is for. Ollama and Open WebUI mentioned as the substrate.
5. The mobile gap: "always on, accessible anywhere" is partially unsolved across all six tools. One sentence.
6. The security crisis as a growth signal, not a death knell. CVE arc shows the space is real. [citations]
7. Series roadmap and teaser to Article 2.

**Enterprise reframe:** "Why builders of the enterprise versions of these systems are paying attention to the open-source personal versions."
**Length:** 800–1,000 words

---

### Article 2 — The Reference

**Type:** Hands-on plus verdict
**Hook:** Connecting an Obsidian vault to WhatsApp in 20 minutes. Zero cloud. Here is what happened.

**Sections:**
1. Setup experience, three observations. Not step-by-step. Full setup notes linked to Track B post A.
2. The demo: on-demand vault query via WhatsApp. One concrete example.
3. The demo: daily briefing. What it pulls, how it reads, whether it is actually useful.
4. Local model vs Claude API: quality, speed, privacy trade-off. One paragraph.
5. Security caveat: current CVE status [cite].
6. Honest verdict and teaser to Article 3.

**Enterprise reframe:** "What enterprise architects notice about OpenClaw's architecture that a hobbyist reviewer would miss."
**Length:** 700–1,000 words

---

### Article 3 — The Memory Bet

**Type:** Hands-on plus argument
**Hook:** Most AI assistants forget everything between sessions. memU bets that is the wrong design.

**Sections:**
1. The memory-first philosophy. Why most AI assistants forget and why memU bets that is the wrong design.
2. Setup and configuration. What "teaching" memU about yourself actually looks like. Full notes linked to Track B post D.
3. Same vault queries, but with accumulated context. How does memory change the answers?
4. The privacy question: a model of you is valuable and vulnerable. What memU does about it.
5. Does persistent memory make the assistant genuinely more useful, or just more familiar?
6. Verdict and teaser to Article 4.

**Enterprise reframe:** "Persistent memory in personal AI maps directly onto a hard problem in enterprise AI governance. Here is what the personal version teaches about the enterprise version."
**Length:** 700–1,000 words

---

### Article 4 — The Lock-In Question

**Type:** NVIDIA API hands-on plus documentation analysis
**Hook:** NVIDIA's enterprise response to the OpenClaw security crisis, and the trade-off it introduces.

**Sections:**
1. The shadow AI reality: enterprise adoption of OpenClaw without IT approval [cite]. CISO-relevant.
2. What NemoClaw adds: OpenShell kernel-level sandboxing, audit trails, Nemotron models, manifest-signed skills. [citations]
3. The hardware reality: DGX-only deployment, NVIDIA AI Enterprise licensing required [cite]. What this means for most organisations.
4. NVIDIA API as the accessible path. What you get (Nemotron model quality), what you give up (the full security stack).
5. The vendor lock-in question. NVIDIA solves security by owning the full stack. Is that the right trade?
6. Compliance angle: DPDP, GDPR, HIPAA. What changes when "shadow AI on a laptop" becomes "regulated AI in a regulated industry."
7. Verdict: right answer for whom, wrong answer for whom. Teaser to Article 5.

**Transparency note:** Hands-on via NVIDIA API catalog. DGX architecture covered via documentation. Explicit about what was and was not tested live.
**Enterprise reframe:** "We have evaluated enterprise trade-offs like this one. Here is what NVIDIA gets right and where the lock-in becomes the cost."
**Length:** 800–1,000 words

---

### Article 5 — The Verdict

**Type:** Synthesis, no setup
**Hook:** Six tools. Several weeks. Here is the framework that holds up.

**Sections:**
1. Revisiting the thesis: Phase 4 is real. The experiment confirmed it. What changed in our view from Article 1 to here.
2. The comparison table. All six tools across: setup friction (1–5), answer quality on same vault queries, security posture, resource usage, enterprise readiness, best-fit use case.
3. The build-on-top question (where Hermes lives in this map): when to fork OpenClaw, when to host Hermes, when to buy NemoClaw. A CTO-level decision framed as an architect question.
4. The security arc in full: from crisis to patches to where things actually stand. Supply chain remains the hard unsolved problem.
5. The NVIDIA lock-in question: final verdict.
6. Enterprise-tier recommendation framework: "If your team is already running OpenClaw without IT approval, here is how to legitimise it. If your CISO is evaluating, here is the question to ask first."
7. What kept running after the experiment ended.
8. Where Phase 4 goes next: the 12-month view.

**Enterprise reframe:** Runs through the entire article. This is the senior-practitioner piece.
**Length:** 1,000–1,200 words

---

## Citation Discipline (Mandatory)

Every specific number needs a sourced URL and an as-of date before drafting begins. If a number cannot be sourced, replace it with a range or remove it.

| Claim | Source needed | Status |
|---|---|---|
| OpenClaw 367K stars in 6 months | GitHub direct, dated | Open |
| ZeroClaw sub-10ms startup, 3.4MB binary | Project README, release notes | Open |
| NanoClaw 4,000 lines, 26K stars | Repo line count plus stars, dated | Open |
| memU privacy model details | Project docs | Open |
| Hermes architecture and intended use | Project docs | Open |
| NemoClaw DGX-only, NVIDIA AI Enterprise licensing | NVIDIA product page | Open |
| OpenShell kernel-level sandboxing | NVIDIA docs | Open |
| "22% of enterprises running OpenClaw without IT approval" | Survey citation (Gartner/Forrester/vendor) | Open |
| Current CVE status per tool | NVD or vendor advisories | Open |
| "9 CVEs in 4 days" type claims | Specific advisory IDs | Open |

---

## Cross-Cutting Themes (Persist Across Track A)

1. **The Phase 4 thesis** — Each Track A article places the tool in the arc.
2. **The enterprise lens** — Every Track A article carries an explicit "Enterprise reframe" beat.
3. **The same test** — Identical Obsidian vault, identical queries across all hands-on work.
4. **The security arc** — Each hands-on article notes current CVE status. Article 5 synthesises the full picture.
5. **The regulatory frame** — Article 4 carries DPDP/GDPR/HIPAA. Article 5 acknowledges where compliance changes the calculus.
6. **Honest over enthusiastic** — What does not work gets said plainly.

---

## Voice Rules

- No em dashes. Short sentences instead.
- No rhetorical questions.
- Do not open any article or LinkedIn post with "I."
- No opening sentence that is a compliment or scene-setter. Get to the substance.
- Specific over generic. Every claim tied to a real data point or real observation.
- Vary sentence length. Mix short and medium. Avoid uniform structure.
- Read-aloud test: if it sounds like a press release, rewrite it.
- One named voice editor reads everything before publish. Voice drift in a three-author series is the biggest quality risk.

---

## Work Split (To Be Agreed)

| Option | Track A | Track B | Byline |
|---|---|---|---|
| 1. Dual byline | Alternate per article | Alternate per setup | "By [A] and [B]" on every piece |
| 2. Lens-led | Lead author owns framing articles | Others own hands-on | "By [A] with [B]" |
| 3. Track-led | One author owns Track A | Others own Track B | Parallel series, mutual cross-promotion |

Decision needed before drafting begins.

---

## Repo File Map

| File / Folder | Purpose |
|---|---|
| `README.md` | What this repo is |
| `Series-Outline.md` | This file |
| `Writing-Guidelines.md` | Voice rules expanded for co-authors (to be created) |
| `Citation-Tables.md` | Sourcing tracker per article (to be created) |
| `track-a-opinion/` | Article drafts (Track A) |
| `track-b-receipts/` | Setup post drafts (Track B) |

---

*v1 — 2026-05-11 — Initial repo version. Cleaned of vault paths. Partnership confirmed (three co-authors). Work split and voice editor pending agreement.*
