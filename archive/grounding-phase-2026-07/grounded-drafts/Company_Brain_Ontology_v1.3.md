Company Brain — Ontology	v1.3

**COMPANY BRAIN**

Ontology

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
| Scope | Ontology only. Memory Model and Product Architecture remain separate documents. |

**Changes in This Revision**

- Theoretical Grounding pass (see `Company_Brain_Theoretical_Foundations_v1.md`). No conceptual decision changed. GROUND sections now carry an inline citation callout. This document is, per Master Plan §2.2, the single best fit for external grounding in the whole document set — DEMO/Enterprise Ontology is a near-complete academic parent for this document as a whole.
- **Exposition rewrite (this pass):** grounding callouts rewritten from citation-then-mention into theory-first exposition — the source theory (principally Dietz/DEMO) stated plainly on its own terms, then an explicit bridge to what this document implements, extends, or diverges from. "Ostensive/performative" language in the SOP/Workflow disambiguation (Section 3) aligned with the plainer "designed/executed" phrasing used consistently elsewhere in this document set.
- All prior v1.2 content, structure, and decisions preserved unchanged.

**Changes in v1.2 (carried forward from prior revision)**

- Added Relationship To Knowledge Representation, clarifying that Ontology defines concepts while Knowledge Objects define their representation (Section 2).
- Updated the Ontology Bridge to include Knowledge Objects between Ontology and Memory (Section 1).
- Added Ontology And Knowledge Objects, introducing Composite Knowledge Objects and their relationship to the Primitive Knowledge Objects defined in Architecture & Vision v2.2 (Section 3).
- Added Open Knowledge Compatibility and Representation Independence statements (Section 2).
- Added Ontology Boundary, clarifying what Ontology is explicitly not responsible for (Section 8).
- Reclassified object-level Knowledge Objects (Person Object, Team Object, Policy Object, etc.) as **Composite Knowledge Objects**, resolving a granularity mismatch against the primitive-level Knowledge Objects defined in Architecture & Vision v2.2 and Memory Model v1.2 (Section 3).
- Fixed a cross-document inconsistency in Decision's composition — removed Context from Decision's "Built From" list (Layer 4), aligning with Architecture & Vision v2.2's four-component definition and with Ontology's own Context Model (Section 4), which defines Context as emergent, not structural.
- Added an explicit Ownership Boundary between Primitive Knowledge Objects (owned by Architecture & Vision) and Composite Knowledge Objects (owned by Ontology) (Section 3).
- Updated the One-Sentence Summary to reflect Ontology's role as the foundation from which Knowledge Objects, Memory, Intelligence, Products, and Technology are derived.

**Resolved In Memory Model v1.2**

- Per-Subtype Commitment Lifecycle Restrictions — see Memory Model v1.2, Section 5.3.

**Still Open (deferred to Memory Model v1.2 / Technical Architecture)**

- Relationship coverage for objects not yet exercised by a real use case.
- Storage and versioning schema for ontology objects — explicitly out of scope for this conceptual document.

## Table of Contents

*Updates automatically in Microsoft Word. If it shows no entries, select it and press F9 to refresh.*

# 1. Purpose

This document defines the ontology of the Company Brain.

The purpose of the ontology is to answer a single question:

**What exists inside the world that the Company Brain understands?**

The ontology serves as the bridge between:

**Atomic Primitives → Ontology → Knowledge Objects → Memory → Intelligence → Products → Technology**

Knowledge Objects are the canonical representations derived from Ontology.

Ontology defines the concepts.

Knowledge Objects define their representation.

The ontology is not a database model.

It is not a technical schema.

It is not a representation format.

It is a conceptual model of organizational reality.

# 2. Ontology Philosophy

### Theoretical Grounding — Enterprise Ontology / DEMO

