# Open Questions & Technical Architecture Backlog

Consolidated register of every open question and explicit/implicit deferral to Technical Architecture, across the full canonical document set (both pre-grounding and grounded versions) plus Foundational Reasoning V4 and the Theoretical Grounding Phase deliverables. This is a backlog for planning the (paused) Technical Architecture phase — not a summary, and not a design document. **No answers or solutions are proposed here.**

**Scope scanned:** Architecture & Vision (v2.2 and v2.3), Ontology (v1.2 and v1.3), Memory Model (v1.2 and v1.3), Product Architecture (v2.1 and v2.2), Intelligence Architecture (v1.0 and v1.1), Trust & Governance Architecture (v1.0 and v1.1), Foundational Reasoning V4 (including §25), Theoretical Foundations v1.0, OKF_Adoption_Mapping.md. README.md and the (non-existent, in this repo) registry/Experience Master Plan/Build Plan files were excluded per standing instruction.

**Method:** five parallel extraction passes (one per document group), then manual merge, deduplication, contradiction-check, and staleness-check across all results. Source citations below are compressed (doc + section) — exact wording is available in the cited section of the named document.

---

## 1. Summary Table

| Category | Count | Highest-Priority Items |
|---|---|---|
| INFRASTRUCTURE | 12 | Storage/database substrate choice (**BLOCKING**); deployment model — hosted SaaS vs. self-hosted/VPC (**BLOCKING**); AI/model stack (SEQUENCE); permission/identity/auth systems (SEQUENCE); audit log storage (SEQUENCE) |
| ALGORITHM / METHOD | 16 | Confidence scoring formula (SEQUENCE); conflict-resolution tie-break mechanics (SEQUENCE); Formation Routing decision logic (SEQUENCE); relevance-ranking algorithm (SEQUENCE); drift evidence-threshold mechanics (SEQUENCE) |
| DATA MODEL / SCHEMA | 5 | Ontology object storage & versioning schema (SEQUENCE); Commitment/Learning Memory technical schema (SEQUENCE); Knowledge Object requirement operationalization (SEQUENCE) |
| INTEGRATION | 3 | MCP Surface protocol implementation (SEQUENCE); Brain-to-Brain Interoperability mechanics (DEFERRABLE); OKF export/import implementation (DEFERRABLE) |
| GOVERNANCE MECHANICS | 3 | Delegation enforcement/real-time scope-validation (SEQUENCE); approval routing by role (DEFERRABLE); learning-candidate validation routing (DEFERRABLE) |
| COST / PERFORMANCE | 1 | Challenge cost/rate-limiting (DEFERRABLE) |
| BUSINESS / PRODUCT | 2 | Deployment/hosting model's business implications (cross-ref'd from Infrastructure #12); Knowledge Representation Explorer feature timing (DEFERRABLE) |
| UNCATEGORIZED | 2 | "What does an autonomous Company Brain look like?"; SECI's three unimplemented modes (boundary, not backlog) |
| **TOTAL** | **44** | — |

**BLOCKING: 2. SEQUENCE: 20. DEFERRABLE: 20. UNCATEGORIZED (not prioritized): 2.**

**Contradictions found: 0 hard contradictions** (no two documents assert different constraints on the same decision). **2 notable tensions/gaps** flagged per explicit instruction — see §3. Neither rises to a formal contradiction; both are reported honestly as directional leans / silences rather than forced into a false conflict.

---

## 2. Full Register

### INFRASTRUCTURE (12)

1. **Storage/database substrate choice** (relational / graph / vector / hybrid) — **BLOCKING**
   Sources: Architecture & Vision v2.2 §1 / v2.3 §1 ("does not define Databases... Infrastructure"); Ontology v1.2 §2, §8 / v1.3 §2, §8 ("Storage Technology" excluded); Memory Model v1.2 §1 / v1.3 §1 ("Does not define: Databases, Storage engines, Graphs, Vectors, Schemas, Infrastructure"); Product Architecture v2.1 §16 / v2.2 §16; Foundational Reasoning Ch.0/Ch.22 ("How should organizational reality be represented technically (storage, schema, versioning)?" — Open).
   Plain language: every document explicitly excludes storage technology from its own scope and points to Technical Architecture. No relational/graph/vector/hybrid decision has been made anywhere in the set.

