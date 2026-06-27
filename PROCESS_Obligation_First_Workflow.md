<!-- ARTIFACT HEADER
Type: Governing Process
Status: Active Default
Mode: Mode 1
Obligation Holder: Human Authors
Promotion Rule: May be amended only via timestamped successor document per Amendment Rule
Notes: Enforces obligation-first epistemic control across all project artifacts -->


# PROCESS: OBLIGATION-FIRST WORKFLOW

**Project:** [Working Title TBD]
**Timestamp:** 2026-01-30 14:28
**Status:** Active / Enforceable
**Supersedes:** PROCESS_Obligation_First_Workflow__20260130-1415.md



---

## Purpose of This Document

This document defines **how work proceeds** under the constraints established in:
- `KNOWLEDGE_GRAPH_Thomas__[latest].md` (your belief graph is your constitution)

**This is a flexible framework, not rigid prescription.** It describes ideal behaviors and goals while allowing adaptation to emerging needs.

**Primary Goals:**
1. **Epistemic Accountability:** Prevent silent epistemic failure as intelligence, tooling, and narrative density increase
2. **Searchability:** Enable efficient retrieval of decision history and conceptual evolution
3. **Traceability:** Maintain clear lineage of responsibility and belief development

This process exists to ensure that:
- obligation is never accidentally displaced,
- comfort incentives are detected early,
- narrative power does not become a substitute for truth-alignment,
- and the project's epistemic history remains searchable and accountable.

---

## PROCESS AXIOM

> **No artifact advances unless its obligation-holder is explicit.**

This applies to:
- stories,
- outlines,
- revisions,
- AI-generated drafts,
- summaries,
- and exports.

Advancement includes _promotion, consolidation, publication, or implied authority_.

---

## SECTION 1 — Roles and Responsibility

### 1.1 Human Authors (Obligation Holders)

Human collaborators:
- define goals,
- decide what counts as "in bounds,"
- accept responsibility for consequences.

They are the **only entities** permitted to:
- declare a file canonical,
- approve publication,
- or accept moral residue.

Obligation cannot be delegated, abstracted, or diffused.

---

### 1.2 AI Systems (Non-Obligated Intelligence)

AI systems may:
- generate drafts,
- analyze structure,
- surface contradictions,
- stress-test claims.

AI systems may not:
- determine truth,
- resolve moral tradeoffs,
- or be treated as authoritative sources.

All AI output is treated as **untrusted intermediate material** until explicitly adopted by a human obligation-holder.

---

## SECTION 2 — Mode Declaration (Mandatory)

**Scope:** Mode declarations apply to **revision work on canonical content** (stories, essays, chapters, analytical sections).

Mode declarations are **not required** for:
- Reference documents (Style Guide, Character Profile, etc.)
- Structural scaffolds (outlines, frameworks)
- Exploratory generation
- Research and analysis tasks

Every substantial **revision interaction** must declare its mode **before** work begins.

Only two valid modes exist.

### MODE 1 — Structural Review

**Focus:**
- coherence
- placement
- flow
- conceptual weight

**Permissions:**
- reordering
- splitting
- reframing
- relocation of material

**Constraints:**
- substance must be preserved **or explicitly relocated**
- no implicit deletion
- no compression without traceability

MODE 1 changes _where_ meaning lives, not _what_ meaning asserts.

---

### MODE 2 — Fidelity-Preserving Revision

**Focus:**
- clarity
- rhythm
- legibility
- precision

**Permissions:**
- sentence-level changes only

**Constraints:**
- zero condensation without acknowledgment
- no semantic drift
- no belief substitution

MODE 2 improves transmission **without changing belief content**.

---

### Undeclared Mode

Undeclared mode = **invalid output**.
Invalid output may be retained as raw material but **may not advance**.

---

### Exploratory Generation (Non-Mode Activity)

Exploratory or speculative generation is permitted **only** under the following conditions:
- it is explicitly labeled _Exploratory_,
- it is non-canonical by default,
- it is not treated as revision of existing artifacts.

Exploration does **not** constitute a mode.
It produces inputs, not advancements.

---

## SECTION 3 — Artifact Lifecycle

### 3.1 Draft Creation

All drafts:
- receive a timestamped filename,
- are assumed **non-canonical**,
- and may contradict existing material.

Drafts are allowed to be wrong.
They are not allowed to be **implicitly right**.

---

### 3.2 Canonical Promotion

A document becomes canonical only when **all** of the following are true:

1. A human obligation-holder explicitly designates it canonical.
2. It references the constitutional principles it relies on.
3. It identifies:
    - what belief it asserts,
    - what belief it strains, modifies, or rejects.

Canonical status is **never inferred** from polish, length, confidence, or narrative force.

