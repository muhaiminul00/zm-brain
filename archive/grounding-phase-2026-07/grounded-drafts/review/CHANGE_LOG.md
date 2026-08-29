# Change Log — Grounding Phase

One line of change tracking, not a diff. For each of the six grounded drafts, in Master Plan §2 order: section → what was added → source cited. Nothing in this phase changed what any layer does — only citations, framing, and (in two cases) factual governance language. Cross-reference: `Company_Brain_Theoretical_Foundations_v1.md` for full citation detail, `COVERAGE_CHECK.md` for confirmation every row below was actually required by the Master Plan.

---

## Exposition Rewrite (Team-Review Second Pass)

The team review verdict on the first pass: it passed the complexity/vocabulary goal, but the grounding *approach* needed restructuring before freeze. The first pass cited theory alongside existing text ("here's a paper that relates to this"). This pass rewrites every GROUND callout across all six documents and all 13 fields in `Company_Brain_Theoretical_Foundations_v1.md` into a **theory-first-then-bridge** structure instead: the source theory is stated plainly, standalone, in language a reader with zero Company Brain context could follow — then bridged explicitly to Company Brain's architecture as one of three stated relationships: **we implement this directly**, **we extend this to handle something the theory didn't anticipate**, or **we diverge from this, and here's why**. No relationship is left for the reader to infer.

**No citation was re-verified and no architectural decision changed in this pass** — this is exposition only, per the team's explicit instruction.

**Four priority fields, rewritten with the fullest theory-first treatment as the fields with the strongest actual relationship to the architecture:**

1. **Organizational Memory Theory (Walsh & Ungson, 1991) → Memory Model, full document.** Strongest single implementation in the package for the core "what is memory" definition (Memory Model §3); explicit, deliberate divergence on the five-type taxonomy, stated as a design choice rather than a gap.
2. **Enterprise Ontology / DEMO (Dietz, 2006/2020) → Ontology, full document.** Master Plan §2.2's own assessment — DEMO is a near-complete parent for this document — is now demonstrated in the exposition itself (Ontology §2), not just asserted in a citation.
3. **Viable System Model (Beer, 1972/1979/1985) → Architecture & Vision, 7-layer pipeline.** Section 7's rewrite leads with Beer's five-subsystem model stated in full, then the compression result (5 of 7 layers implement it directly, 2 extend it) — the exact "we adopt X and extend it with Y" pattern the master plan's original VSM Compression Test already modeled, now applied at the document level, not just in the standalone Theoretical Foundations doc.
4. **Argyris & Schön double-loop learning (1978/1996) → Drift Detection + Learning Memory.** Memory Model §12 now explicitly separates *why* the drift gap opens (Weick) from *how* it closes (Argyris & Schön), rather than citing both in one line; Architecture & Vision §14 and §16 carry the same split.

**Vocabulary pass, run separately from the exposition rewrite:** every term in the Master Plan's rename-candidate list was checked against the actual drafts, not just the table. One genuine swap was made: "ostensive-versus-performative gap" (Architecture & Vision §11, Ontology §3) → "designed-versus-executed gap," aligning it with the plain-language term already used consistently elsewhere in the document set (Ontology's SOP/Workflow disambiguation, Product Architecture's Drift Experience) — same DEMO grounding, no meaning lost. Five terms were kept as Company Brain's own with the reasoning stated explicitly rather than silently retained: Three-Tier Boundary's plain tier names (Product Architecture §15, Trust & Governance Part 8), the five Memory Type names (Memory Model §6), the Relationship Model's From/Relationship/To columns (Ontology §6, Memory Model §11), Write Governance (Memory Model §9), and the Governance Lifecycle's five-word stage names (Trust & Governance Part 6). Full reasoning for each: `Company_Brain_Theoretical_Foundations_v1.md`, Appendix.

**`One_Pager.md` and `RECOGNIZABILITY_TEST_SHEET.md`:** checked against every term touched by the vocabulary pass — no rebuild needed. The one actual swap (ostensive/performative) doesn't appear in either file, and the five KEEP-JUSTIFIED additions are new stated reasoning for existing names, not renamed terms.

---

## Post-Review-Pass Fixes (applied after the first consistency check)

Two items surfaced by the first `CONSISTENCY_CHECK.md` were fixed before this package went further. Both are now closed — see the re-run consistency check for verification detail.

