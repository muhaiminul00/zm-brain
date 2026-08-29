# Recognizability Test Sheet

Flat list, one line each. This is the artifact for the "would an outside technical hire recognize 70%+ of this unaided" test (Master Plan §8 step 6) — not a document to study, a sheet to skim. Term stays the same in every case (Master Plan §0: names don't change) — what's new is the citation now attached to it. Format: **[Company Brain term]** → **[cited parent]** → plain gloss.

---

### Architecture & Vision

- **Living organism framing** → Beer's *Brain of the Firm* → the "company as a living system" metaphor is 50 years old, not new.
- **Coordination Systems** → Winograd & Flores → orgs run on commitments made through conversation, not paperwork.
- **Atomic Primitives (Key Question column)** → Zachman's 6 interrogatives → "Who/What/When/Why" is the same question set enterprise architects have used since 1987.
- **Seven-Layer Pipeline** → Beer's Viable System Model (VSM) → any org that survives needs the same 5 functions; Company Brain names them explicitly.
- **Trust Before Automation (Principle 5)** → Zero Trust → standard security posture: verify before you grant, don't assume.
- **The Brain Must Learn (Principle 7)** → Argyris & Schön, double-loop learning → fixing the rule, not just the instance.
- **Capture/Understanding transition** → Nonaka & Takeuchi, SECI → turning tacit know-how into written-down knowledge.
- **Understanding Layer** → Weick, sensemaking → meaning is made after the fact, not read off reality directly.
- **Knowledge Objects** → Gruber's ontology definition → "an explicit spec of a shared concept" — standard KR terminology.
- **Execution Layer** → Dietz/DEMO's performa/informa/forma → doing the work vs. talking about the work.
- **Exposure Layer (MCP Surface)** → Model Context Protocol, now under the Agentic AI Foundation → the plumbing that lets AI tools plug into external data; no longer solely Anthropic-run.
- **Evolution Layer** → Argyris & Schön → comparing what was designed against what happened, and updating the rule.
- **Trust System (provenance fields)** → W3C PROV-O → standard "who/when/derived-from" vocabulary for tracking where a fact came from.

### Ontology

- **Ontology Philosophy ("abstracted from implementation")** → Dietz/DEMO → literally DEMO's own stated purpose, word for word.
- **Four-layer structure** → DEMO's Cooperation/Action/Process/Fact Model → a near-parallel four-way split of "what an org is."
- **Context Model (emergent, not stored)** → Weick, sensemaking → context is built on the fly from history/goals/rules, not a filed record.
- **Organizational Memory Mapping** → Walsh & Ungson → the first formal academic taxonomy of "how orgs remember."
- **Relationship Model (From/Relationship/To)** → RDF/OWL → subject-predicate-object triples, the standard way to type a graph edge.

### Memory Model

- **"Memory" (core definition)** → Walsh & Ungson (1991) → a persistent record of org history usable for present decisions — an established definition, not a Company Brain invention.
- **Factual / Interaction / Action Memory** → Tulving/Squire, Semantic/Episodic/Procedural memory → cognitive science already has names for 3 of our 5 memory types.
- **Commitment Memory** → Winograd & Flores, conversation-for-action loop → Request→Promise→Report→Accept, extended with real-world exits (Delegated, Renegotiated, Breached).
- **Commitment Memory, Learning Memory (as memory *types*)** → **no analog exists** — flagged KEEP, not forced onto any citation. This is genuine Company Brain IP.
- **Provenance fields** → W3C PROV-O → `wasGeneratedBy` / `wasAttributedTo` / `wasDerivedFrom` — standard vocabulary for "who made this claim."
- **Write Governance** → RBAC / Zero Trust → standard "who's allowed to write what" access-control vocabulary.
- **Memory Drift** → Weick (why it happens) + Argyris & Schön (how it's corrected) → design vs. reality gaps, and fixing the rule once the gap repeats.
- **Conflict Resolution mechanics** → CRDT / eventual-consistency literature — **deliberately not cited yet**, deferred to Technical Architecture since it's implementation-level, not conceptual.

### Product Architecture

- **"Infrastructure, not destination" framing** → Weiser, "calm technology" → tech that disappears into where work already happens (light citation, not load-bearing).
- **MCP Surface / A2A Support** → Model Context Protocol (Agentic AI Foundation) / Agent2Agent Protocol (Linux Foundation) → both are real, vendor-neutral, industry-adopted agent-interop standards, governance-updated for currency.
- **Knowledge Exchange / OKF Compatibility** → Google Cloud's Open Knowledge Format v0.1 → **adopted directly**, not just cited — real spec, published June 2026, Apache 2.0.
- **Consultant Modes (Inquiry/Planning/Review/Simulation)** → Herbert Simon, Intelligence-Design-Choice model → a 1960 decision-theory model, extended by Company Brain with a 4th mode (Simulation) Simon never had.
- **Three-Tier Boundary (Always/Ask First/Never)** → human-in-the-loop / human-on-the-loop / human-out-of-loop taxonomy → standard human-AI autonomy vocabulary, now explicitly shared with Trust & Governance's Human Oversight Authority.
- **Brain-to-Brain Interoperability** → **no format-compatibility parent** — flagged KEEP as a strategic direction, not grounded further.

### Intelligence Architecture (light-touch addendum — frozen document)

- **Reasoning Pipeline (Inquiry/Planning/Review)** → Simon's Intelligence-Design-Choice model → same citation as Consultant Modes above, applied at the mechanism level.
- **Confidence Model** → calibration / Brier-score vocabulary (decision theory) → **noted, not grounded yet** — the quantified version of this belongs to Technical Architecture.
- **Recommendation/Risk/Opportunity/Drift Intelligence, Brain Score, Agent Readiness** → **no academic equivalent** — flagged KEEP, preserved as differentiator.

### Trust & Governance Architecture (light-touch addendum — frozen document)

- **Claim / Evidence** → W3C PROV-O → an assertion plus the support behind it.
- **Approval / Exception / Delegation** → RBAC/ABAC (NIST) → standard access-control vocabulary for who can authorize what.
- **Provenance Architecture** → W3C PROV-O → the strongest single rename opportunity in the whole document set; mapped per-question (who/when/source) consistently with Memory Model's own Provenance section.
- **Authority Model / Delegation / Revocation** → RBAC/ABAC → granting and withdrawing permission, standard vocabulary.
- **Governance Lifecycle (Proposed→Reviewed→Approved→Executed→Audited)** → generic ITIL-style change management → low-priority citation, already clear without it.
- **Human Oversight Authority** → same human-in-the-loop taxonomy as Product Architecture's Three-Tier Boundary → now explicitly unified, not two words for the same idea.

---

## What Stays Unrecognizable On Purpose (genuine Company Brain IP — not a gap in this exercise)

- Drift Detection pipeline (Candidate → Pattern → Signal → Severity)
- Commitment Memory and Learning Memory as persistent, org-level (not individual-cognition) memory types
- Brain Score, Agent Readiness
- Right Memory, Right Moment (Principle 8) and the Exposure Layer it justifies
- Knowledge Exchange / Brain-to-Brain Interoperability as a strategic direction

If a technical hire doesn't recognize these five, that's expected — there's nothing external to recognize. The 70% test should be scored against the ~30 GROUND/VERIFY/ADOPT terms above, not these five.