2. **Deployment model** (hosted SaaS vs. self-hosted / on-premise / VPC, data ownership) — **BLOCKING**
   Sources: absence across the entire document set — no document (old or new version) contains any language on this. See §3 for the specific cross-check requested.
   Plain language: nobody has stated whether Company Brain runs as a shared SaaS product, a dedicated per-customer instance, or a self-hosted/VPC deployment. This affects security architecture, multi-tenancy, and business model simultaneously — high-leverage, unaddressed.

3. **Vector infrastructure** (embeddings store, similarity search) — SEQUENCE
   Sources: Intelligence Architecture v1.0/v1.1 Part 19 Future Boundaries ("Vector Infrastructure"), Out Of Scope ("Vector Databases," "Embeddings").

4. **Graph infrastructure** — SEQUENCE
   Sources: Intelligence Architecture v1.0/v1.1 Part 19 Future Boundaries ("Graph Infrastructure").

5. **AI/model stack** (reasoning engines, model selection, prompting, fine-tuning, RAG, LLMs) — SEQUENCE
   Sources: Intelligence Architecture v1.0/v1.1 Out Of Scope and Part 19; Foundational Reasoning Ch.20 ("models, LLMs, embeddings, vectors, prompts, fine-tuning, RAG, databases, inference infrastructure — all deferred again to Technical Architecture").

6. **Agent runtime infrastructure** — SEQUENCE
   Sources: Intelligence Architecture v1.0/v1.1 Part 19 and Out Of Scope ("Agent Runtime"); Ontology's Ontology Boundary ("Agent Protocols" excluded).

7. **Retrieval systems infrastructure** — SEQUENCE
   Sources: Intelligence Architecture v1.0/v1.1 Part 19.

8. **Execution infrastructure** — DEFERRABLE
   Sources: Intelligence Architecture v1.0/v1.1 Part 19.

9. **Permission / identity / authentication systems** — SEQUENCE
   Sources: Trust & Governance v1.0/v1.1 Part 16 Future Boundaries and Out Of Scope ("Permission Systems," "Identity Systems," "Authentication").

10. **Compliance / security architecture / encryption** — SEQUENCE
    Sources: Trust & Governance v1.0/v1.1 Part 16 and Out Of Scope ("Compliance," "Security," "Encryption," "Security architecture").

11. **Access control implementation** (RBAC/ABAC as actual enforced code, not vocabulary) — SEQUENCE
    Sources: Trust & Governance v1.0/v1.1 Part 16 and Out Of Scope ("RBAC implementation," "Access Control Implementation"). Note: RBAC/ABAC *vocabulary* is grounded (Theoretical Foundations Field 13/11-adjacent) — only the actual enforcement mechanism is open.

12. **Audit log storage/query mechanics** — SEQUENCE
    Sources: Trust & Governance v1.0/v1.1 Document Control "Still Open," Part 12 Auditability, Part 16 Future Boundaries — appears three times within the same document across both versions, consistently unresolved.

---

### ALGORITHM / METHOD (16)

1. **Confidence scoring formula/weights** — SEQUENCE
   Sources: Intelligence Architecture v1.0/v1.1 Document Control "Still Open," Part 13, Part 19 Future Boundaries. Note: the *conceptual* confidence model (levels, asymmetric handling by output type) is fully defined — only the quantitative formula is open. Theoretical Foundations Field 13-adjacent flags calibration/Brier-score vocabulary as the eventual grounding source, explicitly not applied yet.

2. **Drift severity / evidence-threshold calculation mechanics** — SEQUENCE
   Sources: Intelligence Architecture v1.0/v1.1 Part 10 ("requires confidence ≥ Medium" — threshold named, not quantified); Memory Model v1.2/v1.3 §12 (Drift Detection pipeline explicitly has "no academic or industry equivalent found," is "Company Brain's own engineering").

3. **Time Window review-trigger timing/frequency** — DEFERRABLE
   Sources: Intelligence Architecture v1.0/v1.1 Document Control "Still Open," Part 19.

4. **Adaptive Learning repetition count/window** — DEFERRABLE
   Sources: Intelligence Architecture v1.0/v1.1 Document Control "Still Open," Part 14, Part 19.

5. **Conflict-resolution tie-break mechanics** (incl. whether CRDT/eventual-consistency patterns apply) — SEQUENCE
   Sources: Memory Model v1.3 Document Control "Still Open" (explicitly names CRDT/eventual-consistency literature as the natural parent, deferred); OKF_Adoption_Mapping.md §3 ("tie-break rules" deferred to Memory Model + Trust & Governance). **Note:** this item's *shape* changed between v1.2 and v1.3 — see §4 Staleness Check.

