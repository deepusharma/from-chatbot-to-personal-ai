---
title: "NemoClaw via the NVIDIA API catalog (with DGX context)"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: NemoClaw
status: placeholder
author: TBD
word-target: 1500-2000
publishes-first: medium
cross-post: linkedin (7 days after)
track-a-link: "../track-a-opinion/Article-4_The-Lock-In-Question.md"
test-bed: NVIDIA API catalog (Nemotron model). DGX architecture via documentation.
transparency-note: Full NemoClaw stack (OpenShell sandboxing, audit trails) requires DGX hardware not available for this setup. This post covers the NVIDIA API path and architecture analysis only. Be explicit about this throughout.
---

# NemoClaw via the NVIDIA API catalog (with DGX context)

*The full setup notes behind Article 4: The Lock-In Question.*

*Transparency: Hands-on testing was done via the NVIDIA API catalog using Nemotron models. The full NemoClaw stack — OpenShell kernel-level sandboxing, audit trails, manifest-signed skills — requires DGX hardware or DGX Cloud and is covered here through documentation and architecture analysis, not live testing. This distinction is made explicit wherever it matters.*

---

## What NemoClaw Is

<!-- NVIDIA's enterprise response to the OpenClaw security crisis.
     What it adds over base OpenClaw. [cite each feature]

     NemoClaw is NVIDIA's enterprise fork of OpenClaw, adding four security and governance
     features over the base tool: OpenShell kernel-level sandboxing, audit trails, Nemotron
     models, and manifest-signed skills [cite each feature with NVIDIA docs]. These additions
     exist to make OpenClaw deployable in regulated enterprise environments. One paragraph
     covering all four — what each is, not just that it exists. -->

---

## Two Ways to Access It

<!-- Path 1: Full NemoClaw stack (DGX hardware, NVIDIA AI Enterprise license)
     Path 2: NVIDIA API catalog (Nemotron model quality, without the security stack)

     Path 1 (DGX): full NemoClaw stack on DGX hardware with NVIDIA AI Enterprise licensing
     — gets you the complete security stack. Requires hardware most organisations do not
     have, and a licensing agreement to match. Path 2 (API catalog): Nemotron model quality
     through a cloud API, no hardware required, but the security stack is unavailable. This
     post follows Path 2 with documentation-based analysis of Path 1. Be explicit about
     this split at the start and wherever it matters throughout. -->

---

## Path Taken: NVIDIA API Catalog

### Prerequisites

<!-- Document the API catalog setup: account creation requirements, API key provisioning,
     any allowlisting or approval process encountered. Note the specific Nemotron model
     and version used. These steps should be reproducible by any reader with an NVIDIA
     developer account. -->

### Setup

<!-- Actual API configuration steps: how queries are authenticated, what client library
     or curl pattern was used, and any rate limits encountered during testing. Include
     a minimal working example. -->

### The Same Test Queries via Nemotron

<!-- Same three standard queries as Setup A, run via the Nemotron API. Record actual
     results verbatim — the quality column in Article 5's comparison table depends on this
     output. Note the latency for each query alongside the result. -->

**Query 1:** [query text]
**Result:** [actual output]

**Query 2:** [query text]
**Result:** [actual output]

**Query 3:** [query text]
**Result:** [actual output]

### Model Quality vs OpenClaw (Local) vs Claude API

<!-- Fill the table with actual measured results. Use a consistent judgment rubric for
     quality — factual accuracy, instruction-following, answer completeness. Do not use
     vague adjectives like "better"; be specific about what Nemotron did differently on
     which query. -->

| | Nemotron (NVIDIA API) | Local model (OpenClaw) | Claude API |
|---|---|---|---|
| Answer quality | | | |
| Latency | | | |
| Cost | | | |

---

## The Full NemoClaw Stack: Architecture Analysis

<!-- Based on NVIDIA documentation. Clear that this was not tested live. -->

<!-- Cover each of the four security features through NVIDIA documentation, with explicit
     acknowledgment throughout that these were not tested live. For each feature, answer:
     what problem it solves, how it works technically, and what it costs in hardware,
     licensing, or operational complexity. Cite the specific NVIDIA docs for each claim. -->

### OpenShell Kernel-Level Sandboxing

<!-- What it is, what it prevents, which NVIDIA doc describes it [cite]. -->

### Audit Trails

<!-- What is logged, where logs go, what a compliance reviewer can extract from them. [cite] -->

### Manifest-Signed Skills

<!-- What signing covers, what it does not cover, and why it matters for supply chain
     integrity. [cite] -->

### DGX Hardware Requirement

<!-- What DGX is. Why standard cloud GPU VMs do not qualify. [cite]
     What NVIDIA AI Enterprise licensing covers. [cite]

     Explain what DGX-class hardware actually is and why commodity cloud GPU instances
     do not qualify for the full NemoClaw stack. Name the NVIDIA AI Enterprise licensing
     requirement [cite] and what it covers in practice. A reader considering this path
     needs to know the entry cost before going further. -->

---

## The Lock-In Trade-Off

<!-- NVIDIA owns the full stack. Security guaranteed by vendor control.
     What that means for an organisation evaluating this.

     NVIDIA's security answer requires NVIDIA hardware, NVIDIA licensing, and NVIDIA
     operational tooling throughout. One paragraph on what that means for an organisation
     with a multi-year infrastructure plan — stated plainly, without softening. This feeds
     directly into Article 4's central argument about vendor lock-in as a security
     trade-off, not just a procurement inconvenience. -->

---

## Security Notes

<!-- NemoClaw CVE status. [cite]

     NemoClaw CVE status as of the post date [cite]. Note whether the security additions
     — sandboxing, audit trails, manifest-signed skills — change the vulnerability surface
     area compared to base OpenClaw, or whether they add controls on top of the same
     underlying attack surface. -->

---

*Status: Placeholder. Replace this line when drafting begins.*

---

## LinkedIn Post

<!-- Short feed post driving to the Medium Article. Target ~200 words.
     Publish same day as the Medium Article.
     Main author publishes and tags the other two co-authors.
     Co-authors each repost with 3–4 bullets of their own take.

     WRITE: 3–5 specific observations from the setup — what was surprising,
     what differed from the docs, what a builder would want to know first.
     Not "we set up X." End with "Full setup notes on Medium [link]." -->

---

## Three Takes

<!-- 2–3 sentences per co-author in their own voice.
     Anchor question: "What surprised me most about this tool."
     First-person is fine here. Voice rules still apply: no em dashes,
     no rhetorical questions, specific over generic. -->

**[Author A]:**

**[Author B]:**

**[Author C]:**
