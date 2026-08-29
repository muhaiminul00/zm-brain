# Company Brain — Technical Build Master Plan
## Version 1.2 (Final — Canonical Roadmap)
### Status
Approved Technical Roadmap — Post-Conceptual Architecture
July 2026

---

# Purpose

The conceptual architecture is complete and frozen.

This roadmap defines how Company Brain moves from concept into a production system. It does **not** redefine the conceptual architecture. It defines:

- Technical architecture
- Engineering sequencing
- Implementation boundaries
- MVP scope
- Validation gates
- V1 expansion strategy

Guiding philosophy:

> **Adopt proven infrastructure. Engineer proprietary organizational intelligence.**

---

# Core Engineering Principles

## Principle 1 — Architecture ≠ Implementation

Canonical conceptual model: Capture → Understanding → Memory → Intelligence → Execution → Exposure → Evolution.

That's the organizational model. The technical architecture is a separate, implementation-optimized model. Never build one microservice per conceptual layer.

## Principle 2 — Build Only the Differentiation

Everything falls into one of two categories.

**Commodity Infrastructure** (adopt, do not reinvent): APIs, Authentication, Connectors, Embeddings, Retrieval, Storage, Queues, Monitoring, MCP, Hybrid Search.

**Company Brain Engine** (unique IP, engineer here): Organizational Understanding, Knowledge Objects, Memory Formation, Commitment Memory, Trust Objects, Organizational Intelligence, Drift Detection, Organizational Learning.

Engineering effort belongs almost entirely in the second category.

## Principle 3 — Validate Differentiation

The MVP must answer:

> Can Company Brain become trusted organizational memory?

Not:

> Can Company Brain summarize meetings?

## Principle 4 — Vertical Slice

Never build every layer first. Build one complete customer workflow. Validate. Expand.

## Principle 5 — Boring Technology Wins

Prefer mature, proven technologies. Optimize only after validation.

---

# Overall Roadmap

```text
Conceptual Architecture
        │
        ▼
Technical Architecture
        │
        ▼
Platform Foundation
        │
        ▼
Company Brain Engine MVP
        │
        ▼
Customer Validation Gate
        │
        ▼
Company Brain V1
        │
        ▼
Platform Scaling
```

---

# Phase 0 — Technical Architecture

## Goal

Freeze every irreversible engineering decision before implementation begins. No customer-facing development starts before this phase is complete.

## Deliverables

### 1. Resolve Open Technical Questions Backlog

Before any freeze below is finalized, cross-check it against the consolidated open-questions/deferred-items register pulled from the full canonical document set (Architecture & Vision, Ontology, Memory Model, Product Architecture, Intelligence Architecture, Trust & Governance). If that scan hasn't been run yet, run it first — several of the freezes below (storage, retrieval, OKF) depend on knowing what each conceptual doc actually left open versus already implied.

### 2. Canonical Technical Architecture Document

Defines: Services, APIs, Storage, Runtime, Pipelines, Deployment, Event Flow, Internal Contracts. Does not redefine conceptual behavior.

### 3. Freeze Technical Decisions

**Deployment — Frozen:**
> **Self-hosted / Customer VPC first.** Cloud-hosted SaaS supported only as an optional deployment model, not the default.

Reason: enterprise data-ownership expectations, governance, regulatory adoption, AI model flexibility. This decision shapes every infrastructure choice below.

**Storage:**
- Primary database: PostgreSQL
- Vector store: pgvector
- Blob storage: Object Storage
- No dedicated graph database initially — relationship/graph traversal is implemented as relational tables in Postgres, not a separate graph engine. Revisit only if traversal queries become a demonstrated bottleneck (see Scaling, Phase 3).

**Runtime:** FastAPI, Python, Redis, Celery, Docker.

**Retrieval:** Adopt a proven hybrid retrieval architecture, directly based on the public GBrain implementation and its published benchmarks (BM25 + vector search + graph traversal contributing a documented +31-point precision improvement over graph-disabled retrieval).

Stack: BM25, Vector Search (HNSW), Reciprocal Rank Fusion, Metadata Filtering, Graph Traversal (via relational tables, per Storage above), Reranker.

