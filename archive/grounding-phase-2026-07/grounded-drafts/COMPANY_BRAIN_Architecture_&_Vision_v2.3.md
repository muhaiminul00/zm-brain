COMPANY BRAIN — Architecture & Vision	v2.3

**COMPANY BRAIN**

Architecture & Vision

Version 2.3

Canonical Team Document

ZeroManual — Internal

July 2026

## Document Control

| **Field** | **Value** |
| --- | --- |
| Version | 2.3 |
| Status | Canonical Team Document — Grounded Draft, pending human review and freeze |
| Supersedes | Version 2.2 |
| Scope | Architecture & Vision only. The companion Foundational Reasoning document is not affected by this revision. |

**Changes in This Revision**

- Theoretical Grounding pass (see `Company_Brain_Theoretical_Foundations_v1.md` for full citations and fit ratings). No architectural decision changed. Sections marked GROUND in the Master Plan now carry an inline citation callout; nothing else in this document was altered.
- Updated MCP governance language (Section 13) to reflect that MCP is now stewarded by the Agentic AI Foundation, a Linux Foundation directed fund, since December 2025 — no longer solely an Anthropic-governed project. Verified via web search.
- **Exposition rewrite (this pass):** every grounding callout rewritten from a citation aside ("here's a paper that relates to this") into theory-first exposition — the source theory stated plainly on its own terms, then an explicit bridge to how Company Brain relates to it (implements / extends / diverges), never left implicit. Section 11's "ostensive-versus-performative gap" phrase swapped for "designed-versus-executed gap," matching the plain-language term already used consistently elsewhere in this document set (Ontology's SOP/Workflow split, Product Architecture's Drift Experience) — same DEMO grounding, plainer wording.
- All prior v2.2 content, decisions, and structure preserved unchanged. This is a citation, framing, and exposition layer only — no architectural decision changes.

**Changes in v2.2 (carried forward from prior revision)**

- Added Canonical Knowledge Objects as the representation layer between Understanding and Memory (Sections 9 and 10).
- Added Primitive Knowledge Objects and Composite Knowledge Objects, establishing a two-tier organizational knowledge representation model (Section 9).
- Added Knowledge Representation Compatibility and Open Knowledge Format (OKF) alignment guidance (Section 9).
- Added the Exposure Layer, making delivery of memory and intelligence a first-class architectural responsibility (Sections 7 and 13).
- Expanded the Evolution Layer to learn from recommendation outcomes, delivery effectiveness, and human/AI interaction signals (Section 14).
- Added Principle 8 — Right Memory, Right Moment (Section 6).
- Expanded the Trust System to govern Canonical Knowledge Objects in addition to memory records (Section 15).
- Closed architectural open questions already resolved by Memory Model v1.1.

**Resolved In Memory Model v1.1**

- Memory Decay
- Conflict Resolution
- AI Write Governance
- Current vs Superseded Truth Model

See Memory Model v1.2 for authoritative definitions.

## Table of Contents

*Updates automatically in Microsoft Word. If it shows no entries, select it and press F9 to refresh.*

# 1. Introduction

## Purpose of This Document

This document defines the vision, architecture, and mental model of the Company Brain.

It is not a technical architecture document. It does not define:

- Databases
- APIs
- Infrastructure
- AI Models
- Programming Languages
- Frameworks

Instead, it defines:

- The problem we are solving
- What a Company Brain is
- How organizations actually function
- How Company Brain models organizational reality
- How Company Brain creates memory
- How Company Brain generates intelligence
- How Company Brain enables execution
- How Company Brain continuously learns

This document serves as the foundational reference for all future product, design, research, and engineering decisions.

# 2. The Problem

### Theoretical Grounding

March and Simon (*Organizations*, 1958) and Galbraith (*Organization Design*, 1977) established that organizations are bounded-rational information processors: no person or organization can process unlimited information, so structure, hierarchy, and routine exist specifically to manage that limit and absorb uncertainty. The problem below is a direct, applied instance of that finding, not a novel observation this document is making for the first time — organizations losing track of their own knowledge is exactly the kind of information-processing failure this fifty-year-old theory predicts happens when the informal, human-based coping mechanisms (people remembering who knows what) get overloaded. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 9, and Field 5 (Walsh & Ungson, 1991) for the organizational-memory-specific half of the same claim. Fit: Clean — this section implements the problem framing directly.

## Organizations Do Not Have Reliable Memory

Every company generates knowledge continuously. Knowledge is created through:

- Conversations
- Meetings
- Decisions
- Customer interactions
- Processes
- Emails
- Documents
- Chats
- Workflows
- Daily execution

Yet organizations do not possess a coherent memory system. Knowledge becomes fragmented across:

- People
- Documents
- Tools
- Systems
- Departments

