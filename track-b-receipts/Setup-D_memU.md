---
title: "memU: configuring persistent memory for a personal AI"
series: "From Chatbot to Personal AI: Field Notes"
track: B
tool: memU
status: draft
author: TBD
word-target: 1800-2200
publishes-first: medium
cross-post: linkedin (7 days after)
track-a-link: "../track-a-opinion/Article-3_The-Memory-Bet.md"
test-bed: ~/Documents/experiments/from-chatbot-to-personal-ai/vault (custom ingestion — see note)
tested-on: macOS [FILL: version] Apple Silicon
memu-version: [FILL: pip show memu or docker image tag]
test-date: [FILL: date of setup session]
series-note: memU is a memory layer, not an agent. This article covers memU + memUBot as the agent wrapper. Vault queries require a custom ingestion step not needed in other setups.
---

# memU: configuring persistent memory for a personal AI

*The full setup notes behind Article 3: The Memory Bet.*

---

## What memU Is (and Is Not)

memU is not an agent. This matters more than it sounds.

Every other tool in this series is a personal AI assistant you talk to. memU is the memory layer underneath one. It stores structured facts about you and your context across sessions, retrieves them during conversations, and evolves over time. The agent wrapper for day-to-day use is memUBot [github.com/NevaMind-AI/memUBot]. memU is the library memUBot runs on.

The architecture has three layers: a Resource Layer that ingests raw data, a Memory Item Layer that extracts structured facts, and a MemoryCategory Layer that organizes them into a knowledge graph [cite: github.com/NevaMind-AI/memU]. Retrieval is hybrid — semantic vector search plus graph traversal — so the agent can find facts that are semantically similar to your query AND facts that are structurally related to each other.

The argument memU makes against the prevailing direction in AI development: context window scaling is not the right answer to memory. Stuffing more conversation history into a 200k-token window is expensive, lossy when it overflows, and structurally wrong — you do not remember things by replaying them, you remember them because they were important. memU's claim is 92.09% accuracy on the Locomo benchmark [cite: memu.pro]. That number was not verified in this setup.

**What this means for the test vault:** memU does not have a native Obsidian plugin or direct vault integration. The other five tools in this series connect to the vault via a WebSocket plugin or a directory path. memU requires a custom ingestion step to pull your vault notes into the memory store. That step is documented below and takes roughly [FILL: time] minutes on the seven-note test vault.

---

## Prerequisites

- macOS 12 or later. Tested on macOS [FILL: version] on Apple Silicon.
- Python 3.10 or later: `python3 --version`. If missing: `brew install python`.
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) for the PostgreSQL + pgvector stack. Verify: `docker --version`.
- An AI provider API key. memUBot supports multiple providers. This setup used [FILL: which provider]. For free options: Groq (console.groq.com), Google Gemini (aistudio.google.com), OpenRouter (openrouter.ai) — all free tiers, no credit card required.
- The test vault at `~/Documents/experiments/from-chatbot-to-personal-ai/vault`.

Hardware: memU requires a running PostgreSQL instance with the pgvector extension. Docker handles this. The memory store itself is small — the seven-note test vault produces a compact graph. Larger personal vaults (thousands of notes) will require more storage planning.

> **Windows** *(not tested — documentation only)*
>
> Docker Desktop or WSL2 required for PostgreSQL + pgvector. The Python package installs normally on Windows: `pip install memu`. The Docker compose commands are the same as Linux/macOS. If you use WSL2, run everything from inside the WSL environment for consistent path handling.

---

## Installation

memU is infrastructure-heavy compared to the other tools in this series. You are standing up a database before you can talk to an agent. Worth knowing upfront.

**Step 1: Start PostgreSQL with pgvector**

```bash
docker run -d --name memu-postgres \
  -e POSTGRES_USER=postgres \
  -e POSTGRES_PASSWORD=postgres \
  -e POSTGRES_DB=memu \
  -p 5432:5432 \
  pgvector/pgvector:pg16
```