1. **PROV-O per-question retightening.** Trust & Governance v1.1 Part 4 originally assigned one PROV-O term per architectural *layer* (`wasGeneratedBy`→Memory, `wasDerivedFrom`→Intelligence, `wasAttributedTo`→Execution) — loose against PROV-O's actual semantics, since `wasGeneratedBy` relates an entity to an *activity*, not to the agent who asserted it. Retightened to map per *question* instead (`wasAttributedTo`=who, `wasGeneratedBy`=when/by what activity, `wasDerivedFrom`=from what source), applied consistently across Memory, Intelligence, and Execution. The same mapping was mirrored into Memory Model v1.3 §8, which previously only listed the three terms generically without a specific assignment. Both documents' Document Control sections now carry a "Correction (post-review-pass)" note. Affected: `Company_Brain_Memory_Model_v1.3.md` §8, `Company_Brain_Trust_&_Governance_Architecture_v1.1.md` Part 4.
2. **Version-number hygiene.** `OKF_Adoption_Mapping.md` and `Company_Brain_Theoretical_Foundations_v1.md` were written before the rename pass and still cited the six living documents by their pre-rename version numbers throughout. Every occurrence replaced: Architecture & Vision v2.2→v2.3, Ontology v1.2→v1.3, Memory Model v1.2→v1.3, Product Architecture v2.1→v2.2, Intelligence Architecture v1.0→v1.1, Trust & Governance Architecture v1.0→v1.1. Re-grepped after the fix — zero stale references remain in either file.

---

## Architecture & Vision v2.2 → v2.3

| Section | What Changed | Source Cited |
|---|---|---|
| §2 The Problem | Added citation callout — "fragmented memory" framed as an instance of established organizational-information-processing theory | March & Simon (1958); Galbraith (1977); Walsh & Ungson (1991) |
| §3 What Is A Company Brain | Added citation callout — "living organism" framing | Beer (1972, 1979, 1985) |
| §4 Organizational Reality | Added citation callout — "coordination systems" vocabulary | Winograd & Flores (1986); Dietz (2006, 2020) |
| §5 Atomic Primitives | Added citation callout — Key Question column framed as Zachman's interrogatives | Zachman (1987); TOGAF 10th Ed.; Dietz/DEMO |
| §6 Core Principles | Added citation callout on Principle 5 and Principle 7 only. Principle 8 explicitly left uncited (KEEP) | Zero Trust literature (Principle 5); Argyris & Schön (1978, 1996) (Principle 7) |
| §7 Seven-Layer Pipeline | Added citation callout — pipeline framed as VSM specialization; Memory/Exposure flagged as the extension VSM doesn't cover | Beer (1972, 1979, 1985) |
| §8 Capture Layer | Added citation callout — pre-Externalization framing | Nonaka & Takeuchi (1995) |
| §9 Understanding Layer / Knowledge Objects | Added citation callout — sensemaking + SECI Externalization; Gruber's ontology definition; **OKF terminology updated** — "Open Knowledge Format (OKF)" now means Google Cloud's real v0.1 spec, not an internal placeholder | Weick (1979, 1995); Nonaka & Takeuchi (1995); Gruber (1993); Google Cloud OKF v0.1 (2026) |
| §10 Memory Layer / Commitment Lifecycle | Added citation callout — Memory definition; Commitment Lifecycle framed as extension of the conversation-for-action loop | Walsh & Ungson (1991); Winograd & Flores (1986) |
| §10 Memory Architecture (5 types) | Added citation callout — 3 of 5 types map to cognitive-science taxonomy, 2 (Commitment, Learning) explicitly do not and keep their names | Tulving (1972); Squire (2004); Anderson/ACT-R |
| §11 Intelligence Layer | No citation added — explicitly KEEP, no parent found | — |
| §12 Execution Layer | Added light citation callout — performa/informa/forma distinction | Dietz/DEMO (2006, 2020) |
| §13 Exposure Layer | Added citation callout (VSM extension) + **updated governance language**: MCP is now stewarded by the Agentic AI Foundation (Linux Foundation), not solely Anthropic | Beer (VSM extension); verified MCP/Agentic AI Foundation fact |
| §14 Evolution Layer | Added citation callout — Drift→Learning Memory pipeline framed as double-loop learning | Argyris & Schön (1978, 1996) |
| §15 Trust System | Added citation callout — provenance/versioning fields framed with PROV-O terms | W3C PROV-O |
| §16 Organizational Learning Loop | Added citation callout | Argyris & Schön (1978, 1996); Nonaka & Takeuchi (1995) |
| §17–18 Relationship to Products / Long-Term Vision | No citation added — explicitly KEEP | — |

---

## Ontology v1.2 → v1.3