Organizations continue functioning because humans compensate for these gaps. People remember:

- Who knows what
- Why decisions were made
- How exceptions are handled
- What happened previously
- Which process should be followed

AI systems cannot operate this way.

## Why Existing Systems Fail

### Search Systems

Search retrieves information. It does not understand:

- Context
- Intent
- Relationships
- Commitments
- Decisions
- Organizational history

### Knowledge Bases

Knowledge bases store information. They do not:

- Understand
- Reason
- Learn
- Detect gaps
- Preserve organizational memory

### Chatbots

Chatbots generate responses. They do not possess organizational understanding.

### Workflow Systems

Workflow systems execute predefined processes. They do not understand organizational reality.

## The Missing Layer

Between Raw Company Activity and Reliable Human & AI Execution, there is a missing layer. That layer is the Company Brain.

# 3. What Is A Company Brain?

### Theoretical Grounding

Stafford Beer's Viable System Model (*Brain of the Firm*, 1972; *The Heart of Enterprise*, 1979; *Diagnosing the System for Organizations*, 1985) treats any organization capable of sustaining itself as a living system, made of interacting subsystems the same way a body is made of interacting organs — not as a metaphor for effect, but as the literal analytical frame Beer builds his entire model on. The "living organism" framing below is a direct implementation of that fifty-year-old framing, not a Company Brain coinage. The full five-subsystem model and how Company Brain's seven layers relate to it is worked through in Section 7 and the VSM Compression Test in `Company_Brain_Theoretical_Foundations_v1.md`, Field 1. Fit: Clean.

## Definition

A Company Brain is a living organizational reality, memory, and intelligence system that continuously captures, understands, remembers, reasons over, and operationalizes how an organization functions.

It transforms fragmented organizational activity into structured organizational understanding.

The Company Brain becomes the shared source of truth for both humans and AI.

## What A Company Brain Is Not

- A document repository
- A knowledge base
- A wiki
- A search engine
- A chatbot
- A workflow tool
- An automation platform

These may interact with the Brain. They are not the Brain itself.

## What A Company Brain Is

- A model of organizational reality
- An organizational memory system
- An organizational intelligence system
- An organizational learning system

# 4. Organizational Reality

### Theoretical Grounding

Winograd and Flores (*Understanding Computers and Cognition*, 1986) argue that organizational coordination is fundamentally linguistic, not documentary: work happens through recurring conversational structures — requests, promises, reports, acceptances — and an organization is best understood as a network of commitments between people, not a network of paperwork. Jan Dietz's DEMO (2006, 2020) makes a related, complementary claim: an organization's essential model is its network of coordination-acts and production-acts, entirely independent of whatever systems or documents happen to support it today. "Organizations Are Coordination Systems," below, implements both claims directly — it is not a loose analogy to "coordination systems" vocabulary, it is the same underlying claim: documents, SOPs, databases, and workflows are representations; the primitives listed below (Actors, Communications, Commitments, Actions, Resources, Rules, Goals, States, Time, Relationships) are what's actually there. See `Company_Brain_Theoretical_Foundations_v1.md`, Fields 2 and 4. Fit: Clean.

## Core Insight

Before a Company Brain can create memory, it must understand reality. The Brain cannot simply store documents. It must model how organizations actually function.

## Organizations Are Coordination Systems

Organizations are not fundamentally collections of:

- Documents
- SOPs
- Databases
- Workflows

Those are representations. Organizations are systems of coordinated human activity. The Company Brain therefore models:

- Actors
- Communications
- Commitments
- Actions
- Resources
- Rules
- Goals
- States
- Time
- Relationships

These form the foundation of organizational reality. Section 5 defines each of these primitives in detail.

## How Reality Relates To The Pipeline

Organizational Reality is not a separate stage that runs alongside the layers in Section 7. It is the substrate those layers act on.

The Capture and Understanding layers construct a structured model of reality from raw activity. The Memory layer preserves that model through time. The Intelligence layer reasons over it. The Execution layer acts on it. The Exposure layer delivers it. The Evolution layer refines it. There is one pipeline. Organizational Reality is what the pipeline is made of; Section 7 describes how the pipeline operates on it.

# 5. Atomic Primitives of Organizational Reality

### Theoretical Grounding

John Zachman's 1987 framework organizes everything that can be said about an enterprise along six interrogatives — Who, What, Where, When, Why, How — the idea being that a complete model of an organization has to answer all six, not just the ones that are easy to capture in a database. The Key Question column below implements that convention directly for eight of the ten primitives (Actor→Who, Communication→What-was-communicated, Commitment→Who-owes-what-to-whom, Time→When, Goal→Why, and so on), and extends it with two questions Zachman's six-cell grid doesn't ask: State ("what condition is this in") and Relationship ("how is this connected"). Dietz/DEMO's transaction pattern (2006, 2020) grounds the Commitment primitive specifically as the atomic unit of a coordination-act. See `Company_Brain_Theoretical_Foundations_v1.md`, Fields 11 and 4. Fit: Clean for the interrogative convention (implemented directly for 8 of 10 primitives, extended for 2).

