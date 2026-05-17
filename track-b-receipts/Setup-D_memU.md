---
title: "memU: configuring persistent memory for a personal AI"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: memU
status: placeholder
author: TBD
word-target: 1800-2200
publishes-first: medium
cross-post: linkedin (7 days after)
track-a-link: "../track-a-opinion/Article-3_The-Memory-Bet.md"
test-bed: Obsidian vault (same vault, same queries as Setup-A)
note: Memory accumulates over time — document the before and after states separately.
---

# memU: configuring persistent memory for a personal AI

*The full setup notes behind Article 3: The Memory Bet.*

---

## What memU Is

<!-- Memory-first architecture. How it differs from stateless agents.

     memU is a persistent memory layer that wraps or extends a base agent like OpenClaw —
     unlike stateless agents where each session starts blank, memU stores structured facts
     about the user across sessions. Describe the architecture in one sentence: where memory
     is stored, how it is retrieved during a session, and how it integrates with the base
     agent. This sets the frame for everything that follows. -->

---

## Prerequisites

<!-- List what is required. Note if memU requires the base agent (OpenClaw) to already be
     installed and running, or if it can run independently. Specify versions. -->

---

## Installation

<!-- Actual steps taken, delta from docs where applicable. Note any config that must be
     done before first run to avoid memory being stored in unintended locations. -->

---

## Connecting the Obsidian Vault

<!-- Same vault as other setups. Note if memU's memory layer interacts with vault content
     differently from base OpenClaw — does it index vault content into the memory store,
     or treat them as separate knowledge sources? -->

---

## What "Teaching" memU About Yourself Looks Like

<!-- The onboarding process. What information was provided,
     how it was structured, how long it took.

     Walk through the onboarding concretely: what information you provided, in what format,
     and how long before the memory felt meaningful in actual responses. Include one specific
     example — something you taught memU in one session and what it correctly recalled in a
     later session. The technical config is in the Installation section; this is the user
     experience of it, written for someone deciding whether to bother with the onboarding
     investment. -->

---

## The Same Test Queries — Before Memory Accumulates

<!-- Run the standard three queries in the first session before meaningful memory has
     accumulated. These are the baseline results for the memory comparison — record
     verbatim output. -->

**Query 1:** [query text]
**Result (session 1):** [actual output]

**Query 2:** [query text]
**Result (session 1):** [actual output]

**Query 3:** [query text]
**Result (session 1):** [actual output]

---

## The Same Test Queries — After Memory Accumulates

<!-- Same queries after several sessions. Document the delta.

     Same three queries after multiple sessions of use. For each query, document the actual
     delta: what changed in the output and what stayed the same. If a query improved, show
     the before and after output verbatim — the evidence needs to be visible, not described.
     If a query did not change, say so plainly. This section is the core evidence for
     Article 3's argument about whether persistent memory is useful or just familiar. -->

**Query 1:** [query text]
**Result (after memory):** [actual output]
**What changed:**

**Query 2:** [query text]
**Result (after memory):** [actual output]
**What changed:**

**Query 3:** [query text]
**Result (after memory):** [actual output]
**What changed:**

---

## Where the Memory Is Stored

<!-- Local vs cloud. File format. What is actually persisted.

     Local filesystem path, file format (JSON, SQLite, or other), whether any cloud sync
     is involved. One short paragraph — factual, not reassuring. A reader should be able
     to locate and inspect the memory store after reading this section. -->

---

## Privacy Configuration

<!-- What controls exist. What was changed from defaults and why.

     What controls exist over what gets stored, how to delete specific memories, and what
     the default settings are versus what was changed during this setup and why. Be concrete
     — no "takes privacy seriously" language. Name the config keys and what they do. -->

---

## What Surprised Us

<!-- Same format as other setups: two or three specific observations about the memory
     architecture or behavior that a surface-level review would not reveal. -->

---

## What Did Not Work

<!-- Honest account of memory failures, incorrect recalls, or instability encountered.
     Note if the memory store required any cleanup between sessions. -->

---

## Security Notes

<!-- Current CVE status. [cite]

     memU CVE status as of setup date [cite]. Note any specific risks introduced by
     persistent memory — the store is a higher-value target than a stateless agent. -->

---

## Resource Usage

<!-- Actual measured numbers at rest and under a query, with and without memory retrieval.
     Note if memory retrieval adds meaningful latency to query response time. -->

---

*Status: Placeholder. Replace this line when drafting begins.*

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