Jan Dietz's DEMO (Design & Engineering Methodology for Organizations), formalized in *Enterprise Ontology: Theory and Methodology* (2006) and extended in Dietz & Mulder (2020), models an organization as a network of transactions between an initiator and an executor — each transaction a fixed pattern of coordination-acts (request, promise, accept) wrapping one production-act (the actual work). Dietz's central, most load-bearing claim is methodological, not structural: an organization's *essential* model — what it fundamentally is — must be described entirely independent of how it happens to be implemented today. DEMO calls this separating the "essential" layer (coordination and production acts) from the "informational" and "documental" layers (the systems and paperwork that happen to support it right now). An organization's essence doesn't change when the software underneath it changes.

This document implements that separation directly, close to word for word — the statement immediately below, that Company Brain does not model documents, software, databases, or dashboards as primary concepts, is Dietz's own stated purpose, applied. The Ontology is the essential layer; Knowledge Representation, storage, and product interfaces are the informational/documental layers Dietz explicitly subordinates to it. This is the single closest match between an academic parent and a Company Brain document in the entire grounding phase — Master Plan §2.2 identifies DEMO as a near-complete parent for this document as a whole, and the rest of this section works through where that holds exactly and where Company Brain's own four-layer structure only parallels DEMO rather than copying it (Section 3). See `Company_Brain_Theoretical_Foundations_v1.md`, Field 4.

The Company Brain does not model documents, software, databases, or dashboards as primary concepts.

Those are representations.

Instead, the Company Brain models:

- Organizational reality
- Organizational coordination
- Organizational memory

The ontology therefore represents:

- What exists
- How things relate
- How organizations coordinate
- How organizations change through time

## Relationship To Knowledge Representation

The Ontology defines what exists inside organizational reality.

Knowledge Representation defines how ontology objects are represented, exchanged, interpreted, and consumed throughout the Company Brain.

The Ontology remains the source of conceptual truth.

Knowledge Objects are representations derived from Ontology.

The Ontology does not define representation formats.

The Ontology defines the concepts those formats represent.

### Open Knowledge Compatibility

### Theoretical Grounding

Google Cloud's Open Knowledge Format (OKF) v0.1, published June 12, 2026, is a narrow, portability-only spec: knowledge as a directory of markdown files with minimal YAML frontmatter, designed so any producer can write a bundle and any consumer can read it without a shared SDK. Company Brain has **adopted this directly** as its actual Knowledge Exchange interchange format — not cited as an analogy, and not a parallel internal spec kept under the same name. Full field mapping in the companion `OKF_Adoption_Mapping.md`. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 12, and Master Plan §6.

The Company Brain represents ontology objects through Canonical Knowledge Objects compatible with Open Knowledge Format (OKF) v0.1 whenever practical.

OKF compatibility affects representation and exchange.

It does not alter the ontology itself.

The ontology remains independent of any specific representation format.

### Representation Independence

Organizational reality exists independently of how it is represented.

The Ontology remains valid regardless of:

- Databases
- APIs
- Knowledge Formats
- Knowledge Objects
- Storage Technologies
- Product Interfaces

Representations may evolve.

Ontology remains the conceptual foundation.

# 3. Ontology Layers

### Theoretical Grounding

DEMO's own internal structure splits an organization's model into a Cooperation Model (who transacts with whom), an Action Model (the rules governing each transaction), a Process Model (how transactions compose into larger processes), and a Fact Model (the state produced) — a small set of coordination primitives composing upward into the concrete structures an organization actually reasons about. John Zachman's 1987 framework, crossing six interrogatives against multiple levels of abstraction, makes a related claim about comprehensive coverage. The four-layer structure below (Atomic Primitives → Core Objects → Organizational Structures → Operational Constructs) lands on a near-parallel shape to DEMO's own layering — both move from atomic coordination units up to concrete organizational structures — but it wasn't derived by copying DEMO's specific layers; Foundational Reasoning V4 Chapter 10 shows it was arrived at independently, through separate literature research (DEMO among several other sources) and product reasoning that happened to converge on a similar shape. That convergence is worth stating honestly as a strong parallel, not an exact correspondence: Company Brain implements DEMO's philosophy of atomic-to-composite decomposition, and its four-layer shape mirrors DEMO's four-model split without claiming to be a direct copy of it. See `Company_Brain_Theoretical_Foundations_v1.md`, Fields 4 and 11.

