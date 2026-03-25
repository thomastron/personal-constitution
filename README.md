# Personal Constitution — Belief Accountability System

![The Personal Constitution of [User]](_media/Gemini_Generated_Image_pbdkvrpbdkvrpbdk.jpg)

You talk. AI listens, organizes, and pushes back. Your beliefs end up on the record — mapped, connected, and stress-tested.

No coding or software required. For a most simple example: save `KNOWLEDGE_GRAPH_Thomas.md` to your local machine, edit it as needed and make your own `KNOWLEDGE_GRAPH_yournamehere.md`, and then just drag this file into AI conversations as context. Then prompt about any topic. The structure is there so the AI can understand you more deeply. You don't have to think in graphs. That's what the AI is for.

![Help Me Help You](https://media.giphy.com/media/fdLR6LGwAiVNhGQNvf/giphy.gif)

---

## What This Is

Everyone has a personal constitution. It's the set of principles that actually govern how you think, what you defend, and what you won't compromise on — whether you've written them down or not. The difference between having it on paper and not is accountability.

This system is that constitution, in digital form. Instead of pen and paper, you get a packet of structured files that an AI can read, traverse, and reason over. The Knowledge Graph *is* the constitution. They're the same thing.

The core idea: **AI is your wingman.** It holds your beliefs in memory better than you can. It organizes them, maps how they connect, flags where they contradict each other, and points out the blind spots your principles imply but you've never consciously addressed.

Most people argue from System 1 — fast, automatic, pattern-matched. You say what feels right. This system forces System 2: slow, deliberate, effortful reasoning where you actually examine the chain of logic holding your positions together. Not because the AI lectures you, but because it asks the question you haven't asked yourself yet.

**You say what you believe. The AI helps you figure out what that actually means, what it connects to, and where it breaks down.**

The structured format (nodes, edges, syntax) exists so the AI can understand your thinking at a deeper level — not because you need to think that way. You'll rarely look at the raw structure. You'll just talk, and the AI will build the map. The more clearly your beliefs are on record, the more precisely the AI can challenge, support, and extend your thinking.

This repo contains:
- A **knowledge graph** (your constitution) — first principles, frameworks, derived beliefs, evidence, tensions, blind spots, and self-audits
- A **Socratic debate engine** (`/socratic`) that loads the graph and generates targeted questions to probe the weakest structural points
- A **chain-of-reasoning explainer** (`/dog-walk`) for working through complex arguments step by step
- A **governing process** that enforces epistemic accountability across all artifacts
- A **CLAUDE.md** that configures the agentic environment for live debate sessions

Everything is versioned, timestamped, and amendment-traceable.

**NOTE:** _I use an unconventional flat folder structure with date suffixes. This works for small teams and allows for instant visibility into document control history. For example, when browsing the folder sorted alphabetically, the file revision history is fairly obvious as the files create a visual timeline of sorts. It's also more obvious if you are working on an out-of-date file._ 

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

EASIEST OPTION - save the `KNOWLEDGE_GRAPH_Thomas.md` to your local machine, edit it to make your own `KNOWLEDGE_GRAPH_yournamehere.md`, and use it as context to feed into future AI sessions on any platform. 

## For Users of Agentic platforms like Claude Code
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

### Step 1 — Articulate your First Principles

Start by telling the AI what you actually believe at the deepest level — the things you'd defend in any situation, not just positions you hold on particular topics. These become your FP nodes. You don't need to format them yourself; just say them in plain language and let the AI translate. Anything that can't survive being stated universally probably isn't a first principle.

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
