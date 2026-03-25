# Personal Constitution — Belief Accountability System

A structured, machine-traversable knowledge graph of one person's belief system — built for Socratic debate preparation, self-audit, and epistemic accountability. Designed to run inside an agentic AI environment (Claude Code).

---

## What This Is

Most people hold beliefs without mapping them. They argue from positions they can't fully articulate, contradict themselves without noticing, and struggle to distinguish what they actually believe from what they're defending in the moment.

This system is an attempt to fix that — for one person, done rigorously.

The core idea: **put your beliefs on the record, in a structured format, with traceability.** Then use an AI agent to attack them.

This repo contains:
- A **personal constitution** — the foundational principles that govern all downstream beliefs
- A **knowledge graph** of first principles, frameworks, derived beliefs, evidence, tensions, blind spots, and self-audits
- A **Socratic debate engine** (`/socratic`) that loads the graph and generates targeted questions to probe the weakest structural points
- A **chain-of-reasoning explainer** (`/dog-walk`) for working through complex arguments step by step
- A **governing process** that enforces epistemic accountability across all artifacts
- A **CLAUDE.md** that configures the agentic environment for live debate sessions

Everything is versioned, timestamped, and amendment-traceable.

---

## Why It Exists

Three purposes:

1. **Self-audit.** If you can't map your beliefs in a graph, you probably don't know what you believe. Building this forces you to be honest about what grounds what, where tensions are unresolved, and what you're avoiding.

2. **Debate preparation.** When you know which of your nodes are load-bearing — which edges, if removed, collapse the downstream position — you know where you're actually vulnerable. The `/socratic` command turns this into targeted practice.

3. **Public record.** Beliefs stated publicly, with traceability and amendment history, are accountable in a way that private beliefs are not. This is the point. The record is the product.

---

## System Architecture

### Node Taxonomy

| Prefix | Type | Description |
|--------|------|-------------|
| `FP-n` | First Principle | Strong moral/logical default; universal form establishes weight |
| `FR-n` | Framework | Interpretive lens applied to data |
| `DB-n` | Derived Belief | Position held because of Principle + Framework + Evidence |
| `EV-n` | Evidence | External empirical anchor |
| `T-n` | Tension | Genuine or apparent contradiction, with resolution status |
| `BS-n` | Blind Spot | Domain where principles imply undeclared positions |
| `SA-n` | Self-Audit | Calibration challenge; ongoing honest self-assessment |

### Edge Vocabulary

| Relation | Meaning |
|----------|---------|
| `grounds` | Source justifies or supports target |
| `supports` | Evidence anchors a belief |
| `implies` | Principle generates an undeclared position (blind spot) |
| `tensions_with` | Internal conflict requiring resolution |
| `example_of` | Evidence instantiates a framework |
| `contradicts` | Direct conflict — primary Socratic engine target |

### The `load_bearing` Flag

Every edge in `graph_edges_thomas.jsonc` has a `load_bearing` boolean. When `true`: removing this edge structurally collapses the target node. These are the attack surfaces.

This is the single most useful field for debate targeting. The load-bearing edges tell you where the graph is actually vulnerable, not just where it is complex.

### Two-Format Design

The belief system is maintained in two synchronized formats:

| Format | File | Purpose |
|--------|------|---------|
| Prose MD | `KNOWLEDGE_GRAPH_Thomas__[date].md` | Authoritative. Full contextual reasoning, amendment history, application notes. |
| JSONC graph | `graph_thomas.jsonc` + `graph_edges_thomas.jsonc` | Machine-traversable. Debate-ready summaries. Structured for AI loading. |

**The MD is the source of truth.** The JSONC is the operational format. Neither replaces the other.

Section 7 of the MD file contains a human-readable rendering of the full edge list — the sync checkpoint between formats.

---

## Slash Commands

### `/socratic [claim or argument]`

The debate engine. Given a claim from an opponent:

1. Loads the knowledge graph
2. Classifies the claim type and identifies debate tactics in use
3. Finds which Thomas nodes it contradicts
4. Identifies the **load-bearing contradiction** — the one node, if accepted, that collapses the opponent's argument
5. Generates targeted Socratic questions using four tools:
   - **Logic Bridge** — forces justification of topic/position jumps
   - **Binary Constraint** — eliminates the "sometimes/maybe" shuffle
   - **Hypothetical Falsification** — the checkmate for non-truth-seekers
   - **Firehose Freeze** — when they're expanding, not engaging
