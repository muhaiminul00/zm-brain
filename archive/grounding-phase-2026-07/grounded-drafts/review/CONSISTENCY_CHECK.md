# Cross-Document Consistency Check

Verified by grepping the actual grounded-draft text for each term across all files, not by re-reading from memory. Three checks requested, plus what turned up along the way. **Re-run after the two fixes below were applied — both are now closed.**

---

## 1. OKF Usage

**Check:** "OKF" means Google's real OKF v0.1 everywhere, identically, in Architecture & Vision, Ontology, Memory Model, and Product Architecture — none still describe an internal spec.

**Result: PASS.** Grepped "OKF|Open Knowledge Format" across all four documents.

- Architecture & Vision v2.3 §9: "The Company Brain adopts Google Cloud's Open Knowledge Format (OKF) v0.1 directly as its Knowledge Exchange interchange format."
- Ontology v1.3 §2: "**Adopted:** Google Cloud's Open Knowledge Format (OKF) v0.1 ... is Company Brain's actual Knowledge Exchange interchange format, not a parallel internal spec."
- Memory Model v1.3 §4: "The Company Brain maintains compatibility with Open Knowledge Format (OKF) v0.1 — Google Cloud's real, published specification, adopted directly rather than as an internal placeholder concept."
- Product Architecture v2.2 §5: "The Company Brain exchanges Canonical Knowledge Objects through Open Knowledge Format (OKF) v0.1 compatible representations..." with the same "Adopted" callout as Architecture & Vision.

All four use identical framing: real spec, version-numbered (v0.1), Google Cloud, adopted directly, not an internal placeholder. No document still describes OKF as Company Brain's own concept. No change needed here — unaffected by this pass's fixes.

---

## 2. Three-Tier Boundary ↔ Human Oversight Authority Vocabulary

**Check:** Product Architecture's Three-Tier Boundary and Trust & Governance's Human Oversight Authority use the same human-in-the-loop / human-on-the-loop / human-out-of-loop vocabulary, and are now aligned rather than independently grounded.

**Result: PASS, with one honest gap in the taxonomy mapping (not a contradiction). Unaffected by this pass's fixes — carried forward unchanged from the prior check.**

Product Architecture v2.2 §15:
```
Always     → Maps to: human-out-of-loop.
Ask First  → Maps to: human-in-the-loop.
Never      → Maps to: no autonomous path exists regardless of loop position.
```

Trust & Governance v1.1 Part 8:
```
| Three-Tier Boundary | Authority Meaning | Autonomy-Taxonomy Equivalent |
| Always    | Pre-authorized...              | Human-out-of-loop |
| Ask First | Requires Approval...            | Human-in-the-loop |
| Never     | No delegation possible...       | No autonomous path, any position |
```

These two tables assign identical taxonomy terms to identical tiers — confirmed aligned, not just independently cited with different words (which is exactly the problem Master Plan §2.6 flagged).

**Gap worth naming (informational, not a defect):** the taxonomy has three positions (in-the-loop, on-the-loop, out-of-loop); Company Brain's three tiers only use two of them (in-loop, out-of-loop) plus a third catch-all for Never. "Human-on-the-loop" is cited in both documents as part of the taxonomy but no tier maps to it. A sharp reader may ask "what happened to human-on-the-loop?" — worth having an answer ready, not worth fixing.

---

## 3. PROV-O Terminology — RE-CHECKED, NOW CLOSED

**Check:** `wasGeneratedBy` / `wasAttributedTo` / `wasDerivedFrom` (or equivalents) used the same way everywhere Provenance is discussed.

**Result: PASS (was PARTIAL in the prior check — fixed this pass).**

**What was wrong before:** Trust & Governance Part 4 assigned one PROV-O term per architectural *layer* (`wasGeneratedBy`→Memory, `wasDerivedFrom`→Intelligence, `wasAttributedTo`→Execution), which conflated `wasGeneratedBy` (an entity-to-*activity* relation) with an agent-attribution question ("who asserted it"), and Memory Model §8 didn't mirror any specific assignment at all.

**What changed:** Both documents now map the same three terms per *question*, applied consistently across all three layers, rather than one term per layer:

- `wasAttributedTo` (Entity → Agent) → **who** — who asserted a Memory record; who approved or acted in Execution.
- `wasGeneratedBy` (Entity → Activity) → **when / by what process** — the capture/understanding activity behind a Memory record; the reasoning activity behind an Intelligence Object; the execution activity itself.
- `wasDerivedFrom` (Entity → Entity) → **from what source** — the raw artifact a Memory record traces back to; the memory records an Intelligence Object treats as evidence.

Verified by grep — both files now state the identical mapping:

- Memory Model v1.3 §8: "Who asserted it (`wasAttributedTo`) ... When (`wasGeneratedBy`) ... From what source (`wasDerivedFrom`)"
- Trust & Governance v1.1 Part 4: "Memory: who asserted it (`wasAttributedTo`), when / via what capture-or-understanding activity (`wasGeneratedBy`), from what source (`wasDerivedFrom`) ... Execution: who approved, who acted (`wasAttributedTo`); the execution activity itself (`wasGeneratedBy`)"

Both documents' Document Control sections now carry a "Correction (post-review-pass)" note explaining the fix and cross-referencing each other, so a reader who opens only one of the two documents will still see that the mapping was deliberately reconciled, not just happened to match.

**Status: CLOSED.**

---

## 4. Version-Number Hygiene — RE-CHECKED, NOW CLOSED

**What was wrong before:** `OKF_Adoption_Mapping.md` and `Company_Brain_Theoretical_Foundations_v1.md` were both written before the rename pass, and still referenced the six living documents by their pre-rename version numbers (Architecture & Vision v2.2, Ontology v1.2, Memory Model v1.2, Product Architecture v2.1, Intelligence Architecture v1.0, Trust & Governance Architecture v1.0).

**What changed:** Every occurrence of the old version numbers in both files was replaced with the version actually shipped in this package:

| Document | Old | New |
|---|---|---|
| Architecture & Vision | v2.2 | v2.3 |
| Ontology | v1.2 | v1.3 |
| Memory Model | v1.2 | v1.3 |
| Product Architecture | v2.1 | v2.2 |
| Intelligence Architecture | v1.0 | v1.1 |
| Trust & Governance Architecture | v1.0 | v1.1 |

Re-grepped both files for every pre-rename version string (`Architecture v2\.2`, `Ontology v1\.2`, `Memory Model v1\.2`, `Product Architecture v2\.1`, `Intelligence Architecture v1\.0`, `Governance Architecture v1\.0`) — **zero matches remain** in either file. Theoretical Foundations' own document version (its header reads "Version 1.0 — Grounding Phase Deliverable 2 of 6," a distinct, correct version referring to itself, not one of the six living docs) was correctly left untouched.

**Status: CLOSED.**

---

## Summary Table

| Check | Result |
|---|---|
| OKF usage identical across 4 docs | ✅ PASS |
| Three-Tier Boundary ↔ Human Oversight Authority aligned | ✅ PASS (taxonomy only partially used — informational, not a defect) |
| PROV-O terminology used the same way everywhere | ✅ PASS — **fixed this pass**, was PARTIAL |
| Version cross-references current | ✅ PASS — **fixed this pass**, was stale in 2 files |

All four checks now pass. No open items remain from this consistency check. Ready for the team test and, pending your sign-off, for freeze.
