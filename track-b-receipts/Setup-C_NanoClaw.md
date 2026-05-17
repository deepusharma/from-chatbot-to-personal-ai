---
title: "NanoClaw: reading 4,000 lines of agent code in a day"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: NanoClaw
status: placeholder
author: TBD
word-target: 1500-2000
publishes-first: medium
cross-post: linkedin (7 days after)
track-a-link: "../track-a-opinion/Article-5_The-Verdict.md"
test-bed: Obsidian vault (same vault, same queries as Setup-A)
---

# NanoClaw: reading 4,000 lines of agent code in a day

*Hands-on setup and code walkthrough. Referenced in Article 5: The Verdict.*

---

## What NanoClaw Is

<!-- 4,000 lines of Python. [cite line count]
     26K GitHub stars. [cite]
     Why the line count matters: you can read the whole thing in a day.

     NanoClaw is a minimal fork of OpenClaw, approximately 4,000 lines of Python [cite
     actual line count from repo on the date of writing]. Its 26K GitHub stars [cite]
     suggest it attracts readers as much as users — people who want to understand how a
     personal AI agent works, not just run one. The pitch is the line count: a working
     agent you can read end-to-end in a day. -->

---

## Prerequisites

<!-- List what is required. Note if NanoClaw's minimalism means fewer dependencies than
     OpenClaw, and flag any capabilities from OpenClaw that are simply absent here rather
     than configurable. -->

---

## Installation

<!-- Same format as Setup A: actual steps taken, delta from docs, any commands worth
     preserving for reproducibility. Note if the minimalist design simplifies installation
     compared to OpenClaw. -->

---

## Connecting the Obsidian Vault

<!-- Same vault as all other setups. Document what NanoClaw's minimal design means for
     vault configuration in practice — fewer config options, different defaults, or any
     capabilities missing compared to OpenClaw. If it is simpler, say so. -->

---

## The Same Test Queries

<!-- Same three queries as Setup A. Record verbatim results. Pay close attention to where
     answer quality drops compared to OpenClaw — that is the cost of the minimalist
     architecture and the key data for Article 5's comparison table. -->

**Query 1:** [query text]
**Result:** [actual output]

**Query 2:** [query text]
**Result:** [actual output]

**Query 3:** [query text]
**Result:** [actual output]

---

## Reading the Code: Three Architecture Decisions Worth Stealing

<!-- What a practitioner learns from reading the source.
     Specific observations, not general praise.

     This is the unique value of this post — most readers will not read the NanoClaw source
     themselves. Pick three specific architecture decisions worth knowing: how the agent
     handles tool calling, how it manages context, how it structures skills or plugins.
     Cite the actual file names or line ranges in the NanoClaw source so a curious reader
     can verify. No general praise — specific, citable observations only. -->

---

## Two Decisions We Would Not Steal

<!-- Honest about trade-offs made for minimalism.

     Two specific design choices made for minimalism that introduce real constraints in
     production. Not bugs — deliberate trade-offs. Be specific about what those trade-offs
     cost in practice. Cite the relevant code just as in the section above. -->

---

## What Auditability Costs in Practice

<!-- Features sacrificed for transparency.
     Where the constraints show up in daily use.

     Features present in OpenClaw that NanoClaw dropped in the service of minimalism.
     Where do those absences show up in daily use? Not "fewer features" in the abstract —
     name the specific things you could not do that you could do with OpenClaw, and what
     you had to work around or skip. -->

---

## What Surprised Us

<!-- Same format as other setups: two or three specific technical observations. Focus on
     what reading the source revealed that using the tool alone would not have shown. -->

---

## What Did Not Work

<!-- Same format as other setups: honest account of failures and workarounds. -->

---

## Security Notes

<!-- Current CVE status. [cite]

     NanoClaw CVE status as of setup date [cite]. Note if the minimal codebase changes
     the attack surface compared to OpenClaw — fewer lines can mean fewer places to hide
     vulnerabilities, but also fewer maintained defenses. -->

---

## Resource Usage

<!-- Actual measured numbers at rest and under a query. Compare to OpenClaw from Setup A
     to show whether the minimalist design translates to lower resource consumption. -->

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
