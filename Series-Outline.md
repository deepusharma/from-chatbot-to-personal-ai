---
tags: [project, content-series, linkedin, openclaw, local-ai, agentic-ai]
category: "02-Projects"
status: "draft - pending partnership discussion"
created: 2026-05-10
last_updated: 2026-05-11
supersedes: Series-Outline_20260510_v1.md
---

# Series Outline v2: "Field Notes: Local AI Agents"
*An Enterprise Architect's Experiment*

---

## Status and Next Step

This is a working snapshot. It is not the final outline. Several decisions still depend on a conversation with one or two potential co-authors. Once those are resolved, v3 will lock in the partnership shape, the work split, the named voice editor, and whether this is a one-off series or the first run of a recurring publication format.

**Five questions to bring back from the partnership conversation:**

1. Does each potential partner buy the Phase 4 thesis?
2. Which work-split option fits the working relationship and available time?
3. Who is the named voice editor for the series?
4. Is this a one-off series or the first run of a recurring "three engineers, same vault, real verdicts" format?
5. Is the second potential partner in? Is the third potential partner in?

With those five answers, v3 writes itself.

Companion file: `04-Brainstorming/000.08_from-chatbot-to-personal-ai.md` holds the brainstorming context and the back-and-forth that produced this v2.

---

## What Changed From v1

| Area | v1 | v2 |
|---|---|---|
| Structure | Single track, 8 articles | Two tracks. Track A (opinion) at 5 articles. Track B (receipts) at 6 setup posts. |
| The Lens | Named AgenTwin, PrompTwin, Morpheus, Fractal | Fully abstracted. Personal capacity. "We are engineers who build enterprise AI for a living." |
| Phase 2 vs 3 | Underspecified | Phase 2 = humans orchestrate AI through workflows. Phase 3 = AI orchestrates itself within a defined task scope. |
| Apple Intelligence and on-device proprietary AI | Missing | One paragraph in Article 1 placing them in the arc. |
| Mobile native | Missing | One sentence in Article 1 acknowledging it as unsolved for these tools. |
| Regulatory/privacy framing | Missing | Bakes into Article 4 (NemoClaw and lock-in piece). |
| Enterprise lens persistence | Lost in middle articles | Every Track A article has an explicit "What an enterprise builder notices" beat. |
| Citation discipline | Implicit | Mandatory citation block per article in the front-matter. Every specific number sourced before drafting. |
| Voice violations | Article 5 rhetorical-question title, Article 8 "I" opener, five uniform colon-titles | New Track A titles vary structure, no rhetorical questions, no "I" openers. |
| Hermes | Full dedicated article | Folded into Article 5 (The Verdict) as the build-on-top question a CTO actually faces (fork OpenClaw vs host Hermes vs buy NemoClaw). |
| ZeroClaw and NanoClaw | Dedicated Track A articles | Track B deep-dives. Referenced in Article 5 of Track A. |

---

## The Thesis (Tightened)

Four phases of how we relate to AI:

1. **LLMs** — You talk to AI. AI talks back. (ChatGPT, Claude, Gemini)
2. **Agentic Workflows** — Humans orchestrate AI through workflows. (LangChain, n8n, AutoGPT, enterprise agent platforms)
3. **Agents** — AI orchestrates itself within a defined task scope. Multi-agent systems sit here. (Devin, Copilot, custom agents)
4. **True Personal Assistants** — AI that knows YOU. Runs on YOUR hardware. Always on. Accessible anywhere. Not Siri. Not Alexa.

Apple Intelligence and Gemini Nano on-device sit as the proprietary mirror of Phase 4. OpenClaw and its ecosystem are the open-source counterpart, and the first credible open-source proof that Phase 4 is here.

This series tests that proof. Same knowledge base (Obsidian vault). Same queries. Six tools. Honest verdicts.

---

## The Lens (Abstracted)

We are engineers who build enterprise AI for a living. This series tests the open-source personal versions of what we ship to large organisations. That perspective does not appear elsewhere in coverage of this space.

Written in personal capacity. No employer affiliation, no product references, no proof-points beyond the experiment itself. The credibility is in the analysis, not the resume.

---

## Series Metadata

