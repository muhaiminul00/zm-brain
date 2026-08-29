# Company Brain — Spike Implementation Plan
## Version 1.1 (Canonical)
### Sprint 0–2: Thin Design → Spike → Canonical Design
### Precedes Technical Build Master Plan v1.2, Phase 2

---

# Purpose

This plan governs only the next **2–3 weeks**.

It bridges the gap between:

- Frozen conceptual architecture
- Technical Build Master Plan v1.2
- Actual MVP engineering

Its purpose is **not to build Company Brain**.

Its purpose is to replace assumptions about the Understanding Pipeline with measured engineering knowledge.

Everything here is intentionally temporary.

Anything that starts becoming comprehensive, production-ready, or permanent before its planned week is considered scope creep.

---

# Core Philosophy

The spike exists to answer engineering questions, not produce software.

We are optimizing for learning speed, not implementation completeness.

The goal is:

> **Experiment → Observe → Measure → Freeze → Build**

NOT

> Plan → Guess → Build

---

# Week 0 — Engineering Governance + Thin Data Model + Evaluation Setup

---

# 1. Engineering Governance (Day 1)

Effective immediately.

## Rule 1

Conceptual documents are read-only.

Architecture changes only through intentional architecture review.

---

## Rule 2

Every engineering feature must trace to one or more canonical conceptual documents.

Examples

Commitment Engine

→ Memory Model

→ Ontology

Trust Engine

→ Trust & Governance

Consultant

→ Product Architecture

→ Intelligence Architecture

---

## Rule 3

Implementation never redefines conceptual behavior.

If implementation reveals a conceptual issue:

Architecture updates first.

Code follows.

Never the reverse.

---

# 2. Thin Data Model

Only the six MVP Knowledge Objects exist.

Nothing else.

Everything outside this scope is intentionally deferred.

---

| Object | Initial Fields |
|---------|----------------|
| Actor | id, name, role, source_reference |
| Communication | id, type, participants, timestamp, source_reference |
| Commitment | id, who, owes_what, to_whom, deadline, status, confidence, source_reference, created_at |
| Action | id, description, actor, timestamp, source_reference |
| Goal | id, description, owner, source_reference |
| Relationship | id, subject, predicate, object, source_reference |

Every object also contains

- confidence
- source_reference
- schema_version

---

# 3. Thin Database

One table per object.

```
actors

communications

commitments

actions

goals

relationships

sources
```

No ORM optimization.

No migrations.

Hand-written SQL is acceptable.

---

# 4. Gold Dataset

Before any prompt tuning begins,

create a small manually annotated dataset.

Recommended:

5–10 meeting transcripts.

For every transcript,

manually identify:

- Actors
- Communications
- Commitments
- Actions
- Goals
- Relationships

This becomes the permanent evaluation baseline.

Never modify the annotations to fit the LLM.

The LLM must improve toward the dataset.

---

# 5. Spike Exit Criteria

Write these before Week 1 begins.

The spike is complete only when:

✓ Pipeline consistently produces all six object types

✓ Commitment extraction reaches an agreed quality threshold

(The exact number is determined after calibration on the first few transcripts.)

✓ Every Commitment has provenance

✓ Output stores automatically in Postgres

✓ Streamlit answers:

- What commitments exist?
- Who owns them?
- Where did they come from?

If these conditions fail,

the spike continues.

No freezing.

No MVP.

---

# Week 1 — Engineering Spike

Goal:

Discover how the Understanding Pipeline actually behaves.

Nothing more.

---

# Pipeline

```text
Transcript

↓

One handwritten prompt

↓

LLM

↓

Raw JSON

↓

Pydantic Validation

↓

Knowledge Objects

↓

Postgres

↓

Streamlit
```

---

# Absolutely Out of Scope

No LangChain

No LangGraph

No CrewAI

No AutoGen

No Agent Runtime

No Memory Engine

No Retrieval

No Search

No Authentication

No API Layer

No Docker

No CI

No Frameworks

No Production Code

Single Python script.

Nothing more.

---

# Test Dataset

Use

5–10 transcripts.

Include

- Short meeting
- Long meeting
- Informal discussion
- Messy transcript
- Ambiguous commitments
- Explicit commitments

If no customer data exists,

use internal meetings or public transcripts.

Never wait for design partners.

---

# Prompt Versioning

Every prompt is versioned.

Example

```
Prompt v1

Prompt v2

Prompt v3

...

Prompt v17
```