Earlier drafts treated Entity, Relationship, Event, Decision, and Context as the primitives. Research showed these were still composites. The deepest recurring primitives — the ones that do not decompose further — are the ten below.

| **Primitive** | **Definition** | **Examples** | **Key Question** |
| --- | --- | --- | --- |
| Actor | An entity capable of participating in organizational activity. | Employee, Team, Department, Customer, Vendor, AI Agent | Who? |
| Communication | An exchange of meaning between actors. | Meetings, Emails, Messages, Requests, Discussions | What was communicated? |
| Commitment | An obligation, responsibility, promise, expectation, or authorization. | Deliver a report, Approve a budget, Resolve an incident | Who owes what to whom? |
| Action | Work performed that changes organizational state. | Process refund, Deploy software, Approve request | What was done? |
| Resource | Something that can be used, consumed, managed, or affected. | Money, Products, Documents, Customer Accounts | What is being acted upon? |
| Rule | A constraint, policy, authority structure, or governing principle. | Approval thresholds, Security policies, Escalation paths, Spending limits | What is allowed? |
| Goal | A desired future state. | Increase retention, Launch by Q3, Reduce response time | Why are we doing this? |
| State | The current condition of something. | Open, In Progress, Resolved, Approved | What is the current situation? |
| Time | The temporal dimension of organizational activity. | Timestamp, Deadline, Duration, Recurrence | When? |
| Relationship | A meaningful connection between primitives. | Reports-to, Depends-on, Caused-by, Fulfills | How are things connected? |

**Higher-Order Concepts Built From These Primitives**

Everything else in the organization is a composite of the ten primitives above. For example:

| **Concept** | **Composition** |
| --- | --- |
| Decision | Communication + Goal + Rule + Commitment |
| Workflow | Actors + Actions + Rules + States + Commitments |
| Project | Actors + Goals + Resources + Commitments + Actions |

Decision and Workflow are not modeled as separate memory types. They are reconstructed on demand from the primitives that compose them — see the mapping in Section 10.

# **6. Core Principles**

### Theoretical Grounding

Zero Trust security doctrine holds that no actor or system should be trusted by default, inside or outside a boundary — every action is verified against explicit policy before it's granted, rather than assumed safe because of where it originates. Principle 5 (Trust Before Automation) implements this directly: automation is granted only once trust is established, not the other way around. Argyris and Schön's double-loop learning (1978, 1996) — revising the governing rule itself once errors recur, not just patching the latest instance — is what Principle 7 (The Brain Must Learn) implements; the mechanism is worked through in full at Section 14 and Section 16. Principle 8 (Right Memory, Right Moment) and the Exposure Layer it anchors have no external parent — see Master Plan §5 — and are stated here as Company Brain's own contribution, not stretched to fit a citation.

| **#** | **Principle** | **Statement** |
| --- | --- | --- |
| 1 | Reality Before Representation | The Company Brain models organizational reality. Documents and systems are merely representations of that reality. |
| 2 | Memory Over Documents | Documents are sources. Memory is the asset. |
| 3 | Context Over Information | Information without context has limited value. The Brain must preserve why, who, when, and under what conditions — not only what. |
| 4 | Understanding Over Storage | Storage accumulates information. Understanding creates intelligence. |
| 5 | Trust Before Automation | Automation without trust creates risk. |
| 6 | Execution Creates Memory | Every action creates new organizational knowledge. |
| 7 | The Brain Must Learn | The Brain continuously evolves through outcomes and feedback. |
| 8 | Right Memory, Right Moment | The Company Brain is responsible for delivering the right memory, to the right actor, through the right channel, at the right moment. Memory has value only when it reaches the point of work. |

# **7. Company Brain Architecture**

### Theoretical Grounding — The Viable System Model

Stafford Beer's Viable System Model holds that any system that must sustain its own existence over time — a company, a body, a nervous system — needs the same five interacting subsystems, regardless of what the system is made of: **System 1 (Operations)** does the actual work; **System 2 (Coordination)** keeps the operating units from working against each other; **System 3 (Control)** manages internal resources and regulation; **System 4 (Intelligence)** scans the environment and looks forward; **System 5 (Policy)** holds identity and ultimate authority over what's allowed. Beer's further claim — viability requires enough internal variety to absorb whatever the environment throws at it (Ashby's Law of Requisite Variety), sustained through continuous feedback between all five subsystems — is what makes this a model of *staying alive*, not just a org chart.

