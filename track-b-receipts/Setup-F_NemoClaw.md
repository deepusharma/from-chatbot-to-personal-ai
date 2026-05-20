---
title: "NemoClaw via the NVIDIA API catalog (with DGX context)"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: NemoClaw
status: draft
author: TBD
word-target: 1500-2000
publishes-first: medium
cross-post: linkedin (7 days after)
track-a-link: "../track-a-opinion/Article-4_The-Lock-In-Question.md"
test-bed: NVIDIA API catalog (Nemotron model). Vault queries via OpenClaw's obsidian skill.
tested-on: macOS [FILL: version] Apple Silicon
nemoclaw-version: [FILL: from npm list or github release]
test-date: [FILL: date of setup session]
transparency-note: Full NemoClaw stack requires DGX hardware or DGX Cloud — not available for this setup. API catalog path tested live. DGX architecture covered via documentation only.
security-note: CVE-2026-24222 (CVSS 8.6) — sandbox escape via prompt injection. Update to v0.0.18+.
dependency-note: NemoClaw requires OpenClaw to already be installed and running. Do Setup-A before this one.
---

# NemoClaw via the NVIDIA API catalog (with DGX context)

*The full setup notes behind Article 4: The Lock-In Question.*

*Transparency: this article covers two paths. Path 1 (NVIDIA API catalog) was tested live. Path 2 (full NemoClaw stack on DGX hardware) is covered through NVIDIA's documentation only — DGX hardware was not available for this setup. The distinction is called out wherever it matters.*

---

## What NemoClaw Is — and What It Is Not

NemoClaw is not a standalone AI agent. It is NVIDIA's open-source secure deployment wrapper for OpenClaw [github.com/NVIDIA/NemoClaw]. You install OpenClaw first. Then NemoClaw wraps it with NVIDIA's OpenShell runtime, adding four things: guided onboarding, a hardened execution blueprint, policy-based privacy guardrails enforced out-of-process, and routing to Nemotron models or frontier cloud models via a privacy router.

This means Setup-A (OpenClaw) is a prerequisite. If you have not done Setup-A yet, do that first.

NemoClaw does not replace OpenClaw. It does not fork it. If OpenClaw gets a new skill tomorrow, NemoClaw users get it. The trade-off NemoClaw makes explicit: NVIDIA's security answer requires NVIDIA's stack. OpenShell runtime, NVIDIA AI Enterprise licensing for the full deployment, and DGX-class hardware for local Nemotron inference. You are not buying a security feature. You are buying into an infrastructure commitment.

That is the argument Article 4 makes. This article provides the evidence.

---

## Two Paths

**Path 1: NVIDIA API catalog** — Nemotron model quality through a cloud API. No hardware required. The security layer (OpenShell, audit trails, manifest-signed skills) is not available on this path. Tested live in this article.

**Path 2: Full NemoClaw stack** — requires DGX Spark, DGX Station, or RTX PRO workstation for local Nemotron inference with the complete security stack. Not tested here. Covered through NVIDIA documentation and architecture analysis in "The Full NemoClaw Stack" section below.

For macOS users without DGX hardware, Path 1 is the only realistic option. Local Nemotron inference on macOS is documented as incomplete [cite: NVIDIA NemoClaw docs — macOS section].

---

## Prerequisites