[FILL: note if a different postgres password was used and how memU's config was updated to match.]

**Step 2: Install the memU Python package**

```bash
pip install memu
```

[FILL: note Python version used, whether a virtual environment was created, any dependency conflicts.]

**Step 3: Install and configure memUBot**

```bash
git clone https://github.com/NevaMind-AI/memUBot.git
cd memUBot
```

[FILL: document the actual configuration steps — what env vars are required, where the API key is stored, how the database connection string is set. The memUBot README should cover this but note any gaps between the docs and reality.]

**Step 4: Verify the stack**

```bash
docker ps   # postgres container should be running
python -c "import memu; print(memu.__version__)"
```

[FILL: actual output and any errors.]

---

## Connecting the Obsidian Vault

memU does not have a native Obsidian integration. To use the test vault with memU, the vault notes must be ingested into the memory store as a one-time import. This is custom work, but it is not complicated — the vault is a folder of markdown files.

[FILL: document the actual ingestion approach used. Options include: (1) writing a short Python script that reads each .md file and calls memU's ingestion API, (2) using the memU server's bulk import endpoint if one exists [VERIFY: docs.memu.pro], (3) pointing memU's Resource Layer at the vault directory if it supports filesystem sources.]

After ingestion, the vault content lives in the memory graph and is retrieved by memUBot during conversations. Unlike the other five tools, where vault queries happen in real time against the live files, here the vault is a snapshot in the memory store. Changes to the vault notes after ingestion are not reflected until the vault is re-ingested.

[FILL: note the time taken to ingest the seven-note test vault, and estimate how this would scale for a larger vault.]

---

## What "Teaching" memU About Yourself Looks Like

Beyond the vault, memU builds a user profile across sessions. The first session is the most important one — what you tell it about yourself here forms the baseline for everything that follows.

[FILL: document the actual onboarding interaction. What information did memUBot ask for? What did you provide? How long before the memory felt meaningful in query responses — one session, three sessions, never? Include one concrete before-and-after example: something you told memU in session one that it correctly recalled in session two or three. This section is the core case for Article 3's argument.]

---

## The Same Test Queries — Before Memory Accumulates

Run the standard three queries in the first session, before meaningful memory has built up. These are the baseline.

**Query 1:** What are the open blockers across my current projects?

**Result (session 1):**
[FILL: verbatim output. Note whether this came from vault ingestion, from the session context, or from the memory graph.]

---

**Query 2:** What decisions and action items came out of my meetings this week?

**Result (session 1):**
[FILL: verbatim output.]

---

**Query 3:** Summarize what I know about AI tooling and what I still need to research.

**Result (session 1):**
[FILL: verbatim output.]

---

## The Same Test Queries — After Memory Accumulates

Same three queries after [FILL: N] sessions of use.

**Query 1:** What are the open blockers across my current projects?

**Result (after memory):**
[FILL: verbatim output.]

**What changed:**
[FILL: specific delta — did memU recall context from earlier sessions that changed the answer? Did it add anything the vault alone could not have produced? If nothing changed, say so.]

---

**Query 2:** What decisions and action items came out of my meetings this week?

**Result (after memory):**
[FILL: verbatim output.]

**What changed:**
[FILL.]

---

**Query 3:** Summarize what I know about AI tooling and what I still need to research.

**Result (after memory):**
[FILL: verbatim output.]

**What changed:**
[FILL.]

---

## Where the Memory Is Stored

The memory store is a PostgreSQL database running locally via Docker, with the pgvector extension enabling vector similarity search [cite: github.com/NevaMind-AI/memU]. Data lives in your local Docker volume — it does not sync to cloud unless you explicitly configure remote postgres.

- Database: `memu` (or whatever you named it in the Docker run command)
- Docker volume: [FILL: `docker inspect memu-postgres` to find the volume mount path]
- File format: PostgreSQL tables — not human-readable markdown, inspectable via `psql` or any Postgres client

To inspect what is stored: `psql -h localhost -U postgres -d memu` then `\dt` to list tables. The Memory Item and MemoryCategory tables are where the structured facts live.

To back up: `pg_dump -h localhost -U postgres memu > memu-backup.sql`. Do this before experimenting with memory deletion or re-ingestion.

---

## Privacy Configuration

[FILL: document what controls exist over what gets stored. Specific questions to answer: Is there a way to delete a specific memory item without wiping the whole store? What is the default retention — does everything persist forever? Are API calls to the AI provider logged anywhere by memU? Name the config keys and what they do rather than summarizing them.]

---

## What Surprised Us

[FILL after testing: two or three specific observations about the memory architecture. The interesting surprises tend to be around what memU does with conflicting facts — if you tell it one thing and the vault says something different, which wins? How does it handle stale memories when the vault is re-ingested?]

---

## What Did Not Work

[FILL after testing: honest account. Common candidates for memU: Docker postgres not starting, pgvector extension not found, ingestion failing on markdown with unusual frontmatter, memory retrieval not improving after multiple sessions, or the before/after delta being smaller than expected.]

---

## Security Notes

**CVE-2026-25253:** Allows attackers to obtain user authentication tokens [cite: available via NVD]. Patched in version 2026.1.29 [cite: github.com/NevaMind-AI/memU releases]. Check your installed version: `pip show memu`. If it is earlier than 2026.1.29, update before connecting to any messaging channel.

**The memory store as a higher-value target:** A stateless agent has no memory to steal. memU's memory graph contains structured facts about you — your projects, your relationships, your recurring concerns, your decision history. The PostgreSQL database is a higher-value target than any of the other tools in this series. Treat it accordingly:

- Do not expose the Postgres port (5432) to the public internet. The `docker run` command above binds to localhost only. Verify: `docker port memu-postgres`.
- Back up the database before any memU updates.
- If you ever delete the Docker container without backing up the volume, your memory is gone. There is no recovery path.

**The API provider question:** memU sends your session context to whichever AI provider you configured. Unlike Ollama-based setups, your conversation content and retrieved memories travel to an external API on every query. Know which provider you are using and what their data retention policy is.

---

## Resource Usage

| Metric | Value |
|---|---|
| Memory (Postgres at rest) | [FILL] |
| Memory (memUBot process) | [FILL] |
| Memory during query with retrieval | [FILL] |
| Disk (Postgres data + index) | [FILL] |
| Latency added by memory retrieval | [FILL: ms delta vs. direct API call] |

---

*Status: Draft. The before/after memory comparison requires multiple sessions spread over time — budget more than one sitting for this article. Fill all [FILL] markers.*

---

## Three Takes

**[Author A]:**

**[Author B]:**

**[Author C]:**

---

## LinkedIn Post

<!-- 3–5 specific observations. End with "Full setup notes on Medium [link]."
     The interesting angle here is the before/after comparison — pick one specific
     query where memory changed the answer and lead with that. -->
