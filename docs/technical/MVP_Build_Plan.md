# COMPANY BRAIN

# MVP(Prototype) Build Plan

## Version 1.0

## Status
Implementation Planning Document

## Purpose

This document defines the step-by-step technical implementation plan for building the first Company Brain prototype.

This document translates the frozen conceptual architecture into an executable engineering roadmap.

It does not redefine:

- Company Brain architecture
- Ontology
- Memory Model
- Intelligence Model
- Trust Model

Those remain the source of conceptual truth.

Technical implementation must conform to:

- Architecture & Vision
- Ontology
- Memory Model
- Intelligence Architecture
- Trust & Governance Architecture

---

# 1. Build Objective

## Goal

Build the first functional Company Brain prototype capable of:



Organizational Activity


    ↓


Capture


    ↓


Understanding


    ↓


Knowledge Objects


    ↓


Memory Formation


    ↓


Intelligence


    ↓


Human / Agent Consumption



---

# 2. Prototype Scope

The first prototype will NOT attempt to build the full Company Brain.

The goal is proving the core loop:



Raw Company Data

↓

Structured Understanding

↓

Persistent Memory

↓

Reasoning

↓

Useful Answers



---

# 3. Technical Philosophy

## Principle 1

Build the smallest complete Brain loop.

Not isolated components.

The prototype must demonstrate:

Capture → Understanding → Memory → Intelligence


---

## Principle 2

Everything must be traceable.

Every output must answer:

- Where did this come from?
- Why does the system believe this?
- What evidence supports it?
- Which version produced it?


---

## Principle 3

Every experiment must be reproducible.

No manual hidden steps.

Every run should record:



Input

↓

Pipeline Version

↓

Model

↓

Prompt Version

↓

Output

↓

Evaluation



---

# 4. Repository Structure

Initial repository:



company-brain/

│
├── backend/
│
│   ├── api/
│   ├── pipeline/
│   ├── models/
│   ├── database/
│   ├── intelligence/
│   └── evaluation/
│
├── frontend/
│
│   └── streamlit/
│
├── data/
│
│   ├── raw/
│   ├── processed/
│   ├── gold_dataset/
│   └── experiments/
│
├── prompts/
│
│   ├── extraction/
│   ├── reasoning/
│   └── evaluation/
│
├── docs/
│
│   ├── architecture/
│   ├── decisions/
│   ├── experiments/
│   └── logs/
│
├── tests/
│
└── README.md



---

# 5. Development Phases

---

# Phase 0 — Engineering Foundation

## Objective

Create a stable development environment.

## Tasks

### Repository

Create Git repository.

Setup:

- branch strategy
- issue tracking
- documentation structure


---

### Environment

Setup:

- Python environment
- Docker
- Database
- Configuration management


Recommended:

Python

FastAPI

PostgreSQL

Streamlit


---

### Logging System

Create:



logs/

application.log

experiments.log

decisions.log




Every pipeline execution generates logs.

---

# Output

Working engineering foundation.

---

# Phase 1 — Data Foundation

## Objective

Create the first Gold Dataset.

---

# Gold Dataset Strategy

## Decision

Use a simulated organization.

Reason:

A real company dataset creates:

- privacy issues
- incomplete coverage
- inconsistent history

A simulated organization allows:

- controlled reality
- known ground truth
- repeatable evaluation


However:

The dataset should simulate a company, not isolated documents.

---

# Simulated Company Design

Example:



Company:

Acme Robotics

Departments:

Engineering

Sales

Marketing

Finance

Support

Employees:

CEO

CTO

Product Manager

Sales Lead

Engineers

Projects:

Project Alpha

Customer Expansion

Platform Migration

History:

6 months timeline



---

# Dataset Artifact Types

Generate:

## Communication

- Meetings
- Slack conversations
- Emails


## Execution

- Project updates
- Incident reports
- Task completion


## Decision History

- Strategy discussions
- Approvals
- Trade-offs


## Customer Context

- Sales calls
- Feedback
- Complaints


## Operational Knowledge

- SOP discussions
- Policy changes