---

### 3.3 Revision Rules — WRITE NEW, NEVER EDIT

**FIRM POLICY: Always create new timestamped versions. Never edit existing files.**

This policy exists because:
- AI context rot produces silent truncation during edits
- Editing in place risks corrupting the only copy
- Creating new files means truncation produces a *bad new file*, not a *corrupted only file*
- Human can compare versions and choose which to keep
- Simpler mental model eliminates edit-related failure modes

**The protocol:**
1. Read the current version
2. Create a new file with new timestamp
3. Human verifies the new file against the previous version
4. If truncation occurred, human repairs or discards the new file
5. Previous version remains intact regardless of what happens to new version

**What this replaces:**
- ~~preserve epistemic lineage~~ → lineage preserved by keeping all versions
- ~~never overwrite prior versions~~ → cannot overwrite if you only create new
- ~~explicitly note loss of detail~~ → human catches loss via diff comparison

If a revision simplifies complexity, it must state **why simplification is justified** and **what is lost**.

Unacknowledged loss is treated as epistemic failure.

---

## SECTION 4 — Drift Detection

The following are treated as **drift signals**:
- increasing rhetorical confidence without increased evidence,
- repeated smoothing of disagreement,
- comfort-oriented reframing,
- unexplained deletion of nuance,
- narrative coherence replacing explicit claims.

When drift is detected:
- work pauses,
- the issue is documented,
- resolution occurs at the **structural level**, not through surface edits.

---

## SECTION 5 — Story-Specific Constraints

Every story must include an accompanying **Intent Declaration** stating:
- which model or belief it instantiates,
- whose obligation is evaded or reclaimed,
- which comfort incentive is exposed,
- whether the story stabilizes or destabilizes the system.

Stories without intent are treated as **non-aligned artifacts**, regardless of quality or appeal.

---

## SECTION 6 — Disagreement Handling

Disagreement is expected.

When disagreement cannot be resolved:
- both positions are documented,
- neither is erased,
- divergence becomes part of the permanent project record.

False consensus is treated as a failure mode more severe than unresolved conflict.

---

## SECTION 7 — Export and Freeze Protocol

PDF exports represent **epistemic snapshots**, not living documents.

Before export:
- obligation-holder confirms readiness,
- unresolved disagreements are acknowledged,
- timestamp reflects belief state, not convenience.

Exports do **not** retroactively redefine canon.

---

## SECTION 8 — Failure Modes This Process Is Designed to Prevent

- Intelligence outrunning responsibility
- Comfort replacing clarity
- AI output being mistaken for authority
- Narrative coherence masking unresolved belief
- Revision erasing epistemic history
- Speed substituting for correctness
- **Context rot producing silent truncation**
- **In-place edits corrupting the only copy**


---

## SECTION 9 — CLAUDE.md Versioning Exception

### 9.1 The Technical Constraint

Claude Code (the desktop AI assistant application) requires its project instruction file to be named exactly `CLAUDE.md` (case-sensitive). It will not recognize timestamped variants such as `CLAUDE__20260119-0806.md`.

This creates a conflict with Section 3.3 (Write New, Never Edit).

### 9.2 Resolution: Archive-First, Then Edit

For `CLAUDE.md` only, the following modified workflow applies:

**Before ANY modification to CLAUDE.md:**
1. Copy the current `CLAUDE.md` to `_archive/CLAUDE__YYYYMMDD-HHMM.md`
2. Use the timestamp representing when the version was archived
3. This preserves the version that was active at that time
4. **Verify the archive copy exists and is complete before proceeding**

**Then create the update:**
1. Edit `CLAUDE.md` directly in the root directory
2. Document changes in LOG with timestamp and rationale

**Human verification required:**
1. After AI edits CLAUDE.md, human must diff against archived version
2. Human verifies no unintended truncation occurred
3. If truncation detected, human restores from archive and repairs manually

**Result:**
- Archive preserves the known-good version before any edit
- If edit produces truncation, archive enables recovery
- Human verification catches what AI cannot detect

### 9.3 Rationale

This exception:
- **Preserves epistemic discipline:** Archive-first means good version always exists
- **Accommodates technical reality:** Claude Code's hardcoded filename requirement cannot be reconfigured
- **Adds human verification:** Catches truncation that AI cannot detect
- **Creates minimal special-casing:** Only one file receives exceptional treatment

### 9.4 AI Assistant Protocol

When instructed to update `CLAUDE.md`, AI assistants must:
1. **First** copy current `CLAUDE.md` to `_archive/CLAUDE__[timestamp].md`
2. **Verify** the archive copy was created successfully
3. **Then** edit the active `CLAUDE.md`
4. **Request human verification** of the edit against the archive
5. Document the change in the LOG with rationale

