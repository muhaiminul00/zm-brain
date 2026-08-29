# COMPANY BRAIN

# Trust & Governance Architecture

## Version 1.1

### Status
Canonical Conceptual Model — Frozen, Grounding Addendum Applied and Approved (Theoretical Grounding Phase, July 2026)

### Depends On
- Architecture & Vision v2.3
- Ontology v1.3
- Memory Model v1.3
- Product Architecture v2.2
- Intelligence Architecture v1.1

---

## Document Control

**Grounding Addendum (this revision)**

Per Master Plan §2.6, this is an addendum, not a content edit — no authority model, lifecycle, or reconciliation decision below changed. Full citation detail: `Company_Brain_Theoretical_Foundations_v1.md`.

**Correction (post-review-pass):** Part 4's PROV-O mapping originally assigned one term per architectural layer (`wasGeneratedBy`→Memory, `wasDerivedFrom`→Intelligence, `wasAttributedTo`→Execution). This was loose against PROV-O's actual semantics — `wasGeneratedBy` relates an entity to an *activity*, not to an agent, so assigning it to answer "who asserted" conflated the two. Retightened to map per *question* instead of per *layer* (`wasAttributedTo`=who, `wasGeneratedBy`=when/by what process, `wasDerivedFrom`=from what source), applied consistently across all three layers, and mirrored in Memory Model v1.3 §8 so the two documents no longer state the mapping differently.

- Part 3 (Trust Object Model) — Claim and Evidence grounded in W3C PROV-O; Approval, Exception, and Delegation grounded in standard access-control literature (RBAC/ABAC, NIST). Fit: Clean.
- Part 4 (Provenance Architecture) — direct PROV-O alignment, mapped per-question (see Correction above). This is the strongest single rename opportunity in this document, per Master Plan §2.6. Fit: Clean.
- Part 5 (Authority Model / Delegation / Revocation) — grounded in RBAC/ABAC standard delegation vocabulary. Fit: Clean.
- Part 6 (Governance Lifecycle) — optionally grounded in generic ITIL-style change-management approval lifecycles (Proposed→Reviewed→Approved→Executed→Audited is a standard shape). Low priority per Master Plan §2.6 — already clear without the citation, included for completeness.
- Parts 7–8 (Challenge Authority / Human Oversight) — grounded in the same human-in-the-loop / human-on-the-loop / human-out-of-loop taxonomy already applied to Product Architecture's Three-Tier Boundary (Product Architecture v2.2 §15). Master Plan §2.6 flags this as the same idea described twice with different words across the two documents — this addendum notes the shared vocabulary explicitly rather than introducing a new one.
- All other Parts remain **KEEP** — original synthesis, no citation forced.
- **Exposition rewrite (this pass):** every callout above rewritten from citation-then-mention into theory-first exposition — each source theory stated plainly on its own terms, then bridged explicitly to what this document implements, extends, or (for Governance Lifecycle and the plain tier names) deliberately keeps in Company Brain's own words instead.

**Why This Document Exists**
Trust-related concerns were scattered with no single owner across Architecture & Vision, Memory Model, Product Architecture, and Intelligence Architecture. This document is the policy, authority, and lifecycle layer that unifies them — it does not redefine concepts that already have a canonical home.

**Fixed During Planning Review Pass**
- "Human Oversight" categories were a renamed copy of Product Architecture's Three-Tier Boundary System. Collapsed into one system. (Part 8)
- "Challenge Architecture" lifecycle had no reference to Memory Model's Conflict Resolution or Product Architecture's Conflict Experience. Reconciled by division of responsibility. (Part 7)
- "Adaptive Learning Governance" restated Intelligence Architecture Part 14 near-verbatim. Reduced to the one gap Intelligence Architecture left open: approval authority. (Part 10)
- "Governance Model" lifecycle risked becoming a fourth parallel approval system. Reframed as the general case the others instantiate. (Part 6)
- "Trust Lifecycle" had no stated bearer. Bound to the Claim object. (Part 13)
- "Exception" had no relationship to Policy Violation / Drift Signal. Defined as their formal closure path. (Part 3)
- "Agent Governance" overlapped with Agent Readiness with no stated distinction. Split into two explicit axes. (Part 9)

