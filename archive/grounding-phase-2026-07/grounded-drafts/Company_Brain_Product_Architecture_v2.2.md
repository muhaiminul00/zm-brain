# COMPANY BRAIN

# Product Architecture v2.2

## Canonical Product Architecture

### ZeroManual — Internal

### July 2026

---

## Document Control

| Field | Value |
| --- | --- |
| Version | 2.2 |
| Status | Canonical Product Architecture — Grounded Draft, pending human review and freeze |
| Supersedes | Product Architecture v2.1 |
| Depends on | Architecture & Vision v2.3, Ontology v1.3, Memory Model v1.3 |
| Scope | Product Architecture only — how humans and AI systems reach and use organizational memory. |

### Changes In This Revision

- Theoretical Grounding pass (see `Company_Brain_Theoretical_Foundations_v1.md`). No product decision changed. GROUND/VERIFY sections now carry an inline citation callout.
- Updated MCP and A2A governance language (Section 5) — verified via web search that MCP is now stewarded by the Agentic AI Foundation, a Linux Foundation directed fund, since December 2025 (no longer solely Anthropic-governed), and that Google donated A2A to the Linux Foundation in June 2025 for neutral governance.
- OKF references (Section 5) updated to reflect direct adoption of Google Cloud's real OKF v0.1 spec, per the companion `OKF_Adoption_Mapping.md`.
- **Exposition rewrite (this pass):** grounding callouts rewritten from citation-then-mention into theory-first exposition. Section 15's Three-Tier Boundary now states explicitly why its plain-language tier names (Always/Ask First/Never) are retained rather than swapped for the academic human-in-the-loop/on-the-loop/out-of-loop labels, while still citing and aligning with that taxonomy.
- No structural redesign was performed. The Three Exposure Modes remain unchanged.

### Changes In v2.1 (carried forward from prior revision)

- Added Knowledge Exchange.
- Added Open Knowledge Format (OKF) compatibility.
- Added Brain-to-Brain Interoperability direction.
- Added Knowledge Object inspection capabilities.
- Added Knowledge Exchange Governance.
- Added Product Boundary clarification.
- Added Knowledge Representation Explorer future capability.
- Extended Competitive Position with interoperability.

---

# 0. Purpose

This document defines how humans and AI interact with the Company Brain.

The Architecture & Vision document defines:

How the Company Brain works.

The Ontology defines:

What exists inside the Company Brain.

The Memory Model defines:

How organizational reality becomes memory.

This document defines:

How organizational memory reaches humans and AI systems.

---

# 1. Core Product Shift

### Theoretical Grounding

Mark Weiser's "The Computer for the 21st Century" (1991) coined "calm technology" and ubiquitous computing: the strongest technology is the kind that disappears into the environment, doing its job without demanding attention as a destination in its own right. The v2 assumption below — the Brain arrives where work already happens, rather than being a place users must remember to visit — implements that idea directly, though it's cited here as a light, optional reinforcement rather than the load-bearing theory behind this document (Master Plan §2.4). Fit: Clean, light.

## v1 Assumption

User
↓
Open Company Brain
↓
Use Company Brain
↓
Leave Company Brain

This creates a destination product.

The Brain becomes another application users must remember to visit.

---

## v2 Assumption

User
↓
Works Anywhere
↓
Company Brain Arrives There

The Brain becomes infrastructure.

Users remain inside:

* Gmail
* Outlook
* Slack
* Teams
* Calendar
* CRM
* LinkedIn
* ChatGPT
* Claude
* Cursor
* Internal Tools

The Brain delivers memory wherever work is already happening.

---

# 2. Product Philosophy

## Core Law

Users navigate work. The Brain navigates memory and meets them wherever work is happening.

---

## Product Thesis

The Company Brain is not an application.

It is organizational memory infrastructure.

The dashboard is only one way to access it.

---

## Product Goal

Transform organizational memory into:

* Accessible knowledge
* Actionable context
* Trusted decisions
* Coordinated execution

without requiring people to manually search for information.

---

# 3. Exposure Modes

The Company Brain operates through three exposure modes.

