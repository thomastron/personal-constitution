# AGENTS.md — Personal Constitution / Socratic Debater

Instructions for AI coding agents working in this repository: Codex, Claude Code (through `CLAUDE.md`, which imports this file), and any other agent that reads `AGENTS.md`. Read this at the start of every session.

> This is the public proof-of-concept copy of the project. It has one canonical file per type (no timestamp suffixes) and no `_archive/` directory. `CHANGELOG.md` summarizes the version history; the full record is kept in a private working copy.

---

## Project purpose

This project maintains a structured knowledge graph of Thomas's belief system, used for Socratic debate preparation, self-audit, and development of the book *PT$D*.

---

## Context loading

Each file type has exactly one active copy in the repo root, under a static name. There is nothing to disambiguate by filename; just load the file.

| File | Role |
|------|------|
| `KNOWLEDGE_GRAPH_Thomas.md` | Authoritative source. Full prose reasoning, contextual application notes, source citations. |
| `graph_thomas.jsonc` | Compiled node file. Debate-ready text summaries. Machine-traversable. |
| `graph_edges_thomas.jsonc` | All edges: typed relations, `load_bearing` flags, notes. |
| `CHANGELOG.md` | Amendment history: what changed, when, and why. |
| `KNOWLEDGE_GRAPH_PTSD_Book.md` | Separate knowledge graph of the *PT$D* book (BFR-/BTN- IDs), cross-referenced from the main graph. |

Don't load session transcripts, pending-review files (`XXXX`-prefixed), PDFs, or early drafts (`_`-prefixed) unless explicitly asked.

**`/socratic` sessions:** load `KNOWLEDGE_GRAPH_Thomas.md`, `graph_edges_thomas.jsonc`, and an interlocutor graph if the user has built one (none ships in this repo). Skip `graph_thomas.jsonc`: it duplicates the MD in machine format, and for live debate work the MD prose is more useful. The edges file is still worth loading for its precise `load_bearing` flags.

---

## Workflows

Two workflows live in `commands/`:

- `commands/socratic.md` is the Socratic debate engine. Given an opponent's claim, it finds the load-bearing contradiction in Thomas's graph and generates targeted Socratic questions.
- `commands/dog-walk.md` is the chain-of-reasoning explainer. It walks an argument step by step for a specific audience, flagging hidden leaps and filter-premises.

In any agent, run one by asking for it directly, for example: *"Follow `commands/socratic.md` for this claim: …"*. The files are tool-neutral Markdown; the `/socratic` and `/dog-walk` names are how Claude Code exposes them as slash commands (see `CLAUDE.md`).

---

## Knowledge graph architecture

### Two formats (MD + JSONC)

The MD and JSONC files are kept **bidirectionally synced** as a cross-check.

- The **MD is authoritative** for prose reasoning, amendment rationale, and self-audit honesty.
- The **JSONC is the operational format** for graph traversal, load-bearing analysis, and cross-graph contradiction detection.

Each graph file carries a version in its header or `meta` block. Check every file's own header before assuming the formats are in sync, and treat the MD as authoritative when they disagree.

### Edge map (Section 8 of the MD)

The MD's **Section 8 — Edge Map** is the sync checkpoint between formats. Its header records the current sync point. Its subsections still carry the legacy labels `7a`–`7f` from before a v3.1 renumbering:

- **7a**: load-bearing edges (`load_bearing: true`), the primary attack and defense targets
- **7b**: `implies` edges pointing to blind spots (undeclared commitments)
- **7c**: `tensions_with` edges, unresolved internal conflicts
- **7d**: non-load-bearing `grounds` edges (FP→, FR→, T/SA→ subsections)
- **7e**: `supports` and `example_of` edges (the evidence layer)
- **7f**: cross-graph Thomas ↔ interlocutor `contradicts` edges (a stub until an interlocutor graph exists)

Sync rules:

- When edges change in the JSONC, update Section 8 to match.
- When MD prose gains an edge reference (e.g. `[grounds: FP-x]`), add the matching edge to the JSONC.
- 7a and 7f are the most sync-critical subsections.

---

## Node taxonomy

| Prefix | Type | Description |
|--------|------|-------------|
| FP-n | First Principle | Strong moral/logical default; universal form establishes weight |
| FR-n | Framework | Interpretive lens applied to data |
| DB-n | Derived Belief | Position held because of Principle + Data |
| EV-n | Evidence | External empirical anchor |
| T-n | Tension Node | Genuine or apparent contradiction, with resolution status |
| BS-n | Blind Spot | Domain where principles imply undeclared positions |
| SA-n | Self-Audit | Calibration challenge; ongoing honest self-assessment |

## Edge relation vocabulary

| Relation | Meaning |
|----------|---------|
| `grounds` | Source justifies or supports target |
| `supports` | Evidence anchors a belief |
| `implies` | Principle generates an undeclared position (blind spot) |
| `tensions_with` | Internal conflict requiring resolution |
| `example_of` | Evidence instantiates a framework |
| `contradicts` | Direct conflict — primary Socratic engine target |

**`load_bearing: true`** means removing the edge collapses the target node. These are the structurally critical edges for debate targeting.

---

## Amendment protocol

- First Principles can only be revised through an explicit, timestamped amendment with rationale.
- Amendments are written inline in the MD node (e.g. `**v2.0 amendment:**`), summarized in `CHANGELOG.md`, and mirrored in each JSONC file's `meta.note`.
- "Contextual application" is not revision; it is correct use of FR-13.
- Anything an agent produces is untrusted intermediate material until Thomas reviews and adopts it (DB-8).

## Public-copy rules

This repository is public. When adding or editing content:

- Don't add private individuals (friends, family, colleagues), whether named or pseudonymous, and don't quote private correspondence.
- Don't add personal health or medical details, or details about family members.
- Generalize named political figures and movements to structural form (for example, "authoritarian enablers" rather than a named politician's supporters).
- This copy is curated from a private working copy. Don't copy content from private files or earlier versions into it without Thomas's explicit review.

---

## Key structural properties

As derived from `graph_edges_thomas.jsonc` at the 2026-09-24 rewrite. Re-derive them by edge count before relying on them.

- **Most central First Principle:** FP-8 (21 outgoing edges, 7 load-bearing, the highest of any node on both measures).
- **Most central Framework, by tension-resolution role:** FR-13 grounds or dissolves 6 of the 12 tension nodes (T-1, T-2, T-3, T-5, T-6, T-8) plus SA-4. By raw outgoing-edge count it is not the highest (FR-4, FR-1, FR-2, and FR-14 each have more).
- **Most structurally unresolved self-audit:** SA-4 (the honesty tension), with `load_bearing: true` on both its edges: `FP-9 tensions_with SA-4` and `T-8 grounds SA-4`.
- **Cross-graph join point:** Section 8, subsection `7f`: `contradicts` edges between Thomas and interlocutor nodes, a stub until an interlocutor graph is built.

## Companion documents

No interlocutor graph ships in this repo. `KNOWLEDGE_GRAPH_Thomas.md` alone is a self-side graph. The Socratic engine's cross-graph features (Section 8, subsection `7f`, and the interlocutor load step above) activate only once a user builds their own second graph; see the README. Don't assume a companion file exists; check the repo root before referencing one.
