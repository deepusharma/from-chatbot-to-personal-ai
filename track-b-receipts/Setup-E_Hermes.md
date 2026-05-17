---
title: "Hermes: a self-hosted AI API for builders"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: Hermes
status: placeholder
author: TBD
word-target: 1800-2200
medium-article: primary
linkedin-article: cross-post-7d
linkedin-post: true
track-a-link: "../track-a-opinion/Article-5_The-Verdict.md"
test-bed: Obsidian vault (same vault, same queries as Setup-A — with caveat)
scope-note: Hermes is server/API-oriented, not a personal assistant. Vault queries used for comparison only. Document actual intended use case separately.
---

# Hermes: a self-hosted AI API for builders

*Hands-on setup of a self-hosted AI API. Referenced in Article 5: The Verdict.*

---

## What Hermes Is (and Is Not)

<!-- Server-oriented, developer-facing, API-first.
     Not a personal assistant. A self-hosted AI API.
     Who builds with Hermes rather than OpenClaw — and why.

     Hermes is a self-hosted AI API server — not a personal assistant. It exposes API
     endpoints that developers call programmatically, comparable to calling the OpenAI or
     Claude APIs but running on your own hardware. Who builds with Hermes rather than
     OpenClaw: teams needing shared AI infrastructure, developers building applications on
     a local model, or anyone wanting OpenAI-compatible endpoints with a self-hosted
     backend. Establish this clearly before the setup steps — the entire framing of
     this post depends on it. -->

---

## Prerequisites

<!-- Server or VM requirements. Document exactly what was used.

     Server or VM requirements — this differs from the personal-machine setups in other
     posts. Document exactly what was used: hardware spec, OS, Docker version if applicable,
     port requirements. Note the minimum viable hardware for a Hermes deployment that is
     actually useful, not just running. -->

---

## Installation

<!-- Actual steps taken, delta from docs where it applies. Note any port conflicts,
     permission issues, or service startup sequence that was not obvious from the
     documentation. Include exact commands where the docs are ambiguous. -->

---

## API Configuration

<!-- Endpoints, authentication, model configuration.

     Which endpoints are enabled, how authentication is configured, and how the model is
     selected and loaded. Include a minimal working example of a Hermes API call that
     demonstrates the configuration in action — curl or a short Python snippet. This is
     the section that proves to a builder whether Hermes does what they need. -->

---

## The Same Test Queries (with caveat)

<!-- This is not Hermes' intended use case. Document the caveat
     explicitly before the results. -->

<!-- Run the standard three queries via the Hermes API (curl or a script, not a chat
     interface). Document how the queries were sent. Acknowledge the caveat explicitly
     before the results: this is not Hermes' intended use case, and the comparison is for
     consistency across the series. The results feed into Article 5's comparison table. -->

*Note: These queries were run for comparison purposes only. Hermes is designed for programmatic API access, not conversational personal assistant use.*

**Query 1:** [query text]
**Result:** [actual output]

**Query 2:** [query text]
**Result:** [actual output]

**Query 3:** [query text]
**Result:** [actual output]

---

## What Hermes Enables That OpenClaw Cannot

<!-- Programmatic control, team-level deployment, custom integrations.
     Specific examples where possible.

     Programmatic API access with OpenAI-compatible endpoints, team-level model deployment
     where multiple clients share one model server, and custom integrations that a personal
     assistant interface cannot support. Give one specific example of each where possible
     from the actual setup — not hypothetical capabilities, but things that were actually
     demonstrated during this test. -->

---

## When to Choose Hermes Over OpenClaw

<!-- The build-on-top decision. Fork OpenClaw vs host Hermes vs buy NemoClaw.

     The build-on-top decision, stated as named conditions: fork OpenClaw when you need a
     customized personal assistant for one person with full code control; host Hermes when
     you need a shared model API for a team or application; evaluate NemoClaw when
     compliance requirements need a vendor SLA and you have the infrastructure. This section
     is the practitioner's answer to the architectural question raised in Article 5. -->

---

## What Surprised Us

<!-- Same format as other setups: two or three specific technical observations, focused on
     what Hermes does architecturally that a casual API user would not notice. -->

---

## What Did Not Work

<!-- Honest account of failures and workarounds. Note if any OpenAI-compatible features
     did not behave as expected, since that is the most common integration assumption. -->

---

## Security Notes

<!-- Current CVE status. [cite]

     Hermes CVE status as of setup date [cite]. Note any specific risks introduced by
     running an API server compared to a local personal assistant — network exposure,
     authentication gaps, or model access controls. -->

---

## Resource Usage

<!-- Server/VM resource consumption at rest and under load.

     Server or VM resource consumption at rest and under a query load. Note peak memory
     during model inference and whether the hardware used during testing represents a
     realistic minimum or a comfortable deployment spec. -->

---

*Status: Placeholder. Replace this line when drafting begins.*

---

## Medium Article

<!-- PRIMARY PUBLISH — Track B publishes on Medium first.
     The article body above is the draft for this.
     When ready: submit to the series Medium Publication.
     Add the published URL to frontmatter once live. -->

---

## LinkedIn Article

<!-- CROSS-POST — same content as the Medium Article above.
     Add as the opening line: "Originally published on Medium at [URL]."
     Publish 7 days after the Medium Article. -->

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