6. Returns what to ignore (bait claims) and what vulnerabilities to watch for

### `/dog-walk [topic or argument]`

The chain-of-reasoning explainer. Walks a complex argument step-by-step, making each inferential link explicit and checkable. Useful for understanding an opponent's position before attacking it, or for clarifying your own reasoning chain.

---

## How to Use in Claude Code

1. **Clone this repo** and open it as your working directory in Claude Code
2. **CLAUDE.md** will be auto-loaded as session configuration
3. Start a session with `/socratic [opponent's claim]` or `/dog-walk [topic]`
4. The commands load the relevant graph files and execute the protocol

For `/socratic` sessions, the CLAUDE.md instructs Claude to load:
- `KNOWLEDGE_GRAPH_Thomas__[latest].md` — your belief graph (prose)
- `graph_edges_thomas.jsonc` — all edges with load-bearing flags
- Your interlocutor's knowledge graph (if you've built one)

---

## Adapting This for Yourself

This system is designed to be forked and repopulated with your own beliefs.

### Step 1 — Write your Constitution

Start with `CONSTITUTION_Principles__*.md`. These are the non-negotiable constraints on your thinking — not opinions, not positions, but operating principles. State them in universal form. Anything that can't survive being stated universally probably isn't a first principle.

### Step 2 — Build your First Principles layer (FP nodes)

Each FP node should be:
- Stated in universal form
- Defensible without appeal to downstream beliefs
- Grounded in your Constitution or independently justifiable
- Connected to downstream nodes via `grounds` edges

### Step 3 — Add Frameworks, Derived Beliefs, Evidence

FR nodes are lenses — they don't assert facts, they interpret them. DB nodes are positions that depend on both a principle and a framework applied to data. EV nodes are empirical anchors.

### Step 4 — Map your tensions honestly

T nodes are where your system is most interesting. Every belief system has internal tensions. Mapping them forces you to either resolve them or acknowledge they're unresolved. The resolution status matters.

### Step 5 — Self-audit aggressively

SA nodes are where you call yourself out. These are the nodes where your stated beliefs and your actual behavior or reasoning pattern might diverge. These are the most valuable nodes in the graph for debate preparation because they're where you're most vulnerable.

### Amendment Protocol

First Principles may only be revised via **explicit, timestamped amendment** with stated rationale. Amendments are written inline (e.g., `**v2.0 amendment:**`) and summarized in the Changelog. "Contextual application" is not revision — applying a principle to a specific case is correct use of the system, not a change to it.

---

## File Index

| File | Description |
|------|-------------|
| `CLAUDE.md` | Session configuration for Claude Code — context loading rules, architecture overview |
| `CONSTITUTION_Principles__20260129-1145.md` | Foundational principles governing all work |
| `KNOWLEDGE_GRAPH_Thomas__20260324-1000.md` | Full belief graph — authoritative prose version (v2.3) |
| `KNOWLEDGE_GRAPH_Thomas__CHANGELOG__20260323.md` | Amendment history and version log |
| `graph_thomas.jsonc` | Belief graph — JSONC node file (machine-traversable) |
| `graph_edges_thomas.jsonc` | All edges with typed relations and load-bearing flags |
| `PROCESS_Obligation_First_Workflow__20260130-1428.md` | Governing workflow — epistemic accountability protocol |
| `FR-27_Working_Memory__20260323.md` | Example: Framework amendment in progress |
| `self-audit_FR-14_credibility-threshold_20260306.md` | Example: Self-audit challenge on credibility threshold |
| `.claude/commands/socratic.md` | `/socratic` slash command definition |
| `.claude/commands/dog-walk.md` | `/dog-walk` slash command definition |

---

## Key Structural Properties (Thomas's graph, v2.3)

- **Most central First Principle:** FP-8 — grounds the largest number of downstream nodes; most load-bearing edges
- **Most central Framework:** FR-13 — resolves nearly every tension node via contextual application logic
- **Most structurally unresolved self-audit:** SA-4 — honesty tension, `load_bearing: true` on two edges
- **Cross-graph section:** Section 7f in the MD — contradiction edges between this graph and an interlocutor's graph; to be populated when an interlocutor graph is built

---

## License

The system architecture, slash commands, and process documents are free to use and adapt (MIT).

The belief content — First Principles, Frameworks, Derived Beliefs, and all graph nodes — is personal testimony. It is published as a public record, not as a template for your beliefs. Fork the structure; build your own content.