**Fixed During Freeze Pass (v1.0)**
- Delegation is named as an Authority source (Part 5) and given Revocation rules, but — unlike Challenge, Approval, Exception, and Escalation — was never given its own Trust Object Lifecycle. Added. (Part 3)
- Revocation Principle's Approval example used "Granted" where the Approval Lifecycle itself uses "Approved" — same state, two names. Normalized to "Approved" throughout. (Part 5)
- Trust Failure Behavior's "Escalate Authority" step referenced escalation generically rather than invoking the Escalation Lifecycle defined in the same update. Cross-referenced explicitly. (Part 12.1)
- Two sequence statements now coexist (conceptual dependency chain vs. actual document build order) with different orderings of Product/Trust. Both kept, explicitly labeled as answering different questions, to prevent future confusion. (Part 17)

**Still Open (deferred on purpose)**
- Exact approval routing (who specifically, by role, approves what) — Technical Architecture or org-config, not architecture
- Audit log storage/query mechanics — Technical Architecture
- Whether Challenge has a cost/rate-limit to prevent abuse — flagged, not resolved

This document's authority model and lifecycles are frozen. This Grounding Addendum adds citations only.

---

# Why This Document Matters

Most AI products stop at Intelligence. Company Brain's differentiation is:

```text
Memory + Intelligence + Trust
```

Organizations don't operate on intelligence alone — they operate on Authority, Permission, Accountability, Responsibility, Traceability, Governance.

---

# Core Question

> How does the Company Brain ensure that memory, intelligence, humans, agents, and automation operate safely, transparently, and accountably?

---

# Purpose

- Architecture & Vision: how the Brain works
- Memory Model: how the Brain remembers
- Intelligence Architecture: how the Brain thinks
- **Trust & Governance: how the Brain can be trusted, and who has the authority to make that so**

---

# Scope Commitments

- Authority — who is allowed to do what, built on Ontology v1.3's Role/Person/Team objects
- Governance Lifecycle — the general-case approval pattern other documents' mechanisms instantiate
- Challenge Authority — who has standing to dispute a claim
- Accountability — bound to Intelligence Architecture's Owner field
- Trust Object Model — Claim, Evidence, Challenge, Approval, Exception, Escalation, Delegation, each with a lifecycle
- Human Oversight Authority — the authority logic underlying the Three-Tier Boundary
- Agent Governance — Authority axis, distinct from Agent Readiness
- Adaptive Learning Approval Authority — who validates a learning candidate
- Auditability
- Trust Lifecycle — bound to the Claim object
- Delegation Boundary, Revocation, and Trust Failure principles

---

# Out Of Scope

```text
Authentication
RBAC implementation
Encryption
Security architecture
Compliance controls
Infrastructure permissions
Approval routing by specific role/individual
Audit log storage mechanics
```

These belong to Technical Architecture (or org-specific configuration).

---

# Part 0 — Reconciliation Table

| Concept | Canonical Owner | This Document's Role |
|---|---|---|
| Provenance fields | Memory Model v1.3 §7, Intelligence Architecture v1.1 Part 13 | References only |
| Write Governance tiers | Memory Model v1.3 §9 | Supplies the authority model behind the tiers |
| Conflict Resolution (Current/Superseded) | Memory Model v1.3 §10 | Supplies who has standing to dispute |
| Trust Cards (UI) | Product Architecture v2.2 §15 | Supplies what fields a Trust Card must show |
| Three-Tier Boundary | Product Architecture v2.2 §15 | **Single canonical permission system** — authority logic here, UI there |
| Conflict Experience (UI) | Product Architecture v2.2 §17 | Consumes Challenge Authority's rules |
| Confidence, Ownership, Review Trigger | Intelligence Architecture v1.1 Parts 13, 15 | References only |
| Agent Readiness | Intelligence Architecture v1.1 Part 12 | Distinguished from Agent Authority, defined here |
| Adaptive Boundary + write-path | Intelligence Architecture v1.1 Part 14 | References; adds only the approval-authority gap |
| Knowledge Exchange Governance | Product Architecture v2.2 | References; supplies underlying authority/provenance rules |