The seven-layer pipeline below is a direct application of this model, checked rather than asserted through the explicit VSM Compression Test in `Company_Brain_Theoretical_Foundations_v1.md`. Five of seven layers implement VSM's subsystems directly: Capture+Understand implement the System 1/2 sensing function, Execution implements System 1, Intelligence implements System 4, Evolution implements a partial version of the System 3–4 feedback loop, and Trust & Governance (Section 15, a supporting system rather than one of the seven layers) implements System 5. Two layers — Memory and Exposure — have no VSM equivalent, because VSM describes organizations made of people, where memory and delivery happen implicitly through human continuity and informal norms. An AI actor gets neither implicitly: **Company Brain adopts VSM's viability logic and extends it with the two layers VSM left implicit, because in an AI-native organization, memory and delivery can no longer stay implicit.** Full derivation and the two-layer extension argument: `Company_Brain_Theoretical_Foundations_v1.md`, Field 1 and the VSM Compression Test. Fit: Clean (direct implementation) for five layers; explicit, named extension for Memory and Exposure.

The Company Brain consists of seven core layers:

**Capture → Understand → Memory → Intelligence → Execution → Exposure → Evolution**

These seven layers operationalize Organizational Reality end to end.

Capture and Understand construct it.

Memory preserves it.

Intelligence reasons over it.

Execution acts on it.

Exposure delivers it.

Evolution refines it and feeds the result back into Memory.

**Quick Reference**

| **Layer** | **Purpose** | **Key Question** |
| --- | --- | --- |
| 1. Capture | Observe and capture organizational reality. | What is happening? |
| 2. Understand | Transform activity into organizational understanding. | What does this mean? |
| 3. Memory | Preserve organizational understanding through time. | What should never be forgotten? |
| 4. Intelligence | Transform memory into organizational intelligence. | What should we understand? |
| 5. Execution | Transform intelligence into action. | What should happen next? |
| 6. Exposure | Deliver memory, intelligence, and actions to the right human or AI actor. | Who needs to know this? |
| 7. Evolution | Create organizational learning loops. | What changed because of what we did? |

*Sections 8 through 14 define each layer in full.*

# 8. Layer 1 — Capture Layer

### Theoretical Grounding

Nonaka and Takeuchi's SECI model (1995) describes organizational knowledge creation as a cycle converting tacit knowledge (know-how, lived experience) into explicit knowledge (written, codified) and back — Socialization, Externalization, Combination, Internalization. Capture is the layer immediately before Externalization happens: it's where tacit organizational activity — a meeting, a decision made in conversation — first gets observed at all, prior to Section 9's Understanding layer converting it into structured, explicit form. Company Brain does not implement the other three SECI modes (Socialization and Internalization are human processes the architecture doesn't touch); this is a partial, single-mode application by design. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 6. Fit: Partial.

| **Purpose** | Observe and capture organizational reality. |
| --- | --- |
| **Responsibilities** | Collect organizational signals Preserve source information Record activity |
| **Inputs** | People Meetings Emails Chats Systems Documents Workflows Events |
| **Key Question** | What is happening? |
| **Outputs** | Raw activity Raw events Raw communications Raw organizational signals |

# 9. Layer 2 — Understanding Layer

### Theoretical Grounding

Karl Weick's sensemaking theory (1979, 1995) holds that organizations don't perceive a pre-existing, objective environment and react to it — people act first, often on ambiguous information, and only afterward construct a shared, meaningful account of what happened. This layer implements that directly: its job, turning raw captured activity into "what does this mean?", is sensemaking in Weick's precise sense, not a lookup or extraction step. It's also the layer performing Nonaka & Takeuchi's Externalization mode (1995) — tacit activity becoming explicit, structured Knowledge Objects — though, as noted at Section 8, only that one of SECI's four modes. See `Company_Brain_Theoretical_Foundations_v1.md`, Fields 8 and 6. Fit: Clean for the sensemaking framing (direct implementation); Partial for SECI (one mode of four).

| **Purpose** | Transform activity into organizational understanding. |
| --- | --- |
| **Responsibilities** | Identify the atomic primitives present in every signal: Actors, Communications, Commitments, Actions, Resources, Rules, Goals, States, Relationships. Transform captured activity into structured organizational understanding. Produce Canonical Knowledge Objects representing organizational reality. |
| **Inputs** | Captured organizational activity. |
| **Key Question** | What does this mean? |
| **Outputs** | Structured organizational reality represented as Canonical Knowledge Objects. |

## Knowledge Objects

### Theoretical Grounding