---

# Gold Annotation

Each artifact receives expected outputs:

Example:

Input:

Meeting Transcript


Expected:

Actors:

John

Sarah


Commitments:

John → Deliver API by Friday


Goal:

Launch customer beta


Reasoning:

API delay risk


---

# Output

Gold Dataset v1.0

---

# Phase 2 — Capture Layer

## Objective

Convert raw data into normalized inputs.


Build:



Document Loader

↓

Normalizer

↓

Source Object




Supported:

- txt
- markdown
- pdf
- json


---

# Phase 3 — Understanding Layer

## Objective

Convert raw activity into Knowledge Objects.


Pipeline:



Source

↓

LLM Extraction

↓

Primitive Objects

↓

Composite Objects

↓

Validation




---

# First Object Types

Implement:



Actor

Communication

Commitment

Action

Goal

Resource

Relationship




---

# Validation

Every object requires:



id

type

source

timestamp

confidence

evidence




---

# Phase 4 — Memory Layer

## Objective

Persist organizational memory.


Implement first:

## Factual Memory

People

Teams

Projects


## Interaction Memory

Meetings

Discussions


## Commitment Memory

Promises

Tasks

Ownership


## Action Memory

Completed work


Learning Memory comes later.


---

# Phase 5 — Memory Database

## Initial Schema


Tables:



sources

actors

communications

commitments

actions

goals

relationships

memory_records

provenance




---

# Phase 6 — Intelligence Layer

## Objective

Answer questions using memory.


First capability:

Company Consultant


Example:

Question:

"What did we promise Customer X?"


Pipeline:



Question

↓

Context Assembly

↓

Memory Retrieval

↓

Reasoning

↓

Answer

↓

Evidence




---

# Phase 7 — Trust & Provenance

## Objective

Make every answer explainable.


Every answer must show:




Answer

Confidence

Sources

Reasoning Path




---

# Phase 8 — Evaluation Framework

## Objective

Measure improvement.


Metrics:


## Extraction

- Precision
- Recall


## Memory

- Correctness
- Completeness


## Intelligence

- Answer accuracy
- Evidence quality


## Trust

- Unsupported claims
- Hallucination rate


---

# Phase 9 — Streamlit Prototype

## Objective

Create first user interface.


Screens:

---

## Upload

Input company artifacts.


---

## Brain View

Show:

People

Projects

Commitments


---

## Consultant

Ask:

"What happened?"

"What changed?"

"Who owns this?"


---

## Evidence View

Show:

Source

Reasoning

Confidence


---

# Phase 10 — Prototype Completion Criteria

Prototype succeeds when:

A user can:

1. Upload company information

2. System understands it

3. Creates structured knowledge

4. Remembers relationships

5. Answers organizational questions

6. Shows evidence


---

# 6. Engineering Documentation System

Every development activity must update:

---

# Daily Engineering Log

File:



docs/logs/daily_log.md




Template:



Date:

Goal:

Implemented:

Changed:

Problems:

Decisions:

Next Steps:




---

# Architecture Decision Record

File:



docs/decisions/ADR-XXX.md




Template:



Decision:

Context:

Options:

Chosen:

Reason:

Tradeoffs:




---

# Experiment Record

File:



docs/experiments/EXP-XXX.md




Template:



Experiment:

Objective:

Dataset:

Model:

Prompt Version:

Result:

Evaluation:

Learning:




---

# 7. First Technical Milestones

## Milestone 1

Environment Ready

---

## Milestone 2

Gold Dataset v1

---

## Milestone 3

Extraction Pipeline Working

---

## Milestone 4

Knowledge Objects Generated

---

## Milestone 5

Memory Database Working

---

## Milestone 6

Consultant Query Working

---

## Milestone 7

Evaluation Framework Working

---

## Milestone 8

Prototype Demo Ready


---

# Final Engineering Rule

Never build features before answering:

1. What Company Brain concept does this implement?

2. Which document owns this concept?

3. How will we evaluate it?

4. How will we know it improved?

Every technical decision must leave a trace.


---
