# From Chatbot to Personal AI

A collaborative series by three enterprise AI practitioners testing six open-source personal AI agents through the same Obsidian vault, the same queries, and honest verdicts.

**Status:** Work in progress. Drafts and working notes.

---

## What This Is

We are engineers who build enterprise AI for a living. This series tests the open-source personal versions — same knowledge base, same queries, six tools, one honest verdict per tool.

The series covers: OpenClaw, ZeroClaw, NanoClaw, memU, Hermes, NemoClaw.

---

## Two Tracks

**Track A — Opinion**
Five articles. Enterprise architect lens. Senior-practitioner audience (CPOs, VPs, CISOs).
Write to the argument, not to a word count.

**Track B — Receipts**
Six setup posts. 1,500–2,500 words each. Hands-on, technical, replicable.
Every setup runs the same three queries against the same Obsidian vault.

---

## Publishing Flow

### Where everything lives

Every article — Track A and Track B — gets a full article on both LinkedIn and Medium.
These are not summaries of each other. The same article, on both platforms.

### Track A — Opinion articles

| Step | Action |
|---|---|
| 1 | Publish as a **LinkedIn Article** (LinkedIn is primary for opinion/senior audience) |
| 2 | Publish a **LinkedIn Post** same day — hook + 2–3 lines + link to article |
| 3 | Co-authors repost with 3–4 bullets of their own take |
| 4 | After 7 days, cross-post to **Medium** under the series publication, attributed "Originally published on LinkedIn" |

### Track B — Setup posts

| Step | Action |
|---|---|
| 1 | Publish on **Medium** first (primary for long technical content) |
| 2 | Publish a **LinkedIn Post** same day — 3–5 key findings driving to Medium |
| 3 | Co-authors repost with 3–4 bullets of their own take |
| 4 | After 7 days, cross-post to **LinkedIn Article** attributed "Originally published on Medium" |

### LinkedIn posting rule

The lead author for each article publishes the post, tagging the other two.
Each co-author then reposts with 3–4 bullets of their personal take — not a generic share.
This generates three separate content touchpoints per article instead of one.

### Multi-author setup

**Medium:** Create one Medium Publication ("From Chatbot to Personal AI"). All three authors
are members. Each article shows the individual author's name and the publication name.
One of us creates the publication before the first piece goes out.

**LinkedIn:** Articles publish from one profile. The post-and-repost strategy handles
co-author visibility without needing native multi-author support.

---

## Sequence

**Do Track B first.** Track A opinion articles cite specific observations, real output
comparisons, and architecture notes that can only come from having done the setups.
Writing Track A before Track B means writing about things not yet tested.

**Lock the test queries before setup #1.** All six tools run the same three queries.
Setup A (OpenClaw) is the canonical source — other setup files reference it.
Changing the queries mid-series breaks the comparison.

---

## Repo Structure

```
track-a-opinion/       Article drafts (Track A — 5 articles)
track-b-receipts/      Setup post drafts (Track B — 6 setup posts)
assets/diagrams/       Shared conceptual diagrams (Phase 4 arc, comparison table)
assets/screenshots/    Per-tool screenshots for Track B setup posts
Series-Outline.md      Full article outlines and series context
Writing-Guidelines.md  Voice rules for co-authors
Citation-Tables.md     All claims that need sourcing before drafting
```

## Each Article File Contains

- Full article draft (main body)
- `## LinkedIn Post` — the short feed post for each platform step
- `## Three Takes` — 2–3 sentences per co-author in their own voice, on the same anchor question

---

## Before Anyone Starts

Three decisions needed before the first setup session:

1. **Agree on the three test queries** — in writing, in Setup A's "The Test Queries" section
2. **Agree on work split** — who leads which articles (determines who sets up which tool)
3. **Name a voice editor** — one person reads everything before publish; voice drift in a three-author series is the biggest quality risk

Also: create the Medium Publication before the first piece goes out.

---

## Contributing

One branch per article. PRs to main = ready to publish.
