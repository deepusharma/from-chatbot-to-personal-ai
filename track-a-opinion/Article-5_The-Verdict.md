---
title: "The Verdict"
series: "From Chatbot to Personal AI"
track: A
status: draft
author: TBD
word-target: 1000-1200
publishes-first: linkedin
cross-post: medium (7 days after)
track-b-link: none (synthesis article)
---

# The Verdict

*Six tools. Same vault. Same queries. Here is what the experiment actually found.*

---

## Revisiting the Thesis

Article 1 argued that Phase 4 personal AI had arrived — agents that run on your hardware, know your data, take real action, and are model-agnostic. The experiment confirmed the basic thesis. What it also found: the gap between "technically works" and "actually useful every day" is wider than the GitHub star counts suggest.

[FILL: two to three sentences on what changed in your view between writing Article 1 and finishing the setups. Be specific — which assumption was wrong, which held up cleanly, what the mobile gap looks like in practice. If the thesis held up without qualification, say so. Do not soften a genuinely changed view to protect a cleaner narrative arc.]

---

## The Comparison

All six tools. Same hardware, same vault, same three queries.

| Tool | Setup friction | Query quality | Security posture | RAM at rest | Best for |
|---|---|---|---|---|---|
| OpenClaw | [FILL: 1–5] | [FILL] | 138 CVEs, patches ship; verify before running | ~400MB | [FILL] |
| ZeroClaw | [FILL: 1–5] | [FILL] | 0 CVEs; unsafe blocks exist, no published audit | ~5MB | [FILL] |
| NanoClaw | [FILL: 1–5] | [FILL] | CVE-2026-7875 unpatched at research date; container model | [FILL] | [FILL] |
| memU | [FILL: 1–5] | [FILL] | CVE-2026-25253 patched in 2026.1.29; DB exposure | [FILL] | [FILL] |
| Hermes | [FILL: 1–5] | [FILL] | CVE-2026-7396 (WeChat adapter only); check patch status | [FILL] | [FILL] |
| NemoClaw | [FILL: 1–5] | [FILL] | CVE-2026-24222 fixed in v0.0.18; requires OpenClaw underneath | [FILL] | [FILL] |

[FILL: two to three sentences after the table naming the two or three most non-obvious findings — the cells a reader would not predict from the tool descriptions in Article 1. The surprises are the value. The cells a reader could have guessed are less interesting.]

---

## The Build-On-Top Decision

Three tools in this series serve different purposes, and the decision between them is an architectural one.

**Fork OpenClaw** when you need a personal assistant with full code control, one user, and a willingness to stay current on CVEs. It is the most capable out of the box. It is also the tool with the most active attack surface.

**Run Hermes** when the agent needs to be always on, needs to improve over time, and you are willing to wait for the skill library to pay off. Hermes makes the most sense on a VPS running continuously, not on a laptop opened twice a week. The self-improvement loop requires volume to develop. [FILL: note whether this held up in the test sessions or whether the ramp-up period was longer than expected.]

**Evaluate NemoClaw** when compliance requirements are real, you have NVIDIA DGX infrastructure, and the vendor commitment is one you can make for five years. Do not evaluate it as a cheaper path to security — it is not cheaper. It is a different risk profile for a specific infrastructure context.

NanoClaw belongs in a fourth category: tools you fork to learn from, not tools you run in production on a Thursday. The codebase is worth reading. The CVE-2026-7875 container escape is worth knowing about.

---

## The Security Arc

The pattern across all six tools: every tool that marketed itself as a security improvement shipped a security vulnerability in its first few months. NanoClaw's container isolation model produced a container escape. NemoClaw's sandboxing produced a sandbox escape via prompt injection. This is not a coincidence — these are the hardest problems in the space, and the tools attacking them are working in public, which means the failures are visible.

What improved: the CVE processes. OpenClaw's jgamblin/OpenClawCVEs tracker [cite] is a model for open-source security transparency. Patches ship. Advisories are specific. The supply chain question is harder: none of the six tools has a published SBOM or a formal supply chain security posture. The `curl | bash` installers that three of the six tools ship as their primary install path remain the most direct attack vector.