This is adopted infrastructure, not original Company Brain IP — no experimentation here.

**Knowledge Exchange:**
- Internal representation remains Company Brain's canonical Knowledge Object schema.
- Company Brain adopts **Google Open Knowledge Format (OKF) v0.1** as its external Knowledge Exchange format.
- Export/import compatibility with OKF is designed in from MVP, so this is never retrofitted later.
- Full ecosystem interoperability (bi-directional exchange, brain-to-brain) expands in V1.

### 4. Platform Boundary

Permanent three-layer separation — must never blur:

```text
Platform
↓
Company Brain Engine
↓
Applications
```

---

# Phase 1 — Platform Foundation

## Goal

Build reusable infrastructure. Almost no Company Brain intelligence lives here.

**Platform Services:** API Gateway, Capture Service, Memory Service, Reasoning Service, Execution Service.

**Platform Components:** FastAPI, PostgreSQL, pgvector, Redis, Celery, Object Storage, Authentication, Logging, Monitoring, Configuration, Secrets, MCP Server.

**Initial Connectors:** Manual Upload, Markdown, PDF, Meeting Transcript, Email Export. All others (Slack, Notion, Google Workspace, etc.) deferred to Phase 3.

**Retrieval Layer:** Adopt proven patterns exactly as frozen in Phase 0. No experimentation — this layer is infrastructure, not differentiation.

---

# Phase 2 — Company Brain Engine MVP

## Goal

Validate Company Brain's unique value proposition — nothing else.

## MVP Scope — one complete workflow

```text
Meeting Transcript
↓
Understanding
↓
Knowledge Objects
↓
Commitment Detection
↓
Trust Attribution
↓
Memory Formation
↓
Consultant
```

## Understanding Pipeline (MVP implementation)

```text
Normalization
↓
Single LLM Understanding
↓
Knowledge Object Extraction
↓
Validation
↓
Memory Routing
```

Intentionally favors engineering simplicity and learning speed over inference-cost optimization at this stage.

### Planned Optimization (explicitly deferred, not abandoned)

After MVP validation, Understanding becomes a two-stage pipeline:

```text
Deterministic Extraction (names, dates, organizations, metadata, relationships — near-zero marginal cost)
↓
LLM Reasoning (reserved for commitments, intent, trust, organizational reasoning)
↓
Validation
```

Deferred deliberately until scale justifies the added complexity — noted here so it's rebuilt by design later, not re-derived under cost pressure.

## Knowledge Objects (MVP)

Actor, Communication, Commitment, Action, Goal, Relationship. Canonical Company Brain objects, each exportable as OKF-compatible representations from day one. No full ontology yet.

## Commitment Memory — the MVP's primary differentiator

First complete Company Brain memory implementation. Stores: Who, Owes What, To Whom, Deadline, Status, Source, Confidence, Lifecycle.

## Trust MVP — two forms, both required

**Trust Data Model:** persistent, queryable, auditable. Every memory carries Source, Evidence, Timestamp, Confidence, Asserted By — stored as Memory metadata, not just a permission flag.

**Trust Enforcement:** authorization, permissions, approvals, policies, service-boundary checks. Cross-cutting runtime concern, implemented as middleware.

Both required — the data model is what makes Trust a differentiator; the enforcement layer alone would reduce it to a permissions check.

## Consultant MVP

Handles: "What commitments exist?" / "Who owns this?" / "What is overdue?" / "What was promised?" / "Where did this information come from?" / "What evidence supports this?"

Explicitly excluded: recommendations, planning, automation, simulation.

## Explicitly Out of Scope for MVP

Drift Detection, Learning Memory, Recommendations, Risk Detection, Opportunity Detection, Agent Runtime, Mission Control, Ambient Delivery, Workflow Reconstruction, Multi-model orchestration, Multi-tenancy.

**Multi-tenancy clarification:** because deployment is customer-instance-first (self-hosted/VPC), SaaS-style multi-tenancy is not an MVP requirement and may not become a core architectural constraint at all — revisit only if a specific deployment need demands it.