These are not architectural layers.

They are access modes.

Company Brain
(Memory + Intelligence)

        ↓

┌─────────────────────────────┐
│ 1. Ambient Delivery         │
├─────────────────────────────┤
│ 2. Agent Access             │
├─────────────────────────────┤
│ 3. Mission Control          │
└─────────────────────────────┘

All three operate on the same:

* Memory
* Intelligence
* Governance
* Provenance

---

# 4. Exposure Mode 1

# Ambient Delivery

## Purpose

Deliver relevant memory inside the tools people already use.

---

## Design Principle

Capture Everywhere
Understand Centrally
Deliver Everywhere

---

## User Experience

The Brain appears when needed.

Not before.

Not after.

At the moment work is happening.

---

## Gmail / Outlook

While writing an email:

The Brain surfaces:

* Related commitments
* Relevant decisions
* Customer history
* Previous conversations
* Existing risks

Actions:

Insert Context
View Sources
Ask Consultant
Assign To Agent

---

## Slack / Teams

Inside conversations:

The Brain surfaces:

* Relevant decisions
* Open commitments
* Prior discussions
* Team context

without requiring a search.

---

## Calendar

Before meetings:

The Brain generates:

* Meeting brief
* Attendees
* Open commitments
* Prior discussions
* Risks
* Pending decisions

---

## CRM

Inside account pages:

The Brain surfaces:

* Relationship history
* Open commitments
* Incidents
* Stakeholders
* Renewal risk

---

## LinkedIn

While researching or messaging:

The Brain surfaces:

* Existing relationships
* Historical interactions
* Internal experts
* Relevant context

---

## Design Rules

The Brain never interrupts.

The Brain never forces interaction.

The Brain remains silent when no useful memory exists.

Every suggestion is:

* contextual
* dismissible
* explainable
* traceable

---

# 5. Exposure Mode 2

# Agent Access

## Purpose

Allow AI systems to access organizational memory directly.

---

## Core Principle

The Company Brain is an MCP provider.

Not merely an MCP consumer.

---

## MCP Surface

> **Verified:** Model Context Protocol, introduced by Anthropic in November 2024, was donated to and is now stewarded by the Agentic AI Foundation — a directed fund under the Linux Foundation, co-founded by Anthropic, Block, and OpenAI, joining as a founding project in December 2025. Confirmed current via web search. This document's language is updated accordingly; MCP is no longer solely an Anthropic-governed protocol. See Field 13.

Core tools:

brain_search

brain_recall

brain_get_context

brain_get_commitments

brain_get_team_status

brain_check_drift

brain_propose_action

---

## Typical Usage

A user opens:

* ChatGPT
* Claude
* Cursor
* Windsurf
* Codex

and asks:

Prepare a proposal for Acme Corp.

The Brain automatically provides:

* customer history
* commitments
* risks
* previous proposals
* organizational context

through MCP.

---

## Lifecycle Context Injection

MCP alone is reactive.

The Brain additionally supports:

Session Start

Prompt Submit

Task Completion

Turn End

context injection.

Purpose:

Prevent important organizational context from being forgotten during long-running AI workflows.

---

## A2A Support

> **Verified:** Google donated the Agent2Agent (A2A) protocol to the Linux Foundation in June 2025 for neutral governance. Confirmed current via web search.

Company Brain agents are discoverable via A2A.

External agents may:

* request memory
* request actions
* request specialist agents

under governance.

---

## Knowledge Exchange

### Theoretical Grounding

Gruber's ontology definition (1993) and RDF/OWL's relationship conventions (W3C) underlie Knowledge Objects and their typed relationships generally — see Ontology v1.3 §6 and Memory Model v1.3 §11 for where those are implemented directly. Knowledge Exchange itself runs on different, adopted infrastructure: Google Cloud's Open Knowledge Format (OKF) v0.1 is the concrete mechanism realizing everything below, not an analogy to a theory — Composite Knowledge Objects export as OKF concept documents; full mapping in the companion `OKF_Adoption_Mapping.md`. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 12, and Master Plan §6.

