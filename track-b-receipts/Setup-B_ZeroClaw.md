---
title: "ZeroClaw: a Rust rewrite, benchmarked honestly"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: ZeroClaw
status: placeholder
author: TBD
word-target: 1500-2000
publishes-first: medium
cross-post: linkedin (7 days after)
track-a-link: "../track-a-opinion/Article-5_The-Verdict.md"
test-bed: Obsidian vault (same vault, same queries as Setup-A)
---

# ZeroClaw: a Rust rewrite, benchmarked honestly

*Hands-on setup and benchmark. Referenced in Article 5: The Verdict.*

---

## What ZeroClaw Is

<!-- The philosophy: performance, binary size, edge deployment.
     Why it exists. [cite sub-10ms startup, 3.4MB binary]

     ZeroClaw is a Rust rewrite of the OpenClaw core, optimised for startup time and
     binary size. The headline numbers [cite: sub-10ms startup, 3.4MB binary] come from
     the project README — verify them against your actual setup and note any gap. Explain
     why those numbers matter for the environments where ZeroClaw has an advantage over
     OpenClaw. -->

---

## Prerequisites

<!-- Hardware, OS, dependencies.

     What differs from the OpenClaw prerequisites — specifically whether a Rust toolchain
     is required for a source build or if a pre-compiled binary is available for download.
     Specify the binary version or source commit hash used for reproducibility. -->

---

## Installation

<!-- Binary download or build from source. Actual steps taken.

     Document whether you used a pre-built binary or compiled from source. If compiled:
     Rust version, build flags, any compilation errors encountered. If binary: how the
     binary was verified before running. Note the total install footprint. -->

---

## Connecting the Obsidian Vault

<!-- Same vault as OpenClaw setup. What is different about the configuration.

     Use the same vault as the OpenClaw setup. Document what is different about ZeroClaw's
     vault configuration — config file format, indexing approach, path handling — or confirm
     explicitly that it is identical to OpenClaw. Either answer is useful to readers
     migrating from one tool to the other. -->

---

## The Same Test Queries

<!-- Same three queries from Setup A. Record actual results here. -->

<!-- Same three queries as Setup A. Record ZeroClaw's actual responses verbatim — do not
     summarize. The quality comparison in Article 5 depends on the real output text, not
     an impression of it. -->

**Query 1:** [query text]
**Result:** [actual output]

**Query 2:** [query text]
**Result:** [actual output]

**Query 3:** [query text]
**Result:** [actual output]

---

## Performance Comparison vs OpenClaw

<!-- Startup time, response time, memory usage, CPU.
     Actual measured numbers, not spec sheet claims. -->

<!-- Fill the table with actual measured numbers from the same hardware, using the same
     timing method for both tools. The goal is an honest apples-to-apples comparison.
     Use htop or Activity Monitor; do not rely on self-reported metrics from either tool. -->

| Metric | ZeroClaw | OpenClaw |
|---|---|---|
| Startup time | | |
| Response time (query 1) | | |
| Memory at rest | | |
| Memory under load | | |
| Binary/install size | | |

---

## What "Sub-10ms Startup, 3.4MB Binary" Means in Daily Use

<!-- Real difference or spec sheet number? Honest assessment.

     Does the startup speed advantage matter in practice? If the agent runs as a background
     service, startup time is irrelevant; if it is invoked per query, it matters. Give an
     honest assessment of whether the headline spec translates to a perceptible difference
     in day-to-day use on the hardware used for this test. -->

---

## What Surprised Us

<!-- Same format as Setup A: two or three specific technical observations, no general
     impressions. Focus on what the Rust rewrite changed architecturally, not just in
     performance numbers. -->

---

## What Did Not Work

<!-- Same format as Setup A: honest account of failures and workarounds, and whether
     those workarounds are stable. Note if any OpenClaw features are absent in ZeroClaw. -->

---

## Security Notes

<!-- Current CVE status at time of setup. [cite]

     ZeroClaw CVE status as of setup date [cite]. A Rust rewrite may have a different
     vulnerability surface than the Python original — note if any known issues differ
     in type or severity from OpenClaw's CVE history. -->

---

## Who This Is Actually For

<!-- Edge, embedded, resource-constrained environments.
     Where it falls short for personal assistant use.

     Name the specific environments where ZeroClaw's binary size and startup speed create
     real value: edge deployment, resource-constrained hardware, embedded systems. Name the
     environments where those advantages do not matter and OpenClaw is the better starting
     point. This is the honest use-case verdict — not a recommendation, a map. -->

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
