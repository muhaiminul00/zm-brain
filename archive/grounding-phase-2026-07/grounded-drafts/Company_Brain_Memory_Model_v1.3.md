Company Brain — Memory Model	v1.3

**COMPANY BRAIN**

Memory Model

Version 1.3

Canonical Conceptual Model

ZeroManual — Internal

July 2026

## Document Control

| **Field** | **Value** |
| --- | --- |
| Version | 1.3 |
| Status | Canonical Conceptual Model — Grounded Draft, pending human review and freeze |
| Supersedes | Version 1.2 |
| Scope | Memory Model only. Does not define databases, storage engines, graphs, vectors, schemas, APIs, or infrastructure. Those belong to Technical Architecture. |

**Changes in This Revision**

- Theoretical Grounding pass (see `Company_Brain_Theoretical_Foundations_v1.md`). No conceptual decision changed. GROUND sections now carry an inline citation callout.
- Open Knowledge Format references (Section 4) updated to reflect direct adoption of Google Cloud's real OKF v0.1 spec, per Master Plan §6 and the companion `OKF_Adoption_Mapping.md` — internal references to "OKF" now mean this spec directly, not a parallel internal concept.
- **Correction (post-review-pass):** Section 8's PROV-O mapping tightened to assign terms per-question (`wasAttributedTo`=who, `wasGeneratedBy`=when, `wasDerivedFrom`=from what source) rather than loosely, and reconciled against the same mapping in Trust & Governance Architecture v1.1 Part 4, which previously assigned the terms per-layer instead — the two documents now state one consistent mapping.
- **Exposition rewrite (this pass):** grounding callouts rewritten from citation-then-mention into theory-first exposition — the source theory stated plainly on its own terms, then an explicit bridge to what this document implements, extends, or diverges from. This document carries the strongest single relationship in the whole grounding phase (Walsh & Ungson's organizational memory theory, Section 3) and the clearest double-loop-learning implementation (Argyris & Schön, Sections 12–13) — both worked through in full below. Stale version reference to Intelligence Architecture (Section 12) corrected from v1.0 to v1.1.
- All prior v1.2 content, structure, and decisions preserved unchanged.

**Closes (long-standing open questions, carried forward from v1.2)**

- Memory Decay
- Conflict Resolution
- AI Write Governance
- Organizational Truth Handling
- Commitment Per-Subtype Lifecycle Restrictions

**Resolved In Product Architecture v2.1**

- Trust Cards
- Conflict Experience
- Drift Experience

**Still Open (deferred intentionally)**

- The exact mechanism that triggers a decay check (time-based vs. query-triggered) — deferred to Technical Architecture.
- CRDT / eventual-consistency literature as the natural parent for Conflict Resolution mechanics — Master Plan §2.3 flags this as implementation-level and defers the citation to Technical Architecture, not this document.

## Table of Contents

*Updates automatically in Microsoft Word. If it shows no entries, select it and press F9 to refresh.*

# 1. Purpose

This document defines how organizational reality becomes organizational memory.

The Ontology defines what exists. The Memory Model defines how what exists becomes remembered.

This document answers: how does the Company Brain transform organizational reality into persistent organizational memory?

This document is conceptual. It does not define:

- Databases
- Storage engines
- Graphs
- Vectors
- Schemas
- Infrastructure

Those belong to Technical Architecture.

# 2. Relationship to the Company Brain

The Company Brain architecture is:

**Reality → Understanding → Knowledge Objects → Memory → Intelligence → Execution → Exposure → Evolution**

The Memory Model defines the transition between Knowledge Objects and Memory, and the mechanisms through which Memory supports Intelligence, Execution, and Consumption.

The Memory Model is responsible for:

**Knowledge Objects → Memory → Consumption**

within the broader Company Brain architecture.

# 3. What Is Memory?

### Theoretical Grounding — Organizational Memory Theory

J.P. Walsh and G.R. Ungson, in "Organizational Memory" (*Academy of Management Review*, 1991), give the first formal academic definition of what it means for an organization — not just an individual — to remember: organizations retain stored information from their own history, usable in present decisions, through five "retention facilities" (individuals, culture, transformations, structures, external archives), moved through by acquisition, retention, and retrieval. This is the claim the definition below implements directly — "a persistent, structured representation of organizational reality through time" is Walsh & Ungson's 1991 finding, not a novel assertion this document is making for the first time.

Where this document diverges from Walsh & Ungson, deliberately: it does not adopt their five-facility taxonomy (organized by *where* memory physically lives — in people, in culture, in archives). Section 6 below organizes memory by *what kind of thing is being remembered* instead — Factual, Interaction, Commitment, Action, Learning — because Company Brain is architecting the retention mechanism from scratch, not describing an informal one that already exists across people and culture. Three of the five resulting types happen to also map cleanly onto a different theory (cognitive memory systems, Field 10); two — Commitment and Learning — map onto neither taxonomy and are Company Brain's own contribution, grounded instead in Fields 2 and 7 respectively. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 5, for the full working of this divergence.

**Relationship:** we implement Walsh & Ungson's core definition of organizational memory directly; we diverge from their specific five-facility taxonomy by design, replacing it with a question-answering taxonomy suited to something being architected rather than something being described after the fact.

## Definition

**A memory is a persistent, structured representation of organizational reality through time.**

Memory is not storage. Memory is not a document. Memory is not a database record. Memory is organizational understanding that has been preserved.

## Core Principle

The Company Brain remembers reality. It does not remember everything. Memory is selective.

## Memory Formation Principle

Something becomes memory only when it satisfies at least one of the following:

- Changes organizational understanding
- Creates or modifies commitments
- Influences future decisions
- Changes organizational state
- Produces learning
- Affects goals, resources, rules, or relationships

Everything else may be captured. Not everything is remembered.

*This is the operational answer to the Architecture **&** Vision document**'**s Memory layer key question, "what should never be forgotten?" — anything matching one of the six conditions above.*

# 4. Knowledge Representation

### Theoretical Grounding

Tom Gruber's 1993 definition — an ontology is "an explicit specification of a conceptualization" — underlies the Knowledge Object concept generally: a Knowledge Object is exactly that, an explicit, shareable specification of one piece of organizational reality. Separately, Google Cloud's Open Knowledge Format (OKF) v0.1, published June 12, 2026 and verified real via web search (markdown + YAML frontmatter, Apache 2.0, active reference tooling), is a narrow, portability-only interchange format. Company Brain has **adopted OKF directly** — not cited as a parallel to a theory, but taken on as its actual Knowledge Exchange format. Internal references to "OKF" below mean this spec directly. Full field-level mapping in the companion `OKF_Adoption_Mapping.md`. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 12, and Master Plan §6.

## Definition

Knowledge Representation is the process by which organizational reality is transformed into canonical organizational knowledge before becoming memory.

The Understanding Layer produces structured organizational understanding.

That understanding is represented through Knowledge Objects.

Memory Formation then transforms those Knowledge Objects into persistent organizational memory.

## Conceptual Flow

**Reality → Capture → Understanding → Knowledge Objects → Memory Formation → Memory**

## Knowledge Objects

Knowledge Objects are canonical representations of organizational reality produced by the Understanding Layer.

Knowledge Objects are not memory.

Knowledge Objects are normalized organizational knowledge units from which memory is formed.

Knowledge Objects exist at two levels.

### Primitive Knowledge Objects

Primitive Knowledge Objects represent the irreducible organizational primitives defined by the Company Brain Architecture.

The Primitive Knowledge Object set is fixed and consists of:

- Actor Object
- Communication Object
- Commitment Object
- Action Object
- Resource Object
- Rule Object
- Goal Object
- Relationship Object

Primitive Knowledge Objects serve as the foundational representation layer for all higher-order organizational concepts.

### Composite Knowledge Objects

Composite Knowledge Objects represent higher-order organizational concepts.

They are constructed by combining Primitive Knowledge Objects according to the Company Brain Ontology.

Examples include:

- Person Object
- Team Object
- Project Object
- Department Object
- Policy Object
- Workflow Object
- Meeting Object
- Initiative Object

Composite Knowledge Objects mirror Ontology Layers 2–4.

### Memory Formation Relationship

Memory Formation may consume:

- Primitive Knowledge Objects
- Composite Knowledge Objects
- Relationships between both

depending on the type of memory being formed.

### Knowledge Object Requirements

Both Primitive and Composite Knowledge Objects must be:

- Human-readable
- AI-readable
- Traceable
- Portable
- Versionable
- Governed

### Open Knowledge Compatibility

The Company Brain maintains compatibility with Open Knowledge Format (OKF) v0.1 — Google Cloud's real, published specification, adopted directly rather than as an internal placeholder concept.

Knowledge Objects are represented, exchanged, imported, exported, or synchronized through OKF-compatible formats where governance permits. See the companion `OKF_Adoption_Mapping.md` for the concrete Composite Knowledge Object → OKF concept-document field mapping.

The Company Brain extends beyond OKF through:

- Memory Lifecycle Management
- Commitment Memory
- Learning Memory
- Organizational Intelligence
- Governance
- Evolution

OKF explicitly leaves trust, provenance, conflict, and decay semantics as open design space — Company Brain's own layers fill exactly that space, at zero cost to OKF's portability guarantee.

# 5. Memory Creation & Formation Routing

## Formation Pipeline

**Reality → Capture → Understanding → Knowledge Objects → Memory Formation → Memory**

Memory Formation applies only to signals that already satisfy the Memory Formation Principle in Section 3 — Formation Routing decides which memory type(s) a qualifying signal writes to, not whether it qualifies in the first place.

### Memory Formation Clarification

Memory Formation consumes Knowledge Objects rather than raw documents, captured signals, or unstructured organizational activity.

The role of Memory Formation is to determine:

- What should be remembered
- Which memory type should store it
- How it should be linked
- How provenance should be preserved

## Formation Routing Rule

A single understood event may create records in multiple memory types simultaneously. Every resulting memory record:

- Shares a common source reference
- Preserves provenance
- Remains independently queryable

This prevents fragmentation while maintaining traceability.

## Worked Example — Meeting

A meeting occurs. The Understanding layer identifies Communication, Actors, Goals, and Context within it.

| **Memory Type** | **What The Meeting Produces** |
| --- | --- |
| Interaction Memory | Discussion, reasoning, negotiation, and context — recorded directly. |
| Commitment Memory | New commitments, assignments, and ownership changes — recorded in state Requested or Promised. |
| Action Memory | None yet. No execution has occurred. |

Later, when a commitment is fulfilled, Action Memory receives the execution, outcome, and state change — linked back to the originating commitment.

**Result: one meeting may generate 1 Interaction record and N Commitment records, with 0 Action records until execution actually occurs.**

# 6. Memory Types

### Theoretical Grounding

Cognitive science distinguishes three kinds of individual memory: Endel Tulving's semantic memory (general facts, no personal/temporal anchor) and episodic memory (specific events anchored in time and place), and Larry Squire's/John Anderson's procedural memory (skills, know-how) rounding out the taxonomy. Three of the five memory types below implement this directly: Factual Memory is semantic memory, Interaction Memory is episodic memory, Action Memory is procedural memory. The other two — Commitment Memory and Learning Memory — have no individual-cognition equivalent at all, because no single human brain needs to track "an obligation someone else owes me" or "what this organization, collectively, has learned"; those are grounded instead in the Language/Action Perspective (Winograd & Flores, 1986 — see Commitment Memory below) and Argyris & Schön's organizational learning theory (1978, 1996 — see Learning Memory below) respectively. This is a genuine finding, not a gap: it identifies exactly where Company Brain's own intellectual property sits. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 10, for the full worked table.

**Relationship:** we implement the cognitive-science taxonomy directly for 3 of 5 types; the other 2 diverge from it entirely because they describe organizational-level, not individual-level, memory.

The Company Brain contains five memory systems: Factual, Interaction, Commitment, Action, and Learning. Each serves a different purpose.

## 6.1 Factual Memory

| **Purpose** | Preserve stable organizational reality. |
| --- | --- |
| **Inputs** | Actors Resources Goals Policies SOPs Organizational Structures |
| **Stores** | People Teams Departments Roles Goals Policies SOPs Resources |
| **Typical Queries** | Who owns this? What teams exist? What policy governs this? What goals are active? Which role has authority? |
| **Lifecycle** | Observed → Recorded → Updated → Superseded → Archived. Not every record passes through every stage — a Factual record may remain Recorded or Updated indefinitely without ever being Superseded. |

## 6.2 Interaction Memory

| **Purpose** | Preserve organizational reasoning. |
| --- | --- |
| **Inputs** | Meetings Discussions Negotiations Approvals Communications |
| **Stores** | Discussion records Negotiation history Approval conversations Context |
| **Typical Queries** | Why was this discussed? What alternatives existed? Who objected? What reasoning was used? |
| **Lifecycle** | Observed → Interpreted → Recorded → Linked → Archived. As with Factual Memory, a record need not reach every stage to be valid. |

## 6.3 Commitment Memory

### Theoretical Grounding

Winograd and Flores (*Understanding Computers and Cognition*, 1986) describe organizational coordination as a "conversation for action": Request → Promise → (work happens) → Report → Accept, with the Promise creating the atomic commitment the whole conversation exists to track. The lifecycle below implements that loop directly for its core three states (Requested→Promised→Fulfilled maps onto Request→Promise→Accept), and extends it with four states — Delegated, Renegotiated, Cancelled, Breached — the original conversational loop has no name for, because Winograd & Flores modeled a single live conversation, not a persistent record that survives handoffs, scope changes, and expiry. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 2, and Master Plan §5.

**Relationship:** we implement the conversation-for-action loop directly for the core states; we extend it with four additional states the theory doesn't cover, because Commitment Memory as a persistent, stateful record — rather than an in-the-moment conversation — is Company Brain's own addition.

| **Purpose** | Preserve obligations between actors. |
| --- | --- |
| **Inputs** | Assignments, Requests, Responsibilities, Promises, and Decisions. *Decisions trigger new commitments but are themselves reconstructed, not stored — see Section 11.* |
| **Stores** | Commitments Tasks Expectations Ownership Responsibilities |
| **Typical Queries** | What is still open? Who owns this? What is overdue? What did Person X promise? What commitment came from this meeting? |
| **Lifecycle** | Requested → Promised → one of Fulfilled, Declined, Delegated, Cancelled, Renegotiated, or Breached. |
| **Special Property** | Commitment Memory is future-oriented. Most memory records describe reality. Commitments describe intended reality. |

### Per-Subtype Lifecycle Restrictions

By default, every Commitment-derived object inherits the full eight-state Commitment lifecycle.

The table below records the only known exceptions.

Absence from this table means the default eight-state lifecycle applies unrestricted.

| Subtype | Restriction | Reason |
| --- | --- | --- |
| Customer Promise | No Delegated | An external obligation cannot be reassigned the way an internal task can. |
| Customer Promise | Renegotiated requires explicit customer-facing notice | Customer-facing promises cannot silently change terms. |
| Task | None — full 8 states | — |
| Assignment | None — full 8 states | — |
| Approval Obligation | None — full 8 states | — |

New subtypes inherit the full lifecycle unless explicitly added to this table.

## 6.4 Action Memory

| **Purpose** | Preserve what actually happened. |
| --- | --- |
| **Inputs** | Executions Workflow runs Incidents Exceptions State changes |
| **Stores** | Actions Outcomes Incident responses Workflow executions |
| **Typical Queries** | What happened? How was this resolved? What actions fulfilled this commitment? How does this process actually operate? |
| **Lifecycle** | Observed → Recorded → Linked → Used → Archived. Shown as possible stages, not a required sequence. |
| **Special Property** | Action Memory represents observed reality. Not intended reality. |

## 6.5 Learning Memory

### Theoretical Grounding

Argyris and Schön's double-loop learning (1978, 1996) — revising the governing rule itself once errors recur, rather than patching the latest instance — is the mechanism Learning Memory exists to store the output of. As a memory *type*, Learning Memory has no individual-cognition equivalent (Field 10) — it's grounded here instead, in the organizational-learning mechanism it serves, worked through in full at Sections 12–13 below. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 7.

**Relationship:** the underlying mechanism (double-loop learning) is a direct implementation of Argyris & Schön; Learning Memory as a named, persistent memory *type* is Company Brain's own contribution — no theory names "an organization's collective learning" as a thing with its own memory store.

| **Purpose** | Preserve organizational learning. |
| --- | --- |
| **Inputs** | Outcomes Patterns Failures Successes Drift Analysis |
| **Stores** | Lessons Heuristics Patterns Process Improvements Policy Improvements |
| **Typical Queries** | What did we learn? Has this happened before? What usually works? What mistakes should be avoided? |
| **Lifecycle** | Created → Validated → Used → Reinforced or Decayed → Archived. |
| **Special Property** | Learning Memory is the primary memory type subject to decay. Lessons lose relevance when organizational reality changes. |

# 7. Memory Lifecycle

All memory records move through lifecycle stages.

## Active Lifecycle

**Observed → Interpreted → Recorded → Linked → Used → Updated**

## Archive Path

**Updated → Superseded → Archived**

Archived records remain historically true. They are removed from the active working set. They are never silently deleted.

## Decay Path

Decay is different from archival. Decay affects relevance. Not existence.

For example, a lesson learned five years ago may still exist. Its confidence and applicability may decrease.

Decay primarily affects Learning Memory, and secondarily Interaction Memory when context becomes obsolete.

*Decay and archival are independent processes: a fully decayed Learning record is not automatically archived, and may later be explicitly reinforced if the conditions that produced it recur.*

# 8. Provenance

### Theoretical Grounding

The W3C's PROV-O is a formal vocabulary for describing provenance, built on three core relations: `wasGeneratedBy` (an entity was produced by a specific activity), `wasAttributedTo` (an entity is the responsibility of a specific agent), and `wasDerivedFrom` (an entity was derived from another entity). This section implements that vocabulary directly, mapped per *question* rather than assigned loosely: `wasAttributedTo` answers **who asserted it**; `wasGeneratedBy` answers **when**, via the capture/understanding activity that produced the record; `wasDerivedFrom` answers **from what source** — the raw artifact or prior record this memory traces back to. This is the same mapping used in Trust & Governance Architecture v1.1 Part 4, which extends it across Intelligence and Execution as well — stated once here for Memory specifically, not restated with different term assignments there. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 13. Fit: Clean — direct implementation, and the strongest single rename opportunity in this document.

Every memory record carries:

- Who asserted it (`wasAttributedTo`)
- When (`wasGeneratedBy`)
- From what source (`wasDerivedFrom`)
- Under which rule version
- Confidence
- Challenge status

Purpose: memory must be explainable. Every memory must answer the question, why do we believe this?

# 9. Write Governance

### Theoretical Grounding

Role-Based and Attribute-Based Access Control (RBAC/ABAC) and Zero Trust security doctrine hold, respectively, that write permission should be scoped to defined roles/attributes rather than granted broadly, and that no actor should be trusted by default regardless of origin. The table below implements both directly: humans, AI, and automation each get a different, explicitly scoped write permission rather than uniform access. See Master Plan §2.3. Fit: Clean, though light — this is standard access-control vocabulary applied, not a deep theoretical claim.

Memory creation is governed. Not every actor may write every memory.

| **Writer** | **Permissions** |
| --- | --- |
| Human | May create Factual, Interaction, Commitment, and Learning memory, subject to authority. |
| AI | May propose memory updates. Writes may require automatic approval, delegated approval, or human approval, depending on memory type. |
| Automation | Restricted to predefined scopes. Must preserve provenance. |

**Core Principle: AI may contribute memory. AI does not become the source of truth.**

# 10. Conflict Resolution

*Master Plan §2.3 flags CRDT / eventual-consistency literature as the natural academic parent for this mechanism, but explicitly defers that citation to Technical Architecture — it is an implementation-level parent, not a conceptual one, and forcing it here would be exactly the kind of premature technical commitment this phase is scoped to avoid. KEEP for this document; revisit at Technical Architecture.*

Conflicting memories are expected. They are never silently overwritten.

- Rule 1 — Preserve both records.
- Rule 2 — Mark one as Current and the other as Superseded.
- Rule 3 — Maintain provenance for both.

## Tie-Break Rules

When confidence is equal:

- Higher authority source
- More recent evidence
- Explicit human review

## Highest-Risk Memory Type

Factual Memory — for example, two systems disagreeing about account ownership.

# 11. Memory Relationships

### Theoretical Grounding

The W3C's RDF model expresses knowledge as subject-predicate-object triples, forming a traversable graph rather than isolated records. The From/Relationship/To table below implements that directly, under plainer labels than RDF's own Subject/Predicate/Object — same structure, chosen for readability by non-technical stakeholders. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 12. Fit: Clean — direct implementation.

Memory gains value through relationships.

| **From** | **Relationship** | **To** |
| --- | --- | --- |
| Meeting | creates | Commitment |
| Commitment | fulfilled by | Action |
| Action | changes | State |
| Action | contributes to | Learning |
| Learning | updates | Policy or SOP |

*Important: Decision remains reconstructed and Action**'**s resulting state is not reified into a separate "State Change" object — Action Memory already carries the before/after state, which is what Pattern Detection reads. Neither Decision nor a standalone state-change record becomes a new ontology object.*

# 12. Memory Drift

### Theoretical Grounding — Why The Gap Opens, And How It Closes

Two theories are doing two different jobs in this mechanism, and it's worth being explicit about which explains what rather than treating them as interchangeable.

**Why the gap exists:** Karl Weick's sensemaking theory (1979, 1995) argues that organizations don't simply execute a pre-designed plan — people act first, on ambiguous information, and enact an environment that diverges from what was originally designed. That's why Policy/SOP and Workflow diverge in the first place: execution enacts reality moment to moment, design doesn't keep up.

**How the gap gets corrected:** Argyris and Schön (1978, 1996) distinguish single-loop learning (fix the instance, leave the rule alone) from double-loop learning (revise the rule itself once errors recur). This section implements that distinction directly and close to exactly: a single Drift Candidate — one instance of divergence — getting corrected in place is single-loop learning. A confirmed Drift Pattern (Section 13, and Intelligence Architecture v1.1 Part 10) routed into Learning Memory as a policy-improvement candidate, which can then actually revise the Policy or SOP through Section 9's Write Governance, is double-loop learning, happening exactly as Argyris & Schön describe it — not an analogy layered on afterward.

See `Company_Brain_Theoretical_Foundations_v1.md`, Fields 8 and 7. Fit: Clean for both — Weick explains the cause, Argyris & Schön explains the correction, together rather than interchangeably. This is one of the two or three strongest fits in the whole document set.

## Definition

Drift occurs when intended reality differs from observed reality.

The comparison uses:

**Policy → SOP → Workflow**

| **Object** | **Source** |
| --- | --- |
| Policy | Factual Memory |
| SOP | Factual Memory |
| Workflow | Reconstructed from Action Memory |

## Drift Signal

A Drift Signal is generated when recurring execution patterns diverge from intended process design. Examples:

- Approvals skipped
- Unofficial steps added
- Repeated exception handling
- Alternative execution paths emerge

*Drift Signals belong to Intelligence. Not Memory.*

*Drift Detection as a named pipeline (Drift Candidate → Pattern → Signal → Severity, defined in Intelligence Architecture v1.1 Part 10) has no academic or industry equivalent found and is not grounded further — see Master Plan §5. This is Company Brain's own engineering of how double-loop learning gets triggered, not something borrowed from Argyris & Schön, who describe the phenomenon but not a four-stage evidence-threshold pipeline.*

# 13. Organizational Learning

### Theoretical Grounding

This process is the same double-loop learning mechanism grounded at Section 12 — Action Memory → Pattern Detection → Learning Formation → Learning Memory implements Argyris & Schön's (1978, 1996) rule-revision loop end to end, from raw execution data through to an updated Policy. The Evolution Loop below (Policy → SOP → Execution → Action Memory → Learning Memory → Updated Policy) additionally depends on Nonaka & Takeuchi's Externalization mode (1995, Field 6) at the point where observed execution first becomes structured, storable Learning Memory content — the same partial, single-mode SECI application already grounded at Architecture & Vision §8–9. See `Company_Brain_Theoretical_Foundations_v1.md`, Fields 7 and 6. Fit: Clean (Argyris & Schön, direct implementation); Partial (SECI, one mode of four).

Learning occurs when reality updates understanding.

## Process

**Action Memory → Pattern Detection → Learning Formation → Learning Memory → Future Intelligence**

## Evolution Loop

**Policy → SOP → Execution → Action Memory → Learning Memory → Updated Policy**

## What Gets Written

Learning records may contain:

- Conditions
- Observed pattern
- Supporting evidence
- Confidence
- Recommendations

*Typical query: what have we learned from similar situations?*

# 14. Relationship to Intelligence

Memory is not intelligence.

Memory preserves understanding.

Intelligence reasons over memory.

**Reality → Knowledge Objects → Memory → Intelligence**

Without Memory, Intelligence has no continuity.

Without Intelligence, Memory has no operational value.

Memory also serves Consumption.

Intelligence is not the only consumer of memory.

Humans, agents, applications, and exposure systems all consume memory through contextual assembly and delivery.

# 15. Memory Consumption & Delivery

## Definition

Memory Consumption is the process by which stored organizational memory is assembled, contextualized, and delivered to a human or AI actor for use in work.

Memory is not valuable because it exists.

Memory becomes valuable when consumed.

## Context Assembly

Before delivery, memory is assembled into contextual packages.

Memory is rarely delivered as isolated records.

Examples include:

- Meeting Brief
- Executive Brief
- Customer Context
- Incident Context
- Proposal Context
- Project Context

### Inputs

A contextual package may combine:

- Factual Memory
- Interaction Memory
- Commitment Memory
- Action Memory
- Learning Memory

into a single response.

## Memory Delivery Routes

### Ambient Route

Examples:

- Slack Suggestions
- Gmail Context
- Outlook Context
- Calendar Briefs
- CRM Panels
- Browser Extension Context

### Agent Route

Examples:

- MCP Retrieval
- A2A Retrieval
- Context Injection
- Agent Memory Access

### Mission Control Route

Examples:

- Personal Reality
- Team Reality
- Organizational Memory
- Consultant
- Operational Intelligence

## Retrieval Principles

### Principle 1

Memory retrieval should be relevance-driven, not storage-driven.

### Principle 2

The same memory may appear through multiple delivery routes.

### Principle 3

Memory should be delivered at the moment of work whenever practical.

### Principle 4

Humans and AI systems consume memory through the same trust and provenance mechanisms.

## Feedback Signals

Every memory consumption event may generate feedback signals.

Examples:

- Accepted
- Rejected
- Modified
- Ignored
- Escalated
- Acted Upon

### Learning Relationship

**Memory Consumption → Feedback Signal → Evolution → Learning**

## Consumption Principle

Memory exists to improve work.

Memory should be evaluated not only by accuracy and completeness, but also by usefulness at the moment of work.

## Exposure Principle

The same memory may support:

- Human work
- AI work
- Decisions
- Coordination
- Execution

through different delivery mechanisms.

# One-Sentence Summary

| **The Company Brain Memory Model defines how organizational reality becomes canonical knowledge, how that knowledge becomes persistent memory, how memory is trusted, connected, evolved, assembled into context, delivered to humans and AI systems, and continuously improved through learning and feedback.** |
| --- |

ZeroManual — Internal   ·   Page  of