| Field | Value |
|---|---|
| Series name (Track A) | From Chatbot to Personal AI |
| Series name (Track B) | From Chatbot to Personal AI: Field Notes (setup and receipts track) |
| Track A primary platform | LinkedIn Articles |
| Track A secondary platform | Medium publication, canonical URL pointing back to LinkedIn, published 7–14 days later, slightly altered opening |
| Track B primary platform | Medium publication |
| Track B secondary platform | GitHub repo for configs and scripts |
| Track A length | 700–1,000 words per article |
| Track B length | 1,500–2,500 words per setup post |
| Track A cadence | Roughly weekly, soft, with buffer built |
| Track B cadence | When ready, no schedule pressure |
| Test bed | Single Obsidian vault, same queries across all hands-on work |
| Drafts location | `02-Projects/FromChatbotToPersonalAI/Drafts/` |
| Published location | `01-Career/LinkedIn/Published/` and Medium publication |

---

## Two-Track Structure

### Track A — The Verdict (5 articles, LinkedIn primary)

| # | Title (working) | Type | Length | Lead role |
|---|---|---|---|---|
| 1 | The Map | Research and analysis, no setup | 800–1,000 words | Strategic/framing |
| 2 | The Reference | OpenClaw verdict, what it proves | 700–1,000 words | Hands-on plus lens |
| 3 | The Memory Bet | memU as contrarian thesis on persistent memory | 700–1,000 words | Hands-on plus lens |
| 4 | The Lock-In Question | NemoClaw, shadow AI, NVIDIA's enterprise answer | 800–1,000 words | CISO/VP-Eng-targeted |
| 5 | The Verdict | Synthesis, framework, what kept running, 12-month view | 1,000–1,200 words | Strategic/framing |

### Track B — The Receipts (6 setup posts, Medium primary)

| # | Title (working) | Tool | Length |
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
1. The four phases. Brief, punchy. Phase 2 vs 3 distinction made explicit (orchestration burden as the discriminator).
2. Why this is different from Siri, Alexa, ChatGPT. The "true personal assistant" distinction: runs on your hardware, knows your data, takes real action, model-agnostic.
3. The proprietary mirror: Apple Intelligence, Gemini Nano on-device. One paragraph placing them in Phase 4 as the closed counterpart. Bracket what this series covers vs what it does not.
4. The ecosystem map: OpenClaw, ZeroClaw, NanoClaw, memU, Hermes, NemoClaw. One paragraph each: what it is and who it is for. Ollama plus Open WebUI mentioned as the substrate.
5. The mobile gap: "always on, accessible anywhere" is partially unsolved across all six tools today. One sentence, not a paragraph.
6. The security crisis as a growth signal, not a death knell. CVE arc shows the space is real. [citations]
7. Series roadmap and a teaser to Article 2.

**Enterprise reframe:** "Why a builder of the enterprise versions of these systems is paying attention to the open-source personal versions."
**Length:** 800–1,000 words

---

### Article 2 — The Reference

**Type:** Hands-on plus verdict
**Hook:** "Connecting an Obsidian vault to WhatsApp in 20 minutes. Zero cloud. Here is what happened."

**Sections:**
1. Setup experience, three observations. Not step-by-step. Full setup notes linked to Track B post A.
2. The demo: on-demand vault query via WhatsApp. One concrete example.
3. The demo: daily briefing. What it pulls, how it reads, whether it is actually useful.
4. Local model vs Claude API: quality, speed, privacy trade-off. One paragraph.
5. Security caveat: current CVE status [cite].
6. Honest verdict and teaser to Article 3.

**Enterprise reframe:** "What an enterprise architect notices about OpenClaw's architecture that a hobbyist reviewer would miss."
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

**Enterprise reframe:** "Persistent memory in personal AI maps directly onto a hard problem in enterprise prompt governance. Here is what the personal version teaches about the enterprise version."
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
**Enterprise reframe:** "I have sold customers on enterprise trade-offs like this one. Here is what NVIDIA gets right and where the lock-in becomes the cost."
**Length:** 800–1,000 words

---

### Article 5 — The Verdict

**Type:** Synthesis, no setup
**Hook:** Six tools. Several weeks. Here is the framework that holds up.

**Sections:**
1. Revisiting the thesis: Phase 4 is real. The experiment confirmed it. What changed in our view from Article 1 to here.
2. The comparison table. All six tools across:
   - Setup friction (1–5)
   - Answer quality on same vault queries
   - Security posture (current CVE status)
   - Resource usage
   - Enterprise readiness
   - Best-fit use case
3. The build-on-top question (where Hermes lives in this map): when to fork OpenClaw, when to host Hermes, when to buy NemoClaw. A CTO-level question reused as the architect-level argument.
4. The security arc in full: from crisis to patches to where things actually stand. Supply chain remains the hard unsolved problem.
5. The NVIDIA lock-in question: final verdict.
6. Enterprise-tier recommendation framework. Not "personal use → OpenClaw." Instead: "If your team is already running OpenClaw without IT approval, here is how to legitimise it. If your CISO is evaluating, here is the question to ask first."
7. What kept running after the experiment ended.
8. Where Phase 4 goes next: the 12-month view.

