# CLAUDE.md — Socratic Debater Project

Project-level instructions for Claude. Read this at the start of every session.

---

## Context Loading Protocol

This project uses a flat folder with timestamped filenames (e.g., `__20260323-1000`). Full version history is preserved for epistemic lineage per PROCESS §11.

**Always load the most recent version** of each file type, identified by the latest timestamp in the filename. Do not load superseded versions, session transcripts, pending-review files (`XXXX`-prefixed), PDFs, or early drafts (`_`-prefixed) unless explicitly requested.

**Large files to avoid loading whole:**
- `PT$D_book_20260217-1005.md` (~653 KB) — load sections explicitly as needed
- `NARRATIVE_STRUCTURE__20260217-1500.md` (~109 KB) — load explicitly for book structure work

### Session-type context overrides

**`/socratic` sessions:** Load Thomas KG MD + interlocutor KG MD (if present) + `graph_edges_thomas.jsonc`. **Skip `graph_thomas.jsonc`.** The node JSONC duplicates the MD content in machine format; for live debate work the MD prose is more useful and loading both wastes ~78k tokens. The edges JSONC is still worth loading — it provides precise load-bearing flags not easily scanned from the MD. Confirmed 2026-03-22.

---

## Project Purpose

This project maintains a structured knowledge graph of Thomas's belief system for use in Socratic debate preparation, self-audit, and book development (PT$D). The primary subjects are Thomas (self-side) and Friend S (interlocutor-side).

---

## Knowledge Graph Architecture

### File Roles

| File | Role |
|------|------|
| `KNOWLEDGE_GRAPH_Thomas__[date].md` | Authoritative source. Full prose reasoning, contextual application notes, amendment history, source citations. |
| `graph_thomas__[date].jsonc` | Compiled node file. Debate-ready text summaries. Machine-traversable. |
| `graph_edges_thomas__[date].jsonc` | All edges: typed relations, load_bearing flags, notes. |
| `KNOWLEDGE_GRAPH_Interlocutor__[date].md` | Interlocutor's belief system (same structure as Thomas's). |

### Two-Format Design (MD + JSONC)

The MD and JSONC files are **bidirectionally synced** as a cross-checking mechanism and to preserve future compatibility options.

- The **MD is the authoritative source** for prose reasoning. Full contextual application notes, amendment rationale, and self-audit honesty live there.
- The **JSONC is the operational format** for graph traversal, load-bearing analysis, and cross-graph contradiction detection.
- Neither format is more token-efficient than the other (~26,500 tokens MD vs. ~28,000 tokens JSONC combined). The difference is *structure vs. prose*, not cost.

### Edge Map (Section 7 of the MD)

The MD file contains a **Section 7 — Edge Map** at the bottom: a human-readable rendering of the full JSONC edge list. This is the primary sync checkpoint between formats.

**Sync protocol:**
- The Section 7 header notes the current sync point version and date (e.g., `v2.0 / 2026-03-15`)
- When edges change in the JSONC, Section 7 must be updated to match
- When an edge is added to the MD prose (e.g., a new `[grounds: FP-x]` reference), a corresponding edge must be added to the JSONC
- The load-bearing (7a) and cross-graph (7f) subsections are the most sync-critical

**Section 7 structure:**
- **7a** — Load-bearing edges (any relation, `load_bearing: true`) — primary attack/defense targets
- **7b** — Implies edges → blind spots (undeclared commitments)
- **7c** — Tensions (`tensions_with`) — unresolved internal conflicts
- **7d** — Grounds, non-load-bearing (FP→, FR→, T/SA→ subsections)
- **7e** — Supports & example_of (evidence layer)
- **7f** — Cross-graph Thomas ↔ interlocutor `contradicts` edges (stub until interlocutor graph is built)

---

## Node Taxonomy

| Prefix | Type | Description |
|--------|------|-------------|
| FP-n | First Principle | Strong moral/logical default; universal form establishes weight |
| FR-n | Framework | Interpretive lens applied to data |
| DB-n | Derived Belief | Position held because of Principle + Data |
| EV-n | Evidence | External empirical anchor |
| T-n | Tension Node | Genuine or apparent contradiction, with resolution status |
| BS-n | Blind Spot | Domain where principles imply undeclared positions |
| SA-n | Self-Audit | Calibration challenge; ongoing honest self-assessment |

---

## Edge Relation Vocabulary

| Relation | Meaning |
|----------|---------|
| `grounds` | Source justifies or supports target |
| `supports` | Evidence anchors a belief |
| `implies` | Principle generates an undeclared position (blind spot) |
| `tensions_with` | Internal conflict requiring resolution |
| `example_of` | Evidence instantiates a framework |
| `contradicts` | Direct conflict — primary Socratic engine target |

**`load_bearing: true`** — removing this edge collapses the target node. These are the structurally critical edges for debate targeting.

---

## Key Structural Properties

- **Most central First Principle:** FP-8 (grounds the largest number of downstream nodes; most load-bearing edges)
- **Most central Framework:** FR-13 (resolves nearly every tension node via contextual application logic)
- **Most structurally unresolved self-audit:** SA-4 (honesty tension, `load_bearing: true` on two edges)
- **Cross-graph join point:** Section 7f — `contradicts` edges between Thomas and interlocutor nodes; to be populated when the interlocutor graph is built

---

## Amendment Protocol

- First Principles can only be revised via explicit, timestamped amendment with rationale
- Amendments are written inline in the MD node (e.g., `**v2.0 amendment:**`) and summarized in the Changelog (Section 6)
- The JSONC `meta.note` field should reflect the same amendment summary
- "Contextual application" is not revision — it is correct use of FR-13

---

## Active Companion Documents

- `KNOWLEDGE_GRAPH_FriendS__20260322-1000.md` — Friend S's belief system (anonymized; see README for how to build your own)

> Use timestamps in filenames to identify the current version of each file.