The Company Brain supports portable knowledge exchange through Canonical Knowledge Objects.

Where governance permits, knowledge may be:

* Exported
* Imported
* Shared
* Synchronized

through standardized representations.

Knowledge Exchange operates independently from memory storage and user interfaces.

The same organizational understanding may be exchanged across systems while preserving provenance, governance, trust, and traceability.

### Open Knowledge Compatibility

The Company Brain exchanges Canonical Knowledge Objects through Open Knowledge Format (OKF) v0.1 compatible representations whenever governance permits.

OKF compatibility allows organizational knowledge to move between systems without requiring those systems to share implementation details.

### Brain-to-Brain Interoperability

*No external grounding forced — Master Plan §5 marks Knowledge Exchange / Brain-to-Brain Interoperability as a strategic direction, original IP, not a format-compatibility claim to be grounded further.*

Future Company Brain instances may exchange Canonical Knowledge Objects directly.

Examples include:

* Customer ↔ Vendor coordination
* Subsidiary ↔ Parent organization coordination
* Multi-company projects
* Partner ecosystem coordination

All exchanges remain governed by:

* Trust
* Provenance
* Access Controls
* Organizational Policy

---

## Agent Access Principle

**AI systems should consume organizational memory as naturally as humans do.**

The Company Brain should serve not only as a memory provider but also as a trusted knowledge exchange participant within broader organizational ecosystems.

Future Agent Access may support governed exchange of Canonical Knowledge Objects between organizations, systems, and Company Brain instances while preserving provenance and trust.

---

# 6. Exposure Mode 3

# Mission Control

## Purpose

Provide a dedicated environment for:

* investigation
* governance
* coordination
* oversight

---

## Mission Control Is Not

The primary workplace.

---

## Mission Control Is

The place users go when deeper understanding is required.

---

# 7. Mission Control Surface

# Personal Reality

## Key Question

What requires my attention?

---

## Contains

* Open commitments
* Overdue commitments
* Today's work
* Team context
* Decisions affecting me
* Suggested actions

---

## Purpose

Turn memory into daily operational clarity.

---

# 8. Mission Control Surface

# Team Reality

## Key Question

How is my team performing?

---

## Contains

* Team commitments
* Risks
* Blockers
* Dependencies
* Capacity
* Drift signals

---

## Purpose

Turn organizational memory into team awareness.

---

# 9. Mission Control Surface

# Reality Feed

## Key Question

What changed that matters?

---

## Sources

* Commitments
* Decisions
* Policy updates
* Drift signals
* Agent approvals
* Learning events
* Conflicts

---

## Multi-Channel Delivery

Reality Feed exists in:

* Dashboard
* Slack
* Email
* Browser Extension
* Mobile

The feed is not tied to one interface.

---

## Purpose

Reduce organizational forgetting.

---

# 10. Mission Control Surface

# Organizational Memory

## Key Question

Why?

---

## Capabilities

* Search
* Timeline
* Relationship Graph
* Provenance
* History

---

## Example Questions

Why did we choose microservices?

Who approved this?

What happened last time?

What commitments came from this meeting?

---

## Purpose

Turn memory into organizational understanding.

---

## Inspect Knowledge Object

Users may inspect the underlying Knowledge Object representation associated with any memory record.

Inspection may expose:

* Source
* Provenance
* Relationships
* Version History
* Confidence
* Governance Metadata

This capability exists primarily for:

* Auditing
* Governance
* AI Explainability
* Debugging
* Investigation

The purpose is transparency and traceability, not everyday navigation.

---

# 11. Mission Control Surface

# Consultant

## Key Question

What should we do?

---

## Modes

### Theoretical Grounding

Herbert Simon's *The New Science of Management Decision* (1960) breaks decision-making into three phases: **Intelligence** (gathering information about the situation), **Design** (working out possible courses of action), and **Choice** (evaluating and selecting among them). Verified: this is Simon's original three-phase model — a fourth phase (Implementation) appears only in his later writing, not the 1960 original. Inquiry Mode implements the Intelligence phase directly, Planning Mode implements Design, Review Mode implements Choice. Simulation Mode is Company Brain's own extension beyond Simon's three phases — "what happens if" scenario comparison isn't one of his original phases, and this document doesn't force it to look like a borrowed fourth one. See `Company_Brain_Theoretical_Foundations_v1.md` and Intelligence Architecture v1.1 Part 6 for the full reasoning-pipeline grounding.

