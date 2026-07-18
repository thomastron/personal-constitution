# /socratic — Socratic Debater Engine

## What this command does

Given a claim, position, or argument from a bad-faith interlocutor, this command:
1. Loads the Thomas knowledge graph as context
2. Identifies which Thomas nodes the claim contradicts
3. Identifies the load-bearing contradiction (the anchor)
4. Generates Socratic questions using the established tools
5. Flags any Firehose/expansion tactics in use

## How to use

```
/socratic [paste or describe the opponent's claim or argument here]
```

---

## Execution instructions

When this command is invoked:

### Step 1 — Load context
Read the following files:
- `graph_thomas.jsonc` — Thomas's full belief graph (stable current pointer)
- `graph_edges_thomas.jsonc` — All edges including contradiction flags (stable current pointer)
- `KNOWLEDGE_GRAPH_FriendS__[latest].md` — Interlocutor's belief graph (if it exists)

### Step 2 — Classify the claim
Analyze the opponent's argument:
- What type of claim is it? (First Principle / Factual / Procedural / Rhetorical)
- Is this good-faith or bad-faith? What is the evidence for that classification?
- What debate tactic is in use, if any? (Whataboutism / Word salad / False premise / Ad hominem / Firehose / Strawman via over-literalization)

### Step 3 — Find the contradictions
Search the Thomas graph for nodes that directly contradict the claim:
- Start with First Principles (FP nodes) — these are the strongest anchors
- Check Derived Beliefs (DB nodes) for more specific contradictions
- Check existing contradiction edges in graph_edges_thomas.jsonc

### Step 4 — Identify the load-bearing node
Apply FR-12 (Firehose Triage Protocol):
- Which Thomas node, if the opponent accepted it, would collapse their argument?
- That is the anchor. Everything else is decoration.

### Step 5 — Generate Socratic questions
Using the four Socratic tools, generate questions targeting the load-bearing contradiction:

**Logic Bridge** — forces them to justify the topic/position jump
> "I'm struggling to see the connective tissue — how does [their claim] logically address [the contradiction]?"

**Binary Constraint** — eliminates the maybe/sometimes shuffle
> "Is it your position that [fact] is categorically false, or that it is true but irrelevant? It can't be both."

**Hypothetical Falsification** — the checkmate for non-truth-seekers
> "What specific piece of evidence, if I provided it right now, would be sufficient to change your mind on this?"

**Firehose Freeze** — when they're expanding, not engaging
> "You've made [N] points, but they all seem to rely on [X] being true. Can we verify [X] before we deal with the rest?"

### Step 6 — Output format

Return:

```
CLAIM CLASSIFICATION
Type: [claim type]
Good faith: [yes / no / unclear] — [brief reason]
Tactic detected: [tactic name or none]

LOAD-BEARING CONTRADICTION
Thomas node: [ID + label]
Why it's load-bearing: [1-2 sentences]

ANCHOR QUESTION (use this first)
[The single best Socratic question to open with]

FOLLOW-UP QUESTIONS (if they dodge)
1. [Logic Bridge or Binary Constraint]
2. [Hypothetical Falsification]

WHAT TO IGNORE
[List any decorative claims that are bait — do not chase these]

WATCH FOR
[Any self-audit nodes (SA) or blind spots (BS) that make Thomas vulnerable on this topic]
```

---

## Governing principles for this command

- **Contraction, not expansion.** Every output should collapse argument surface area.
- **The anchor holds.** Do not follow topic hops. Return every response to the load-bearing node.
- **FR-13 applies.** If the opponent attacks the literal form of a Thomas statement, name it as a strawman and redirect.
- **DB-11 applies to this output.** This command's output is AI-generated and has no epistemic authority until Thomas reviews and adopts it.
