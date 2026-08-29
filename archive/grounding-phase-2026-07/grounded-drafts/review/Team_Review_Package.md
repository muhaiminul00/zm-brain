# Company Brain — Theoretical Grounding Phase: Team Review Package

*Read time: ~10 minutes. This is what you need before the review meeting — not the six full grounded documents.*

**This is a second, short read, not a full re-review.** If you already reviewed the first pass, you only need to re-check two things this time: the **Field-Strength Verdict** below (new), and that the theory-first rewrite (visible throughout the linked grounded drafts, and summarized in the recognizability sheet below) actually reads as direction rather than decoration. The One-Pager, Recognizability Sheet, and Three Questions are unchanged from the first pass — you don't need to re-read them line by line unless something there is still bothering you.

---

## What This Was, And Why

A recurring complaint from the team was that Company Brain's vocabulary is hard to parse — almost everything in the architecture was named fresh, with no recognizable prior art to anchor it. That complaint, plus a build-risk concern (a concept with 30-50 years of field-testing behind it is lower-risk to build against than a fully invented one), triggered this phase.

**First pass** mined thirteen academic fields and industry standards and attached a citation wherever one genuinely fit, flagging what didn't rather than forcing it. The team's verdict on that pass: it worked for the complexity goal, but the *approach* needed to change before freeze — citing a paper next to existing text ("here's something that relates to this") isn't the same as showing the architecture is a stated application of that theory.

**Second pass (this one)** rewrote every grounding point across all six documents into **theory-first-then-bridge** exposition: the source theory is stated in full, in plain language, standalone — a reader with zero Company Brain context should understand the theory from that paragraph alone — and only then is Company Brain's architecture connected to it, as one of three explicitly stated relationships: **we implement this directly**, **we extend this to handle something the theory didn't anticipate**, or **we diverge from this, and here's why**. Nothing is left for the reader to infer. A separate vocabulary pass also checked every rename candidate the first pass had flagged but not acted on — one genuine plain-language swap was made, five terms were deliberately kept with the reasoning now stated in the document instead of left implicit.