[FILL: update the specific patch status for each tool's major CVE at time of final write. These change. The table above has the CVE numbers; verify current status against live advisories before publishing.]

---

## The NVIDIA Lock-In: Final Verdict

[FILL: after running all six tools, one paragraph, direct verdict on the NemoClaw trade-off. Does the security stack justify the infrastructure commitment for your likely reader? State a position — "right for regulated industries with existing NVIDIA infrastructure, wrong for everyone else making a new decision" is a position. "It depends" is not.]

---

## The Enterprise Framework

Two scenarios that come up in actual enterprise AI conversations.

**Scenario A: Your team is already running OpenClaw without IT approval.**
The path to legitimising it: first, establish what version is running and whether it has patches for CVE-2026-25253 and CVE-2026-32922. Second, move from personal WhatsApp accounts to either a dedicated number or the Business Cloud API — this changes the data handling from "whatever the individual set up" to something auditable. Third, decide whether the current setup needs containment (restrict to low-sensitivity data, isolated from production systems) or migration (move to NemoClaw if DGX hardware exists, move to ZeroClaw if the goal is reducing attack surface with no infrastructure change). Do not mandate shutdown without an alternative — it will move underground and become harder to find.

**Scenario B: Your CISO is evaluating personal AI agents for the first time.**
The first question to ask: is the goal to enable the use case securely, or to prevent the use case? If the goal is prevention, the conversation needs to include what happens when prevention fails — and given the 22% adoption rate without IT approval [cite: verify], the probability of failure is meaningful. The more productive framing: treat personal AI agents as a new category of shadow IT, apply the same playbook that worked for shadow SaaS in 2018, and pick the containment architecture that matches your compliance posture. NemoClaw for regulated industries. ZeroClaw plus policy for everyone else.

---

## What Kept Running

[FILL: after the experiment ended, which tools stayed installed and why. Name the tool and the specific use case. If nothing stayed running, say that — it is the most honest signal in the series about what is actually useful versus technically interesting. Do not editorialize; report.]

---

## Where Phase 4 Goes Next

Three things to watch in the next 12 months:

**On-device model progress.** Apple Intelligence and Gemini Nano are closing the quality gap with cloud models on specific task types. When an on-device model can handle the synthesis queries that currently require a cloud API call, the privacy trade-off in this comparison table changes significantly. The timeline depends on whether Apple ships the rumoured on-device reasoning model update before mid-2027 [cite: verify].

**Open-source security maturity.** The CVE arc in this space is accelerating, not slowing. More users means more security researchers. More security researchers means more advisories. The question is whether patch velocity keeps pace. OpenClaw's track record on patch turnaround is [FILL: report actual patch timing from the CVE tracker]. If it is less than 30 days on critical advisories, the maturity signal is real. If patches are taking longer, the adoption curve is running ahead of the security posture.

**Enterprise adoption patterns.** The shadow AI problem does not get smaller as AI capabilities improve. The question is whether enterprise security teams get ahead of it with tooling like NemoClaw, or whether the containment approach always lags adoption. The answer determines whether this space stays in the open-source personal category or migrates into enterprise procurement cycles within two years.

---

*Status: Draft. Table needs real data from all six setups. "What Kept Running" and the thesis revisit sections need real experience. The enterprise framework and security arc are ready for final review — verify the 22% citation before publishing.*

---

## Three Takes

**[Author A]:**

**[Author B]:**

**[Author C]:**

---

## LinkedIn Post

Six tools. Same vault. Same three queries across all of them.

The finding that surprised me most: [FILL: the single most non-obvious finding from the comparison table. Not a general impression — the specific cell or observation that would not be predictable from the tool descriptions.]

The security picture is more nuanced than the CVE counts suggest. Every tool marketed as a security improvement shipped a vulnerability in its first few months. The difference is whether the advisory process is transparent and the patches ship fast.

The full comparison table, the build-on-top decision framework, and what actually kept running after the experiment ended: full article linked.
