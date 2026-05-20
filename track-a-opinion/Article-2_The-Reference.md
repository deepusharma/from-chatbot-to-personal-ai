---
title: "The Reference"
series: "From Chatbot to Personal AI"
track: A
status: draft
author: TBD
word-target: 700-1000
publishes-first: linkedin
cross-post: medium (7 days after)
track-b-link: "../track-b-receipts/Setup-A_OpenClaw.md"
---

# The Reference

*[Full setup notes: Setup-A_OpenClaw.md]*

---

## Setup: Three Observations

The step-by-step is in the Track B post. Three things worth naming here that the docs do not prepare you for.

**Observation 1:** [FILL: one paragraph — what was easier than expected, what that reveals about how OpenClaw is designed. Specific and architectural, not a general impression. Example register: "The installer handles Node version conflicts automatically, which tells you something about how often that comes up."]

**Observation 2:** [FILL: one paragraph — what required a workaround and what the workaround reveals. The WhatsApp QR code stability, the Gatekeeper block, or whatever actually caused friction. One specific thing that did not match the docs.]

**Observation 3:** [FILL: one paragraph — what the architecture reveals that surface-level usage would not show. Something a practitioner who reads code would notice. This is the observation that feeds the enterprise reframe below.]

---

## The Demo: On-Demand Vault Query

[FILL: pick one of the three test queries and paste the actual output verbatim or near-verbatim. Set it up in one sentence — what you asked and why that query tests something real. Then show the output. Do not summarize it. The specificity is the point.]

One thing to note about the output: [FILL: one honest observation — where it was better than expected, where it was wrong or incomplete, or what the response reveals about how OpenClaw retrieves from the vault.]

---

## The Demo: Daily Briefing

[FILL: describe the daily briefing specifically. What it pulled from the vault, how the output read, whether you would actually use it every day. If the answer is "impressive the first time, off after a week," say that. The Track B post has the config details; this section is the honest user experience.]

---

## Local Model vs Claude API

[FILL: one paragraph comparing the two paths on the three test queries. Name the actual Ollama model used. Note which query type showed the biggest quality difference — synthesis queries (blockers, decisions) tend to separate small local models from large cloud ones faster than summarization queries. Name the trade-off plainly: local is private and free, the gap on complex queries is real.]

---

## Security Caveat

OpenClaw has 138 disclosed CVEs across its first five months [cite: jgamblin/OpenClawCVEs]. The one most relevant to this exact setup is CVE-2026-25253: a cross-site WebSocket hijacking vulnerability in the local WebSocket server that the ObsidianClaw plugin connects through [cite: oasis.security]. [FILL: note the patch status of CVE-2026-25253 in the version installed. Two sentences maximum.]

The full security arc runs through Article 5. For this setup: verify the version you install has patches for the WebSocket advisory before running it with a browser open.

---

## Verdict

[FILL: two honest sentences. What OpenClaw delivers and where it falls short. What you would change about the setup if doing it again. Do not hedge — land on a position.]

The next article tests whether the thing OpenClaw most conspicuously lacks — memory between sessions — is actually a problem worth solving, or whether the solution creates problems of its own.

---

## Enterprise Reframe

[FILL: one specific observation a hobbyist reviewer would not make. Candidates from the setup: how OpenClaw's skill architecture maps onto enterprise plugin governance, what the WebSocket design reveals about the security model's original assumptions, or how the local-vs-cloud model choice maps onto data residency decisions enterprise teams make at scale. Be specific — name the architectural observation, then the enterprise implication.]

---

*Status: Draft. Most sections require real setup data. Fill during and after the Setup-A session. The enterprise reframe should come from a genuine observation during setup, not be reverse-engineered from what sounds smart.*

---

## Three Takes

**[Author A]:**

**[Author B]:**

**[Author C]:**

---

## LinkedIn Post

[FILL: open with the single strongest observation from the setup — not "I connected my vault to WhatsApp" but the specific surprising or non-obvious thing that happened. One or two supporting lines. End with "Full article linked." No scene-setter, no "I just published." Get to the substance on line one.]