Tom Gruber's 1993 paper defines an ontology as "an explicit specification of a conceptualization" — a formal, shareable statement of what exists in a domain. Knowledge Objects implement that definition directly: they are the explicit, shareable specification of organizational reality that everything downstream (Memory, Intelligence, Products) consumes. Separately, Company Brain has adopted Google Cloud's Open Knowledge Format (OKF) v0.1 directly as infrastructure, not cited as an analogy — Composite Knowledge Objects export as OKF concept documents; full field-level mapping in the companion `OKF_Adoption_Mapping.md`. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 12. Fit: Clean (Gruber, direct implementation); Adopted (OKF, infrastructure not theory).

Knowledge Objects are canonical representations of organizational reality produced by the Understanding Layer.

They are derived from the Company Brain Ontology and provide a standardized representation that can be consumed by Memory, Intelligence, Products, and external systems.

Knowledge Objects are:

- Human-readable
- AI-readable
- Traceable
- Versionable
- Portable

Knowledge Objects are not memory.

They are the representation layer from which memory is formed.

### Primitive Knowledge Objects

These are the eight canonical, irreducible Knowledge Object types, one per atomic primitive (Section 5).

This is a closed set.

- Actor Object
- Communication Object
- Commitment Object
- Action Object
- Resource Object
- Rule Object
- Goal Object
- Relationship Object

### Composite Knowledge Objects

Composite Knowledge Objects represent Core Objects, Organizational Structures, and Operational Constructs (Ontology Layers 2–4).

Each Composite Knowledge Object is built by combining Primitive Knowledge Objects, mirroring how Ontology composes higher-order objects from atomic primitives.

Composite Knowledge Objects are defined and owned by the Ontology document.

Architecture & Vision defines only the Primitive layer.

### Ownership Boundary

Architecture & Vision defines only the Primitive Knowledge Object layer.

Primitive Knowledge Objects are the canonical representation of the atomic primitives that form the foundation of organizational reality.

Composite Knowledge Objects are defined, structured, and governed by the Ontology.

Architecture intentionally does not define Composite Knowledge Objects.

Their structure, relationships, inheritance rules, and composition logic are owned by the Ontology and may evolve independently of the Architecture document.

### Knowledge Representation Compatibility

The Company Brain adopts Google Cloud's Open Knowledge Format (OKF) v0.1 directly as its Knowledge Exchange interchange format (see companion OKF Adoption Mapping document for the full field mapping).

Knowledge Objects serve as the Company's canonical representation layer and are exchanged through OKF-compatible representations where governance permits.

# 10. Layer 3 — Memory Layer

### Theoretical Grounding

J.P. Walsh and G.R. Ungson's "Organizational Memory" (1991) gives the first formal academic definition: organizations retain stored information from their own history, usable in present decisions, through five "retention facilities" — individuals, culture, transformations, structures, and external archives — moved through by acquisition, retention, and retrieval. This layer implements that core definition directly: "preserve organizational understanding through time" is Walsh & Ungson's claim, not a novel one. Company Brain does not adopt their five-facility taxonomy, though — it organizes memory by *what kind of thing is remembered* instead (see Section 10.1 below, Memory Architecture), because Company Brain is architecting the retention mechanism from scratch rather than describing an informal one that already exists. Separately, Winograd & Flores's conversation-for-action loop (1986) grounds the Commitment Lifecycle specifically: Request→Promise→Report→Accept implements directly as Requested→Promised→Fulfilled, extended below with four additional real-world exit states the original loop has no name for. See `Company_Brain_Theoretical_Foundations_v1.md`, Fields 5 and 2. Fit: Clean for the core definition (direct implementation); deliberate divergence, not a gap, on the five-facility taxonomy.

| **Purpose** | Preserve organizational understanding through time. This is the actual memory system of the Company Brain. |
| --- | --- |
| **Responsibilities** | Maintain five distinct, purpose-built memory stores Attach provenance, time, and state to every record Preserve relationships and links across memory types Track the lifecycle of every open commitment Serve relevant memory to the Intelligence layer on demand |
| **Inputs** | Canonical Knowledge Objects. |
| **Key Question** | What should never be forgotten? |
| **Outputs** | Persistent organizational memory. |

## Memory Formation

The Memory Layer operates on Canonical Knowledge Objects produced by the Understanding Layer.

Memory Formation transforms Knowledge Objects into persistent organizational memory through routing, lifecycle management, provenance tracking, and relationship preservation.

Knowledge Objects are representations of reality.

Memory is the preserved understanding of reality through time.

## Memory Architecture

The Brain consists of five memory systems.

### Theoretical Grounding