**Relationship:** we implement Simon's three-phase model directly for Inquiry/Planning/Review; Simulation Mode is an explicit extension, not a borrowed fourth phase.

### Inquiry

What do we know?

---

### Planning

What should we do?

---

### Review

Are we on track?

---

### Simulation

What happens if?

---

## Consultant Rules

Every answer includes:

* Sources
* Confidence
* Reasoning
* Recommended action

---

## Purpose

Turn memory into decisions.

---

# 12. Mission Control Surface

# Agent System

## Key Question

Can someone do this for me?

---

## Core Principle

Agent is a verb.

Not a destination.

---

## User Experience

Anywhere a human can be assigned:

Assign To Agent

exists.

---

## Agent Categories

* Support
* Scheduling
* Review
* Execution
* Research
* Specialist

---

## Purpose

Turn memory into delegated execution.

---

# 13. Mission Control Surface

# Automation

## Key Question

Can this happen automatically?

---

## Principle

Automation emerges from repeated behavior.

---

## Sources

Repeated patterns from:

* Commitments
* Actions
* Workflows
* Learning

---

## Lifecycle

Draft
↓
Testing
↓
Approval
↓
Active
↓
Paused
↓
Archived

---

## Purpose

Turn recurring work into systems.

---

# 14. Mission Control Surface

# Operational Intelligence

## Key Question

How healthy is the organization?

---

## Views

### Organizational Health

---

### Commitment Velocity

---

### Learning Velocity

---

### Drift Monitor

---

### Agent Performance

---

## Purpose

Turn memory into organizational visibility.

---

## Future Capability — Knowledge Representation Explorer

A dedicated interface for exploring:

* Knowledge Objects
* Relationships
* Provenance Chains
* Version History
* Representation Lineage

Primary users:

* Administrators
* Governance Teams
* AI Auditors
* Advanced Investigators

The Knowledge Representation Explorer is intended as an advanced governance and explainability capability rather than a primary workflow.

---

# 15. Trust & Governance

## Core Principle

Memory must be trusted.

Trust must be visible.

---

# Trust Cards

Every important claim displays:

Source

Confidence

Authority

Last Updated

Challenge Status

### Representation Visibility

Where appropriate, users may inspect the Knowledge Object representation that produced a memory record.

This capability supplements, but does not replace, existing Trust Card metadata.

Trust Cards remain the primary trust surface.

Knowledge Object inspection provides deeper explainability when required.

---

# Three-Tier Boundary System

### Theoretical Grounding