**CLAUDE.md is the only file where in-place editing is permitted**, and only because the tool requires it. All other files follow Section 3.3 (Write New, Never Edit).

---

## SECTION 10 — LOG.md Versioning

### 10.1 Policy Change (2026-01-30)

LOG.md switches from append-only to **timestamped versions**.

**Previous policy:** Append-only single file
**New policy:** New timestamped LOG file each work session

### 10.2 Rationale

Even append operations carry risk:
- AI context rot could truncate during append
- Long LOG files approach context window limits
- Timestamped versions eliminate all edit risk
- Session-based files are easier to navigate

### 10.3 Protocol

**Starting a work session:**
1. Create new LOG file: `LOG__YYYYMMDD-HHMM.md`
2. Reference previous LOG at top of new file
3. Add entries for current session

**LOG file structure:**
```markdown
# LOG — [Date]

**Previous LOG:** `LOG__[previous-timestamp].md`
**Session start:** [timestamp]

---

## [Time] - [Entry Title]

[Entry content]

---
```

**End of session:**
- No special action required
- File remains as record of that session
- Next session creates new file

### 10.4 Finding Information

To search across LOG history:
- Use grep/search across all `LOG__*.md` files
- Files are chronologically ordered by filename
- Each file references its predecessor for chain navigation

---

## SECTION 11 — File Deletion Policy

### 11.1 No Permanent Deletion

**Files are NEVER permanently deleted from the project.**

This applies to:
- Superseded process documents
- Obsolete drafts
- Exploratory artifacts
- Misnamed files
- Failed experiments
- AI-generated material deemed unsuitable
- Truncated/corrupted versions (valuable as failure records)

### 11.2 Archive Protocol

When a file is no longer active or needed in the root directory:

1. **Move (do not delete)** the file to `_archive/`
2. **Preserve the original filename** exactly as it was
3. **Document the archival** in the LOG with:
   - Timestamp of archival
   - Reason for archival
   - What (if anything) supersedes it

### 11.3 Rationale

Permanent deletion:
- **Erases epistemic history** — prevents reconstruction of decision lineage
- **Eliminates traceability** — no way to verify what was tried and rejected
- **Creates memory holes** — later collaborators cannot understand why certain paths weren't taken
- **Violates PRINCIPLE 10** — "Time Is Part of the Argument"; timestamps record belief evolution
- **Prevents learning from failure** — unsuccessful approaches are valuable data

The `_archive/` folder serves as:
- **Epistemic fossil record** — preserves what was believed when
- **Decision audit trail** — shows why current approach was chosen over alternatives
- **Insurance against memory failure** — prevents "we never tried that" errors
- **Honesty mechanism** — no hiding of failed attempts or abandoned ideas
- **Recovery source** — truncated files can be repaired from archived versions

### 11.4 AI Assistant Protocol

When an AI assistant or human collaborator determines a file should be removed from active use:

1. **NEVER use `rm`, `del`, or equivalent deletion commands**
2. **ALWAYS use `mv` / `move` to relocate to `_archive/`**
3. **Document in LOG** why the file was archived

### 11.5 Disk Space Exception

If disk space becomes genuinely constrained (unlikely for text files), the human obligation-holder may authorize permanent deletion of specific archived files, but this requires:
- Explicit human decision (never AI-initiated)
- Documented rationale in LOG
- Acknowledgment of what epistemic history is being sacrificed

This should be treated as an **exceptional failure condition**, not routine practice.

---

## SECTION 12 — Context Rot and Human Verification

### 12.1 The Problem: Context Rot

AI systems operating on long documents face a structural constraint: **finite context windows**.

As conversations progress and documents grow:
- Earlier content gets compressed or displaced from active context
- Long documents create pressure to "summarize" or "reference previous versions"
- This pressure produces **silent truncation**—content loss disguised as efficiency
- The AI cannot reliably detect its own context loss

**Context rot is not a bug to be fixed—it is a structural force to be managed.**

Like fear (PRINCIPLE 4), context rot:
- operates invisibly,
- distorts outputs systematically,
- and requires explicit countermeasures.

### 12.2 The Solution: Write New + Human Verification

The combination of two mechanisms prevents context rot from being catastrophic:

1. **Write New, Never Edit (Section 3.3):** Truncation produces a bad *new* file, not a corrupted *only* file
2. **Human Verification:** Human compares new version to previous, catches truncation, repairs or discards

**The human obligation-holder bears responsibility for document integrity.**

AI is intelligence amplifier; human is integrity guarantor.

### 12.3 Verification Protocol

After AI creates a new version of any document:

1. **Compare new version to previous version** using file diff tools (VS Code, git diff, etc.)
2. **Check for unexpected truncation:**
   - Line count decreased when additions were expected
   - Sections replaced with "see previous version" references
   - Content summarized without explicit acknowledgment
3. **Verify structural completeness:**
   - All expected sections present
   - Cross-references still valid
   - No "orphaned" references to removed content

**If truncation detected:**
- Discard the truncated new file (or archive it as failure record)
- Human repairs manually, creating correct new version
- Document the failure in LOG

### 12.4 AI Assistant Protocol

When operating on documents, AI assistants should:

1. **Always create new timestamped files** (never edit in place, except CLAUDE.md)
2. **Warn the human** when document length approaches context pressure
3. **Never use "see previous version" as substitute for content**
4. **Never truncate with summary tables that replace detail**
5. **Explicitly state** if unable to hold full document in context
6. **Request human verification** after creating new versions

### 12.5 Rationale

This section exists because:
- **Context rot is invisible to AI** — the system doesn't know what it's forgotten
- **Truncation looks like efficiency** — removing "redundant" content feels helpful
- **Silent loss violates PRINCIPLE 6** — epistemic fidelity requires acknowledged loss
- **Human tools (diff) detect what AI cannot** — comparative analysis reveals truncation
- **Write-new eliminates catastrophic failure** — bad new file ≠ corrupted only file

The human-in-the-loop is not a bottleneck—it is the **integrity mechanism** that makes AI collaboration trustworthy.

### 12.6 Document Integrity Responsibility

**Document integrity is a human obligation, not an AI capability.**

AI systems can:
- Generate content
- Follow formatting rules
- Attempt to preserve structure

AI systems cannot:
- Guarantee they haven't forgotten earlier content
- Verify their own completeness
- Detect their own context loss

Therefore:
- Human verifies AI output
- Human catches truncation
- Human repairs or discards bad versions
- Human bears obligation for final document state

This is not a workaround—it is the correct division of labor between intelligence (AI) and obligation (human).

---


## SECTION 13 — Document Splitting and Truncation Protocol

### 13.1 The Tradeoff

Living documents face competing pressures:
- **Completeness:** Full context produces better AI-assisted work
- **Token efficiency:** Long documents cause context window degradation ("rot")
- **Version sprawl:** Duplicating content across timestamped versions wastes space

No single approach optimizes all three. This section establishes when splitting is acceptable and what safeguards are required.

### 13.2 When Splitting Is Permitted

Document splitting (where a newer version omits content available in an older version) is permitted **only** when:

1. The **omitted content is stable** (not actively being revised)
2. The newer document contains **prominent, unmissable warnings** citing the companion document
3. The warnings specify **exactly what is omitted** and **why**
4. A reader encountering the newer document **cannot proceed without awareness** of the dependency

### 13.3 Required Warning Elements

When a document depends on a companion for completeness, it must include:

1. **Header-level warning** (within first 30 lines) with visual marker (⚠️)
2. **Specific filename** of the companion document
3. **List of what is omitted** from current document
4. **List of what is complete** in current document
5. **Rationale** for the split

Example warning format:
```
⚠️ **DOCUMENT DEPENDENCY WARNING** ⚠️

This document is INCOMPLETE without: `FILENAME__YYYYMMDD-HHMM.md`

**Omitted from this version:** [specific list]
**Complete in this version:** [specific list]
**Rationale for split:** [brief explanation]

Both documents must be read together for full context.
```

### 13.4 Human Verification Checkpoint

**AI systems cannot self-certify completeness when working with split documents.**

Before accepting AI work products that reference split documents, the human obligation-holder must verify:
- AI read both documents (not just the newer one)
- AI did not false-present work as complete when it relied on truncated context
- References to omitted content are accurate

This is an instance of PRINCIPLE 1: AI may generate sophisticated outputs from incomplete context without realizing the incompleteness. The obligation to verify completeness cannot be delegated to the AI.

### 13.5 Failure Modes Prevented

This protocol addresses:
- AI presents work as complete when it only read the truncated version
- Future collaborators miss critical context because warnings were insufficient
- "Context collapse" where LLMs assume they have full picture
- Split documents drift apart without anyone noticing the divergence
- Human accepts AI certification of completeness when AI lacked full context

### 13.6 When NOT to Split

Do not split documents when:
- The "stable" content is actually under active revision
- Warnings would be longer than the content saved by truncating
- The split would require constant cross-referencing during normal use
- The human cannot practically verify AI read both documents

When in doubt, preserve completeness over token efficiency.

---


## Amendment Rule

Changes to this process require:

1. A new timestamped process document.
2. Identification of the failure the change addresses.
3. Explicit acknowledgment of tradeoffs introduced.

Silent mutation of process is prohibited.

---

**End of Document**