---

# Part 1 — What Is Trust?

> Trust is the confidence that organizational memory, intelligence, agents, and actions are accurate, explainable, accountable, and governed.

---

# Part 2 — Trust Philosophy

- **Trust Is Visible** — cannot be hidden
- **Trust Requires Provenance** — every important claim needs evidence
- **Trust Requires Accountability** — every action needs an owner
- **Trust Requires Explainability** — every recommendation requires reasoning
- **Trust Requires Challenge** — truth must be disputable
- **Trust Requires Human Authority** — humans remain the final authority

---

# Part 3 — Trust Object Model

### Theoretical Grounding

Two different bodies of standard vocabulary ground this model, each covering a different half of it. The W3C's PROV-O formally distinguishes entities (things), activities (processes that produce or use entities), and agents (who's responsible) — Claim and Evidence below implement that vocabulary directly: a Claim is an entity's assertion, Evidence is the entity's attribution and derivation trail. Standard RBAC/ABAC access-control literature (as codified by NIST) governs who may authorize, revoke, or except a permission — Approval, Exception, and Delegation below implement that vocabulary directly: each is a defined authorization event with its own lifecycle, not an ad hoc mechanism. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 13 (PROV-O) and Field 11's neighboring access-control literature. Fit: Clean — both halves are direct implementations.

Each object maps onto, rather than duplicates, an existing canonical object (Part 0). Trust Objects are governance objects — not static concepts. A Trust Object's lifecycle governs its *trust state*; it does not replace the underlying Memory or Intelligence lifecycle it concerns.

### Claim
A Memory record or Intelligence Object's assertion, viewed through a trust lens. Not a new stored object. Carries the Trust Lifecycle (Part 13).

### Evidence
The Sources field already present on every Memory record and Intelligence Object. This document defines who may submit Evidence and what authority is required for it to count — it does not add a new field.

### Challenge
A formal dispute against a Claim. Distinct from Memory Model's automatic Conflict Resolution (contradicting records) — Challenge handles disputed-but-not-necessarily-contradicting claims.

**Lifecycle:** Raised → Reviewed → Resolved → Accepted / Rejected

### Approval
An authorization event, instantiated differently per context (Write Governance tier, Three-Tier Boundary gate, Adaptive Learning approval) but governed by one authority model.

**Lifecycle:** Requested → Reviewed → Approved / Rejected → Executed

### Exception
A formally approved deviation. **This is the resolution path for an open Policy Violation or Drift Signal** (Intelligence Architecture Part 15) when the divergence is accepted rather than corrected — closing those objects via Exception rather than Resolved-as-fixed.

**Lifecycle:** Proposed → Reviewed → Approved → Active → Expired / Revoked

### Escalation
A request to raise authority. Defines the authority chain that Intelligence Architecture's confidence-based and readiness-based triggers invoke. Intelligence Architecture decides *when*; this document defines *to whom* and *with what standing*.

**Lifecycle:** Requested → Assigned → Reviewed → Resolved

### Delegation
A transfer of existing authority from one actor to another. Named as an Authority source in Part 5; given its own lifecycle here for consistency with the other five Trust Objects.

**Lifecycle:** Delegated → Active → Revoked / Expired

---

# Part 4 — Provenance Architecture

### Theoretical Grounding