**Nothing about what any layer does changed, in either pass.** What changed is exposition, framing, and (in a few places) vocabulary — plus two live facts that needed correcting regardless (MCP's and A2A's governance moved to neutral industry foundations since these documents were last written, and Google's Open Knowledge Format, previously an internal placeholder term, was adopted as a real, external, verified spec). Every citation in this package — roughly 30 sources — was independently verified by web search before use in the first pass; the second pass re-verified none of them and changed no architectural decision, per the explicit instruction that this was an exposition rewrite, not new research.

---

## Field-Strength Verdict (New This Pass — Read This First)

This is the single most important new fact from the second pass: not every one of the 13 fields earns the same strength of claim, and forcing them all to look equally strong would be dishonest. Here's the honest breakdown.

**11 of 13 fields now read as "we implement this directly" (for at least part of the mapping) or "we extend it" — a stated, checkable relationship, not a resemblance:**
VSM (5 of 7 layers direct, 2 — Memory, Exposure — explicitly extended), Language/Action Perspective, Speech Act Theory, Enterprise Ontology/DEMO, Organizational Memory Theory, Argyris & Schön's double-loop learning, Sensemaking Theory, the Information-Processing View, the Cognitive Memory Systems Taxonomy, Zachman's framework, and Formal Ontology/RDF/PROV-O/MCP/A2A.

**1 field downgraded, honestly, to "we are consistent with" — not implement, not extend:**
Nonaka & Takeuchi's SECI model. Company Brain applies exactly one of its four modes (Externalization — turning captured activity into structured Knowledge Objects) and doesn't touch the other three (Socialization, Combination, Internalization). Claiming "implement" or "extend" for the whole theory would overstate what's actually there. This is now stated as a partial, single-mode application, not stretched to look stronger.

**Correctly left with no theoretical claim at all — this is Company Brain's actual IP, not a gap:**
Intelligence Architecture's core reasoning outputs (Recommendation, Risk, Opportunity, and Drift Intelligence, Brain Score, Agent Readiness), the Drift Detection pipeline's specific mechanics, Commitment Memory and Learning Memory as named memory types, and Knowledge Exchange/Brain-to-Brain Interoperability as a strategic direction. No field mapping was forced onto any of these — none was found, and none should have been.

Full field-by-field detail, including the explicit implement/extend/diverge statement for every field: `Company_Brain_Theoretical_Foundations_v1.md`, especially its closing "Field Strength Summary" section.

---

## The One-Pager

Full content below (also stands alone as `One_Pager.md` if that renders better for your meeting format — same content either way).

---

# Company Brain — On One Page

*For a non-technical reader: exec, investor, or new hire. Built from the VSM Compression Test in `Company_Brain_Theoretical_Foundations_v1.md`. Nothing here changes the architecture — it's the same seven layers, mapped to a fifty-year-old model of how any viable organization works, so the shape is recognizable in one sitting.*

## The one-sentence idea

Every organization that survives already runs on five functions — sensing what's happening, doing the work, reasoning about the future, and governing itself. Company Brain makes those five functions explicit and adds two more that only become necessary once AI, not just humans, needs to act on them: **remembering**, and **delivering the right thing to the right person at the right moment**.

## The model this borrows from

In 1972, management scientist Stafford Beer described the **Viable System Model (VSM)**: any organization capable of sustaining itself needs five interacting subsystems. It doesn't matter if the organization is a company, a body, or a country — the same five functions show up:

```
 System 5 — Policy         "What are we, and what do we allow?"
 System 4 — Intelligence   "What's coming, and what should we do about it?"
 System 3 — Control        "Are we running well right now?"
 System 2 — Coordination   "Are our parts fighting each other?"
 System 1 — Operations     "Who's doing the actual work?"
```

This is not a new idea Company Brain invented — it's fifty years of prior art, still taught and used today. What Company Brain does is apply it to an AI-native organization, where two of the functions VSM always assumed would stay informal — memory and delivery — can no longer be left informal.

## The mapping

```
 VSM SUBSYSTEM              COMPANY BRAIN LAYER            WHY IT MAPS
 ─────────────              ───────────────────            ───────────
 System 1/2 (sensing)   →   CAPTURE + UNDERSTAND           Observing & making sense
                                                            of what's happening, before
                                                            anything is decided.

 [ no VSM equivalent ]  →   MEMORY                         ★ EXTENSION. A human org
                                                            remembers through people
                                                            who stay in their roles.
                                                            An AI actor has no such
                                                            continuity unless memory
                                                            is built as its own layer.

 System 4 (Intelligence)→   INTELLIGENCE                   Scanning memory for risk,
                                                            opportunity, drift, and
                                                            recommendations — the
                                                            same forward-looking job
                                                            VSM assigns System 4.

 System 1 (Operations)  →   EXECUTION                      The units that do the
                                                            organization's actual work.

 [ no VSM equivalent ]  →   EXPOSURE                       ★ EXTENSION. A human org
                                                            delivers the right info
                                                            to the right person through
                                                            informal norms nobody
                                                            designs. An AI actor needs
                                                            delivery engineered on
                                                            purpose, or nothing reaches
                                                            the point of work.

 System 3/4 (feedback)  →   EVOLUTION                      Comparing what was designed
                                                            against what actually
                                                            happened, and closing the
                                                            loop — System 3-4's audit
                                                            and feedback function.

 System 5 (Policy)      →   TRUST & GOVERNANCE             Identity, authority, and
                             (sits alongside the            what's allowed — sits
                              pipeline, not inside it)      outside the seven-layer
                                                            pipeline the same way
                                                            System 5 sits above
                                                            System 1-4, not inside them.
```

**Five of seven map cleanly. Two are the deliberate extension** — and that's the answer the whole team needs when someone asks "why does this need two more layers than a normal org chart?" Because a normal org chart is made of people, and people remember and communicate without anyone architecting it. An AI-native organization doesn't get that for free.

## The one paragraph to remember

> **Company Brain adopts VSM's fifty-year-old logic for what makes an organization viable, and extends it with two layers VSM always left implicit — Memory and Exposure — because in an AI-native organization, those can no longer stay implicit.**

## What's genuinely new here (not borrowed from anywhere)

A handful of things in Company Brain don't map onto VSM, DEMO, organizational memory theory, or anything else out there — and that's worth saying plainly, not hiding:

- **Drift Detection** (the Candidate → Pattern → Signal → Severity pipeline)
- **Commitment Memory** and **Learning Memory** as persistent, organization-level memory types (no equivalent in individual human cognition)
- **Brain Score** and **Agent Readiness**
- **Right Memory, Right Moment** as a named principle, and the **Exposure Layer** it justifies
- **Knowledge Exchange / Brain-to-Brain Interoperability** as a strategic direction

Everything else in the architecture has a recognizable fifty-year-old (or, in the case of the Open Knowledge Format, fifty-day-old) parent theory or standard behind it. Full citations: `Company_Brain_Theoretical_Foundations_v1.md` and `Bibliography.md`.

---

## The Recognizability Test Sheet

**Read this in 5 minutes before the meeting.** This is the actual test artifact — for every renamed or newly-cited term in the six documents, one line: what it's called, what it's grounded in, and a plain-English gloss. If you recognize roughly 70% of these unaided, the grounding did its job. The full version with all ~30 terms organized by document lives in `RECOGNIZABILITY_TEST_SHEET.md` in this folder — reproduced here in full so you don't have to open a second file:

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

### What Stays Unrecognizable On Purpose (genuine Company Brain IP — not a gap)

- Drift Detection pipeline (Candidate → Pattern → Signal → Severity)
- Commitment Memory and Learning Memory as persistent, org-level (not individual-cognition) memory types
- Brain Score, Agent Readiness
- Right Memory, Right Moment (Principle 8) and the Exposure Layer it justifies
- Knowledge Exchange / Brain-to-Brain Interoperability as a strategic direction

If you don't recognize these five, that's expected — there's nothing external to recognize. Score the 70% test against the ~30 terms above, not these five.

---

## Three Questions For The Team To Answer During Review

**a. Does the VSM-based one-pager make the pipeline easier to explain to a new hire or exec than the original 7-layer framing alone?**
The test is whether "we adopted a 50-year-old model and extended it with two layers" lands better in one meeting than walking through all seven layers cold. If it doesn't land better, the one-pager isn't earning its place.

**b. Any term in the recognizability sheet that's still unclear, or feels like a forced-fit citation rather than a genuine improvement?**
Every GROUND/VERIFY/ADOPT term above is supposed to survive scrutiny — if any of them reads as decorative rather than explanatory, that's a signal the citation should be dropped, not defended.

**c. Anything on the KEEP list (original IP) that you think DOES have a real academic or industry parent we missed?**
The five KEEP items above were checked and came up empty, but the team has broader exposure than the search that produced this package. If someone recognizes a real parent for Drift Detection, Commitment/Learning Memory, Brain Score, Agent Readiness, or Knowledge Exchange as a strategic direction, that's worth surfacing now, before freeze — not after.

---

## Going Deeper

If you want to see the actual grounded documents rather than this summary:

- **Full grounded drafts:** `/grounded-drafts/` — six documents, version-bumped, each with inline citation callouts marking exactly what was added and where (Architecture & Vision v2.3, Ontology v1.3, Memory Model v1.3, Product Architecture v2.2, Intelligence Architecture v1.1, Trust & Governance Architecture v1.1).
- **Full field-by-field grounding with citations and fit ratings:** `Company_Brain_Theoretical_Foundations_v1.md`
- **What changed, section by section, without re-reading full documents:** `review/CHANGE_LOG.md` — see "Exposition Rewrite" at the top for what this second pass specifically changed
- **Confirmation every Master Plan §2 row was actually addressed:** `review/COVERAGE_CHECK.md`
- **Cross-document consistency verification (OKF, Three-Tier/Human Oversight vocabulary, PROV-O terminology):** `review/CONSISTENCY_CHECK.md`
- **Full bibliography, every source verified:** `Bibliography.md`
- **OKF adoption detail:** `OKF_Adoption_Mapping.md`
- **Why this phase happened, in the project's own reasoning-trail voice:** `Company_Brain_Foundational_Reasoning_V4.md`, new §25

Nothing here has been merged into the canonical document set or frozen. This package exists so this second, shorter team pass can happen efficiently — freeze decisions wait for explicit go-ahead after this pass, not before.