Endel Tulving's semantic/episodic distinction (1972) and Larry Squire's broader memory-systems taxonomy (2004) — extended computationally in John Anderson's ACT-R — describe how individual human cognition organizes memory: semantic memory holds general facts with no personal or temporal anchor, episodic memory holds specific events anchored in time and place, procedural memory holds skills and know-how. Three of Company Brain's five memory types implement this directly: Factual Memory is semantic memory, Interaction Memory is episodic memory, Action Memory is procedural memory. Two types — Commitment Memory and Learning Memory — have no individual-cognition equivalent at all, and that's not a gap in the mapping: no single human brain needs a memory system for "an obligation someone else owes me" or "what this organization, collectively, has learned," because those aren't things an individual mind has to track. This divergence is the clearest evidence in the whole document set of where Company Brain's actual intellectual property sits — see Master Plan §5, `Company_Brain_Theoretical_Foundations_v1.md` Field 10, and the worked example there. Fit: Clean for 3 of 5 types (direct implementation); deliberate divergence for the other 2.

| **Memory Type** | **Purpose** | **Stores** | **Key Question** |
| --- | --- | --- | --- |
| Factual Memory | Preserve what exists. | Actors, Resources, Structures, Policies, Goals, Processes | What do we know? |
| Interaction Memory | Preserve organizational reasoning. | Discussions, Decisions, Tradeoffs, Context | Why do we know it? |
| Commitment Memory | Preserve commitments and obligations. | Promises, Responsibilities, Ownership, Expectations | Who owes what to whom? |
| Action Memory | Preserve execution history. | Actions, Outcomes, Exceptions, Escalations | What actually happened? |
| Learning Memory | Preserve organizational learning. | Lessons, Patterns, Successes, Failures, Improvements | What have we learned? |

## Commitment Lifecycle

Commitment Memory does not store promises as static facts. Every commitment carries a state, so the Brain can always answer whether an obligation is open, at risk, or resolved.

| **State** | **Definition** | **Typical Trigger** |
| --- | --- | --- |
| Requested | An actor has asked for a commitment; not yet binding. | A request is raised in a Communication. |
| Promised | The responsible actor has accepted the obligation. Binding, with a condition of satisfaction and, where relevant, a due date. | The responsible actor accepts the request. |
| Delegated | The obligation has been transferred to another actor. The original commitment closes; a new one opens. | The responsible actor hands the work to someone else. |
| Fulfilled | The condition of satisfaction has been met and accepted by the requester. | Work is completed and accepted. |
| Declined | The request was not accepted. No obligation is created. | The requested actor refuses the request. |
| Cancelled | A previously active commitment is withdrawn by agreement before fulfillment. | Requester or responsible actor withdraws it. |
| Renegotiated | Scope, deliverable, or due date is changed by agreement. The original commitment closes; a new version opens, linked to it. | Terms change mid-flight. |
| Breached | The due date passed, or the condition was rejected, without fulfillment, cancellation, delegation, or renegotiation. | Deadline passes with no resolution. |

*Flow: Requested → Promised → one of Fulfilled, Declined, Cancelled, Delegated, Renegotiated, or Breached. Delegated and Renegotiated always link forward to a new commitment record rather than mutating the original — the history of the change is part of the memory.*

## Primitive-to-Memory Mapping

Every atomic primitive from Section 5 has an explicit home in the memory architecture. Actor, Resource, Rule, and Goal are facts about what exists, so they live in Factual Memory. State, Time, and Relationship are not separate stores — they are attributes carried by every record in every memory type.

| **Primitive** | **Primary Memory Home** | **How It Is Used Elsewhere** |
| --- | --- | --- |
| Actor | Factual Memory | Referenced as a participant by every Interaction, Commitment, and Action record. |
| Resource | Factual Memory | Referenced by Action (what was acted on) and Commitment (what was promised). |
| Rule | Factual Memory | Referenced by Commitment (terms and authority) and Intelligence (compliance checks). |
| Goal | Factual Memory | Referenced by Interaction (why a decision was made) and Intelligence (progress evaluation). |
| Communication | Interaction Memory | The source of new Commitments and the basis for reconstructing Decisions. |
| Commitment | Commitment Memory | Created by Communication; discharged, breached, or delegated through Action. |
| Action | Action Memory | Updates Resource state; fulfills or breaches open Commitments. |
| State | Attached to every record, in every memory type | Not a separate store. Every Commitment, Action, and fact carries its current condition. |
| Time | Attached to every record, in every memory type | Not a separate store. Every record is timestamped and time-qualified. |
| Relationship | Expressed as links across all memory types | Not a separate store. The connective structure that lets memory be traversed as a graph. |

# 11. Layer 4 — Intelligence Layer

*No external grounding forced — Master Plan §2.1 marks this KEEP: no single clean academic parent exists for the Intelligence layer as a whole. Treated as primary original contribution.*

