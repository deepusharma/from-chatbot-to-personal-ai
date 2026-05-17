---
title: "NemoClaw via the NVIDIA API catalog (with DGX context)"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: NemoClaw
status: placeholder
author: TBD
word-target: 1500-2000
platform-primary: Medium
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
     What it adds over base OpenClaw. [cite each feature] -->

---

## Two Ways to Access It

<!-- Path 1: Full NemoClaw stack (DGX hardware, NVIDIA AI Enterprise license)
     Path 2: NVIDIA API catalog (Nemotron model quality, without the security stack) -->

---

## Path Taken: NVIDIA API Catalog

### Prerequisites

### Setup

### The Same Test Queries via Nemotron

**Query 1:** [query text]
**Result:** [actual output]

**Query 2:** [query text]
**Result:** [actual output]

**Query 3:** [query text]
**Result:** [actual output]

### Model Quality vs OpenClaw (Local) vs Claude API

| | Nemotron (NVIDIA API) | Local model (OpenClaw) | Claude API |
|---|---|---|---|
| Answer quality | | | |
| Latency | | | |
| Cost | | | |

---

## The Full NemoClaw Stack: Architecture Analysis

<!-- Based on NVIDIA documentation. Clear that this was not tested live. -->

### OpenShell Kernel-Level Sandboxing

### Audit Trails

### Manifest-Signed Skills

### DGX Hardware Requirement

<!-- What DGX is. Why standard cloud GPU VMs do not qualify. [cite]
     What NVIDIA AI Enterprise licensing covers. [cite] -->

---

## The Lock-In Trade-Off

<!-- NVIDIA owns the full stack. Security guaranteed by vendor control.
     What that means for an organisation evaluating this. -->

---

## Security Notes

<!-- NemoClaw CVE status. [cite] -->

---

*Status: Placeholder. Replace this line when drafting begins.*
