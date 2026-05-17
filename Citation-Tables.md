# Citation Tables

Every specific number used in the series needs a sourced URL and an as-of date before it goes into a draft. This file tracks the status of every claim.

**Rule:** If a claim cannot be sourced, replace it with a range or remove it. Do not publish an unsourced number.

**How to update:** Change `Open` to `Verified` when sourced, add the URL and the date you checked it. Change to `Removed` if the number does not hold up.

---

## Series-Wide Claims

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| "22% of enterprises running OpenClaw without IT approval" | Survey — Gartner, Forrester, or vendor | | | Open |

---

## Article 1 — The Map

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| OpenClaw 367K GitHub stars | GitHub repo, direct count | | | Open |
| OpenClaw stars in 6 months | GitHub repo creation date vs star count | | | Open |
| OpenClaw launch date (Nov 2025 as Clawdbot) | Project release history or blog | | | Open |

---

## Article 2 — The Reference (OpenClaw)

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| CVE-2026-32922 CVSS 9.9 | NVD advisory | | | Open |
| 40+ CVEs patched in v2026.2.12 | Project changelog or CVE list | | | Open |
| 9 CVEs in 4 days (Mar 2026) | NVD or project security advisories | | | Open |
| 1,400+ malicious skills on ClawHub | Project security report or news coverage | | | Open |
| Manifest-signed skills added v2026.4.12 | Project changelog | | | Open |

---

## Article 3 — The Memory Bet (memU)

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| memU privacy model details | Project docs or README | | | Open |
| memU current CVE status | NVD or project security advisories | | | Open |

---

## Article 4 — The Lock-In Question (NemoClaw)

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| NemoClaw DGX-only deployment requirement | NVIDIA product page or docs | | | Open |
| NVIDIA AI Enterprise licensing required separately | NVIDIA licensing page | | | Open |
| DGX Cloud not accessible via standard Azure GPU VMs | NVIDIA DGX Cloud docs | | | Open |
| OpenShell kernel-level sandboxing | NVIDIA NemoClaw docs | | | Open |
| Manifest-signed skills in NemoClaw | NVIDIA docs | | | Open |
| Nemotron model details (model name, capability) | NVIDIA API catalog | | | Open |
| NemoClaw current CVE status | NVD or NVIDIA security advisories | | | Open |

---

## Article 5 — The Verdict

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| All claims carried forward from Articles 1–4 | See above | | | Per above |

---

## Track B — Setup Posts

### Setup A — OpenClaw

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| Setup time ("20 minutes") | Your own measurement during setup | | | Open |
| Local model used (Ollama/Llama version) | Your setup notes | | | Open |
| WhatsApp integration method | OpenClaw docs | | | Open |

### Setup B — ZeroClaw

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| Sub-10ms startup time | Project README or benchmark | | | Open |
| 3.4MB binary size | Project release notes | | | Open |
| Written in Rust | Project README | | | Open |
| ZeroClaw current CVE status | NVD or project advisories | | | Open |

### Setup C — NanoClaw

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| 4,000 lines of Python | Line count from repo (run wc -l or cloc) | | | Open |
| 26K GitHub stars | GitHub repo, direct count | | | Open |
| NanoClaw current CVE status | NVD or project advisories | | | Open |

### Setup D — memU

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| memU architecture details | Project docs | | | Open |
| Memory storage method (local vs cloud) | Project README | | | Open |

### Setup E — Hermes

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| Hermes server/VM requirements | Project docs | | | Open |
| Hermes API specification | Project docs or OpenAPI spec | | | Open |
| Hermes current CVE status | NVD or project advisories | | | Open |

### Setup F — NemoClaw (NVIDIA API)

| Claim | Source needed | URL | Checked | Status |
|---|---|---|---|---|
| NVIDIA API catalog access method | NVIDIA developer docs | | | Open |
| Nemotron model name and version used | NVIDIA API catalog | | | Open |
| DGX hardware specifications (for architecture section) | NVIDIA product page | | | Open |

---

## How to Add a New Claim

Add a row to the relevant table:

```
| [Claim as you intend to write it] | [Where to find the source] | | | Open |
```

Fill in the URL and Checked date when you verify it. Change Status to `Verified`. If the number is wrong or unpublishable, change Status to `Removed` and note what you used instead.
