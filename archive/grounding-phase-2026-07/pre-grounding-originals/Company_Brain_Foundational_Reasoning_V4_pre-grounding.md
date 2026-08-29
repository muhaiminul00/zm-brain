# Company Brain — Foundational Reasoning
### Version 4.0 — CTO Working Reference & LLM/Agent Context Document
### Internal — Not a team-facing document. Not canonical. Preserves reasoning, not specification.

---

## 0. What This Document Is

This is not a spec. It is the reasoning trail behind the specs.

Six canonical documents currently define the Company Brain. They are the
source of truth for *what was decided*. This document exists to capture
*why*, in chronological order, including the wrong turns, so that:

- the CTO has a single place to reconstruct project context without
  re-reading six formal documents end to end, and
- any LLM or agent given this file as context understands the reasoning
  chain well enough to extend the work without contradicting decisions
  already made, re-litigating closed questions, or re-introducing concepts
  that were deliberately rejected.

If something in this document conflicts with a canonical document below,
**the canonical document wins.** This file is the map, not the territory.

### Canonical Documents (status as of this writing)

| Document | Version | Status | Defines |
|---|---|---|---|
| Architecture & Vision | v2.2 | Canonical | The seven-layer pipeline (incl. Exposure), atomic primitives, Primitive Knowledge Objects, memory architecture overview, commitment lifecycle, ostensive/performative drift, provenance requirements |
| Ontology | v1.2 | Canonical | What first-class objects exist (Core Objects, Organizational Structures, Operational Constructs), their composition, Composite Knowledge Objects, their memory homes, their relationships |
| Memory Model | v1.2 | Canonical | How reality becomes memory: Knowledge Representation, formation routing, the five memory types in full, lifecycle, decay, provenance, write governance, conflict resolution, per-subtype commitment lifecycle, drift, learning loop, Memory Consumption & Delivery |
| Product Architecture | v2.1 | Canonical | How organizational memory reaches humans and AI systems: three exposure modes, Knowledge Exchange, OKF(Google Cloud's published) compatibility, Brain-to-Brain interoperability, governance, MVP prioritization |
| Foundational Reasoning | v4.0 (this file) | Reference only | Why each of the above exists, in what order, and what each one fixed in the one before it |

**In progress (planning stage, not canonical):**

| Document | Status | Defines |
|---|---|---|
| Intelligence Architecture v1 | Planning only — two working files exist (`reasoning_1`, `planning_1`), not yet drafted as a canonical document | How memory becomes understanding: context assembly, reasoning pipeline, recommendation/risk/opportunity/drift intelligence, Consultant reasoning, Agent intelligence, confidence model, adaptive intelligence |

**Not yet started:** Trust & Governance Architecture, Technical Architecture, MVP Architecture.

---

## 1. The Original Problem

Companies possess enormous amounts of knowledge. AI cannot reliably use it.

The starting observation, lifted from the YC "Company Brain" thesis:
organizations function because humans compensate for fragmented knowledge —
they remember who knows what, why decisions were made, how exceptions get
handled, what happened before. AI systems have none of that continuity.

Original question: *what is the missing layer between company knowledge and
reliable AI execution?* At the time, no answer existed.

## 2. Early Assumptions

Three beliefs preceded any architecture:

1. Knowledge already exists inside companies. The problem is organization
   and operationalization, not creation.
2. The future bottleneck is organizational context, not model intelligence.
3. If organizational understanding could be structured, AI could execute
   meaningfully more work.

At this stage the working vocabulary was still "knowledge," "information,"
"documentation," "context" — none of which survived into the final
architecture as primitives.

## 3. The First Architecture (Rejected)

Capture → Understand → Memory → Reason → Act.

Five layers. The first real insight inside it: the problem is not storing
information, it's transforming information into execution. This framing
held up. The five-layer shape didn't — it conflated "Reason" and "Act" in a
way that later got pulled apart into Intelligence, Execution, *and*
Evolution once it became clear that learning from outcomes was a distinct
function from acting on intelligence.

## 4. Early Misconceptions (Rejected, kept here so they don't get re-proposed)

- **Knowledge bases** — store information, don't create organizational
  intelligence. Rejected as the core product.
- **Search** — retrieves, doesn't understand. Rejected as the core product.
- **Chat interfaces** — an interface, not the underlying system. Reclassified
  as a surface, not a layer.
- **AI models as the moat** — model capability is a commodity that improves
  continuously; organizational memory compounds and doesn't. Rejected as the
  defensibility thesis. Organizational memory became the moat thesis instead.

## 5. Lessons From Operational Intelligence OS v1

External input, initially read as a competing vision, later understood as
solving an adjacent problem. Contributed: governance, traceability,
readiness, knowledge-gap detection, measurement. Net conclusion: **Company
Brain ≠ Operational Intelligence.** The Brain remembers; Operational
Intelligence evaluates. This distinction held all the way through — it's
why "Derived Intelligence Objects" (Knowledge Gap, Operational Risk, Brain
Score, Drift Signal, etc.) are explicitly excluded from the Ontology in
v1.1/v1.2 Section 7 and assigned to an Intelligence layer instead.

## 6. Lessons From Operational Intelligence OS v2

Shifted focus toward Workspace, Consultant, Agents, Automation. The
strongest contribution was conceptual, not technical: the Consultant model
(Brain → Consultant → Recommendation → Action) and the idea that the Brain
should be active, not passive. Risk flagged at the time: the architecture
could collapse into a workspace-centered model. Resolution: **Company Brain
≠ Workspace.** The Brain is the system; Workspace is one interaction layer
among several (Consultant, Agent System, Automation Studio being others) —
this is why Workspace shows up in Architecture as a Supporting System, not
as the core model.

## 7. The Memory Breakthrough

First major reframe. Knowledge, documents, and databases are not memory.
Memory is context, relationships, experience, decisions, outcomes. The
operative question changed from *how do we organize knowledge* to *how do
organizations remember*. This is the point where "Company Brain" stopped
being a knowledge system in anyone's head and became a memory system.

## 8. The Early Memory Architecture Insight

(Historical note: this chapter described the *first* four-memory-type model
— Factual, Interaction, Action, Learning — discovered before Commitment
Memory existed and long before the actual Memory Model document existed.
Renamed from the original "The Memory Model" chapter title to avoid
collision with the canonical Memory Model document described in Chapter 17.
Treat this chapter as "the first sketch," not as describing the current
system.)

Four memory types, defined by the question each answers: Factual (what do
we know), Interaction (why do we know it), Action (what happened), Learning
(what have we learned). Commitment Memory (who owes what to whom) was added
later, after ontology research made clear that obligations needed their own
stateful store rather than living as static facts inside Factual Memory.

## 9. The Biggest Breakthrough — The Organizational Reality Shift

The most consequential reframe in the project. The architecture had been:
Knowledge → Memory → Reasoning. This felt incomplete because it never
answered *what exactly is being remembered*. Resolution: the Company Brain
is not fundamentally a memory system — it's fundamentally a model of
organizational reality. Memory is one capability built on top of that
model. Architecture changed to: **Reality → Memory → Intelligence →
Execution.** Every document since has been downstream of this single shift.

## 10. The Atomic Primitive Discovery

Question: what is organizational reality actually made of? Early
candidates — Entity, Relationship, Event, Decision, Context — were tested
and rejected as still-composite (each decomposes further). Independent
literature research (DEMO, REA, TOVE, Edinburgh Enterprise Ontology, BWW,
Searle's social ontology, Singh's social commitments, BFO/DOLCE/UFO,
Feldman-Pentland routines) converged on the same ten irreducible primitives
the project landed on independently:

**Actor, Communication, Commitment, Action, Resource, Rule, Goal, State,
Time, Relationship.**

This convergence between independent research and independent product
reasoning is the single strongest validation signal in the whole project.
Decision and Workflow were confirmed as composites (Decision = Communication
+ Goal + Rule + Commitment; Workflow = Actors + Actions + Rules + States +
Commitments), matching Simon/March and Feldman-Pentland's "routines are
units of analysis, not atoms" finding.

## 11. The Architecture Stabilizes (v2.0 → v2.1)

The first full Architecture & Vision document (v2.0) adopted the ten
primitives and added a fifth memory type (Commitment Memory). A structured
review pass found five concrete gaps before it could be treated as stable:

1. **Layer-count mismatch.** Architecture & Vision described six layers
   (Capture → Understand → Memory → Intelligence → Execution → Evolution).
   An earlier draft of this Foundational Reasoning document (the prior
   "Current Architecture" chapter, since removed) described only four
   conceptual layers (Reality → Memory → Intelligence → Execution),
   silently dropping Capture and Evolution. Two canonical-feeling documents
   disagreed with each other. Fixed in v2.1 by making explicit that Reality
   is not a seventh layer — it's the substrate the six layers operate on.
2. **Commitment Memory had no state machine.** It stored "promises" as
   static nouns. Fixed by adding the eight-state lifecycle: Requested →
   Promised → one of Fulfilled, Declined, Delegated, Cancelled,
   Renegotiated, or Breached.
3. **Goal had no memory home.** It was a primitive with nowhere to live.
   Fixed with an explicit Primitive-to-Memory Mapping table placing Goal in
   Factual Memory, and clarifying that State, Time, and Relationship are
   cross-cutting attributes on every record, not separate stores.
4. **No mechanism for ostensive-vs-performative drift detection.** Rules
   describe designed process; Action Memory describes what actually
   happened; nothing compared the two. Fixed by adding an explicit
   Intelligence-layer responsibility (detect the gap) and an
   Evolution-layer responsibility (route confirmed divergence into Learning
   Memory).
5. **Provenance was only generically implied**, not a stated requirement.
   Fixed by adding an explicit Trust System responsibility: every memory
   record must carry source, asserting actor, timestamp, and the
   policy/rule version in effect.

Architecture & Vision v2.1 is the result. It is stable enough to build on.

## 12. The Missing Layer Realization — Ontology

After v2.1 stabilized, the instinct was to move straight to Product
Architecture. That instinct was wrong, and recognizing why it was wrong is
its own important step.

Product Architecture answers *how do users interact with the Brain*. But a
more fundamental question was still unanswered: *what are the actual
first-class objects a user or agent interacts with?* The Architecture
document defines primitives (Actor, Commitment, Goal...) and memory types
(Factual, Commitment...) but never defines the nouns in between — Employee,
Team, Project, Incident, SOP, Task, Meeting. Without that layer, every
Product Architecture decision (what can Consultant reason about, what are
Workspace's primary views, what objects can an Agent manipulate) would be
speculative.

This produced the corrected sequencing:

**Atomic Primitives → Ontology → Memory Model → Product Architecture**

— not "Ontology & Memory Model" as one document (the original plan), but
two separate documents, because Memory Model needs to answer *how does
something become memory*, and that question is unanswerable until *what can
become memory* is already defined. Ontology had to come first and stand
alone.

## 13. The Ontology Layer (v1.1)

Ontology v1.0 (first draft) defined four layers — Atomic Primitives → Core
Objects → Organizational Structures → Operational Constructs — and
populated them with twenty objects (six Core Objects: Person, Team, Role,
Customer, Vendor, Agent; five Organizational Structures: Department, Goal,
Initiative, Project, Organization; nine Operational Constructs: Commitment,
Task, Workflow, SOP, Policy, Decision, Meeting, Incident, Opportunity).

Review pass found four gaps, plus one caught opportunistically:

1. **No composite-to-memory mapping.** Objects built from Commitment (like
   Task) had no stated memory home, recreating the exact orphan problem
   Goal had before v2.1 — just one layer up. Fixed with a full per-object
   Primary Memory Home / Cross-Reference table covering all twenty objects.
2. **No lifecycle inheritance rule.** Task, Assignment, Approval Obligation,
   and Customer Promise all list Commitment as a component but it was never
   stated whether they inherit Commitment's eight-state lifecycle wholesale
   or need their own. Fixed by stating the default rule explicitly (they
   inherit it by default) and explicitly deferring per-subtype restrictions
   to Memory Model v1 — which, notably, did *not* resolve this either; it's
   still open at this point in the timeline (later resolved — see Chapter
   19).
3. **Relationship Model covered less than half the Core Objects.** Role,
   Department, Customer, Vendor, and Agent had zero relationships defined.
   Fixed by adding eight new relationship rows (Person occupies Role, Role
   reports to Role, Team belongs to Department, Department belongs to
   Organization, Customer holds Commitments, Vendor provides Resources,
   Agent acts on behalf of Person or Team, Agent executes Actions).
4. **SOP, Policy, and Workflow were indistinguishable on paper.** All three
   draw heavily on Rule and Goal. Fixed by mapping them onto the same
   ostensive-vs-performative distinction already established in Architecture
   v2.1: **Policy is the constraint** (what is allowed), **SOP is the
   design** (how this is supposed to happen, written before execution),
   **Workflow is the observation** (how this actually happens, reconstructed
   from Action Memory after the fact). This is the same drift-detection
   mechanism from v2.1 Section 11, just given concrete objects to compare.
5. **(Bonus catch.)** "Opportunity" appeared twice — once as a Layer 4
   Operational Construct (a CRM-style tracked record with a goal, resource,
   and commitment attached) and once as a Derived Intelligence Object (an
   AI-surfaced pattern hinting value might exist) — with no distinction
   between them, directly violating the document's own rule that derived
   intelligence objects don't belong in the ontology. Fixed by renaming the
   Intelligence-layer version to **Opportunity Signal**, and stating
   explicitly that a Signal becomes an Opportunity only once a human or
   agent commits resources to formally pursuing it.

Ontology v1.1 is the result. It answers *what exists*, cleanly enough to
build a Memory Model on top of it.

## 14. The Memory Model (v1.1)

With Ontology settled, Memory Model v1 could finally answer its founding
question directly: when something happens, how does it become memory —
concretely, mechanically, not just conceptually?

The centerpiece is the Meeting worked example: a meeting occurs, the
Understanding layer identifies Communication/Actors/Goals/Context inside
it, and Formation Routing fans that single event out into one Interaction
Memory record (the discussion itself) and N Commitment Memory records
(state Requested or Promised) — with zero Action Memory records until
someone actually executes on a commitment, at which point Action Memory
receives the execution and links back to the originating commitment. This
example is the operational answer the whole project had been circling
since Chapter 1.

Memory Model v1.1 also operationally closed four open questions that had
been tracked, unresolved, since the earliest Foundational Reasoning drafts:

- **How memory decays** — Decay Path (confidence/relevance drops) kept
  explicitly distinct from Archive Path (record retired from active set but
  never deleted). Decay primarily affects Learning Memory and, secondarily,
  stale Interaction Memory context.
- **How conflicting memories are resolved** — never silently overwritten;
  both versions persist, one marked Current and one Superseded, with
  tie-break rules (higher-authority source, more recent evidence, explicit
  human review) when confidence is equal.
- **How AI is permitted to write into memory** — Humans may create Factual,
  Interaction, Commitment, and Learning memory subject to authority; AI may
  *propose* memory updates requiring automatic, delegated, or human
  approval depending on type; Automation is restricted to predefined
  scopes. Core principle: AI may contribute memory, AI does not become the
  source of truth.
- **What counts as organizational truth** — resolved operationally rather
  than philosophically. The system always knows which record it currently
  treats as Current vs. Superseded. That operational answer is the only
  one the system needs; it doesn't have to adjudicate truth in the abstract.

Review pass on the draft found six smaller fixes:

1. Section 10's relationship chain had invented a "State Change" object to
   sit between Action and Learning — directly contradicting the
   document's own stated rule against inventing new ontology objects, one
   section after Decision and Outcome were correctly kept out as
   reconstructed/attribute-only. Removed; Action now contributes to
   Learning directly, since Action Memory already carries the before/after
   state that Pattern Detection reads.
2. The section titled "Provenance & Write Governance" only ever contained
   provenance — Write Governance was already its own separate section.
   Retitled to "Provenance" to match its actual content.
3. Factual, Interaction, and Action lifecycle diagrams read as mandatory
   sequences. Clarified as possible stages — a record can sit at "Updated"
   indefinitely and never reach "Superseded."
4. Decay Path and Archive Path were presented as two unconnected paths with
   no stated relationship. Connected explicitly: decay does not
   automatically trigger archival, and a fully decayed Learning record can
   later be explicitly reinforced if the conditions that produced it recur.
5. The Memory Formation Principle (Section 3 — six conditions for something
   to qualify as memory) and the Formation Routing pipeline (Section 4 —
   how a qualifying event fans out across memory types) were adjacent but
   never explicitly linked. Connected: routing only applies to signals that
   already passed the formation filter.
6. Commitment Memory listed "Decisions" as an input, which could be
   misread as Decision being stored — clarified that Decisions trigger new
   Commitment records while remaining themselves reconstructed, not stored.

Memory Model v1.1 is the result. It is the document that finally explains
the mechanism the project had been reasoning toward since Chapter 7.

## 15. Pattern Across The First Three Review Passes

Worth naming explicitly, since it recurred well beyond this point too:
every review pass on Architecture v2.1, Ontology v1.1, and Memory Model v1.1
found the same shape of error — a document states a rule (don't invent new
objects, give every layer the same five fields, don't let two documents
define the same concept differently) and then violates its own rule a few
sections later, almost always at a transition point between sections
written at different times. The fix is never to relax the rule; it's to
find where the document contradicts itself and correct the violation. This
is the most reliable single review heuristic to come out of the project:
**state the rule, then go hunting for the place the document already broke it.**

As later chapters show, this same heuristic is what caught the v1.1→v1.2
cross-document granularity and composition mismatches (Chapter 19).

## 16. Current Beliefs

- Organizations are coordination systems, not document collections.
- Memory is more valuable than documentation; understanding is more
  valuable than storage; reality is more fundamental than memory.
- Trust must exist before automation.
- Agents are actors, not tools — and are consumers of memory, not producers
  of truth.
- Search is a feature, not the product.
- The strongest moat is accumulated organizational memory, because model
  capability is a commodity and organizational memory compounds.
- Ontology has to be stable before Memory Model is meaningful, Memory
  Model has to be stable before Product Architecture is anything but
  speculative, and — as of this revision — Product Architecture has to be
  stable before Intelligence Architecture can be anything but speculative.
  Every layer depends on the one before it being settled first; this
  project has now demonstrated that dependency four times in a row
  (Architecture needed primitives settled; Ontology needed Architecture
  settled; Memory Model needed Ontology settled; Intelligence Architecture
  needs Product Architecture settled).
- Delivery is not an afterthought. Memory that is never surfaced at the
  point of work has no operational value — this belief hardened into
  Architecture v2.2's Principle 8 (Right Memory, Right Moment) and the
  Exposure Layer (Chapter 17 below).
- Representation is not the same thing as meaning. Ontology defines what
  exists; Knowledge Objects define how it's represented; conflating the two
  was an early near-miss, caught and corrected (Chapter 18).

## 17. The Pause — Why The Project Stopped Mid-Build

After Product Architecture v2.0 shipped, the natural next step was Technical
Architecture. The project deliberately paused instead and rewound to
re-examine three things already in motion before building further:

1. **The Exposure Layer.** Product Architecture v2.0 had already built out
   three exposure modes (Ambient Delivery, Agent Access, Mission Control) in
   detail — but Architecture & Vision v2.1 had no corresponding layer in its
   six-layer pipeline. Delivery was being treated as a product-only concern,
   invisible at the architecture level. This was the same orphan pattern
   Goal hit in Chapter 11 and Task hit in Chapter 13, one level up: a
   first-class concern with no architectural home. Resolution: promote
   Exposure to a seventh core layer (Capture → Understand → Memory →
   Intelligence → Execution → **Exposure** → Evolution), add Principle 8
   (Right Memory, Right Moment), and expand Evolution to learn from
   delivery/recommendation outcomes, not just operational outcomes. This is
   what produced Architecture & Vision v2.2.

2. **Evolution Layer priority.** Once Exposure was added, it became clear
   Evolution had been under-specified relative to its actual importance —
   it was the layer responsible for closing the loop on everything the
   other six layers produced (including the new Exposure layer's delivery
   outcomes), but its responsibilities list in v2.1 was thin. Evolution was
   reprioritized and expanded in v2.2 to explicitly evaluate recommendation
   outcomes, agent performance, and exposure effectiveness — not just
   compare designed-vs-executed process.

3. **Open Knowledge Format (OKF - Google Cloud's published).** A representation-layer question that
   turned out to be bigger than it first looked. See Chapter 18.

The "pause and rewind" was itself a deliberate application of the Chapter 15
heuristic at the cross-document level: state the rule (every layer needs an
explicit architectural home), then go hunting for where the documents
already violated it. Exposure was the violation. Fixing it required revising
all four canonical documents, not just adding a section to one.

## 18. The OKF Reasoning — Knowledge Objects As The Missing Representation Layer

The OKF question arrived as "should we adopt the Open Knowledge Format,"
but answering it honestly required two passes.

**First pass.** Treated OKF as a storage-format detail. Conclusion: don't
add a new architectural layer for it; mention it as an implementation note
inside the Memory Layer ("Memory Layer, stored in OKF-compatible
structure"). Strategic read at the time: nobody buys "we use OKF," they buy
"the company never loses knowledge" — so keep it backstage, mention briefly
in Memory Architecture, omit from any investor-facing material aimed at
non-technical audiences.

**Second pass — the actual breakthrough.** Revisiting the question against
both Architecture and Memory Model side by side surfaced a real gap that the
first pass had missed: the Understanding Layer outputs "Structured
Organizational Reality" and the Memory Layer consumes it, but no document
defined what that structured output actually *was* — its canonical
representation. Reality, Primitives, and Memory Types were all defined.
Knowledge Object Format, Interchange Format, and Representation Standard
were not. That's not a storage detail; that's a missing pipeline stage.

Resolution: introduce **Knowledge Objects** as the canonical representation
sitting between Understanding and Memory, without adding a new top-level
layer (which would have broken the seven-layer model's elegance). Concrete
placement:

```text
Understanding
↓
Knowledge Objects   ← new
↓
Memory Formation
↓
Memory
```

This in turn required a granularity decision, made permanent in this
revision cycle:

- **Primitive Knowledge Objects** — the eight atomic types (Actor,
  Communication, Commitment, Action, Resource, Rule, Goal, Relationship
  Object), a closed set, owned by Architecture & Vision.
- **Composite Knowledge Objects** — object-level representations (Person
  Object, Team Object, Policy Object, Meeting Object, etc.), built by
  combining Primitive KOs the same way Ontology composes Core Objects from
  primitives, owned by Ontology.

OKF itself was positioned as a *compatibility target*, not a dependency:
the Company Brain maintains OKF-compatible representations where governance
permits, and extends beyond OKF through memory lifecycle, commitment
state, learning, and governance — capabilities no open knowledge standard
covers. This is the same "don't let the open standard become the product"
instinct from the first pass, now grounded in an actual architectural
placement instead of a footnote.

Cross-document landing:

- Architecture & Vision v2.2 — defines Primitive Knowledge Objects, the
  Understanding Layer's new output, Knowledge Representation Compatibility.
- Memory Model v1.2 — adds a full Knowledge Representation section (new
  Section 4), defining both KO tiers, the Memory Formation relationship,
  and Open Knowledge Compatibility in memory-specific terms.
- Ontology v1.2 — adds Composite Knowledge Objects, an explicit Ownership
  Boundary (Architecture owns Primitive, Ontology owns Composite), and
  states plainly that Ontology remains representation-independent — the
  ontology is true regardless of what format represents it.
- Product Architecture v2.1 — adds Knowledge Exchange, OKF-compatible
  export/import, Knowledge Object inspection (for audit/governance, not
  daily navigation), and a future Brain-to-Brain interoperability
  direction.

This sequencing — OKF question asked once, answered shallow, asked again,
answered structurally — is the same pattern as Chapter 12 (the premature
move to Product Architecture before Ontology existed). Both times the fix
was the same: don't skip a representation/foundation layer just because the
immediate question seems answerable without it.

## 19. The Three Cross-Document Flags — Found And Closed

A scan across the four updated canonical documents (Architecture v2.2,
Ontology v1.2, Memory Model v1.2, Product Architecture v2.1), done after all
four were drafted, surfaced three remaining inconsistencies that none of
the individual document review passes had caught, because each was visible
only by comparing documents against each other rather than reading any one
in isolation.

**Flag 1 — Knowledge Object granularity mismatch.** Architecture and Memory
Model used "Knowledge Object" for the eight primitive types. Ontology
independently used the same term for object-level representations (Person
Object, Team Object). Same name, two different granularities, no stated
relationship between them.

*Resolution:* Two-tier hierarchy, not a single flat term. Primitive
Knowledge Objects (closed set of 8, owned by Architecture) and Composite
Knowledge Objects (open set, one per ontology object, owned by Ontology,
built by combining Primitives). Commitment Object is the one deliberate
exception that exists in both tiers, called out explicitly so it doesn't
read as an error. This mirrors the existing Atomic Primitive → Core Object
composition pattern exactly — no new mechanism was invented, the existing
one was just applied one level up to representations.

**Flag 2 — Decision composition mismatch.** Architecture & Vision defined
Decision = Communication + Goal + Rule + Commitment (4 components). Ontology
defined Decision = Communication + Goal + Rule + Commitment + Context (5).

*Resolution:* Architecture's four-component version wins; Context dropped
from Ontology's Decision row. Reason: Ontology's own Context Model (Section
4) already defines Context as *emergent* — generated from Goals, Rules,
Relationships, History, Actions, Commitments, Time, Resources — not a
structural building block. Listing it as a "Built From" component
contradicted Ontology's own definition of what Context is. This is a
within-document self-contradiction (the Chapter 15 heuristic again), not
just a cross-document one — Ontology had violated its own rule about what
counts as structural versus emergent.

**Flag 3 — Commitment per-subtype lifecycle, orphaned between documents.**
Ontology v1.1 flagged per-subtype lifecycle restrictions as open and
deferred to Memory Model v1. Memory Model v1.1 received the question and
deferred it again, unresolved — no document ever actually owned closing it.
By the time Memory Model v1.2 was drafted for unrelated reasons (OKF,
Knowledge Representation), this question was still sitting open with no
owner.

*Resolution:* Closed in Memory Model v1.2 using the same default-plus-
exceptions pattern that already closed decay, conflict resolution, and AI
write governance in v1.1. Default: every Commitment-derived object inherits
the full eight-state lifecycle. Stated exceptions: Customer Promise cannot
be Delegated (external obligations can't be unilaterally reassigned the way
internal Tasks can), and Customer Promise's Renegotiated state requires
explicit customer-facing notice (internal commitments can renegotiate
silently between responsible actors; customer-facing ones cannot). Task,
Assignment, and Approval Obligation get the full 8 states, no restriction.

All three flags are now closed as of Architecture v2.2, Ontology v1.2,
Memory Model v1.2, and Product Architecture v2.1.

## 20. The Next Gap Realization — Intelligence Architecture

With Architecture, Ontology, Memory Model, and Product Architecture now
mutually consistent, a structured review (preserved in
`Intelligence_Architecture_v1__reasoning_1` and `_planning_1`) surfaced the
next missing layer, using the same diagnostic question that found Ontology
in Chapter 12 and Exposure in Chapter 17: *what does Product Architecture
already assume exists, that no document actually defines?*

Product Architecture v2.0/v2.1 already contains Consultant, Recommendations,
Drift Detection, Risk Detection, Opportunity Detection, Operational
Intelligence, Agent reasoning, and Context Assembly as named product
surfaces — but no document explains how any of them actually produce their
output. Consultant is currently "Question → Answer" with no defined
reasoning steps in between. Drift Detection compares Policy → SOP →
Workflow but never defines how, how often, at what confidence threshold.

This is structurally identical to the Chapter 12 gap (Product Architecture
referencing nouns Ontology hadn't defined yet) and the Chapter 17 gap
(Product Architecture having built Exposure behavior Architecture hadn't
architected yet). The pattern has now recurred three times: **Product
Architecture keeps moving faster than the conceptual layer underneath it,
and each time, the fix has been to go back and write the missing
conceptual document rather than let Product Architecture quietly become the
de facto specification for something it was never meant to define.**

Proposed scope for Intelligence Architecture v1 (planning stage, not yet
drafted as canonical): Intelligence Philosophy (Memory ≠ Intelligence),
Intelligence Inputs, Context Assembly, the Reasoning Pipeline (Situation →
Goal → Constraint → Commitment → Risk → Opportunity Evaluation →
Recommendation Generation), Recommendation/Risk/Opportunity/Drift
Intelligence, Consultant Intelligence (per-mode reasoning behavior for
Inquiry/Planning/Review/Simulation), Agent Intelligence, a Confidence Model,
and Adaptive Intelligence (the distinction between raw feedback observation
and validated, repeated feedback that actually constitutes learning — a
guardrail against the system self-corrupting on noisy single-instance
feedback).

Explicitly out of scope for Intelligence Architecture, same as every prior
conceptual document: models, LLMs, embeddings, vectors, prompts,
fine-tuning, RAG, databases, inference infrastructure — all deferred again
to Technical Architecture.

A new document, **Trust & Governance Architecture**, was also identified as
needed after Intelligence Architecture, since trust-related concerns (Trust
Cards, Provenance, Governance, Memory Writes, Knowledge Exchange Governance,
Agent Permissions, Conflict Resolution) are now scattered across four
different canonical documents with no single owner.

## 21. Current Architecture — Reconciled Final State

The seven-layer pipeline (Architecture & Vision v2.2) and the conceptual
"what feeds what" chain are the same thing described at two different
resolutions. The Chapter 17 (v3.0) four-layer simplification is retired
again; this is the corrected, current statement:

**Reality → Capture → Understanding → Knowledge Objects → Memory →
Intelligence → Execution → Exposure → Evolution**

Where Reality is not a discrete layer but the substrate; Capture and
Understanding jointly construct the structured version of Reality;
Knowledge Objects (Primitive and Composite) are the canonical representation
of that structure; Memory preserves it through time; Intelligence reasons
over it; Execution acts on it; Exposure delivers it to the human or AI actor
who needs it, at the moment of work; Evolution refines all of the above —
including delivery effectiveness, not just operational outcomes — and feeds
the result back into Memory. There is one pipeline, not several competing
ones.

## 22. Open Questions — Current Status

| Question | Status |
|---|---|
| How does organizational reality become memory? | **Closed** — Memory Model v1.2, Formation Routing |
| How does memory decay? | **Closed** — Memory Model v1.2, Decay Path |
| How are conflicting memories resolved? | **Closed** — Memory Model v1.2, Conflict Resolution |
| How is AI permitted to write into memory? | **Closed** — Memory Model v1.2, Write Governance |
| What constitutes organizational truth? | **Closed operationally** — Current/Superseded marking; not resolved philosophically, by design |
| What is the ideal ontology of a company? | **Closed for v1.2** — Ontology v1.2; expected to gain objects as real use cases exercise it |
| Do all Commitment-derived objects need the full eight-state lifecycle? | **Closed** — Memory Model v1.2, Per-Subtype Lifecycle Restrictions table |
| What is the canonical representation between Understanding and Memory? | **Closed** — Architecture v2.2 / Memory Model v1.2, Primitive & Composite Knowledge Objects |
| Is Knowledge Object the same concept at every granularity? | **Closed** — two-tier model, Primitive (Architecture-owned) vs. Composite (Ontology-owned) |
| What is Decision actually built from? | **Closed** — Communication + Goal + Rule + Commitment; Context is emergent, not structural |
| Does delivery/exposure have an architectural home? | **Closed** — Architecture v2.2, Exposure Layer (Layer 6) |
| How are provenance, conflicts, and drift surfaced to humans? | **Closed** — Product Architecture v2.0/v2.1, Trust Cards, Conflict Experience, Drift Experience |
| How does the Brain reason — generate recommendations, detect risk/opportunity/drift? | **Open** — scoped in Intelligence Architecture v1 planning docs, not yet drafted as canonical |
| How does Consultant think, per mode? | **Open** — same, deferred to Intelligence Architecture v1 |
| How is confidence calculated conceptually? | **Open** — same, deferred to Intelligence Architecture v1 |
| How does the Brain's reasoning improve from feedback without self-corrupting on noisy signals? | **Open** — same, deferred to Intelligence Architecture v1 (Adaptive Intelligence) |
| What triggers a decay check — time-based or query-triggered? | **Open** — explicitly deferred to Technical Architecture |
| How should organizational reality be represented technically (storage, schema, versioning)? | **Open** — explicitly out of scope for all conceptual documents; Technical Architecture's job |
| Where do scattered trust/governance concerns get a single home? | **Open** — Trust & Governance Architecture identified as needed, not yet started |
| What does an autonomous Company Brain look like? | **Open** — not yet addressed at any layer |

## 23. Recommended Roadmap

```text
DONE ✓ Foundational Reasoning (this document, v4.0)
DONE ✓ Atomic Primitives
DONE ✓ Architecture & Vision v2.2
DONE ✓ Ontology v1.2
DONE ✓ Memory Model v1.2
DONE ✓ Product Architecture v2.1
NEXT → Intelligence Architecture v1
THEN → Trust & Governance Architecture v1
THEN → Technical Architecture
THEN → MVP Architecture
```

Intelligence Architecture is now the largest conceptual gap in the system.
It is unblocked: it can answer what Consultant reasons about, how Drift/Risk
/Opportunity detection actually work, and how Agents consume intelligence,
by direct reference to Ontology v1.2's object list, Memory Model v1.2's
memory types and write-governance rules, and Product Architecture v2.1's
already-built Consultant/Agent/Drift/Conflict surfaces — instead of
guessing, the same way Product Architecture was unblocked once Ontology and
Memory Model existed (Chapter 19, v3.0 timeline).

## 24. Final Reflection

The project began as a question about AI automation. It became a question
about organizational memory. It became a question about organizational
reality. Then, after four documents stabilized, it became clear those four
documents didn't yet agree with each other on delivery, representation, or
a handful of cross-document details — and resolving that took a deliberate
pause rather than pushing forward into Technical Architecture on a
foundation that wasn't actually settled.

The current honest belief: the Company Brain is not a knowledge base,
memory system, workflow engine, agent platform, or chatbot. It is a living
model of organizational reality that defines what exists, represents it
canonically, remembers it faithfully, delivers it at the point of work, and
— once Intelligence Architecture exists — will reason over what it
remembers and improve its own understanding over time. Five documents deep
now, the project has stress-tested its own foundation four times (Chapters
11, 13, 14, and 19) and held each time. The next stress test is
Intelligence Architecture: the first document whose job is not to define
what the Brain knows, but how it thinks.