- OpenClaw installed and configured from Setup-A. NemoClaw wraps it — it does nothing standalone.
- Node.js 20 or later: `node --version`.
- An NVIDIA developer account for API catalog access: [build.nvidia.com](https://build.nvidia.com). Free credits are available — no credit card required to start.
- The test vault at `~/Documents/experiments/from-chatbot-to-personal-ai/vault`, already configured in OpenClaw via Setup-A.

> **Windows** *(not tested — documentation only)*
>
> WSL2 with Docker Desktop required. Allocate at least 8GB to WSL in `.wslconfig`:
> ```
> [wsl2]
> memory=8GB
> ```
> Windows is described as "experimentation" territory by NVIDIA, not production-ready [cite: NVIDIA NemoClaw docs — Windows section]. GPU passthrough in WSL2 for local Nemotron inference is unstable. API catalog path should work on Windows via WSL2 without GPU involvement.

---

## Path 1: NVIDIA API Catalog Setup

**Step 1: Get an NVIDIA API key**

Sign in at [build.nvidia.com](https://build.nvidia.com). Navigate to the NemoClaw listing [VERIFY: build.nvidia.com/spark/nemoclaw or similar]. Generate an API key. Free credits are included on new accounts.

[FILL: document the exact steps — whether the API key is provisioned per-model or per-account, any approval process encountered, and how long it took.]

**Step 2: Install NemoClaw**

```bash
npm install -g git+https://github.com/NVIDIA/NemoClaw.git
```

[VERIFY: whether this is the current install method or whether an npm package exists at registry. Check the README.]

[FILL: actual output, install time, any errors.]

**Step 3: Run the onboarding wizard**

```bash
nemoclaw onboard
```

The wizard configures the API key, the routing between OpenClaw and the Nemotron inference endpoint, and the channel connections. Since OpenClaw is already installed, channels configured in Setup-A should carry over.

[FILL: document what the wizard actually asks, what defaults it suggested, and what was changed. Note whether OpenClaw's existing config was detected automatically or required manual input.]

**Step 4: Test the connection**

```bash
nemoclaw status
```

[FILL: actual output.]

---

## Connecting the Obsidian Vault

NemoClaw does not add Obsidian integration — it inherits whatever OpenClaw has. If the ObsidianClaw plugin was configured in Setup-A and the vault was accessible, it should work the same way through NemoClaw.

[FILL: confirm this is correct, or document what additional configuration was needed. Note whether the vault connection worked immediately after `nemoclaw onboard` or required re-configuration.]

---

## The Same Test Queries via Nemotron

Queries sent via the NVIDIA API catalog path, running against the same test vault.

**Query 1:** What are the open blockers across my current projects?

**Result:**
[FILL: verbatim output. Note latency.]

---

**Query 2:** What decisions and action items came out of my meetings this week?

**Result:**
[FILL: verbatim output. Note latency.]

---

**Query 3:** Summarize what I know about AI tooling and what I still need to research.

**Result:**
[FILL: verbatim output. Note latency.]

---

## Model Quality and Cost Comparison

| | Nemotron (NVIDIA API) | Local model (from Setup-A) | Claude API (from Setup-A) |
|---|---|---|---|
| Query 1 quality | [FILL] | [from Setup-A] | [from Setup-A] |
| Query 2 quality | [FILL] | [from Setup-A] | [from Setup-A] |
| Query 3 quality | [FILL] | [from Setup-A] | [from Setup-A] |
| Avg latency | [FILL] | [from Setup-A] | [from Setup-A] |
| Cost per session | [FILL: credits used] | Free (local) | [from Setup-A: $ per session] |

---

## The Full NemoClaw Stack: Architecture Analysis

*Based on NVIDIA documentation only. None of the following was tested live.*

### OpenShell Kernel-Level Sandboxing

OpenShell is NVIDIA's secure execution runtime that confines what an AI agent can do at the OS level [cite: NVIDIA NemoClaw docs — OpenShell section]. It enforces syscall restrictions and directory access policies out-of-process — meaning the guardrails do not run inside the agent, they run around it. An agent that tries to read a path it is not supposed to reach gets blocked by OpenShell before the attempt lands.

This is architecturally different from NanoClaw's Docker-based isolation. Docker puts the agent in a container. OpenShell restricts what the agent's process can do on the host. Both have limits, as the respective CVEs demonstrate.

[FILL: verify the above against the current NVIDIA docs and correct any inaccuracies. Cite the specific documentation page.]

### Audit Trails

NemoClaw logs agent actions to an audit trail that compliance reviewers can query [cite: NVIDIA docs]. [FILL: document what is logged — tool calls, file accesses, API calls, or all of the above. Note where the logs are stored and whether they are tamper-evident. This is the section most relevant to the CISO audience in Article 4.]

### Manifest-Signed Skills

Skills installed in NemoClaw are cryptographically signed [cite: NVIDIA docs]. An unsigned skill cannot be loaded. This addresses the supply chain risk of installing a community-published skill that contains malicious code — a risk that is present in OpenClaw's skill ecosystem and explicitly absent here.

[FILL: verify the signing mechanism — what key infrastructure is used, whether NVIDIA controls the signing authority, and what happens to community-contributed skills that are not NVIDIA-signed.]

### DGX Hardware Requirement

DGX Spark and DGX Station are NVIDIA's AI-specific workstations, with shared CPU/GPU memory pools designed for large model inference [cite: NVIDIA DGX Spark product page]. Standard cloud GPU instances — an A100 on AWS, a V100 on GCP — do not qualify for the full NemoClaw stack. The licensing is tied to DGX-class hardware.

One documented gotcha: do not use `nvidia-smi` for capacity planning on DGX Spark. CPU and GPU share one memory pool, and `nvidia-smi` does not reflect the shared allocation correctly [cite: github.com/NVIDIA/NemoClaw issue #3231].

---

## The Lock-In Trade-Off

The security story NemoClaw tells is coherent: OpenShell sandboxing, audit trails, signed skills, and Nemotron inference on NVIDIA hardware form a defensible posture for regulated environments. The price is that every element of the stack is NVIDIA. Hardware, licensing, runtime, model family.

For an organization planning a multi-year infrastructure investment, that is not incidental. It is the whole question. The security guarantees and the vendor commitment are the same contract, signed simultaneously.

That tension is what Article 4 argues. The evidence for both sides of it lives in this article.

---

## What Surprised Us

[FILL after testing: specific observations. The most common surprise in Path 1 is how much (or how little) the Nemotron model quality differs from OpenAI or Claude on vault queries. NemoClaw's security story is compelling on paper — the interesting question is whether the model quality justifies the infrastructure commitment for users without DGX hardware.]

---

## What Did Not Work

[FILL after testing. Known open issues: OpenClaw agent inside the NemoClaw vLLM sandbox sometimes cannot reach the local OpenClaw gateway and falls back to the embedded provider [cite: github.com/NVIDIA/NemoClaw issue #3256]. Document whether this was encountered and what the fallback behavior looked like.]

---

## Security Notes

**CVE-2026-24222 (CVSS 8.6):** A remote attacker can send prompt-injected content causing NemoClaw's sandbox initialization component to read and exfiltrate host environment variables not properly restricted during sandbox creation [cite: nvidia.custhelp.com/app/answers/detail/a_id/5837, thehackerwire.com/vulnerability/CVE-2026-24222]. Improper access control. No privileges required.

Remediation: update to NemoClaw v0.0.18 or later [cite: NVIDIA security bulletin]. [FILL: verify your installed version and whether the patch is applied.]

The irony of this CVE is worth naming plainly: the tool whose primary value proposition is hardened security against OpenClaw's 138 CVEs shipped a sandbox escape in its own initialization layer. The escape vector is prompt injection — the same class of attack that the security layer is designed to mitigate. As one security researcher put it: "NemoClaw improves containment. It does not rewrite your IAM model." [cite: thehackerwire.com/vulnerability/CVE-2026-24222]

The practical checklist:
- Update to v0.0.18+ before running.
- On the API catalog path (Path 1), the sandbox is not in play — you are calling a cloud API. CVE-2026-24222 is relevant only on the full DGX stack.
- The OpenClaw CVEs from Setup-A still apply to the OpenClaw layer underneath NemoClaw. NemoClaw adds a security layer; it does not replace the base.

---

*Status: Draft. Path 1 (API catalog) sections ready to fill during setup. Path 2 (DGX) sections are documentation-based and should be marked clearly as such in the final article. Verify all NVIDIA doc citations — their documentation structure changes frequently.*

---

## Three Takes

**[Author A]:**

**[Author B]:**

**[Author C]:**

---

## LinkedIn Post

<!-- 3–5 specific observations. End with "Full setup notes on Medium [link]."
     The lock-in framing is the angle that will land with a VP/CISO audience.
     The CVE-24222 irony is the quip. Use one, not both. -->