| Section | What Changed | Source Cited |
|---|---|---|
| §2 Ontology Philosophy | Added citation callout — "abstracted from implementation" framed as DEMO's own stated purpose; **OKF terminology updated** in Open Knowledge Compatibility subsection | Dietz (2006, 2020); Google Cloud OKF v0.1 (2026) |
| §3 Ontology Layers | Added citation callout (heavy) — four-layer structure framed as parallel to DEMO's Cooperation/Action/Process/Fact Model split | Dietz (2006, 2020); Zachman (1987) |
| §3 Layer 4 (Policy/SOP/Workflow) | Added light citation callout — ostensive/performative distinction | Dietz/DEMO (coordination-act vs. production-act) |
| §4 Context Model | Added citation callout — Context-as-emergent framed as sensemaking/enactment | Weick (1979, 1995); Austin (1962); Searle (1969) |
| §5 Organizational Memory Mapping | Added citation callout | Walsh & Ungson (1991) |
| §6 Relationship Model | Added citation callout — From/Relationship/To table framed as RDF-style triples | W3C RDF/OWL |
| §7 Derived Intelligence Objects | No citation added — explicitly KEEP | — |
| §8 Ontology Boundary | No citation added — explicitly KEEP | — |

---

## Memory Model v1.2 → v1.3

| Section | What Changed | Source Cited |
|---|---|---|
| §3 What Is Memory? | Added citation callout — definition upgraded from assertion to established theory | Walsh & Ungson (1991) |
| §4 Knowledge Representation | Added citation callout for Gruber; **OKF terminology updated** — internal "OKF" now means Google Cloud's real v0.1 spec directly, cross-referenced to `OKF_Adoption_Mapping.md` | Gruber (1993); Google Cloud OKF v0.1 (2026) |
| §5 Formation Routing | No citation added — explicitly KEEP | — |
| §6 Memory Types | Added citation callout (partial, by design) — 3 of 5 types map cleanly to cognitive-science taxonomy; Commitment Memory and Learning Memory explicitly flagged as having no individual-cognition analog | Tulving (1972); Squire (2004); Anderson/ACT-R; (Commitment: Winograd & Flores 1986; Learning: Argyris & Schön 1978, 1996) |
| §7 Memory Lifecycle | No new callout beyond §8 (Provenance carries the citation for this area) | — |
| §8 Provenance | Added citation callout (strongest single rename opportunity in this document); per-question mapping (`wasAttributedTo`=who, `wasGeneratedBy`=when, `wasDerivedFrom`=source), reconciled with Trust & Governance Part 4 during post-review-pass fixes | W3C PROV-O |
| §9 Write Governance | Added light citation callout | Standard RBAC / Zero Trust vocabulary |
| §10 Conflict Resolution | Added explicit note that CRDT/eventual-consistency literature is the natural parent but is deliberately **not** cited here — deferred to Technical Architecture per Master Plan §2.3. Section remains KEEP for this phase | — (deferred, not grounded) |
| §11 Memory Relationships | Added citation callout — subject–predicate–object framing | W3C RDF/OWL |
| §12 Memory Drift | Added citation callout (heavy) — Weick explains why the gap exists, Argyris & Schön explains how it's corrected | Weick (1979, 1995); Argyris & Schön (1978, 1996) |
| §13 Organizational Learning | Added citation callout | Argyris & Schön (1978, 1996); Nonaka & Takeuchi (1995) |
| §14–15 Relationship to Intelligence / Consumption & Delivery | No citation added — explicitly KEEP | — |

---

## Product Architecture v2.1 → v2.2

| Section | What Changed | Source Cited |
|---|---|---|
| §1 Core Product Shift | Added optional, light citation callout — "calm technology" strengthens the infrastructure-not-destination framing. Explicitly flagged as non-load-bearing | Weiser (1991) |
| §4 Ambient Delivery | No citation added — explicitly KEEP | — |
| §5 MCP Surface | **Governance language updated** — MCP confirmed stewarded by the Agentic AI Foundation (Linux Foundation) since December 2025, not solely Anthropic | Verified via web search |
| §5 A2A Support | **Governance language updated** — Google's donation of A2A to the Linux Foundation (June 2025) noted | Verified via web search |
| §5 Knowledge Exchange | Added citation callout; **OKF terminology updated** — Open Knowledge Compatibility subsection now points to the real, adopted OKF v0.1 | Gruber (1993); W3C RDF/OWL; Google Cloud OKF v0.1 (2026) |
| §5 Brain-to-Brain Interoperability | Explicit note added: no external grounding forced — Master Plan §5 marks this a strategic direction, not a format-compatibility claim | — (KEEP, confirmed) |
| §6–14 Mission Control surfaces | No citation added — explicitly KEEP | — |
| §11 Consultant (modes) | Added citation callout — Inquiry/Planning/Review modes framed as Simon's Intelligence–Design–Choice model; Simulation Mode noted as Company Brain's own extension beyond Simon's three phases | Simon (1960) |
| §15 Three-Tier Boundary | Added citation callout — Always/Ask First/Never mapped explicitly to human-out-of-loop / human-in-the-loop / no-autonomous-path | Human-AI interaction literature (standard taxonomy) |
| §16–19 Product Boundary, Conflict/Drift/Learning Experience | No citation added — explicitly KEEP | — |
| §20 Competitive Position | No citation added — explicitly KEEP | — |
| §21–22 MVP Prioritization, Success Metrics | No citation added — explicitly KEEP | — |

