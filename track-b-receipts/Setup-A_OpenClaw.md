---
title: "Setting up OpenClaw with an Obsidian vault and WhatsApp"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: OpenClaw
status: placeholder
author: TBD
word-target: 1800-2500
publishes-first: medium
cross-post: linkedin (7 days after)
track-a-link: "../track-a-opinion/Article-2_The-Reference.md"
test-bed: Obsidian vault (same vault, same queries across all setups)
---

# Setting up OpenClaw with an Obsidian vault and WhatsApp

*The full setup notes behind Article 2: The Reference.*

---

## Prerequisites

<!-- Hardware, OS, dependencies. What you need before you start.

     List the actual hardware, OS, and dependency versions used in this setup — macOS or
     Linux version, Docker version if used, Ollama version, and any minimum RAM or storage
     requirements discovered during setup. This is the reproducibility baseline; future
     readers need these specifics to troubleshoot on different hardware. Verify versions
     against what was actually used, not what the docs recommend. -->

---

## Installation

<!-- What was actually done. Not a copy of the official docs.
     The delta between docs and reality.

     What you actually did, in the order you did it — not a copy of the official docs. Note
     the delta between what the docs say and what reality required. If a step failed and
     you took a different path, document that path with the actual commands. Readers
     following this post are more likely to hit your detours than the happy path. -->

---

## Connecting the Obsidian Vault

<!-- How vault access was configured. What path, what permissions,
     what surprised.

     Describe how vault access was configured: the directory path used, permissions
     required, and whether the vault needs indexing or pre-processing before OpenClaw can
     query it. Note anything that surprised you — folder structure assumptions, character
     encoding issues, or symlink handling. Other setups reference this section as the
     canonical vault config baseline. -->

---

## Connecting WhatsApp

<!-- The integration method used. What worked, what required a workaround.

     Describe the integration method used (WhatsApp Web bridge, Baileys library, or other).
     Document what worked on the first try, what required iteration, and whether the
     connection is stable for daily use or fragile. If the integration method changes the
     security profile of the overall setup, note it explicitly here. -->

---

## Local Model vs API Setup

<!-- Ollama/Llama local setup OR Claude API — document whichever was used.
     Versions, config, any gotchas.

     Document whichever path was used: Ollama model name and version if local, or Claude
     API key configuration if API. Note any config tuning done — context window settings,
     system prompt changes, temperature adjustments. This section feeds directly into the
     quality comparison in Article 2, so be precise about what was running during the test
     queries. -->

---

## The Test Queries

<!-- Same queries used across all six tools. Record them here once,
     reference this file from other setups. -->

<!-- This file is the canonical source for the three standard queries used across all six
     setups. Record the exact query text here; other setup files reference back to this.
     Record OpenClaw's actual response verbatim or near-verbatim — the comparison across
     articles depends on the real output text, not a summary of it. -->

**Query 1:** [query text]
**Result:** [actual output]

**Query 2:** [query text]
**Result:** [actual output]

**Query 3:** [query text]
**Result:** [actual output]

---

## What Surprised Us

<!-- Specific observations a hobbyist reviewer would not notice.

     Two or three specific technical observations a hobbyist reviewer would not make —
     architecture decisions baked into the design, assumptions in the config, or performance
     behaviors that diverged from the documentation. No general impressions; specifics only.
     This feeds the enterprise reframe in Article 2. -->

---

## What Did Not Work

<!-- Honest about failures, workarounds, or skipped steps.

     Honest account of what failed, what workarounds were applied, and whether those
     workarounds are stable for daily use. If a feature described in the docs did not work
     on this setup, name it and note whether it is a known issue with a filed ticket or an
     undocumented gap. -->

---

## Security Notes

<!-- Current CVE status at time of setup. [cite]
     What was done to mitigate.

     Current CVE status for OpenClaw as of the setup date, with specific advisory IDs cited
     [cite]. Note what mitigations were applied — and if none were applied, say so plainly.
     This feeds both the security caveat in Article 2 and the full security arc in
     Article 5. -->

---

## Resource Usage

<!-- Memory, CPU, disk at rest and under load. Actual numbers.

     Actual measured numbers: memory at rest, memory under a query, CPU during inference,
     disk footprint. Use Activity Monitor or htop output, not estimates. Note whether
     resource usage scales with vault size — this matters for readers with large vaults. -->

---

## Setup Time

<!-- Actual elapsed time from zero to working.

     Elapsed time from a clean machine to first successful vault query via WhatsApp,
     broken down by phase: installation, vault config, WhatsApp bridge, model download.
     This is the evidence behind the "20 minutes" claim in the Article 2 hook — verify it
     against your actual elapsed time and report honestly if it took longer. -->

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
