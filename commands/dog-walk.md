# /dog-walk — Explain a Chain of Reasoning Step by Step

## What this command does

When you can see the whole logical path clearly but others keep getting lost, this command helps you slow down and walk them through it. One step at a time. No teleporting.

The name: when you walk a dog, you don't teleport to the destination. You take each step deliberately, and the dog stays with you at every one. A "leap" in an explanation is when you jump from step 3 to step 7 — you arrive, but the listener is still standing at step 3.

## How to use

```
/dog-walk [paste or describe what you're trying to explain]
```

Optionally add:
- **Audience:** who you're explaining it to (their background, what they already accept)
- **Destination:** what conclusion you want them to reach

---

## Execution instructions

When this command is invoked:

### Step 1 — Gather (if not already provided)

If the user hasn't specified, ask:
1. **What are you trying to explain?** (a few sentences is fine)
2. **Who is the audience?** What do they already know or accept? What worldview or background are they coming from?
3. **What is the destination?** What conclusion or understanding do you want them to arrive at by the end?

Don't ask all three as a form. Ask conversationally. If most of this is clear from context, skip the question and proceed.

---

### Step 2 — Check for a filter-premise

Before mapping the chain, ask: **does the audience hold a belief that would silently veto the conclusion, no matter how cleanly the chain is walked?**

A filter-premise is not a gap inside the chain — it's a frame the audience brings in that pre-rejects the destination. Common forms:
- **Futility:** "There's nothing we can do about it anyway."
- **Irrelevance:** "That might be true, but it doesn't affect me."
- **Distrust of source:** "That's what they want me to think."
- **Prior conclusion:** "I already know how this works."

If a filter-premise is present, walking the chain more clearly will not help. The listener will process every step through the filter and arrive at the same rejection. This is not a leap problem — it's a **wrong chain** problem.

When a filter-premise is detected:
1. **Name it explicitly** in the output — "The audience's filter-premise is X."
2. **Identify whether there is a parallel chain** that doesn't depend on the contested premise. Often the speaker is walking Chain A (which the filter blocks) when Chain B (which bypasses the filter entirely) leads to the same destination.
3. **Route the walk down Chain B.** Acknowledge Chain A honestly — if the audience is partly right about it, say so — then put it down and pick up the chain that doesn't require their agreement on the contested point.
4. If no parallel chain exists, the walk must address the filter-premise first, as its own mini-walk, before the main chain can proceed.

> **Example:** The speaker wants to argue that personal silence enables authoritarianism. The audience's filter is "not much I can do about it." Chain A (silence has macro consequences) requires the audience to believe individual action moves historical outcomes — which they've rejected. Chain B (silence changes the person who stays silent, regardless of outcome) doesn't require that belief at all. Put Chain A down. Walk Chain B.

---

### Step 3 — Map the chain

Lay out the raw chain privately (not yet shown to user) before producing the walk:

- **Starting point:** The premise or fact the audience already accepts. This is where the dog's leash starts.
- **Destination:** The conclusion you want to reach.
- **Links:** Every step between them. Write them out in order, one per line.

For each link, ask: *Is this connection spelled out, or is it assumed?* Mark assumed connections with `[LEAP?]`.

---

### Step 4 — Audit the leaps

A leap is any place where the speaker expects the listener to:
- Silently fill in a logical connection
- Remember a point made several steps ago
- Recognize a pattern the speaker sees intuitively but hasn't named

Leaps are not failures — they're just invisible steps. The goal is to make them visible.

For each `[LEAP?]` flagged in Step 2:
- Write out what the listener would need to already believe or know for this step to follow naturally
- Decide: is that something this audience has, or does it need to be stated?

---

### Step 5 — Write the walk

Now produce the explanation as a clean, sequential walk. Use this structure:

**The Walk: [Topic]**

> **Audience:** [who this is written for]
> **Starting from:** [the premise they accept]
> **Arriving at:** [the conclusion]

Then the numbered steps:

```
1. [Starting point — stated plainly, the thing they already accept]

2. [First link] — Because of [1], it follows that [2]. [Brief explanation of why.]

3. [Second link] — Now that we know [2], we can see that [3]. [Brief explanation.]

4. [Continue until destination] — And since [N-1], we arrive at [destination].
```

Rules for the walk:
- Each step must connect explicitly to the one before it. Use transition language: *"Because of this...", "Which means...", "So now we know...", "That's why..."*
- Keep steps short. One idea per step.
- Never skip a link, even if it feels obvious. State it anyway.
- If a step requires the listener to remember something from three steps ago, restate it briefly: *"(Recall from step 2 that...)"*

---

### Step 6 — Flag remaining gaps

After the walk, add a short section:

**Watch for these gaps:**
- List any steps that are still doing a lot of work silently — places where the audience might nod along but not actually track the connection
- Flag any steps that depend on assumed shared values or background knowledge that the specific audience may not have
- Note if the walk is too long — if there are more than ~7 steps, consider whether it can be split into two shorter walks

---

### Step 7 — Output format

Return:

```
THE CHAIN MAP
[Starting point] → [step 2] → [step 3] → ... → [Destination]
(Leaps flagged: [list any that were bridged])

THE WALK
[Full numbered walk with explicit transitions]

WATCH FOR
[Any gaps, assumed knowledge, or audience-specific risks]
```

---

## Governing principles for this command

- **Diagnosis before prescription.** Before suggesting how to explain something, map what's actually breaking down. The walk comes after the audit, not instead of it.
- **The listener is not the problem.** Lost listeners are usually a sign of a hidden leap, not a dumb audience.
- **State the obvious.** In a walk, obvious steps earn trust. They let the listener say "yes, yes" before you ask them to say "yes" to something harder.
- **Check the leash before you walk.** If the audience holds a filter-premise — a belief that pre-rejects the destination regardless of how clearly the chain is walked — walking more clearly won't help. Find the chain that doesn't require their agreement on the contested point, and walk that one instead.
- **One dog, one leash.** Stay on the single chain. If there's a side argument or a supporting point, it goes in a footnote — not in the walk.
- **The connection is the content.** The value of this process is not the steps themselves but the explicit *because* between each one. That's what people miss.