Never overwrite prompts.

Every run references exactly one prompt version.

---

# Raw Artifact Storage

Every run stores

```
Transcript

↓

Prompt Version

↓

Raw LLM Response

↓

Validated Objects

↓

Database Records
```

Raw output is never discarded.

It becomes the permanent debugging reference.

---

# Engineering Metadata

Capture every run.

Store

- Model
- Model Version
- Prompt Version
- Schema Version
- Timestamp
- Token Count
- Cost
- Latency
- Validation Errors

This metadata becomes part of the evaluation history.

---

# Evaluation Methodology

Every transcript is evaluated against the Gold Dataset.

Measure

## Precision

How many extracted objects are correct?

---

## Recall

How many expected objects were missed?

---

## False Positives

Objects that do not exist.

---

## False Negatives

Objects that should exist but do not.

---

## Commitment Accuracy

Correct

- Owner
- Recipient
- Obligation
- Deadline
- Status

---

## Evidence Accuracy

Can every Commitment point back to supporting transcript evidence?

---

## Relationship Accuracy

Are extracted relationships correct?

---

# Quality Hierarchy

Optimization follows this order.

Level 1

Valid JSON

↓

Level 2

Correct Objects

↓

Level 3

Correct Relationships

↓

Level 4

Correct Commitments

↓

Level 5

Correct Evidence

Never optimize higher levels before lower ones stabilize.

---

# Logging

Every run records

- Prompt Version
- Validation Failures
- Hallucinations
- Missing Objects
- Cost
- Latency
- Confidence
- Manual Notes

The log is more valuable than the code.

---

# Decision Log

Create

```
DECISION_LOG.md
```

Every architectural decision gets one page.

Examples

Decision 001

Why PostgreSQL?

Decision 002

Why Single Prompt?

Decision 003

Why Commitment First?

Decision 004

Why OKF?

Decision 005

Why No Framework?

This document prevents future architectural drift.

---

# SPIKE_LEARNINGS.md

Maintain continuously.

Example

```
Prompt 8

Deadline extraction weak

Prompt 11

Actor extraction improved

Prompt 17

Hallucinates commitments

Need validation layer

Confidence below expectation
```

This document is the primary deliverable of Week 1.

---

# Week 1.5 — Evaluation & Iteration

The midpoint of the spike.

Run the pipeline against the Gold Dataset.

Compare

```
Gold Dataset

↓

Pipeline Output

↓

Evaluation Metrics

↓

Prompt Improvements
```

Repeat until exit criteria are satisfied.

This is where engineering learns.

Not during Week 2.

---

# Week 2 — Freeze Understanding v0.1

Only if Week 1 exit criteria are met.

Do not freeze guesses.

Freeze observed behavior.

---

# Freeze

## Understanding Pipeline v0.1

Document

- Inputs
- Outputs
- Validation Rules
- Retry Logic
- Error Handling
- Confidence Metadata

Only include behavior observed during the spike.

Nothing hypothetical.

---

## Freeze Schema v0.1

Revise the Week 0 Thin Data Model.

Only change fields proven necessary.

Freeze

- Knowledge Objects
- Database Schema
- Relationships

---

## Freeze Service Contracts

Capture

↓

Understanding

↓

Memory

Define

- API Contracts
- Pydantic Models
- Event Contracts

---

## Repository

Now create

- FastAPI Skeleton
- Docker
- CI
- Basic Project Structure

Not before.

---

# Week 3+

The spike ends.

It is not extended.

It is not maintained in parallel.

It becomes historical reference.

Development now follows the Technical Build Master Plan v1.2.

---

# Handoff

Engineering proceeds with

Commitment Detection

↓

Trust Attribution

↓

Memory Formation

↓

Consultant

using the frozen Understanding Pipeline v0.1.

---

# One Rule For The Entire Plan

If any activity begins producing

- permanent architecture
- production code
- comprehensive documentation
- generalized frameworks

before its scheduled week,

stop immediately.

Scope has expanded.

Return to the learning objective.

---

# Definition of Success

At the end of this spike,

the team should know—not assume—

- how transcripts become Knowledge Objects
- how reliable commitment extraction is
- where the pipeline fails
- what metadata is actually useful
- what schema survives contact with real data
- what should become Understanding Pipeline v0.1

The output of this spike is **engineering knowledge**.

The MVP is built on that knowledge—not on assumptions.