Human-AI interaction literature describes autonomy along a standard three-way split: **human-in-the-loop** (a human must approve before an action executes), **human-on-the-loop** (a human monitors and can intervene, but approval isn't required per instance), and **human-out-of-loop** (the system acts independently, no human checkpoint). No single canonical source defines this — it's an established convention across human-AI interaction and human-factors literature. Always, Ask First, and Never below implement two of these three positions directly (Always↔human-out-of-loop, Ask First↔human-in-the-loop); Never has no loop-position equivalent at all, since it blocks the action regardless of who's watching.

**Vocabulary choice, stated explicitly:** the tier names below stay "Always / Ask First / Never" rather than being swapped for "human-out-of-loop / human-in-the-loop / [no equivalent]." A product user acting on this boundary needs an instruction they can follow immediately — "Ask First" tells them what happens next; "human-in-the-loop" describes an academic category they'd have to translate before acting on. The academic taxonomy is cited here, and used to align this system explicitly with Trust & Governance's Human Oversight Authority (Trust & Governance v1.1 Part 8, which the reconciliation table in that document already unifies with this one) — but it supplements the plain names rather than replacing them. See `Bibliography.md`, "Human-AI Autonomy." Fit: Clean for 2 of 3 tiers (direct implementation); Never has no taxonomy equivalent.

## Always

No approval required.

*Maps to: human-out-of-loop.*

---

## Ask First

Approval required.

*Maps to: human-in-the-loop.*

---

## Never

Forbidden.

*Maps to: no autonomous path exists regardless of loop position.*

---

## Knowledge Exchange Governance

Knowledge Exchange must preserve:

* Provenance
* Ownership
* Access Rights
* Trust Metadata
* Governance Classification

Knowledge Exchange never bypasses organizational governance.

Exporting knowledge remains subject to the same approval requirements as any other governed organizational action.

Interoperability expands distribution.

It does not weaken trust.

---

## Purpose

Enable safe human-agent collaboration.

---

# 16. Product Boundary

Product Architecture defines how organizational understanding reaches humans and AI systems.

Product Architecture does not define:

* Ontology
* Knowledge Representation Standards
* Knowledge Object Schemas
* Memory Formation
* Memory Lifecycle
* Storage Technology
* Database Architecture

Those responsibilities belong to:

* Architecture & Vision
* Ontology
* Memory Model
* Technical Architecture

The Product Architecture consumes organizational understanding.

It does not define organizational understanding.

---

# 17. Conflict Experience

## Purpose

Show how the Brain resolves conflicting memories.

---

## Every Conflict Shows

Current

Superseded

Why Current Won

Challenge

---

## Design Principle

Never silently overwrite organizational truth.

---

# 18. Drift Experience

## Purpose

Reveal divergence between:

Designed Reality

vs

Observed Reality

---

## Comparison

Policy
↓
SOP
↓
Workflow

---

## Examples

* Skipped approvals
* Shadow processes
* Repeated exceptions
* Emerging practices

---

## Purpose

Transform hidden organizational change into visible signal.

---

# 19. Learning Experience

## Purpose

Ensure organizational learning becomes reusable memory.

---

## Sources

* Incidents
* Decisions
* Projects
* Drift analysis
* Outcomes

---

## Output

* Lessons
* Heuristics
* Recommendations
* Process improvements

---

## Purpose

Prevent repeated mistakes.

---

# 20. Competitive Position

Most competitors provide:

Memory
+
Search
+
AI

or

Ambient Context
+
MCP

The Company Brain combines:

Governed Memory
+
Commitment Intelligence
+
Conflict Resolution
+
Drift Detection
+
Operational Intelligence
+
Ambient Delivery
+
MCP-Native Access

## Additional Strategic Differentiator

### Interoperability

Future Company Brain instances may exchange governed Knowledge Objects while preserving provenance, trust metadata, ownership, and governance controls.

This extends the vision beyond:

```text
Memory Infrastructure
```

toward:

```text
Knowledge Infrastructure
```

The long-term objective is not merely remembering organizational reality.

It is enabling trusted organizational knowledge to move safely between systems, agents, and organizations.

---

# 21. MVP Prioritization

## P0

* MCP Server
* Ambient Delivery (Gmail + Slack)
* Trust Cards
* Three-Tier Governance
* Reality Feed Infrastructure

---

## P1

* Personal Reality
* Team Reality
* Consultant
* Organizational Memory

---

## P2

* Agent System
* A2A Integration
* Conflict Experience
* Drift Experience

---

## P3

* Automation Studio
* Full Operational Intelligence
* Knowledge Exchange
* Knowledge Representation Explorer

---

# 22. Success Metrics

## Adoption

* % interactions outside dashboard
* MCP usage
* Ambient suggestion usage

---

## Operational Impact

* Commitment fulfillment rate
* Time-to-awareness reduction
* Drift resolution rate

---

## Trust

* Challenge rate
* Conflict resolution accuracy
* Agent escalation rate

---

# One-Sentence Summary

The Company Brain is not a dashboard users must remember to visit; it is governed organizational memory and intelligence that reaches humans and AI systems wherever work occurs, while providing trusted investigation, governance, interoperability, and knowledge exchange through Mission Control, Agent Access, and Ambient Delivery.
