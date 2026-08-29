# Coverage Check — Master Plan §2 Touch-Map vs. Grounded Drafts

Every row of Master Plan §2's six document tables, checked against the actual grounded drafts in `/grounded-drafts/`. Format: Doc → Section → Master Plan Action → Done? Anything not fully addressed is called out under "Gaps Found" at the bottom — nothing is silently skipped.

Legend: **GROUND** = cited/renamed, **KEEP** = no citation forced, **VERIFY** = confirmed current, **ADOPT** = decided integration, **GROUND(light/optional)** = citation added but explicitly non-load-bearing.

**Re-verified after the team-review exposition rewrite:** every row below was re-checked against the actual document text after all GROUND callouts were rewritten from citation-then-mention into theory-first-then-bridge exposition. Coverage is unchanged at 100% — the rewrite changed *how* each row is grounded (theory stated first, relationship to the architecture stated explicitly as implement/extend/diverge), not *whether* it's grounded. See `CHANGE_LOG.md`, "Exposition Rewrite," for what changed structurally, and the field-strength summary at the bottom of `Company_Brain_Theoretical_Foundations_v1.md` for which fields support "we implement/extend" vs. the weaker "we are consistent with."

---

## §2.1 Architecture & Vision v2.2 → v2.3

| Section | Master Plan Action | Done? |
|---|---|---|
| 2. The Problem | GROUND (March & Simon, Walsh & Ungson) | ✅ Y |
| 3. What Is A Company Brain | GROUND (Beer) | ✅ Y |
| 4. Organizational Reality / Coordination Systems | GROUND heavy (Winograd & Flores, Dietz) | ✅ Y |
| 5. Atomic Primitives | GROUND heavy (Zachman + DEMO) | ✅ Y |
| 6. Core Principles | GROUND partial (Principle 5 → Zero Trust; Principle 7 → Argyris & Schön) | ✅ Y |
| 7. Seven-Layer Pipeline | GROUND (Beer's VSM; run compression test; flag Memory/Exposure as extension) | ✅ Y — compression test lives in Theoretical Foundations, referenced inline |
| 8–9. Capture / Understanding | GROUND (Nonaka & Takeuchi, Weick) | ✅ Y |
| 9. Knowledge Objects | GROUND + ADOPT (Gruber; OKF) | ✅ Y |
| 10. Memory Layer / Commitment Lifecycle | GROUND (Walsh & Ungson; Winograd & Flores) | ✅ Y |
| 11. Intelligence Layer | KEEP | ✅ Y — explicit KEEP note added |
| 12. Execution Layer | GROUND light (DEMO performa/informa/forma) | ✅ Y |
| 13. Exposure Layer | VERIFY (MCP governance) | ✅ Y |
| 14. Evolution Layer | GROUND (Argyris & Schön) | ✅ Y |
| 15. Trust System (summary) | GROUND (PROV-O) | ✅ Y |
| 16. Organizational Learning Loop | GROUND (Argyris & Schön, Nonaka & Takeuchi) | ✅ Y |
| 17–18. Relationship to Products / Long-Term Vision | KEEP | ✅ Y — no citation forced, unchanged |

**Row count: 16/16 addressed.**

---

## §2.2 Ontology v1.2 → v1.3

| Section | Master Plan Action | Done? |
|---|---|---|
| 2. Ontology Philosophy | GROUND (Dietz) | ✅ Y |
| 3. Ontology Layers | GROUND heavy (DEMO split; Zachman) | ✅ Y |
| 4. Context Model | GROUND (Weick; Speech Act felicity conditions) | ✅ Y |
| 5. Organizational Memory Mapping | GROUND (Walsh & Ungson) | ✅ Y |
| 6. Relationship Model | GROUND (RDF/OWL) | ✅ Y |
| 7. Derived Intelligence Objects | KEEP | ✅ Y |
| 8. Ontology Boundary | KEEP | ✅ Y |

**Row count: 7/7 addressed.**

---

## §2.3 Memory Model v1.2 → v1.3

| Section | Master Plan Action | Done? |
|---|---|---|
| 3. What Is Memory? | GROUND (Walsh & Ungson) | ✅ Y |
| 4. Knowledge Representation / Knowledge Objects | GROUND + ADOPT (Gruber; OKF) | ✅ Y |
| 5. Formation Routing | KEEP | ✅ Y |
| 6. Memory Types | GROUND partial (Tulving/Squire/ACT-R map 3 of 5) | ✅ Y |
| 7–8. Lifecycle / Provenance | GROUND (PROV-O) | ✅ Y |
| 9. Write Governance | GROUND (RBAC/Zero Trust) | ✅ Y |
| 10. Conflict Resolution | KEEP, flag CRDT for Technical Architecture | ✅ Y — explicit deferral note added, not grounded here |
| 11. Memory Relationships | GROUND (RDF triple) | ✅ Y |
| 12. Memory Drift | GROUND heavy (Weick; Argyris & Schön) | ✅ Y |
| 13. Organizational Learning | GROUND (same as #7/#6) | ✅ Y |
| 14–15. Relationship to Intelligence / Consumption & Delivery | KEEP | ✅ Y |

**Row count: 11/11 addressed.**

---

## §2.4 Product Architecture v2.1 → v2.2

| Section | Master Plan Action | Done? |
|---|---|---|
| 1–3. Core Product Shift / Philosophy / Exposure Modes | GROUND optional, light (Weiser) | ✅ Y |
| 4. Ambient Delivery | KEEP | ✅ Y |
| 5. Agent Access — MCP Surface, A2A Support | VERIFY (MCP under AAIF) | ✅ Y |
| 5. Knowledge Exchange / OKF Compatibility | ADOPT | ✅ Y |
| 6–14. Mission Control surfaces | KEEP | ✅ Y |
| 15. Trust & Governance — Three-Tier Boundary | GROUND (human-in-the-loop taxonomy) | ✅ Y |
| 16–19. Product Boundary, Conflict/Drift/Learning Experience | KEEP | ✅ Y |
| 20. Competitive Position | KEEP | ✅ Y |
| 21–22. MVP Prioritization, Success Metrics | KEEP | ✅ Y |

**Row count: 9/9 addressed.**

*Note: §11 Consultant (modes) received a GROUND citation (Simon's Intelligence-Design-Choice model) that is not a distinct row in Master Plan §2.4's table — it is explicitly covered under Master Plan §2.5's Intelligence Architecture Part 6 row instead, and was cross-applied to Product Architecture's own Consultant section since the two describe the same modes. Not a gap; flagged here only for traceability.*

---

## §2.5 Intelligence Architecture v1.0 → v1.1

| Section | Master Plan Action | Done? |
|---|---|---|
| Part 6, Reasoning Pipeline by Consultant Mode | GROUND (Simon's Intelligence-Design-Choice model) | ✅ Y |
| Part 13, Confidence Model | GROUND light, forward-looking (Brier-score vocabulary, flag for Technical Architecture) | ✅ Y — noted, explicitly not force-graded as a current rename |
| Parts 7–10 (Recommendation/Risk/Opportunity/Drift Intelligence) | KEEP | ✅ Y |
| Part 15 (Brain Score, Agent Readiness) | KEEP | ✅ Y |

**Row count: 4/4 addressed.**

---

## §2.6 Trust & Governance Architecture v1.0 → v1.1

| Section | Master Plan Action | Done? |
|---|---|---|
| Part 3, Trust Object Model | GROUND (PROV-O for Claim/Evidence; RBAC/ABAC/NIST for Approval/Exception/Delegation) | ✅ Y |
| Part 4, Provenance Architecture | GROUND heavy (1:1 PROV-O) | ✅ Y |
| Part 5, Authority Model / Delegation / Revocation | GROUND (RBAC/ABAC) | ✅ Y |
| Part 6, Governance Lifecycle | GROUND optional (ITIL-style) | ✅ Y |
| Part 7–8, Challenge Authority / Human Oversight | GROUND, unify vocabulary with Product Architecture | ✅ Y — explicit shared-taxonomy table added |
| Rest | KEEP | ✅ Y — no citation forced elsewhere |

**Row count: 6/6 addressed.**

---

## §2.7 Foundational Reasoning V4

| Requirement | Done? |
|---|---|
| No rename pass — content of Chapters 0–24 untouched | ✅ Y — verified byte-for-byte carryover, no edits |
| Append one new numbered section (§25) logging the grounding phase | ✅ Y |

**Row count: 2/2 addressed.**

---

## Deliverables Checklist (Master Plan §7)

| # | Deliverable | Done? |
|---|---|---|
| 1 | `Company_Brain_Theoretical_Foundations_v1.md` — 13 fields, citation/summary/mapping/fit each | ✅ Y |
| 2 | Vocabulary Rename Table (appendix inside Theoretical Foundations) | ✅ Y |
| 3 | Updated canonical documents (6 living docs, version-bumped) | ✅ Y |
| 4 | One-page "Company Brain on One Page" | ✅ Y |
| 5 | OKF Adoption Mapping | ✅ Y |
| 6 | Bibliography.md | ✅ Y |

**Row count: 6/6 addressed.**

---

## §3 Memory Types Cognitive Science Mapping (worked example table)

Master Plan §3's own worked table (Factual≈Semantic, Interaction≈Episodic, Action≈Procedural, Commitment=no analog, Learning=partial) — reproduced verbatim in Theoretical Foundations Field 10 and referenced in Memory Model v1.3 §6. ✅ Y

## §4 VSM Compression Test

Full 5-step exercise (re-derive 7 layers from 5 subsystems, identify Memory/Exposure as the extension, write the required paragraph) — done as its own subsection in Theoretical Foundations, and the required paragraph is reproduced in Architecture & Vision v2.3 §7's callout and in `One_Pager.md`. ✅ Y

## §5 What Does Not Get Renamed (Original IP list)

All six items (Drift Detection, Commitment Memory, Learning Memory, Brain Score/Agent Readiness, Right Memory Right Moment + Exposure Layer, Knowledge Exchange/Brain-to-Brain Interoperability) — confirmed KEEP with no forced citation across every relevant document. Cross-checked against `RECOGNIZABILITY_TEST_SHEET.md`. ✅ Y

## §6 OKF Adoption

Full mapping done as its own deliverable, and the "adopted, not internal-placeholder" status is now consistent across all four documents that reference it (see `CONSISTENCY_CHECK.md`). ✅ Y

---

## Gaps Found

**None found in touch-map coverage** — every row in Master Plan §2's six tables, plus §3–§7's exercises and deliverables, was addressed in the grounded drafts.

Two **process/hygiene issues** turned up during the first review pass — both now fixed and re-verified. Full detail in `CONSISTENCY_CHECK.md`:

1. ~~`OKF_Adoption_Mapping.md` and `Company_Brain_Theoretical_Foundations_v1.md` cited the six documents by pre-rename version numbers.~~ **Fixed** — every occurrence replaced with the versions actually shipped (v2.3/v1.3/v1.3/v2.2/v1.1/v1.1); re-grepped, zero stale references remain.
2. ~~Trust & Governance Part 4's PROV-O mapping assigned terms per architectural layer rather than per PROV-O's actual per-question semantics, and wasn't mirrored in Memory Model.~~ **Fixed** — both documents now state the identical per-question mapping (`wasAttributedTo`=who, `wasGeneratedBy`=when, `wasDerivedFrom`=source), cross-referenced in both Document Control sections.

**Current status: zero open gaps, zero open hygiene issues.** Both fixes re-verified against a fresh grep of the actual file contents, not re-asserted from memory.

---

## Vocabulary Pass Coverage (Team-Review Second Pass)

Separate check, requested alongside the exposition rewrite: every rename *candidate* in the Master Plan's touch-map and this document's own rename table was checked against the actual drafts to confirm it landed, not just the table entry. Result:

| Term | Candidate Action | Landed? |
|---|---|---|
| "Ostensive-versus-performative gap" | Swap to plain equivalent | ✅ Swapped — now "designed-versus-executed gap" in Architecture & Vision §11 and Ontology §3, matching the language already used in Ontology's SOP/Workflow disambiguation and Product Architecture's Drift Experience |
| Three-Tier Boundary tier names | Consider swap to human-in-the-loop taxonomy | ✅ Kept, justified explicitly in Product Architecture §15 and Trust & Governance Part 8 — plain names are the product-facing instruction, taxonomy is cited alongside, not substituted in |
| Five Memory Type names | Consider swap to Semantic/Episodic/Procedural | ✅ Kept, justified explicitly in Memory Model §6 — plain, question-answering names read more clearly to a non-specialist |
| Relationship Model columns (From/Relationship/To) | Consider swap to RDF's Subject/Predicate/Object | ✅ Kept, justified explicitly in Ontology §6 and Memory Model §11 — structurally identical, plainer labels |
| Write Governance | Consider swap to "Access Control" (RBAC's own term) | ✅ Kept, justified explicitly in Memory Model §9 — more precise than the general RBAC/ABAC term |
| Governance Lifecycle stage names | Consider swap to ITIL's own vocabulary | ✅ Kept, justified explicitly in Trust & Governance Part 6 — simpler than ITIL's multi-stage vocabulary, same shape |

All six candidates the Master Plan flagged for possible renaming were checked; one had a genuine, low-cost plain-language improvement available and was swapped, five were deliberately kept with the reasoning now stated in the document rather than left implicit. No candidate was silently left untouched.