6. **Formation Routing decision logic** (which memory type(s) a signal writes to, beyond the one worked example given) — SEQUENCE
   Sources: Memory Model v1.2/v1.3 §5.

7. **Relevance-driven retrieval/ranking algorithm** — SEQUENCE
   Sources: Memory Model v1.2/v1.3 §15 Retrieval Principles ("relevance-driven, not storage-driven" — no scoring method given).

8. **Context Assembly bounding/ranking algorithm** — SEQUENCE
   Sources: Intelligence Architecture v1.0/v1.1 Part 5 (Context Package — "a bounded set of memories," bounding method unspecified).

9. **Risk/Opportunity pattern-detection and scoring/weighting** — SEQUENCE
   Sources: Intelligence Architecture v1.0/v1.1 Parts 7–9 (sources listed, no weighting or threshold logic).

10. **Simulation Mode scenario-generation and outcome-comparison mechanics** — DEFERRABLE
    Sources: Product Architecture v2.1/v2.2 §11 Consultant; Intelligence Architecture Part 6.

11. **Understanding Layer extraction algorithm** (how raw activity becomes structured primitives, mechanically) — SEQUENCE
    Sources: Architecture & Vision v2.2/v2.3 §9 (responsibilities stated as a list of WHAT to identify, no HOW).

12. **Intelligence Layer general reasoning/pattern-detection algorithm** — SEQUENCE
    Sources: Architecture & Vision v2.2/v2.3 §11.

13. **Confidence decay formula** (rate of decrease over time) — DEFERRABLE
    Sources: Intelligence Architecture v1.0/v1.1 Part 15.1; Memory Model v1.2/v1.3 §7 Decay Path.

14. **Escalation trigger thresholds** ("sufficient evidence" for mandatory vs. discretionary escalation) — DEFERRABLE
    Sources: Intelligence Architecture v1.0/v1.1 Part 6 Failure Handling.

15. **Challenge resolution mechanics** (what evidence causes a Challenge to succeed) — DEFERRABLE
    Sources: Trust & Governance v1.0/v1.1 Part 7.

16. **Decay-check trigger mechanism** (time-based vs. query-triggered) — DEFERRABLE
    Sources: Memory Model v1.2/v1.3 Document Control "Still Open"; Foundational Reasoning Ch.0/Ch.22 ("What triggers a decay check — time-based or query-triggered?" — Open, unchanged).

---

### DATA MODEL / SCHEMA (5)

1. **Relationship coverage / exhaustive schema** — DEFERRABLE
   Sources: Ontology v1.2 §6 / v1.3 §6 (identical wording both versions: "a representative set, not an exhaustive schema... will be added as Memory Model defines storage and traversal requirements").

2. **Ontology object storage and versioning schema** — SEQUENCE
   Sources: Ontology v1.2/v1.3 Document Control "Still Open" ("Storage and versioning schema for ontology objects — explicitly out of scope for this conceptual document").

3. **Composite Knowledge Object evolution/versioning mechanics** — DEFERRABLE
   Sources: Ontology v1.2/v1.3 §3 Ownership Boundary ("may evolve as the Ontology evolves" — no migration/versioning mechanics stated).

4. **Knowledge Object requirement operationalization** (what "portable," "versionable," "governed" mean technically) — SEQUENCE
   Sources: Memory Model v1.2/v1.3 §4 Knowledge Object Requirements.

5. **Commitment Memory / Learning Memory technical schema** (state-machine implementation for the two memory types with no external theoretical parent) — SEQUENCE
   Sources: Theoretical Foundations v1.0 Field 5 Bridge (flags both types as needing their own mechanism, one grounded in Field 2, one in Field 7, neither with a ready-made technical schema).

---

### INTEGRATION (3)

1. **MCP Surface protocol implementation details** — SEQUENCE
   Sources: Product Architecture v2.1/v2.2 §5 (tool names like `brain_search`, `brain_recall` are specified conceptually; actual protocol-level implementation is not).

2. **Brain-to-Brain Interoperability technical mechanics** — DEFERRABLE
   Sources: Product Architecture v2.1/v2.2 §5 ("Future Company Brain instances may exchange Canonical Knowledge Objects directly" — HOW is unspecified). Explicitly P3/future-tier in MVP Prioritization.