The ontology consists of four layers.

**Atomic Primitives → Core Objects → Organizational Structures → Operational Constructs**

## Ontology And Knowledge Objects

The Ontology defines organizational concepts.

Knowledge Objects are canonical representations of those concepts.

Knowledge Objects do not introduce new organizational concepts.

They are representations of existing ontology concepts.

### Composite Knowledge Objects

Composite Knowledge Objects represent Core Objects, Organizational Structures, and Operational Constructs.

Each Composite Knowledge Object is built by combining Primitive Knowledge Objects (the eight atomic types defined in Architecture & Vision v2.2), the same way Ontology Layer 2–4 objects are built from Atomic Primitives.

| Ontology Concept | Composite Knowledge Object |
| --- | --- |
| Person | Person Object |
| Team | Team Object |
| Commitment | Commitment Object |
| Policy | Policy Object |
| Meeting | Meeting Object |

**Note:** Commitment Object appears in both tiers.

It exists as:

- A Primitive Knowledge Object representing the Commitment primitive.
- A Composite Knowledge Object representing the Commitment ontology object.

This is intentional.

Commitment is one of the few concepts that exists both as an atomic primitive and as a first-class ontology object.

### Ownership Boundary

Architecture & Vision defines the Primitive Knowledge Object layer.

Primitive Knowledge Objects correspond to the atomic primitives that form the foundation of organizational reality.

Ontology defines Composite Knowledge Objects.

Composite Knowledge Objects are derived from Core Objects, Organizational Structures, and Operational Constructs and may evolve as the Ontology evolves.

Memory Model defines how both Primitive and Composite Knowledge Objects become persistent organizational memory.

Product Architecture defines how memory derived from those objects is consumed by humans and AI systems.

## Layer 1 — Atomic Primitives

The irreducible building blocks of organizational reality.

These primitives are defined in the Architecture & Vision document and serve as the foundation for both Ontology and Primitive Knowledge Objects.

Everything else in this ontology is derived from them.

- Actor
- Communication
- Commitment
- Action
- Resource
- Rule
- Goal
- State
- Time
- Relationship

These primitives are defined in the Architecture & Vision document. Everything else in this ontology is derived from them.

## Layer 2 — Core Objects

Core Objects are the first-class entities that exist inside the Company Brain — the primary objects humans and AI reason about.

| **Object** | **Built From** | **Represents** | **Examples** |
| --- | --- | --- | --- |
| Person | Actor, Relationships, Commitments, Actions | An individual participant within organizational reality. | Employee, Manager, Founder, Contractor |
| Team | Actors, Relationships, Goals, Commitments | A coordinated group of actors. | Engineering, Operations, Customer Success |
| Role | Actor, Rule, Commitment, Relationship | A set of expected responsibilities and authority. | CTO, Product Manager, Support Lead |
| Customer | Actor, Goals, Commitments, Actions | An external actor receiving value from the organization. | Enterprise account, Trial user, Free-tier user |
| Vendor | Actor, Commitments, Resources | An external actor providing value to the organization. | Software supplier, Contractor agency, Payment processor |
| Agent | Actor, Rules, Goals, Actions | An AI participant operating within organizational reality. Agents are actors, not tools. | Support agent, Scheduling agent, Code review agent |

*Person and Team additionally carry standing key questions that the eventual Workspace views are built around — for Person: who is this, what do they own, what have they influenced; for Team: what is it responsible for, what goals does it own, how does it interact with other teams.*

## Layer 3 — Organizational Structures

These define how organizations are organized.

| **Object** | **Built From** | **Represents** | **Examples** |
| --- | --- | --- | --- |
| Department | Teams, Goals, Relationships | A major organizational function. | Engineering, Sales, Operations |
| Goal | Goal Primitive, Relationships, Time | A desired future state. | Increase retention, Launch product, Reduce support cost |
| Initiative | Goal, Commitments, Actions, Resources | A coordinated effort pursuing a goal. | Q3 retention push, Platform migration |
| Project | Actors, Goals, Resources, Actions, Commitments | A bounded execution effort. | Website redesign, API v2 launch |
| Organization | Teams, Departments, Goals, Rules, Relationships | The entire company. | ZeroManual |