**Enterprise reframe:** Runs through the entire article. This is the senior-practitioner piece.
**Length:** 1,000–1,200 words

---

## Citation Discipline (Mandatory)

Every specific number in the series needs a sourced URL and an as-of date before the draft begins. Build this block into every article's front-matter. If a number cannot be sourced, replace it with a range or remove it.

Initial citation table to source tonight, regardless of partnership outcome:

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

If any of these do not hold up to sourcing, the v3 outline trims the claim.

---

## Work-Split Options (Three to Discuss)

| Option | Track A primary | Track B primary | Implied byline | Best when |
|---|---|---|---|---|
| **1. Dual byline, balanced** | Alternate per article | Alternate per setup | "By [Name] and [Name]" on every piece | Roughly equal effort and equal seniority |
| **2. Lens-led** | Deepak (opinion, framework) | Co-author (hands-on, technical) | "By [Name] with [Name]" — clear lead and contributor | Asymmetry in tenure or lens depth |
| **3. Track-led** | Deepak owns Track A | Co-author owns Track B | Two parallel series, mutual cross-promotion | Both want independent author surfaces |

**Honesty note on Option 1**: even with a 2-2-1 article-count split across three people, whoever owns Article 1 (The Map) and Article 5 (The Verdict) carries the editorial spine of the series. The middle pieces are downstream of the framework set in Article 1. The actual influence split is closer to 60-20-20 even when the article count looks like 2-2-1. Worth being honest about that with partners up front.

---

## Partnership Scenarios

### Scenario A — Solo

If no partnership materialises, the two-track structure probably collapses. Workload solo across both tracks is roughly 100+ hours.

Adjusted shape: keep Track A as 5 opinion articles. Drop Track B as a series. Setup details get linked out as standalone Medium posts published whenever ready. No commitment to setup cadence. Total workload around 60 hours.

### Scenario B — Two-person partnership

The two-track structure works. Lens-led work split (Option 2) is the honest match if the co-author is recently promoted, less tenured, practitioner-architect. Total workload around 30–50 hours per person.

LinkedIn co-author mechanics: alternate primary author per article, credit co-author in first line, non-author cross-shares from their account.

### Scenario C — Three-person partnership

Highest credibility frame: "three independent senior architects ran the same experiment on the same vault and reached different conclusions on which tool fits which job." Three-person disagreement reads as a finding, not a debate. Two-person disagreement reads as a debate.

LinkedIn rotation: Article 1 from Author A, Article 2 from B, Article 3 from C, Article 4 from A, Article 5 from B. Each name carries the byline at least once. Others cross-share.

Track B distribution: 6 setup posts divided across 3 people = 2 each. Clean split.

Total workload around 20–35 hours per person.

**Risks specific to three-person:**
- Voice drift compounds. One named voice editor is non-negotiable.
- Dropout risk goes up with three calendars. Mitigation: complete Articles 1, 2, and 5 of Track A plus OpenClaw and memU Track B setups before publishing anything. Roughly 40% in the bank before the public cadence starts.
- Decision protocol needs explicit tiebreakers per axis, not just majority vote. Voice editor tiebreaks on editorial calls. Technical lead tiebreaks on tool-setup calls. Audience-and-positioning tiebreaks on framing calls. Prevents 2-vs-1 dynamics from becoming personal.

**Diagnostic question for the third partner:**
Does the third person bring a different lens, or another instance of the same lens? Different-lens trio gets sharper analysis. Same-lens trio gets stronger credibility ("three independent senior architects agreed"). Both work. Decide intentionally.

---

## Cross-Cutting Themes (Persist Across Track A)

1. **The Phase 4 thesis** — Each Track A article places the tool in the arc.
2. **The enterprise lens** — Every Track A article carries an explicit "Enterprise reframe" beat to keep the senior-audience altitude.
3. **The same test** — Identical Obsidian vault, identical queries across all hands-on work.
4. **The security arc** — Each hands-on article notes current CVE status. Article 5 synthesises the full picture.
5. **The regulatory frame** — Article 4 carries DPDP/GDPR/HIPAA. Article 5 acknowledges where compliance changes the calculus.
6. **Honest over enthusiastic** — What does not work gets said plainly.

---

## Voice Rules (from Voice-Preferences.md, Applied Here)