3. **OKF export/import implementation mechanics** (beyond the field-level mapping already done) — DEFERRABLE
   Sources: OKF_Adoption_Mapping.md (field mapping is now resolved by the grounding phase; the actual serialization/import code is not addressed, correctly, since that's implementation).

---

### GOVERNANCE MECHANICS (3)

1. **Delegation enforcement / real-time scope-constraint validation** — SEQUENCE
   Sources: Trust & Governance v1.0/v1.1 Part 5 (rules stated: delegation cannot exceed granted authority, must be traceable — enforcement mechanism not specified).

2. **Exact approval routing** (who, by role, approves what) — DEFERRABLE
   Sources: Trust & Governance v1.0/v1.1 Document Control "Still Open," Part 16 (explicitly "Technical Architecture or org-config, not architecture").

3. **Learning-candidate validation authority routing** (org-config specifics) — DEFERRABLE
   Sources: Trust & Governance v1.0/v1.1 Part 10 (principle stated — "Owner of the pattern's domain" — exact org-config routing left open).

*(One additional governance item — "single home for trust/governance concerns" — appeared as Open in Foundational Reasoning Ch.22 but is now resolved. Not counted in the live backlog; see §4 Staleness Check.)*

---

### COST / PERFORMANCE (1)

1. **Challenge cost/rate-limiting** (whether disputing a claim needs a cost or rate-limit to prevent abuse) — DEFERRABLE
   Sources: Trust & Governance v1.0/v1.1 Document Control "Still Open" ("Whether Challenge has a cost/rate-limit to prevent abuse — flagged, not resolved"), unchanged across both versions.

---

### UNCATEGORIZED (2)

1. **"What does an autonomous Company Brain look like?"**
   Source: Foundational Reasoning Ch.0/Ch.22 ("Open — not yet addressed at any layer"). Doesn't fit any bucket cleanly — it's a strategic/product-vision question about the end state of the system, not a specific technical, algorithmic, or governance decision. Flagged rather than forced into a category.

2. **SECI's three unimplemented modes** (Socialization, Combination, Internalization)
   Source: Theoretical Foundations v1.0 Field 6. This is not really a deferred *decision* — it's an acknowledged, permanent scope boundary (Company Brain doesn't architect human-to-human tacit knowledge transfer). Included here only because it could be misread as an open item; it isn't a backlog entry in the normal sense.

---

## 3. Contradictions & Tensions (Called Out Separately, Per Instruction)

**Zero hard contradictions found** — no two documents defer the same decision while implying different constraints or answers on it. The register above and the two specific checks below were both examined for this; none qualify as a formal contradiction (two docs actively disagreeing). What follows are two **tensions/gaps**, reported honestly as such rather than inflated into contradictions that aren't really there.

### (a) Infrastructure strategy — does anything lean toward or rule out a "GBrain-style" substrate?

The literal term "GBrain" does not appear anywhere in the document set (confirmed independently by all five extraction passes). No document leans toward or rules out any *named* substrate.

**Tension worth flagging:** the *conceptual* data model is not neutral, even though the documents frame the *infrastructure* choice as fully open. Ontology's Relationship Model (§6) and Memory Model's Memory Relationships (§11) are explicitly grounded in RDF/OWL's subject–predicate–object triple convention ("From/Relationship/To... without relationships, the Brain becomes storage; with relationships, the Brain becomes understanding" — Theoretical Foundations Field 12). That's a graph-shaped conceptual model. Meanwhile, Intelligence Architecture's Part 19 treats "Graph Infrastructure" and "Vector Infrastructure" as two independent, equally-undecided line items, with no acknowledgment that the conceptual model already leans graph-shaped. This isn't a contradiction (a graph-shaped conceptual model can still be implemented on a relational, document, or native graph store), but it is a real, unacknowledged lean — worth surfacing before Technical Architecture treats "graph vs. vector vs. relational" as a clean-slate decision.

### (b) Deployment model — does anything assume hosted SaaS in a way that conflicts with self-hosted/VPC reasoning?

I don't have visibility into the specific prior-session reasoning about enterprise ownership/self-hosting the request refers to — that conversation isn't part of this session's context, so I can only evaluate what's actually in the documents, not cross-check against a chat I can't see.

On the documents alone: **no document assumes or states hosted SaaS**, and none assumes self-hosted/VPC either — deployment model is uniformly and completely absent from the entire set (confirmed independently by all five extraction passes). There is nothing to contradict, because nothing is asserted.

**Soft signal worth flagging:** Product Architecture's Brain-to-Brain Interoperability (§5) describes "Customer ↔ Vendor coordination," "Subsidiary ↔ Parent organization coordination" as *separate Company Brain instances* exchanging data with each other. That framing — distinct instances per organization, exchanging governed objects across a boundary — reads more naturally as a per-tenant/dedicated-instance model (consistent with self-hosted or single-tenant deployment) than as one shared multi-tenant SaaS platform where "instances" wouldn't need to exchange data at all. This is a soft lean in the text, not a stated decision, and not a conflict with anything else — flagged because it's the closest thing to a signal on this question anywhere in the set.