## Layer 4 — Operational Constructs

These represent how work actually happens.

### Theoretical Grounding

DEMO distinguishes coordination-acts (requesting, promising, accepting — the talking) from the single production-act each transaction wraps (the actual work) — sometimes stated as the performa/informa/forma distinction. The Policy/SOP/Workflow disambiguation below implements that distinction directly: Policy is the constraint (closest to DEMO's rule-governance layer), SOP is the designed sequence of coordination-and-production (written before execution), Workflow is the executed pattern (production-acts as they actually occurred). See `Company_Brain_Theoretical_Foundations_v1.md`, Field 4. Fit: Partial — this document implements the coordination/production distinction for one specific disambiguation, not DEMO's full transaction model.

| **Object** | **Built From** | **Represents** | **Examples** |
| --- | --- | --- | --- |
| Commitment | Commitment Primitive, Actor, Time, State | An obligation between actors. | Assignment, Responsibility, Approval obligation, Customer promise |
| Task | Commitment, Action, Goal | A discrete unit of work. | Write report, Fix bug, Approve invoice |
| Workflow | Actors, Actions, Rules, States, Commitments | A repeatable pattern of organizational execution. Not a memory type — a derived construct. | Refund process, Onboarding sequence, Incident response |
| SOP | Rules, Actions, Goals | The intended way work should occur. | Refund SOP, Onboarding SOP |
| Policy | Rules, Goals, Authority | A governing organizational constraint. | Spending limit policy, Data retention policy |
| Decision | Communication, Goal, Rule, Commitment | A commitment to a future course of action. Not atomic — reconstructed from multiple primitives. | Pricing change, Hiring decision, Vendor selection |
| Meeting | Actors, Communications, Time | A coordination event. | Standup, Planning session, Customer call |
| Incident | Actions, Resources, Commitments, States | An unexpected operational disruption. | Outage, Data breach, Missed deadline |
| Opportunity | Goal, Resource, Commitment | Potential future value. | Upsell, Partnership, Expansion deal |

*Context is emergent (Section 4), surfaced when reasoning over a Decision — not a structural component of it. This aligns Decision's composition with Architecture & Vision v2.2.*

## Commitment Lifecycle

The Commitment object follows the same eight-state lifecycle defined in the Architecture & Vision document:

*Requested → Promised → one of Fulfilled, Declined, Delegated, Cancelled, Renegotiated, or Breached.*

### Lifecycle Inheritance

Any ontology object that lists Commitment among its Built From components inherits this eight-state lifecycle by default. This applies to Task, and to the Assignment, Approval Obligation, and Customer Promise examples listed above.

An object only departs from the default lifecycle once a future revision defines a narrower one explicitly. Per-subtype restrictions are defined in Memory Model v1.2, Section 5.3.

### Disambiguating Policy, SOP, and Workflow

Policy, SOP, and Workflow all draw heavily on Rule and Goal, which can make them look interchangeable. They are not — each answers a different question.

| **Object** | **Nature** | **Answers** |
| --- | --- | --- |
| Policy | The constraint. Defines what is allowed, required, or prohibited, and who has authority to grant exceptions. Changes rarely. | What is allowed? |
| SOP | The design. The prescribed sequence of steps for satisfying a Policy or achieving a Goal in a recurring situation. Written before execution. | How is this supposed to happen? |
| Workflow | The observation. The pattern reconstructed from Action Memory showing how work actually happened across many executions. Exists only after execution. | How does this actually happen? |

SOP and Workflow are the same situation viewed from two sides: SOP is the designed version; Workflow is the executed version (DEMO's own labels for this pair are "ostensive" and "performative" — Company Brain uses the plainer terms consistently across this document set, same underlying distinction). This is exactly the distinction the Architecture & Vision document's Intelligence layer is built to detect — it compares SOP against Workflow to surface drift between policy and practice. Policy sits one level above both, constraining what any SOP or Workflow is allowed to specify.

# 4. Context Model

### Theoretical Grounding

Karl Weick (*The Social Psychology of Organizing*, 1979; *Sensemaking in Organizations*, 1995) argues meaning isn't perceived directly off reality — it's constructed retrospectively and socially, from the surrounding conditions of an ambiguous situation. Context below implements that directly: it is explicitly not a stored primitive, generated instead from Goals, Rules, Relationships, History, Actions, Commitments, Time, and Resources on demand — exactly matching Weick's claim that meaning is assembled from surrounding conditions, not filed away as a fact. Separately, Austin (1962) and Searle (1969) describe "felicity conditions" — the background circumstances that determine whether a speech act succeeds (a promise only counts as a promise if the right conditions hold) — which ground Context's role as the background against which a Communication or Commitment is interpreted. See `Company_Brain_Theoretical_Foundations_v1.md`, Fields 8 and 3. Fit: Clean — direct implementation.

Context is not treated as a primitive. Context is an emergent construct.

Context is generated from:

- Goals
- Rules
- Relationships
- History
- Actions
- Commitments
- Time
- Resources

For example, a decision's context may include previous decisions, active goals, existing commitments, resource constraints, and current organizational state.

*Context answers: why did this happen?*

# 5. Organizational Memory Mapping

### Theoretical Grounding

Walsh & Ungson's 1991 taxonomy retains organizational memory through five facilities — individuals, culture, transformations, structures, external archives. Company Brain implements their underlying claim (that organizational memory needs a defined retention mechanism) directly, but maps ontology objects to Company Brain's own five memory types below rather than Walsh & Ungson's five facilities — see Memory Model v1.3 §3 and `Company_Brain_Theoretical_Foundations_v1.md` Field 5 for why that divergence is deliberate, not a gap. This section is the object-level instance of that same mapping decision. Fit: Clean for the underlying retention claim; the specific taxonomy is Company Brain's own.

Every ontology object maps into memory. This section gives two views: which objects each memory type stores, and — closing the gap left open in the previous draft — exactly where each individual object lives and where else it is referenced.

## By Memory Type

| **Memory Type** | **Stores** |
| --- | --- |
| Factual Memory | People, Teams, Departments, Roles, Goals, Policies, SOPs, Resources, Organization structure |
| Interaction Memory | Meetings, Discussions, Negotiations, Approvals |
| Commitment Memory | Responsibilities, Assignments, Promises, Obligations, Expectations, Tasks |
| Action Memory | Workflows (as executed), Incidents, Executions, Exceptions, Outcomes |
| Learning Memory | Lessons, Patterns, Failures, Successes, Process improvements, Policy improvements |

## By Object — Primary Home and Cross-References

| **Object** | **Primary Memory Home** | **Also Referenced In** |
| --- | --- | --- |
| Person | Factual Memory | Interaction (decisions made), Commitment (what they own), Action (what they did) |
| Team | Factual Memory | Commitment (goals and commitments owned), Interaction (team discussions) |
| Role | Factual Memory | Inherited through Person — no independent record |
| Customer | Factual Memory | Commitment (promises made to them), Action (interactions and outcomes) |
| Vendor | Factual Memory | Commitment (contracts and obligations), Action (deliveries) |
| Agent | Factual Memory | Action (what it executed), Commitment (what it owns) |
| Department | Factual Memory | — |
| Goal | Factual Memory | Interaction (why a decision was made), Intelligence (progress evaluation) |
| Initiative | Factual Memory | Commitment Memory and Action Memory (the commitments and actions inside it) |
| Project | Factual Memory | Commitment Memory and Action Memory |
| Organization | Factual Memory | — |
| Commitment | Commitment Memory | Action Memory (the action that fulfills or breaches it) |
| Task | Commitment Memory (inherits from Commitment) | Action Memory (the execution record once complete) |
| Workflow | Not stored — reconstructed on demand | Action Memory (executed steps), Commitment Memory (commitments fulfilled), Factual Memory (the SOP or Rule it follows) |
| SOP | Factual Memory | Intelligence (compared against Workflow to detect drift) |
| Policy | Factual Memory | Commitment Memory (terms referenced by commitments), Intelligence (compliance checks) |
| Decision | Not stored — reconstructed on demand | Interaction Memory (the discussion), Commitment Memory (the commitment created), Factual Memory (the Goal or Rule referenced) |
| Meeting | Interaction Memory | — |
| Incident | Action Memory | Commitment Memory (response obligations created) |
| Opportunity | Factual Memory | Commitment Memory (commitments made to pursue it), Action Memory (actions taken toward it) |

# 6. Relationship Model

### Theoretical Grounding

The W3C's RDF and OWL specifications express knowledge as subject–predicate–object triples with formally typed relationships, forming a traversable graph. The From/Relationship/To table below implements that convention directly — it is structurally the same triple, just with plainer column labels than RDF's own "Subject/Predicate/Object," chosen because "From/Relationship/To" reads more naturally for non-technical stakeholders reviewing this document. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 12. Fit: Clean — direct implementation, relabeled for readability.

No object exists in isolation. The Company Brain is fundamentally relational — without relationships, the Brain becomes storage; with relationships, the Brain becomes understanding.

| **From** | **Relationship** | **To** |
| --- | --- | --- |
| Person | belongs to | Team |
| Team | owns | Goal |
| Goal | drives | Initiative |
| Initiative | contains | Projects |
| Project | creates | Commitments |
| Commitment | fulfilled by | Actions |
| Action | changes | State |
| Decision | creates | Commitments |
| Policy | constrains | Actions |
| Incident | triggers | Actions |
| Learning | updates | Policy |
| Person | occupies | Role |
| Role | reports to | Role |
| Team | belongs to | Department |
| Department | belongs to | Organization |
| Customer | holds | Commitments (contracts, promises) |
| Vendor | provides | Resources |
| Agent | acts on behalf of | Person or Team |
| Agent | executes | Actions |

*This is a representative set, not an exhaustive schema. Relationships not yet modeled here will be added as Memory Model defines storage and traversal requirements.*

# 7. Derived Intelligence Objects

*No external grounding — Master Plan §2.2 marks this KEEP: original, no external analog.*

These are not stored directly. They emerge from reasoning, and belong to the Intelligence layer, not the Ontology layer:

- Knowledge Gap
- Operational Risk
- Agent Readiness
- Brain Score
- Recommendation
- Prediction
- Opportunity Signal
- Drift Signal
- Policy Violation
- Process Bottleneck

*Opportunity Signal is the Intelligence layer**'**s pattern-detected hint that potential value may exist — for example, a usage pattern suggesting a customer is ready for an upsell. It becomes an Opportunity, the Layer 4 ontology object, once a human or agent commits resources to formally pursuing it.*

# 8. What The Company Brain Ultimately Understands

*No external grounding — scoping statement, Master Plan §2.2 marks KEEP.*

The Company Brain does not understand documents.

It understands organizational reality:

**Who exists → What they are trying to achieve → What commitments exist → What actions occur → What rules govern behavior → How everything is connected → How reality changes through time**

Everything else is a representation of those concepts.

## Ontology Boundary

The Ontology is responsible for defining organizational reality.

The Ontology is not responsible for:

- Knowledge Representation Formats
- Memory Lifecycle
- Memory Formation
- Memory Retrieval
- Product Experiences
- User Interfaces
- Agent Protocols
- Storage Technology

Those concerns belong to other Company Brain documents.

# One-Sentence Summary

| **The Company Brain Ontology defines the objects, structures, and relationships that make up organizational reality, serving as the conceptual foundation from which Knowledge Objects, Memory, Intelligence, Products, and Technology are derived.** |
| --- |

ZeroManual — Internal   ·   Page  of