- No em dashes. Short sentences instead.
- No rhetorical questions. (Caught in v1: Article 5 title. Fixed in v2.)
- Do not open any article or LinkedIn post with "I." (Caught in v1: Article 8 title. Fixed in v2.)
- Vary title structure across the series. (Caught in v1: five of six tool-titles used `Toolname: subtitle`. Fixed in v2.)
- No opening sentence that is a compliment or scene-setter. Get to the substance.
- Specific over generic. Every claim tied to a real data point or real observation.
- Vary sentence length. Mix short and medium. Avoid uniform structure.
- Read-aloud test: if it sounds like a press release, rewrite it.
- Co-author voice drift: one named voice editor reads everything aloud before publish.

---

## Voice-Editor Decision (Critical for Multi-Author)

If two or more authors, one of them is the named voice editor. The voice editor reads every piece aloud before publish and reconciles drift to a single shared voice.

Two choices on how the editor edits:
- **Heavier hand**: editor edits everything into their own voice. More coherent series, less distinct author voices.
- **Lighter hand**: editor preserves each author's voice and only catches AI-tells and rule violations. Authentic three-person feel, slightly less coherent.

Recommended: heavier hand for the senior-audience track. Three voices in a CPO-targeted opinion piece reads as committee. One unified voice reads as a partnership with shared conviction.

---

## File Map

| File | Purpose |
|---|---|
| `02-Projects/FromChatbotToPersonalAI/Series-Outline_20260510_v1.md` | v1 outline (superseded) |
| `02-Projects/FromChatbotToPersonalAI/Series-Outline_20260511_v2.md` | This file. v2 working draft. |
| `04-Brainstorming/000.08_openclaw-series.md` | Brainstorming session notes (to be updated after partnership conversation) |
| `02-Projects/FromChatbotToPersonalAI/Drafts/Article-1_The-Map.md` | Article 1 draft (to be created post-v3 lock) |
| `02-Projects/FromChatbotToPersonalAI/Drafts/Article-2_The-Reference.md` | Article 2 draft (to be created post-v3 lock) |
| `02-Projects/FromChatbotToPersonalAI/Drafts/Article-3_The-Memory-Bet.md` | Article 3 draft (to be created post-v3 lock) |
| `02-Projects/FromChatbotToPersonalAI/Drafts/Article-4_The-Lock-In-Question.md` | Article 4 draft (to be created post-v3 lock) |
| `02-Projects/FromChatbotToPersonalAI/Drafts/Article-5_The-Verdict.md` | Article 5 draft (to be created post-v3 lock) |
| `02-Projects/FromChatbotToPersonalAI/Setups/` | Track B setup post drafts (to be created post-v3 lock) |

---

## Open Decisions (Bring Back from Partnership Conversation)

1. **Thesis buy-in** from each potential partner. If anyone does not buy Phase 4, the partnership does not work.
2. **Work split**: Option 1 (dual byline), Option 2 (lens-led), or Option 3 (track-led).
3. **Named voice editor**.
4. **One-off vs recurring format**. Is "three engineers, same vault, real verdicts" a single Phase 4 series or the first run of a publishable format that gets reused for other domains? Decide up front because it changes naming, publication setup, and visual identity work.
5. **Third partner in or out**. And if in, same-lens or different-lens trio?
6. **Series name for Track A**. Candidates: "The Phase 4 Verdict," "Where Personal AI Actually Stands," "Local AI: Field Verdicts."
7. **Whose vault is the test bed?** Recommended: Deepak's, since methodology depends on a single consistent vault.

---

## Work That Starts Tonight Regardless of Partnership Outcome

1. **Source every number in the citation table above.** This work is identical whether one, two, or three people end up on the byline. If a number does not source, trim or replace it before v3.
2. **Confirm the Track A title.** Three working candidates above. Decide.
3. **Stand up the Medium publication shell** (name placeholder, both/three author seats placeholder). Cheap to do now, expensive to delay.

---

*Version history:*
*v1 — 2026-05-10 — Initial outline. 8 articles. Narrative arc added. Hermes included. Timeline constraint removed. Opus evaluation criteria written.*
*v2 — 2026-05-11 — Pending partnership discussion. Two-track structure (Track A opinion, 5 articles; Track B receipts, 6 setups). Lens fully abstracted to personal capacity. Phase 2 vs 3 tightened. Apple Intelligence, mobile gap, regulatory framing added. Hermes folded into Article 5. ZeroClaw and NanoClaw moved to Track B. Voice violations from v1 fixed. Citation discipline made mandatory. Three partnership scenarios (solo, two-person, three-person) documented. Five open decisions flagged for the conversation.*
