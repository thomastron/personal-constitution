## Personal Constitution — Belief Accountability System

![](_media/WhatEgo.jpeg)

You talk. AI listens, organizes, and pushes back. Your beliefs end up on the record — mapped, connected, and stress-tested. This is not ego preservation. 

No fancy coding or software skills required! 

A simple example:  
_1. Save `KNOWLEDGE_GRAPH_Thomas.md` to your local machine_  
_2. (OPTIONAL) edit it as needed to make your own `KNOWLEDGE_GRAPH_yournamehere.md`_  
_3. Just drag or upload the file into any AI conversations as CONTEXT._  
_4. Start the conversation. Prompt (declare or query) about any topic._   

The structure is there so the AI can understand you more deeply. You don't have to think in graphs. That's what the AI is for.

![Help Me Help You](https://media.giphy.com/media/fdLR6LGwAiVNhGQNvf/giphy.gif)

---
## What you're looking at (pick your lens)

Depending on why you're here:

**1. If you're here to USE the system:**  
> Everything after this section explains how.

**2. If you're evaluating AI / data architecture:**  
>This is a hand-built, machine-traversable knowledge graph — ~150+ typed nodes (first principles, frameworks, derived beliefs, evidence, tensions, blind spots, self-audits) with typed edges and `load_bearing` flags marking the dependencies that would collapse downstream positions if removed. It ships in dual format (prose Markdown for humans, JSONC for machine traversal), with a Socratic debate engine (`/socratic`) and a chain-of-reasoning explainer (`/dog-walk`) that run against the graph in any agentic coding tool (Claude Code, Codex, or any agent that reads `AGENTS.md`). Amendments to first principles are versioned and timestamped. The design problem it solves — getting a reasoning system to honestly report the structure of its own beliefs, including the uncomfortable parts — is the human-side analog of AI alignment work on eliciting honest internal state.

**3. If you're evaluating systems engineering:**  
>This is documentation architecture. It demonstrates failure-mode thinking applied to belief systems — the `load_bearing` flag is FMEA for arguments — plus disciplined change control (timestamped amendments only, no silent edits) and cross-referenced document structure that stays navigable at scale. The methods came from engineering document control; the substrate happens to be epistemology. 


**NOTE:** this machinery was developed alongside — and stress-tested by — a full-length book written under the same constitutional governance principles. The book ships as AI-loadable epistemic infrastructure at [thomastron.github.io/PT$D](https://github.com/thomastron/thomastron.github.io/tree/main/PT%24D).

## Introduction

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
- An **AGENTS.md** that configures the agentic environment for live debate sessions (read natively by Codex and other agents; `CLAUDE.md` imports it for Claude Code)

Everything is versioned, timestamped, and amendment-traceable.

**NOTE:** _This public repo is a proof of concept. My private working copy uses an unconventional flat folder structure with date-suffixed filenames: sorted alphabetically, the files form a visual timeline of revisions, and it's obvious when you're working on an out-of-date file. This copy keeps one canonical file per type, and the full amendment history stays in the private copy._ 

---

### Why It Exists

Three purposes:

1. **Self-audit.** If you can't map your beliefs in a graph, you probably don't know what you believe. Building this forces you to be honest about what grounds what, where tensions are unresolved, and what you're avoiding.

2. **Debate preparation.** When you know which of your nodes are load-bearing — which edges, if removed, collapse the downstream position — you know where you're actually vulnerable. The `/socratic` command turns this into targeted practice.

3. **Public record.** Beliefs stated publicly, with traceability and amendment history, are accountable in a way that private beliefs are not. This is the point. The record is the product.

---

### System Architecture

#### Node Taxonomy

| ...Prefix... | Type | Description |
|--------|------|-------------|
| `FP-n` | First Principle | Strong moral/logical default; universal form establishes weight |
| `FR-n` | Framework | Interpretive lens applied to data |
| `DB-n` | Derived Belief | Position held because of Principle + Framework + Evidence |
| `EV-n` | Evidence | External empirical anchor |
| `T-n` | Tension | Genuine or apparent contradiction, with resolution status |
| `BS-n` | Blind Spot | Domain where principles imply undeclared positions |
| `SA-n` | Self-Audit | Calibration challenge; ongoing honest self-assessment |

#### Edge Vocabulary

| Relation | Meaning |
|----------|---------|
| `grounds` | Source justifies or supports target |
| `supports` | Evidence anchors a belief |
| `implies` | Principle generates an undeclared position (blind spot) |
| `tensions_with` | Internal conflict requiring resolution |
| `example_of` | Evidence instantiates a framework |
| `contradicts` | Direct conflict — primary Socratic engine target |

#### The `load_bearing` Flag

Every edge in `graph_edges_thomas.jsonc` has a `load_bearing` boolean. When `true`: removing this edge structurally collapses the target node. These are the attack surfaces.

This is the single most useful field for debate targeting. The load-bearing edges tell you where the graph is actually vulnerable, not just where it is complex.

#### Two-Format Design

The belief system is maintained in two synchronized formats:

| Format | File | Purpose |
|--------|------|---------|
| Prose MD | `KNOWLEDGE_GRAPH_Thomas__[date].md` | Authoritative. Full contextual reasoning, amendment history, application notes. |
| JSONC graph | `graph_thomas.jsonc` + `graph_edges_thomas.jsonc` | Machine-traversable. Debate-ready summaries. Structured for AI loading. |

**The MD is the source of truth.** The JSONC is the operational format. Neither replaces the other.

Section 7 of the MD file contains a human-readable rendering of the full edge list — the sync checkpoint between formats.

---

### Slash Commands

#### `/socratic [claim or argument]`

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

#### `/dog-walk [topic or argument]`

The chain-of-reasoning explainer. Walks a complex argument step-by-step, making each inferential link explicit and checkable. Useful for understanding an opponent's position before attacking it, or for clarifying your own reasoning chain.

---

### How to Use in Claude Code
EASIEST OPTION - save the `KNOWLEDGE_GRAPH_Thomas.md` to your local machine, edit it to make your own `KNOWLEDGE_GRAPH_yournamehere.md`, and use it as context to feed into future AI sessions on any platform. 

### For Users of Agentic platforms (Claude Code, Codex, and others)
1. **Clone this repo** and open it as your working directory in your agent
2. **AGENTS.md** is loaded as session configuration: natively by Codex and other AGENTS.md-aware agents, and by Claude Code through `CLAUDE.md`, which imports it
3. Ask the agent to run a workflow, e.g. *"Follow `commands/socratic.md` for this claim: …"* or *"Follow `commands/dog-walk.md` for: …"*. In Claude Code, copying the files into `.claude/commands/` also enables `/socratic` and `/dog-walk` as slash commands.
4. The workflows load the relevant graph files and execute the protocol

For `/socratic` sessions, AGENTS.md tells the agent to load:
- `KNOWLEDGE_GRAPH_Thomas.md` — your belief graph (prose)
- `graph_edges_thomas.jsonc` — all edges with load-bearing flags
- Your interlocutor's knowledge graph (if you've built one)

Visually Interact with the demo graphs in this repo:
[![drapedapes.org/personal-constitution/graph_viewer](https://github.com/thomastron/personal-constitution/blob/master/_media/CPT2603290913-1100x569.gif?raw=true)](https://drapedapes.org/personal-constitution/graph_viewer.html)
[drapedapes.org/personal-constitution/graph_viewer](https://drapedapes.org/personal-constitution/graph_viewer.html)


---

### Adapting This for Yourself

This system is designed to be forked and repopulated with your own beliefs.

#### Step 1 — Articulate your First Principles

Start by telling the AI what you actually believe at the deepest level — the things you'd defend in any situation, not just positions you hold on particular topics. These become your FP nodes. You don't need to format them yourself; just say them in plain language and let the AI translate. Anything that can't survive being stated universally probably isn't a first principle.

#### Step 2 — Build your First Principles layer (FP nodes)

Each FP node should be:
- Stated in universal form
- Defensible without appeal to downstream beliefs
- Grounded in your Constitution or independently justifiable
- Connected to downstream nodes via `grounds` edges

#### Step 3 — Add Frameworks, Derived Beliefs, Evidence

FR nodes are lenses — they don't assert facts, they interpret them. DB nodes are positions that depend on both a principle and a framework applied to data. EV nodes are empirical anchors.

#### Step 4 — Map your tensions honestly

T nodes are where your system is most interesting. Every belief system has internal tensions. Mapping them forces you to either resolve them or acknowledge they're unresolved. The resolution status matters.

#### Step 5 — Self-audit aggressively

SA nodes are where you call yourself out. These are the nodes where your stated beliefs and your actual behavior or reasoning pattern might diverge. These are the most valuable nodes in the graph for debate preparation because they're where you're most vulnerable.

#### Amendment Protocol

First Principles may only be revised via **explicit, timestamped amendment** with stated rationale. Amendments are written inline (e.g., `**v2.0 amendment:**`) and summarized in the Changelog. "Contextual application" is not revision — applying a principle to a specific case is correct use of the system, not a change to it.

---

### File Index

| File | Description |
|------|-------------|
| `AGENTS.md` | Agent session configuration (Codex, Claude Code, others) — context loading rules, architecture overview, public-copy rules |
| `CLAUDE.md` | Claude Code entry point — imports `AGENTS.md`, plus Claude-specific notes |
| `KNOWLEDGE_GRAPH_Thomas.md` | Full belief graph — authoritative prose version |
| `CHANGELOG.md` | Amendment history and version log |
| `graph_thomas.jsonc` | Belief graph — JSONC node file (machine-traversable) |
| `graph_edges_thomas.jsonc` | All edges with typed relations and load-bearing flags |
| `graph_viewer.html` | Interactive viewer for the two JSONC files |
| `KNOWLEDGE_GRAPH_PTSD_Book.md` | Knowledge graph of the *PT$D* book |
| `PROCESS_Obligation_First_Workflow.md` | Governing workflow — epistemic accountability protocol |
| `FR-27_Working_Memory.md` | Example: Framework amendment in progress |
| `commands/socratic.md` | `/socratic` workflow definition |
| `commands/dog-walk.md` | `/dog-walk` workflow definition |

---

### Key Structural Properties (Thomas's graph, v2.3)

- **Most central First Principle:** FP-8 — grounds the largest number of downstream nodes; most load-bearing edges
- **Most central Framework:** FR-13 — resolves nearly every tension node via contextual application logic
- **Most structurally unresolved self-audit:** SA-4 — honesty tension, `load_bearing: true` on two edges
- **Cross-graph section:** Section 7f in the MD — contradiction edges between this graph and an interlocutor's graph; to be populated when an interlocutor graph is built

---

### License

The system architecture, slash commands, and process documents are free to use and adapt (MIT).

The belief content — First Principles, Frameworks, Derived Beliefs, and all graph nodes — is personal testimony. It is published as a public record, not as a template for your beliefs. Fork the structure; build your own content.