---

## Intelligence Architecture v1.0 → v1.1 (light-touch addendum, per Master Plan §2.5 "frozen document")

| Section | What Changed | Source Cited |
|---|---|---|
| Document Control | New "Grounding Addendum" block added, listing exactly what was and wasn't touched | — |
| Part 6 Reasoning Architecture | Added citation callout — Inquiry/Planning/Review mapped to Intelligence/Design/Choice; Simulation Mode explicitly noted as extending beyond Simon's three phases, not a forced fourth phase | Simon (1960) |
| Part 7–10 (Recommendation/Risk/Opportunity/Drift Intelligence) | No citation added — explicitly KEEP, confirmed in a new callout at Part 7 and a note at Part 10 | — |
| Part 13 Confidence Model | Added a "noted, not grounded further" callout — calibration/Brier-score vocabulary flagged as the eventual parent, explicitly deferred to Technical Architecture, consistent with prior "Still Open" status | Calibration / Brier-score vocabulary (decision theory) — noted, not cited as a current rename |
| Part 15 Intelligence Object Model | No citation added — explicitly KEEP, confirmed in a new callout | — |
| All version cross-references | Updated to point at v2.3/v1.3/v1.3/v2.2 of the four documents this depends on | — |

---

## Trust & Governance Architecture v1.0 → v1.1 (light-touch addendum, per Master Plan §2.6)

| Section | What Changed | Source Cited |
|---|---|---|
| Document Control | New "Grounding Addendum" block added | — |
| Part 3 Trust Object Model | Added citation callout — Claim/Evidence → PROV-O; Approval/Exception/Delegation → RBAC/ABAC/NIST | W3C PROV-O; RBAC/ABAC (NIST) |
| Part 4 Provenance Architecture | Added citation callout (heavy) — per-question mapping across all three layers: `wasAttributedTo`=who (Memory: asserted; Execution: approved/acted), `wasGeneratedBy`=when/by what activity (all three layers), `wasDerivedFrom`=from what source (Memory: raw artifact; Intelligence: evidence). Corrected during post-review-pass fixes from an earlier per-layer assignment that was loose against PROV-O's actual semantics. Flagged as the strongest single rename opportunity in the whole document set | W3C PROV-O |
| Part 5 Authority Model | Added citation callout | RBAC/ABAC standard delegation vocabulary |
| Part 6 Governance Lifecycle | Added optional, low-priority citation callout | Generic ITIL-style change-management lifecycle |
| Part 7 Challenge Authority | Added citation callout — explicitly unifies vocabulary with Product Architecture's Three-Tier Boundary rather than re-describing it | Human-AI interaction literature (standard taxonomy) |
| Part 8 Human Oversight Authority | Added citation callout + table mapping Always/Ask First/Never to the same taxonomy used in Product Architecture §15 | Human-AI interaction literature (standard taxonomy) |
| All version cross-references | Updated to point at v2.3/v1.3/v1.3/v2.2/v1.1 of the five documents this depends on | — |

---

## Foundational Reasoning V4 (append-only, no rename pass per Master Plan §2.7)

| Section | What Changed | Source Cited |
|---|---|---|
| Chapters 0–24 | **Untouched.** No edits, per this document's own founding rule and the Master Plan's explicit instruction. | — |
| New §25 | Appended: narrates why this phase happened, what mapped to what, the VSM Compression Test result, the OKF adoption decision, and the confirmed KEEP list. Explicitly notes that Chapters 0/22–23 are now stale (they describe Intelligence Architecture and Trust & Governance as not-yet-started) and states this is left uncorrected by design. | Cross-references `Company_Brain_Theoretical_Foundations_v1.md`, `OKF_Adoption_Mapping.md` |

---

## New Standalone Deliverables (no prior version to diff against)

| File | Content |
|---|---|
| `OKF_Adoption_Mapping.md` | Composite Knowledge Object → OKF v0.1 field mapping; what Company Brain layers on top |
| `Company_Brain_Theoretical_Foundations_v1.md` | All 13 fields, VSM Compression Test, vocabulary rename table appendix |
| `One_Pager.md` | VSM-based one-page summary for a non-technical reader |
| `Bibliography.md` | Full verified reference list |