The W3C's PROV-O formalizes provenance through three relations: `wasGeneratedBy` (an entity was produced by a specific activity), `wasAttributedTo` (an entity is the responsibility of a specific agent), and `wasDerivedFrom` (an entity was derived from another entity). This document implements that vocabulary directly, applied per *question* rather than one term per layer — matching how PROV-O's own semantics actually divide, not a loose borrowing: `wasAttributedTo` answers **who** — who asserted a Memory record, who approved or acted in Execution. `wasGeneratedBy` answers **when / by what process** — the capture/understanding activity behind a Memory record, the reasoning activity behind an Intelligence Object, the execution activity itself. `wasDerivedFrom` answers **from what source** — the raw artifact a Memory record traces back to, or the memory records an Intelligence Object treats as evidence. This same per-question mapping is mirrored in Memory Model v1.3 §8, corrected from an earlier draft that had assigned one term per *layer* instead (which conflated `wasGeneratedBy`'s activity-relation with an agent-attribution question). See `Company_Brain_Theoretical_Foundations_v1.md`, Field 13. Fit: Clean — direct implementation, and the strongest single rename opportunity in this document.

Provenance fields are owned by Memory Model v1.3 §7 and Intelligence Architecture v1.1 Part 13 — not redefined here. Every significant object across Memory, Intelligence, and Execution must answer "where did this come from, under what authority":

- Memory: who asserted it (`wasAttributedTo`), when / via what capture-or-understanding activity (`wasGeneratedBy`), from what source (`wasDerivedFrom`)
- Intelligence: what evidence it reasoned over (`wasDerivedFrom`), what reasoning activity produced it (`wasGeneratedBy`), what confidence
- Execution: who approved, who acted (`wasAttributedTo`); the execution activity itself (`wasGeneratedBy`)

---

# Part 5 — Authority Model

### Theoretical Grounding

Role-Based and Attribute-Based Access Control (RBAC/ABAC) formalize authority as something that originates from defined structures — roles, ownership, policy — and can be transferred (delegated) without being created out of nothing, and can be granted or withdrawn (revoked) without disrupting the underlying structure. The Delegation Boundary Principle and Revocation Principle below implement that directly: delegation only redistributes existing authority, never exceeds it, and remains fully traceable; revocation requires equal-or-greater authority than the original grant. See `Company_Brain_Theoretical_Foundations_v1.md`, Field 13 (adjacent access-control literature) and Master Plan §2.6. Fit: Clean — direct implementation.

Authority sources, built on Ontology v1.3's existing Person/Team/Role objects and relationships:

```text
Role
Ownership
Policy
Delegation
Approval
```

Key questions answered by reference to Role/Ownership/Policy — not a new identity system: who can write, who can approve, who can challenge, who can delegate.

## Delegation Boundary Principle

Delegation transfers authority. **Delegation does not create authority.**

**Rule 1:** Delegated authority may never exceed the authority originally granted.

**Rule 2:** Delegation chains must remain traceable — every delegation must answer: who delegated, to whom, when, under what authority.

**Rule 3:** Delegation may be constrained by Policy, Ownership, Three-Tier Boundary, or Approval Conditions.

Authority originates from organizational structures. Delegation only redistributes existing authority.

## Revocation Principle

Authority is not permanent. Approvals, Exceptions, and Delegations may be withdrawn.

**Rule:** Any delegated authority, Approval, or Exception may be revoked by an actor possessing equal or greater authority than the one who granted it.

**Examples** *(state names normalized to match each Trust Object's lifecycle in Part 3):*

```text
Approval:    Approved → Revoked
Exception:   Active → Revoked → Policy Enforcement Restored
Delegation:  Active → Revoked → Authority Returns To Granting Actor
```

Governance must support both granting and withdrawing authority. Authority may expand. Authority may also contract.

---

# Part 6 — Governance Lifecycle (General Case)

### Theoretical Grounding

ITIL-style change management defines a standard shape for any governed change: a request is proposed, reviewed, approved, implemented, and audited afterward — the same shape underlies most formal change-control processes in operations. The lifecycle below implements that general shape directly, in plainer, five-word form (Proposed→Reviewed→Approved→Executed→Audited) rather than ITIL's own more elaborate vocabulary (Request for Change, CAB approval, build, test, implement, post-implementation review) — cited here as a low-priority, optional parallel per Master Plan §2.6, since the plain version is already clear without the ITIL reference doing real explanatory work.

**Vocabulary choice, stated explicitly:** the simpler five-stage names stay rather than adopting ITIL's own terms, because this document's audience needs the general pattern the other three architectures instantiate, not a full change-management vocabulary import.

```text
Proposed → Reviewed → Approved → Executed → Audited
```

This is the general pattern that Memory Model's Write Governance tiers, Product Architecture's Three-Tier Boundary, and Intelligence Architecture's Adaptive Boundary each instantiate as specific, simpler cases:

| Instance | Maps To |
|---|---|
| Memory Writes | Memory Model v1.3 Write Governance (auto/delegated/human = compressed Reviewed→Approved) |
| Agent Actions | Three-Tier Boundary (Always = skips Review/Approval; Ask First = full lifecycle; Never = blocked at Proposed) |
| Policy Changes | Full lifecycle, human-required |
| Learning Updates | Intelligence Architecture's propose-then-govern write path — this document supplies the Approved step's authority |

---

# Part 7 — Challenge Authority

### Theoretical Grounding

The same human-in-the-loop / human-on-the-loop / human-out-of-loop taxonomy grounding Product Architecture's Three-Tier Boundary (Product Architecture v2.2 §15, and Part 8 immediately below) applies here too — standing to challenge is a form of oversight authority, not a separate concept. Master Plan §2.6 identifies that this document's Challenge Authority and Product Architecture's Three-Tier Boundary were, in an earlier draft, describing the same underlying idea with two different vocabularies; this section is unified with Part 8's treatment rather than re-deriving its own. See the "Human-AI Autonomy" entry in `Bibliography.md`.

Principle: no organizational truth is beyond challenge. (Lifecycle defined in Part 3.)

**Division of responsibility:**
- This document: who has standing to raise a Challenge, and under what authority it resolves
- Memory Model v1.3 (Conflict Resolution): how a resolved factual conflict is marked Current/Superseded
- Product Architecture (Conflict Experience): how challenge and resolution are displayed

Applies to: Memory, Recommendations, Risk Assessments, Agent Actions, Policy Interpretation.

---

# Part 8 — Human Oversight Authority

### Theoretical Grounding

Human-AI interaction literature describes autonomy along a standard three-way split: human-in-the-loop (approval required before an action executes), human-on-the-loop (a human monitors and can intervene, but isn't required to approve each instance), and human-out-of-loop (the system acts independently). This document implements that taxonomy directly for the authority logic behind Product Architecture's Three-Tier Boundary (v2.2 §15): Always is pre-authorized (human-out-of-loop), Ask First requires Approval per Part 3 (human-in-the-loop), and Never blocks the action regardless of confidence or readiness — a position the taxonomy itself doesn't name, since it isn't really a loop-position at all. Product Architecture keeps the plain tier names for product-facing use (see that document's own explicit justification, §15); this document supplies the authority reasoning underneath them, using the academic taxonomy directly rather than restating it in different words — the same idea, described once, not twice. See `Bibliography.md`, "Human-AI Autonomy."

**The authority logic behind the existing Three-Tier Boundary System (Product Architecture v2.2 §15) — not a separate categorization.**

| Three-Tier Boundary | Authority Meaning | Autonomy-Taxonomy Equivalent |
|---|---|---|
| Always | Pre-authorized; no per-instance Approval needed | Human-out-of-loop |
| Ask First | Requires Approval (Part 3) before execution | Human-in-the-loop |
| Never | No delegation possible regardless of confidence or readiness | No autonomous path, any position |

This document defines *why* something sits in a tier; Product Architecture defines how it's surfaced and configured.

---

# Part 9 — Agent Governance

Two distinct axes, both required to pass before an agent acts:

| Axis | Question | Owner |
|---|---|---|
| **Agent Readiness** | Can the agent act with sufficient confidence? | Intelligence Architecture v1.1 Part 12 |
| **Agent Authority** | Is the agent allowed to act at all? | This document |

Concepts: Agent Authority · Agent Scope · Agent Boundary (Three-Tier Boundary applied to a specific agent) · Agent Escalation (uses Part 3's Escalation Lifecycle) · Agent Accountability (binds to Intelligence Architecture's Owner field).

An agent can be Ready but lack Authority (Never tier) — must not act. An agent can have Authority but lack Readiness — must escalate per Intelligence Architecture Part 13. See also Part 12.1's Trust-First Rule.

---

# Part 10 — Adaptive Learning Approval Authority

Intelligence Architecture v1.1 Part 14 already defines Observation ≠ Learning, Repeated Validated Feedback = Learning, and that validated learning is proposed to Memory Model's Write Governance rather than written directly. Not restated here.

**The one gap this document closes:** who has authority to validate a learning candidate before it's proposed. Conceptually: the Owner of the pattern's domain (e.g., a Policy's owner validates a candidate that would update that Policy) — using the Authority Model from Part 5, not a separate mechanism.

---

# Part 11 — Trust Surfaces

UI ownership stays with Product Architecture. This document specifies what each surface must be able to show:

- Trust Cards (Product Architecture §15) — Claim, Evidence, Challenge status
- Confidence Indicators — sourced from Intelligence Architecture Part 13
- Provenance View — sourced from Part 4
- Challenge Button — invokes Part 7's authority check
- Approval Requests — invokes Part 6's lifecycle

---

# Part 12 — Auditability

Every significant event must be reconstructable: Who? What? When? Why? Under Which Authority? — answerable by composing Part 4 (Provenance) + Part 5 (Authority) + Part 6 (Governance Lifecycle stage at time of event). Storage/query mechanics deferred to Technical Architecture.

---

# Part 12.1 — Trust Failure Principle

**Purpose:** define system behavior when trust requirements cannot be satisfied.

**Trust failure conditions may include:**
```text
Missing provenance
Conflicting authority
Unresolved challenge
Insufficient evidence
Expired approval
Invalid delegation
Confidence below required threshold
```

**Trust Failure Behavior:**

```text
Disclose Uncertainty
↓
Limit Automation
↓
Escalate Authority — invokes the Escalation Lifecycle (Part 3): Requested → Assigned → Reviewed → Resolved
↓
Request Human Review
```

**Principle:** the Company Brain must never hide uncertainty. Trust failures should reduce autonomy rather than increase risk.

**Relationship To Intelligence Architecture:** low-confidence intelligence affects *reasoning* behavior (Intelligence Architecture Part 13). Trust failure affects *governance* behavior. Related but distinct mechanisms.

**Trust-First Rule:** when Intelligence and Trust disagree —

```text
Trust Overrides Autonomy
```

An agent may be Ready. An agent may not be Authorized. An action may appear beneficial. An action may still be blocked. Trust requirements always take precedence over autonomous execution — this is the same two-axis gate established in Part 9, stated as a tie-break rule.

---

# Part 13 — Trust Lifecycle

**Bound to the Claim object (Part 3).**

```text
Asserted → Verified → Trusted → Challenged → Revalidated
```

A Claim re-enters Challenged whenever a Challenge is raised against it, and exits to either Revalidated (Challenge rejected, confidence restored) or back to Verified at reduced confidence (Challenge accepted, Memory Model's Conflict Resolution executes).

---

# Part 14 — Relationship To Other Architectures

| Layer | What Trust & Governance Supplies |
|---|---|
| Memory | Authority behind Write Governance tiers; Challenge standing behind Conflict Resolution |
| Intelligence | Approval authority for Adaptive Learning; Authority axis alongside Agent Readiness |
| Product | Authority logic behind Three-Tier Boundary and Trust Card contents |
| Execution | Who approved, who acted (Part 4) |
| Exposure | Which Trust Surfaces show which authority state |

---

# Part 15 — Worked Example

```text
Agent recommends policy exception
↓
Agent Readiness check (Intelligence Architecture): confidence High → proceeds
↓
Agent Authority check (this document): action falls in "Ask First" tier → Approval required
↓
Manager (Owner, Part 5 Authority Model) reviews
↓
Manager raises Challenge against the underlying Risk Assessment (Part 7, Challenge Lifecycle)
↓
Challenge Reviewed → Evidence (existing Sources field) re-examined
↓
Challenge Rejected → Claim moves Challenged → Revalidated (Part 13)
↓
Exception formally Proposed → Reviewed → Approved → Active (Part 3) — closes the related Operational Risk via Exception, not Resolved
↓
Memory updated through standard Write Governance (Memory Model v1.3)
↓
Six months later: Exception Expires automatically, or is Revoked by an actor of equal/greater authority (Part 5 Revocation Principle) → Policy Enforcement Restored
↓
Audit trail reconstructable via Part 12
```

---

# Part 16 — Future Boundaries

Deferred to Technical Architecture:
```text
Permission Systems
Identity Systems
Authentication
Compliance
Security
Access Control Implementation
Approval routing by specific role/individual
Audit log storage mechanics
```

---

# Part 17 — Document Sequence

Two sequence statements coexist by design, answering different questions:

**Conceptual dependency chain** (what each layer needs from the one before it):
```text
Reality → Ontology → Memory → Intelligence → Trust → Product → Technical
```

**Actual canonical build order** (the order documents were written; Product Architecture v2.1 predates this document):
```text
Foundational Reasoning → Architecture & Vision → Ontology → Memory Model →
Product Architecture → Intelligence Architecture → Trust & Governance Architecture →
Technical Architecture
```

The conceptual chain explains *why* Trust & Governance leans on Product Architecture's existing UI patterns (Trust Cards, Three-Tier Boundary) without having authored them. The build order is the literal sequence to read or reference.

---

# Final Deliverable Goal

After reading this document, a team member should be able to answer:
- Why should we trust the Brain?
- Who can do what, and on what authority?
- Who approved this? Who challenged this? Why do we believe this?
- How is authority delegated, and how is it taken back?
- What happens when trust requirements can't be met — does the system hide it or surface it?
- When Intelligence says go and Trust says no, which wins?
- How are agents constrained, separately from whether they're confident enough to act?
- Where exactly does this document end and Memory Model / Product Architecture / Intelligence Architecture begin?

---

# Freeze Statement

With Trust Object Lifecycles (including the added Delegation Lifecycle), the Delegation Boundary Principle, the Revocation Principle (terminology normalized against Part 3), the Trust Failure Principle (cross-referenced to the Escalation Lifecycle), and now a Grounding Addendum (PROV-O alignment in Parts 3–4, RBAC/ABAC in Part 5, unified human-in-the-loop vocabulary in Parts 7–8) incorporated and reconciled, and approved by team review, Trust & Governance Architecture v1.1 is frozen as of the Theoretical Grounding Phase freeze, July 2026.

No further Trust & Governance Architecture content revisions are planned before:

```text
Technical Architecture v1
```

Remaining questions are implementation concerns and belong to Technical Architecture or organization-specific configuration (see Document Control, "Still Open").

---

# One-Sentence Summary

Trust & Governance Architecture defines the authority, accountability, provenance, challenge, approval, delegation, revocation, and oversight mechanisms — each with its own governed lifecycle, and a trust-first rule that overrides autonomous execution when intelligence and governance disagree — that allow organizational memory and intelligence to operate safely, transparently, and accountably across humans, agents, and automation, by unifying rather than duplicating what Memory Model, Product Architecture, and Intelligence Architecture already established.