*Vocabulary note (this pass): "the ostensive-versus-performative gap" below has been swapped for the plain-language term already used consistently elsewhere in this document set — "designed-versus-executed" (see Ontology's SOP/Workflow disambiguation, Product Architecture's Drift Experience). Same underlying grounding (Dietz/DEMO's coordination-act/production-act distinction, `Company_Brain_Theoretical_Foundations_v1.md` Field 4), plainer wording, no meaning lost.*

| **Purpose** | Transform memory into organizational intelligence. |
| --- | --- |
| **Responsibilities** | Reason over memory Detect patterns Identify risks Detect gaps Generate recommendations Support decisions Detect drift between how work is designed to happen (Rules) and how it actually happens (Action Memory) — the designed-versus-executed gap |
| **Inputs** | All memory systems. |
| **Key Question** | What should we understand? |
| **Outputs** | Insights Recommendations Opportunities Warnings Plans Drift signals between policy and practice |

# 12. Layer 5 — Execution Layer

### Theoretical Grounding

Dietz/DEMO (2006, 2020) distinguishes coordination-acts (the talking — requesting, promising, accepting) from the single production-act each transaction wraps (the actual work) — DEMO's "performa/informa/forma" framing. Execution implements the production-act half of that distinction directly: it's where intelligence and recommendations turn into actual organizational work, as opposed to the coordination that precedes it (captured earlier in Communication and Commitment). See `Company_Brain_Theoretical_Foundations_v1.md`, Field 4. Fit: Partial — this layer implements one half (production-acts) of DEMO's coordination/production distinction; the coordination half lives upstream in the Commitment primitive and Memory Layer.

| **Purpose** | Transform intelligence into action. |
| --- | --- |
| **Responsibilities** | Execute work Coordinate activity Complete commitments Operate the organization |
| **Inputs** | Intelligence and recommendations. |
| **Key Question** | What should happen next? |
| **Outputs** | Actions and outcomes. |

## Participants

| **Humans** | **AI** |
| --- | --- |
| Employees Managers Operators Executives | Assistants Agents Workflows Automations |

# **13. Layer 6 — Exposure Layer**

### Theoretical Grounding

Beer's VSM assumes that "getting the right information to the right person" happens implicitly, through the informal communication norms of a human organization — it names no subsystem for delivery, because in a human organization nobody has to architect it. The VSM Compression Test (`Company_Brain_Theoretical_Foundations_v1.md`) confirms Exposure has no VSM equivalent for exactly this reason, and Company Brain extends VSM here deliberately: an AI actor has no informal communication norms to rely on, so exposure has to become a first-class, engineered layer or nothing reaches the point of work. Separately, the MCP Surface this layer defines runs on real, adopted infrastructure, not an analogy — Model Context Protocol is now stewarded by the Agentic AI Foundation, a Linux Foundation directed fund, since December 2025, confirmed via web search, no longer solely governed by Anthropic. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 1 (VSM) and Field 13 (MCP). Fit: Explicit extension (Exposure); Adopted infrastructure (MCP), verified current.

| **Purpose** | Deliver memory, intelligence, and actions to humans and AI systems through appropriate channels. |
| --- | --- |
| **Responsibilities** | Ambient Delivery, Agent Access, Mission Control Delivery, Reality Feed Distribution, Context Injection, Notification Routing, Multi-channel Memory Exposure |
| **Inputs** | Memory, Intelligence, Execution |
| **Key Question** | Who needs to know this? Where should it appear? When should it appear? How should it be delivered? |
| **Outputs** | Slack Suggestions, Email Context, Calendar Briefs, CRM Context, Browser Extension Context, MCP Responses, Reality Feed Items, Mission Control Views |

# **14. Layer 7 — Evolution Layer**

### Theoretical Grounding

Chris Argyris and Donald Schön (*Organizational Learning*, 1978; *Organizational Learning II*, 1996) distinguish two levels of learning from error. **Single-loop learning** detects an error and corrects the action — the rule that produced it stays unquestioned. **Double-loop learning** goes further: it questions and revises the governing rule itself once errors recur, rather than patching the latest instance. Evolution implements this distinction directly, not as an analogy: comparing designed process against executed Action patterns and correcting one instance is single-loop learning; routing a *confirmed, recurring* divergence into Learning Memory as a policy-improvement candidate — which can then actually change the Policy or SOP through Memory Model's Write Governance — is double-loop learning, happening close to exactly as Argyris & Schön describe it. The specific mechanics of how that gets triggered (the Drift Candidate→Pattern→Signal→Severity pipeline, Intelligence Architecture v1.1 Part 10) are Company Brain's own engineering on top of the theory, not something borrowed from it. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 7. Fit: Clean — one of the strongest direct implementations in the whole document set.

| **Purpose** | Create organizational learning loops. Ensure the Brain continuously improves. |
| --- | --- |
| **Responsibilities** | Evaluate outcomes, Capture lessons, Update memory, Improve future reasoning, Detect drift, Analyze feedback, Evaluate recommendations, Evaluate agent performance, Evaluate exposure effectiveness, Generate policy update candidates, Compare designed rules and processes against executed Action patterns and route confirmed divergence into Learning Memory as candidate process improvements |
| **Inputs** | Actions, outcomes, feedback signals, recommendation outcomes, exposure outcomes |
| **Key Question** | What changed because of what we did? |
| **Outputs** | Updated organizational memory, updated organizational understanding, updated learning signals, policy improvement candidates |

The Evolution Layer learns not only from organizational outcomes, but also from how humans and AI systems interact with delivered memory, recommendations, and actions.

Examples include:

- Accepted Suggestions
- Rejected Suggestions
- Ignored Suggestions
- Agent Approval Rates
- Agent Rejection Rates
- Exposure Effectiveness

These become learning signals used to improve future reasoning and delivery.

# 15. Supporting Systems

Supporting systems operate across all layers. They are not the Brain itself. They enable safe interaction with the Brain.

## **Trust System**

### Theoretical Grounding

The W3C's PROV-O is a formal vocabulary for describing provenance — where information came from and who's responsible for it — built on three core relations: `wasGeneratedBy` (an entity was produced by a specific activity), `wasAttributedTo` (an entity is the responsibility of a specific agent), and `wasDerivedFrom` (an entity was derived from another entity). This system's provenance and versioning fields implement that vocabulary directly, mapped by question rather than loosely borrowed: `wasAttributedTo` answers who asserted something; `wasGeneratedBy` answers when and by what activity; `wasDerivedFrom` answers what source it traces back to. The same mapping is used identically in Memory Model v1.3 §8 and Trust & Governance v1.1 Part 4. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 13. Fit: Clean — direct implementation.

| **Purpose** | Ensure organizational understanding remains trustworthy. |
| --- | --- |
| **Responsibilities** | Source traceability, Ownership Verification, Audit history, Confidence assessment, Governance, Provenance & versioning, Knowledge Representation Governance |
| **Key Question** | Can we trust this? |

### Knowledge Representation Governance

Ensure Canonical Knowledge Objects remain:

- Consistent
- Traceable
- Versioned
- Portable
- Governed

across all Company Brain components.

## Consultant System

| **Purpose** | Help humans and AI understand and improve the organization. |
| --- | --- |
| **Responsibilities** | Recommendations Guidance Reviews Planning support Continuous improvement |
| **Key Question** | What should we do next? |

## Workspace System

| **Purpose** | Provide interfaces for interacting with the Brain. |
| --- | --- |
| **Responsibilities** | Search Views Dashboards Knowledge Studio Automation Studio Reporting |
| **Key Question** | How do we interact with the Brain? |

# **16. Organizational Learning Loop**

### Theoretical Grounding

This loop is the same double-loop learning mechanism grounded at Section 14 (Argyris & Schön, 1978, 1996), shown here end-to-end against the full pipeline rather than isolated to the Evolution layer alone, plus the Externalization step from Nonaka & Takeuchi's SECI model (1995, grounded at Sections 8–9) that converts observed reality into structured Knowledge Objects in the first place. See `Company_Brain_Theoretical_Foundations_v1.md`, Fields 7 and 6. Fit: Clean (Argyris & Schön, direct implementation); Partial (SECI, one mode of four).

| **Traditional Systems** | **Company Brain** |
| --- | --- |
| Store → Retrieve | Observe Reality → Understand Reality → Create Knowledge Objects → Create Memory → Generate Intelligence → Execute → Expose → Learn → Update Reality Model |

The Brain continuously improves its understanding of the organization.

# **17. Relationship to Products**

*No external grounding — aspirational/product framing, Master Plan §2.1 marks KEEP.*

The Company Brain is the foundation. Products are built on top.

**Company Brain → Intelligence → Exposure → Applications → Interfaces**

The Brain remains the source of truth.

Products do not replace the Brain.

They expose and operationalize it.

Everything else is an interaction layer.

# **18. Long-Term Vision**

*No external grounding — aspirational framing, Master Plan §2.1 marks KEEP.*

**Today:**

Organizations operate through fragmented knowledge.

**Tomorrow:**

Organizations operate through a Company Brain.

The Company Brain becomes the living model of organizational reality.

- It remembers.
- It understands.
- It reasons.
- It coordinates.
- It delivers.
- It learns.

Humans and AI operate from the same shared understanding. The organization becomes capable of preserving and compounding its intelligence over time.

# One-Sentence Summary

| **The Company Brain is a living organizational reality, knowledge, memory, intelligence, exposure, and learning system that models how an organization functions, preserves what it learns, reasons over what it knows, delivers the right understanding at the right moment, and enables both humans and AI to operate from a shared understanding of reality.** |
| --- |

ZeroManual — Internal   ·   Page  of