---

# Customer Validation Gate

No expansion beyond MVP until validation succeeds.

## Success Criteria

**Technical:**
- Commitment extraction accuracy ≥ [threshold — to be set from a calibration test against real transcripts before Phase 2 build begins, not invented in this document]
- Provenance attached to every stored commitment, with no exceptions
- Consultant retrieves correct commitments consistently
- Stable end-to-end workflow

**Customer:** at least several design-partner organizations confirm that:
- Commitment tracking solves a real problem
- Trust/provenance increases their confidence in the answers
- They would continue using the product
- They would replace or augment an existing workflow with it

If these conditions aren't met, the roadmap pauses. Engineering revisits the MVP before proceeding — expansion is not the default outcome of reaching this gate.

---

# Phase 3 — Company Brain V1

## Goal

Expand from Commitment Memory into full organizational memory.

**Memory Expansion:** Factual, Interaction, Commitment, Action, Learning Memory — all five types.

**Complete Ontology:** Atomic Primitives → Core Objects → Organizational Structures → Operational Constructs.

**Trust & Governance — full expansion:** Claim, Evidence, Challenge, Approval, Delegation, Exception, Escalation, each with Lifecycle, Audit, Governance, and Enforcement.

**Intelligence:** Context Assembly, Recommendations, Operational Risk, Opportunity Detection, Knowledge Gaps, Consultant Modes, Confidence Model.

**Drift Detection:** Candidate → Pattern → Signal → Severity, connected to Policies, SOPs, Workflows, Learning. One of Company Brain's strongest, least-contested differentiators — no direct competitor implements this today.

**Organizational Learning:** Learning Memory → Validated Feedback → Policy Suggestions → Human Approval → Memory Update.

**Execution:** Agent Context, Task Plans, Human Approval, Escalation, Execution Guidance. Autonomous execution remains optional, never default.

**Exposure:** expand beyond Consultant — Mission Control, Timeline, Workspace, Memory Cards, Notifications, Ambient Delivery.

**Connectors:** expand to Slack, Teams, Google Workspace, Notion, GitHub, Jira, CRM, ERP, Custom APIs.

**Security & Compliance:** begins in V1, not before. Owner: Platform Team. Includes SSO, Audit Logs, Encryption Hardening, Compliance Controls, Data Residency, Enterprise Security Review — expect enterprise customers from the design-partner pool to raise this earlier than V1 in conversation, even if implementation waits.

---

# Scaling (only after product-market fit)

Distributed Workers, Caching, Horizontal APIs, Streaming, Graph Database (only if traversal load specifically justifies it), Model Routing, Inference Cost Optimization.

---

# Final Technical Architecture

```text
                    Applications
────────────────────────────────────────────
Mission Control · Consultant · Workspace
Agents · Dashboards · Integrations
────────────────────────────────────────────
            Company Brain Engine
────────────────────────────────────────────
Understanding Pipeline · Knowledge Object Engine
Commitment Engine · Memory Formation · Memory Services
Trust Engine · Context Builder · Reasoning Engine
Drift Engine · Learning Engine · Execution Planner
────────────────────────────────────────────
             Platform Foundation
────────────────────────────────────────────
API Gateway · Authentication · Capture · Connectors
FastAPI · PostgreSQL · pgvector · Redis · Celery
Object Storage · MCP · Logging · Monitoring · Secrets
────────────────────────────────────────────
                Infrastructure
────────────────────────────────────────────
Containers · Servers · Networking
Deployment · Backups · Observability
```

---

# Engineering Philosophy

Build the minimum. Validate the differentiation. Adopt everything already solved. Engineer only what makes Company Brain unique.

---

# Definition of Success

**MVP:** Company Brain becomes trusted organizational memory. Users can confidently answer: What commitments exist? Who owns them? Where did this come from? Why should I trust it?

**Version 1:** Company Brain evolves into an organizational intelligence platform that can Remember, Explain, Govern, Reason, Detect Drift, Learn, and Assist Execution — while remaining transparent, trustworthy, and human-governed throughout.