---

## 4. Staleness Check (Grounding-Phase-Touched Items)

Per instruction: confirmed whether any open item's *shape* changed during the grounding phase's theory-first rewrite without its "still open" status being updated to match.

- **Memory Model's Conflict Resolution (§10 / Document Control "Still Open"):** shape changed, status correctly preserved. Pre-grounding (v1.2) deferred this with no named theoretical parent. Post-grounding (v1.3) explicitly names CRDT/eventual-consistency literature as "the natural academic parent" while still correctly deferring the actual citation and mechanics to Technical Architecture (Master Plan §2.3's own instruction). This is the grounding phase doing its job correctly — enriching the deferral with a pointer, not resolving it prematurely. Not a staleness bug.

- **Foundational Reasoning Chapter 22's "Open Questions — Current Status" table: genuinely stale, four rows.** This table was written when Intelligence Architecture and Trust & Governance were "planning stage, not canonical" (per Chapter 0's original framing). Both are now frozen, canonical documents (v1.1 each). Per the document's own append-only rule, Chapter 22's narrative table was correctly left untouched at freeze — but read in isolation, it now overstates what's open:
  - *"How does the Brain reason — generate recommendations, detect risk/opportunity/drift?"* — listed Open, "scoped in Intelligence Architecture v1 planning docs, not yet drafted as canonical." **Now answered conceptually** by Intelligence Architecture v1.1 Parts 6–10. Only the quantitative mechanics remain open (already captured above under ALGORITHM/METHOD items 1–2, 8–9).
  - *"How does Consultant think, per mode?"* — listed Open. **Now answered conceptually** by Intelligence Architecture v1.1 Part 6 and Product Architecture's Consultant Modes section. No open item remains beyond what's already captured.
  - *"How is confidence calculated conceptually?"* — listed Open. **Now answered** by Intelligence Architecture v1.1 Part 13 (levels, asymmetric handling). Only the *formula* is open (captured above).
  - *"How does the Brain's reasoning improve from feedback without self-corrupting on noisy signals?"* — listed Open. **Now answered conceptually** by Intelligence Architecture v1.1 Part 14's Learning Rule (Observation ≠ Learning; Repeated Validated Feedback = Learning). Only the exact repetition count/window is open (captured above).
  - *"Where do scattered trust/governance concerns get a single home?"* — listed Open, "Trust & Governance Architecture identified as needed, not yet started." **Fully resolved** — Trust & Governance Architecture v1.1 exists, is canonical, and its own Document Control explicitly states it closes this exact question. This row should read Closed.

  None of these four are counted as live backlog items above — the register reflects their *actual* current (quantitative-mechanics-only) status, not Chapter 22's stale framing. Flagged here so the discrepancy between the narrative chapter and the actual document set is visible, not silently absorbed.

- **No other staleness found.** The remaining open items (storage substrate, deployment model, RBAC implementation, audit mechanics, etc.) read identically in pre-grounding and grounded versions — the theory-first rewrite added citations and exposition around them without changing their shape or status.

---

## 5. Business / Product Sub-List (Separate Owner — Not Technical Backlog)

1. **Deployment/hosting model's business dimension** — cross-referenced from Infrastructure item #2. The technical question (SaaS vs. self-hosted/VPC) has a business twin (pricing model, enterprise contract terms, data-ownership commitments) that isn't addressed anywhere in the document set either. Flagged here so it doesn't get treated as purely a Technical Architecture decision.

2. **Knowledge Representation Explorer — feature scope and timing** — Product Architecture v2.1/v2.2 §14, listed as a "Future Capability," and §21 MVP Prioritization places it at P3 (lowest tier). This is a product-prioritization open item, not a technical one — when to build it is a roadmap decision, not an architecture decision.

**No pricing, licensing, or business-model content was found anywhere in the scanned document set.** These are conceptual architecture documents; business-model decisions genuinely don't appear, rather than being deferred with a flag word. Noted explicitly rather than assumed absent.

---

## What This Register Does Not Do

Per instruction: no item above has a proposed answer, resolution, or design attached. Priority flags (BLOCKING / SEQUENCE / DEFERRABLE) reflect only *when* a decision needs making relative to the start of Technical Architecture, not *what* the decision should be. No source document was edited to produce this register.
