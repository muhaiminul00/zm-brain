# Company Brain — Theoretical Grounding & Vocabulary Alignment
## Master Plan — Pre-Technical Phase

Status: Proposed
Depends on: Architecture & Vision v2.2, Ontology v1.2, Memory Model v1.2, Product Architecture v2.1, Intelligence Architecture v1.0, Trust & Governance v1.0, Foundational Reasoning V4
Scope: Conceptual grounding only. No technical architecture, no schemas, no infra. Same boundary every canonical doc already holds.

---

## 0. Goal Of This Phase

Not new concepts. Not a rewrite.

Take the 7 canonical documents. For every layer, primitive, and mechanism: find the existing academic field or industry standard that already describes it. Where one exists — adopt its vocabulary, cite it, compress the explanation. Where none exists — mark it explicitly as original IP, keep the custom term, don't force a citation that doesn't fit.

Two problems this solves:
1. Team complexity complaint — private vocabulary replaced with recognizable vocabulary.
2. Build risk — a concept that already has 30-50 years of field-testing (VSM, DEMO, organizational memory theory) is lower-risk to build against than a fully invented one.

Output of this phase = a vocabulary + citation layer laid over the existing architecture. Architecture content does not change. Names, framing, and citations do.

---

## 1. Fields To Mine

13 fields. Ordered by how much of the architecture they explain.

| # | Field | Core Source(s) | What It Gives Us | Primary Target |
|---|---|---|---|---|
| 1 | Management Cybernetics — Viable System Model | Stafford Beer, *Brain of the Firm* (1972); *The Heart of Enterprise* (1979); *Diagnosing the System for Organizations* (1985) | Whole-org model as 5 interacting subsystems (Operations, Coordination, Control, Intelligence, Policy); recursion; Ashby's Law of Requisite Variety; feedback-loop viability | 7-layer pipeline, overall "Brain" framing |
| 2 | Language/Action Perspective | Terry Winograd & Fernando Flores, *Understanding Computers and Cognition* (1986) | Commitments as the atomic unit of coordination; conversation-for-action loop (Request→Promise→Report→Accept) | Atomic Primitives, Commitment Memory lifecycle |
| 3 | Speech Act Theory | J.L. Austin, *How to Do Things with Words* (1962); John Searle, *Speech Acts* (1969) | Formal basis under #2 — utterances as acts (commissives, directives) | Commitment primitive, Action primitive |
| 4 | Enterprise Ontology / DEMO | Jan Dietz, *Enterprise Ontology: Theory and Methodology* (Springer, 2006); Dietz & Mulder, *Enterprise Ontology: A Human-Centric Approach* (Springer, 2020) | Formal transaction pattern (initiator/executor, coordination-acts vs production-facts); org modeled independent of implementation — closest academic twin to our Ontology + Primitives split | Ontology doc, in full |
| 5 | Organizational Memory Theory | J.P. Walsh & G.R. Ungson, "Organizational Memory," *Academy of Management Review* 16(1), 1991, pp. 57–91 | First formal definition + taxonomy of organizational memory; retention facilities; acquisition/retention/retrieval processes | Memory Model doc, definition + formation sections |
| 6 | Knowledge Creation Theory (SECI) | Ikujiro Nonaka & Hirotaka Takeuchi, *The Knowledge-Creating Company* (1995) | Tacit↔explicit knowledge conversion cycle (Socialization, Externalization, Combination, Internalization) | Capture → Understanding transition, Knowledge Object formation |
| 7 | Organizational Learning Theory | Chris Argyris & Donald Schön, *Organizational Learning: A Theory of Action Perspective* (1978); *Organizational Learning II* (1996) | Single-loop (fix the error) vs double-loop (fix the rule) learning | Learning Memory, Drift Detection, Evolution Layer |
| 8 | Sensemaking Theory | Karl Weick, *Sensemaking in Organizations* (1995); *The Social Psychology of Organizing* (1979) | How ambiguous reality becomes shared, retrospective meaning; enactment | Understanding Layer, Context Model, Drift (intended vs observed) |
| 9 | Information-Processing View of Organizations | James March & Herbert Simon, *Organizations* (1958); Jay Galbraith, *Organization Design* (1977) | Org as bounded-rational information processor; uncertainty reduction via structure | Problem Statement, Organizational Reality section |
| 10 | Cognitive Memory Systems Taxonomy | Endel Tulving, "Episodic and Semantic Memory" (1972); Larry Squire, "Memory Systems of the Brain" (2004); John Anderson, ACT-R (procedural/declarative) | Established memory-type vocabulary | Memory Types table (partial mapping — see §2) |
| 11 | Enterprise Architecture Standards | John Zachman, "A Framework for Information Systems Architecture," *IBM Systems Journal* (1987); The Open Group, TOGAF Standard, 10th Edition | Standard taxonomy for "what exists in an enterprise"; the What/How/Where/Who/When/Why interrogatives | Ontology layers, Primitive naming |
| 12 | Formal Ontology / Knowledge Representation Standards | Tom Gruber, "A Translation Approach to Portable Ontology Specifications," *Knowledge Acquisition* 5(2), 1993; W3C RDF/OWL; **Open Knowledge Format (OKF) v0.1** — Google Cloud, published June 12, 2026 | Canonical definition of "ontology"; graph-based knowledge representation conventions; **adopted directly as our Knowledge Exchange interchange format** | Knowledge Objects, Open Knowledge Compatibility sections (appears in 4 docs) |
| 13 | Agent Interoperability & Provenance Standards | Model Context Protocol — Anthropic, Nov 2024, now stewarded by the Agentic AI Foundation (Linux Foundation, since Dec 2025); Agent2Agent (A2A) protocol — Google; W3C PROV-O provenance vocabulary | Already-standard exposure/interop layer; formal provenance vocabulary | Exposure Layer, MCP Surface, Provenance Architecture |

Decision on #12: Company Brain adopts Google Cloud's Open Knowledge Format (OKF) v0.1 as its Knowledge Exchange interchange format, rather than maintaining a parallel internal spec under the same name. Composite Knowledge Objects export as OKF concept documents (`type` field + markdown body); our Trust, Provenance, and Governance layers wrap on top of OKF's minimal spec, which intentionally defines interoperability only, not content model or trust semantics. Full mapping in §6.

---

## 2. Document-By-Document Touch Map

Action legend: **GROUND** = keep concept, cite existing theory/standard, consider renaming. **KEEP** = original IP, no external parent exists, do not force one. **VERIFY** = already uses a real standard name, just confirm currency/accuracy. **DECIDE** = naming collision or open choice requiring a call, not just a citation.

### 2.1 Architecture & Vision v2.2

| Section | Action | Ground In |
|---|---|---|
| 2. The Problem | GROUND | March & Simon (#9), Walsh & Ungson (#5) — the "fragmented memory" problem is itself an established academic finding, not just our claim |
| 3. What Is A Company Brain | GROUND | Beer (#1) — "living organism" framing already has 50 years of precedent under this exact metaphor |
| 4. Organizational Reality / Coordination Systems | GROUND (heavy) | Winograd & Flores (#2), Dietz/DEMO (#4) — "coordination systems" is literally their vocabulary |
| 5. Atomic Primitives | GROUND (heavy) | Zachman's 6 interrogatives (#11) + DEMO transaction pattern (#4) — near 1:1 mapping, see §3 |
| 6. Core Principles | GROUND (partial) | Principle 5 (Trust Before Automation) → Zero Trust literature; Principle 7 (Brain Must Learn) → Argyris & Schön double-loop (#7) |
| 7. Seven-Layer Pipeline | GROUND | Beer's VSM 5-subsystem model (#1) as parent theory. Run the compression test (§4). Memory + Knowledge Object layers have no VSM analog — flag as extension, not deviation |
| 8–9. Capture / Understanding | GROUND | Nonaka & Takeuchi SECI (#6), Weick sensemaking (#8) |
| 9. Knowledge Objects | GROUND + ADOPT | Gruber's ontology definition (#12); Composite Knowledge Objects map onto Google's OKF v0.1 concept-document format — see §6 |
| 10. Memory Layer / Commitment Lifecycle | GROUND | Walsh & Ungson (#5); Winograd & Flores conversation-for-action loop (#2) — Request/Promise/Report/Accept maps directly onto our Commitment states |
| 11. Intelligence Layer | KEEP | No single clean academic parent — treat as primary original contribution |
| 12. Execution Layer | GROUND (light) | DEMO's production-act / coordination-act distinction, "performa/informa/forma" (#4) |
| 13. Exposure Layer | VERIFY | MCP (#13) — confirm governance now sits under Agentic AI Foundation, not Anthropic solely |
| 14. Evolution Layer | GROUND | Argyris & Schön double-loop (#7) |
| 15. Trust System (summary) | GROUND | W3C PROV-O (#13) |
| 16. Organizational Learning Loop | GROUND | Argyris & Schön (#7), Nonaka & Takeuchi (#6) |
| 17–18. Relationship to Products / Long-Term Vision | KEEP | Aspirational/product framing, no change needed |

### 2.2 Ontology v1.2

This document is the single best fit for external grounding. DEMO/Enterprise Ontology (#4) is a near-complete academic parent for this entire doc.

| Section | Action | Ground In |
|---|---|---|
| 2. Ontology Philosophy | GROUND | Dietz (#4) — "abstracted from implementation" is DEMO's own stated purpose, word for word |
| 3. Ontology Layers (Primitives → Core Objects → Org Structures → Operational Constructs) | GROUND (heavy) | DEMO's Cooperation/Action/Process/Fact Model split; Zachman's 6×6 matrix (#11) |
| 4. Context Model | GROUND | Weick sensemaking (#8); Speech Act felicity conditions (#3) |
| 5. Organizational Memory Mapping | GROUND | Walsh & Ungson retention-facility taxonomy (#5) |
| 6. Relationship Model | GROUND | RDF/OWL relationship-typing convention (#12) |
| 7. Derived Intelligence Objects | KEEP | Original, no external analog |
| 8. Ontology Boundary | KEEP | Scoping statement, no change |

### 2.3 Memory Model v1.2

| Section | Action | Ground In |
|---|---|---|
| 3. What Is Memory? | GROUND | Walsh & Ungson's formal definition (#5) — direct citation upgrades this from assertion to established theory |
| 4. Knowledge Representation / Knowledge Objects | GROUND + ADOPT | Gruber (#12) for the ontology definition. **Adopted**: Google Cloud's real "Open Knowledge Format (OKF) v0.1" (June 2026 — markdown+YAML, AI-agent knowledge interchange, Apache 2.0, active adoption) becomes Company Brain's actual Knowledge Exchange interchange format. Internal references to "OKF" now mean this spec directly, not a parallel internal concept. Mapping in §6. |
| 5. Formation Routing | KEEP | Implementation-adjacent, no theory needed |
| 6. Memory Types | GROUND (partial — see §3 table) | Tulving/Squire cognitive taxonomy (#10) maps 3 of 5 types cleanly; Commitment and Learning have no clean cognitive-science analog — keep custom |
| 7–8. Lifecycle / Provenance | GROUND | W3C PROV-O vocabulary (#13) — direct terminology swap available (wasGeneratedBy, wasAttributedTo, wasDerivedFrom) |
| 9. Write Governance | GROUND | Standard RBAC/Zero Trust vocabulary |
| 10. Conflict Resolution | KEEP (flag for technical phase) | CRDT / eventual-consistency literature is the natural parent but it's implementation-level — defer citation to Technical Architecture, not this phase |
| 11. Memory Relationships | GROUND | RDF triple model (subject–predicate–object) (#12) |
| 12. Memory Drift | GROUND (heavy) | Weick's enacted-vs-intended environment (#8); Argyris & Schön double-loop trigger (#7) |
| 13. Organizational Learning | GROUND | Same as #7, #6 |
| 14–15. Relationship to Intelligence / Consumption & Delivery | KEEP | Product-level, no deep theory required |

### 2.4 Product Architecture v2.1

| Section | Action | Ground In |
|---|---|---|
| 1–3. Core Product Shift / Philosophy / Exposure Modes | GROUND (optional, light) | Mark Weiser, "The Computer for the 21st Century" (1991) — "calm technology," ubiquitous computing that disappears into the environment. One-line citation, strengthens the "infrastructure not destination" pitch |
| 4. Ambient Delivery | KEEP | Product/UX, no deep theory beyond #above |
| 5. Agent Access — MCP Surface, A2A Support | VERIFY | MCP now under Agentic AI Foundation (Linux Foundation) since Dec 2025 — update any doc language that implies sole Anthropic governance |
| 5. Knowledge Exchange / OKF Compatibility | ADOPT | Google's OKF v0.1 adopted directly as interchange format — see §6 |
| 6–14. Mission Control surfaces | KEEP | Product/UX layer, largely original, no external grounding needed |
| 15. Trust & Governance — Three-Tier Boundary (Always / Ask First / Never) | GROUND | Human-AI interaction literature's autonomy-level taxonomy (human-in-the-loop / human-on-the-loop / human-out-of-loop) — standard vocabulary already exists for exactly this 3-way split |
| 16–19. Product Boundary, Conflict/Drift/Learning Experience | KEEP | UX-level |
| 20. Competitive Position | KEEP | Market framing |
| 21–22. MVP Prioritization, Success Metrics | KEEP | Execution-level |

### 2.5 Intelligence Architecture v1.0

Frozen document. Recommend an addendum, not an edit.

| Section | Action | Ground In |
|---|---|---|
| Part 6, Reasoning Pipeline by Consultant Mode (Inquiry/Planning/Review/Simulation) | GROUND | Herbert Simon's Intelligence–Design–Choice model of decision-making, *The New Science of Management Decision* (1960) — near-direct parallel to Inquiry/Planning/Review |
| Part 13, Confidence Model | GROUND (light, forward-looking) | Calibration/Brier-score vocabulary from decision theory — flag for Technical Architecture, not full rewrite now |
| Parts 7–10 (Recommendation/Risk/Opportunity/Drift Intelligence), Part 15 (Brain Score, Agent Readiness) | KEEP | No academic equivalent — genuine original contribution, preserve as differentiator |

### 2.6 Trust & Governance Architecture v1.0

| Section | Action | Ground In |
|---|---|---|
| Part 3, Trust Object Model (Claim/Evidence/Challenge/Approval/Exception/Escalation/Delegation) | GROUND | W3C PROV-O (#13) for Claim/Evidence; standard access-control literature (RBAC/ABAC, NIST) for Approval/Exception/Delegation |
| Part 4, Provenance Architecture | GROUND (heavy) | Direct 1:1 W3C PROV-O alignment — strongest single rename opportunity in this doc |
| Part 5, Authority Model / Delegation / Revocation | GROUND | RBAC/ABAC standard delegation vocabulary |
| Part 6, Governance Lifecycle (Proposed→Reviewed→Approved→Executed→Audited) | GROUND (optional) | Generic change-management lifecycle (ITIL-style change approval) — low priority, already clear |
| Part 7–8, Challenge Authority / Human Oversight | GROUND | Same human-in-the-loop taxonomy as Product Architecture Three-Tier Boundary — unify vocabulary across both docs, currently described twice with different words for the same idea |
| Rest | KEEP | Original synthesis |

### 2.7 Foundational Reasoning V4

**No rename pass.** This document is explicitly the reasoning trail, not a spec — its value is preserving what was actually decided and why, in the words used at the time. Editing it defeats its purpose.

Instead: append one new numbered section (§25) at the end, logging this grounding phase itself — what was mapped to what, and why — consistent with how every prior phase was logged. This keeps the CTO/LLM context document complete without disturbing history.

---

## 3. Memory Types — Cognitive Science Mapping (worked example)

Shows how the mapping exercise should read once done. Use this as the template for other tables.

| Company Brain Memory Type | Cognitive Science Analog | Fit | Note |
|---|---|---|---|
| Factual Memory | Semantic Memory (Tulving, 1972) | Clean | Stable facts about the world, no personal/temporal anchor |
| Interaction Memory | Episodic Memory (Tulving, 1972) | Clean | Time- and context-anchored events |
| Action Memory | Procedural Memory (Squire 2004; Anderson, ACT-R) | Clean | "How it's done," observed execution |
| Commitment Memory | — | No analog | Future-oriented; describes intended, not observed, reality. Individual human cognition has no equivalent — this is organizational-specific. Ground instead in Language/Action Perspective (#2). **Keep custom name.** |
| Learning Memory | — | Partial | Individual cognition has no org-learning equivalent. Ground in Argyris & Schön (#7) instead of cognitive science. **Keep custom name.** |

Two of five types are genuinely novel. That's a good finding, not a gap — it tells you exactly where the real IP is.

---

## 4. The VSM Compression Test

One required exercise before finalizing renames:

1. Take Beer's 5 subsystems (Operations, Coordination, Control, Intelligence, Policy).
2. Try to re-derive the 7-layer pipeline (Capture→Understand→Memory→Intelligence→Execution→Exposure→Evolution) as a specialization of the 5.
3. Expected result: Capture+Understand ≈ System 1/2 sensing function; Execution ≈ System 1; Intelligence layer ≈ System 4 (environment scanning); Trust/Governance ≈ System 5 (policy/identity); Evolution ≈ System 3-4 feedback loop.
4. Memory and Exposure as *first-class, named layers* have no direct VSM equivalent — VSM assumes memory and delivery implicitly inside its channels. This is where Company Brain genuinely extends VSM for an AI-native context.
5. Write this up explicitly: "we adopt VSM's viability logic, and we extend it with two layers VSM left implicit — Memory and Exposure — because in an AI-native org, those can no longer stay implicit."

That one paragraph, cited, does more for the "too complex" complaint than any glossary — it gives the team a 50-year-old mental model to hang the new one on, plus a one-sentence reason for the two new layers.

---

## 5. What Explicitly Does Not Get Renamed (Original IP — protect these)

- Drift Detection (Drift Candidate → Pattern → Signal → Severity pipeline) — no academic or industry equivalent found
- Commitment Memory as a first-class memory type — extension beyond Language/Action Perspective, which treats commitments as events, not as a persistent memory store with its own lifecycle
- Learning Memory as an org-level (not individual-level) memory type
- Brain Score, Agent Readiness — Intelligence Architecture Part 15 output types
- Right Memory, Right Moment (Principle 8) and the Exposure Layer as a first-class architectural responsibility
- Knowledge Exchange / Brain-to-Brain Interoperability as a strategic direction (governed cross-org knowledge movement, not just format compatibility)

These stay named as-is. Do not force-fit a citation. Where asked "what's genuinely new here," this is the list to point at.

---

## 6. Open Knowledge Format (OKF) — Adoption

**"Open Knowledge Format / OKF"** appears in Architecture & Vision §9, Ontology §2, Memory Model §4, Product Architecture §5 — currently our own internal term for a compatibility concept.

**Decision: adopt Google Cloud's Open Knowledge Format (OKF) v0.1 directly**, published June 12, 2026 — markdown + YAML frontmatter, Apache 2.0, open specification, already shipping reference tooling (enrichment agents, visualizers). Rather than maintain a parallel internal spec under the same name, Company Brain's Knowledge Exchange layer standardizes on the real, public OKF.

**Mapping:**
- Composite Knowledge Object → OKF concept document (single required field: `type`; body is free-form markdown).
- Knowledge Object relationships → standard markdown links between OKF concept files, forming the graph.
- Company Brain adds on top, since OKF deliberately leaves these undefined: Trust tiers, Provenance (who asserted, when, under what authority), Contradiction/conflict semantics (Current vs Superseded), Confidence and decay.

This is the correct division of labor: OKF solves *portability* (any producer, any consumer, no SDK required). Company Brain's Trust & Governance and Memory Model layers solve *governance* — a problem OKF v0.1 explicitly states is still open design space. Brain-to-Brain Interoperability (Product Architecture §5) becomes: two Company Brain instances exchanging OKF-formatted Composite Knowledge Objects, each wrapped in Company Brain's own provenance and trust metadata.

Net effect: our exposure/interop story gains a live, external, multi-vendor ecosystem instead of a hypothetical one, at zero cost to the parts of the architecture that are genuinely ours (trust, provenance, conflict resolution, decay).

---

## 7. Deliverables Of This Phase

Six outputs. All conceptual, none technical.

1. **`Company_Brain_Theoretical_Foundations_v1.md`** — new canonical document. One section per field in §1, each with: source citation, one-paragraph summary, explicit mapping to Company Brain concepts, confidence of fit (clean / partial / none).
2. **Vocabulary Rename Table** — old term → new/retained term → source → which doc(s) affected. Delivered as an appendix inside Theoretical Foundations, not a separate doc.
3. **Updated canonical documents** — same 7 docs, same architecture, terminology and citations updated per §2. Version bump only (e.g. Architecture & Vision v2.2 → v2.3). No structural changes.
4. **One-page "Company Brain on One Page"** — VSM-style diagram, 5-to-7 layer mapping from §4, built for a non-technical reader (exec/investor/new hire). This is the direct fix for the team's complexity complaint.
5. **OKF Adoption Mapping** — one page, formalizes §6: Composite Knowledge Object → OKF concept document field mapping, plus what Company Brain layers on top (trust, provenance, conflict, decay). Feeds directly into Knowledge Exchange sections of Memory Model and Product Architecture.
6. **Bibliography.md** — full reference list (below), permanently attached to the project, cited by short-form (Author, Year) everywhere else.

---

## 8. Working Method

1. **OKF adoption mapping (1–2 days):** formalize §6 — Composite Knowledge Object field mapping to OKF's `type`/markdown structure, plus what Company Brain layers on top. Do first, since Knowledge Exchange language elsewhere depends on it.
2. **Draft (1 week):** Theoretical Foundations doc — one field at a time, in the order listed in §1 (highest-leverage fields first: VSM, Language/Action Perspective, DEMO, Organizational Memory Theory).
3. **Compression test (2–3 days):** §4 exercise, written up as its own subsection.
4. **Rename pass (1 week):** apply §2 table to each of the 6 living canonical docs (not Foundational Reasoning — append-only per §2.7). Version-bump each.
5. **One-pager (2–3 days):** build the VSM-mapped single page from the compression test output.
6. **Internal review:** re-share with the team that flagged complexity. Test: can a technical hire outside the project recognize 70%+ of the vocabulary unaided? If not, iterate rename pass before moving on.
7. **Freeze.** Only after step 6 passes, resume Technical Architecture — implementers now have field-tested prior art to build against instead of only internal docs.

Total estimate: ~3–4 weeks conceptual work, zero engineering.

---

## 9. Bibliography

**Cybernetics / Systems**
- Beer, S. (1972). *Brain of the Firm*. Allen Lane. (2nd ed. 1981, John Wiley & Sons.)
- Beer, S. (1979). *The Heart of Enterprise*. John Wiley & Sons.
- Beer, S. (1985). *Diagnosing the System for Organizations*. John Wiley & Sons.

**Language/Action & Speech Acts**
- Winograd, T., & Flores, F. (1986). *Understanding Computers and Cognition: A New Foundation for Design*. Ablex Publishing.
- Austin, J.L. (1962). *How to Do Things with Words*. Oxford University Press.
- Searle, J. (1969). *Speech Acts: An Essay in the Philosophy of Language*. Cambridge University Press.

**Enterprise Ontology**
- Dietz, J.L.G. (2006). *Enterprise Ontology: Theory and Methodology*. Springer.
- Dietz, J.L.G., & Mulder, H.B.F. (2020). *Enterprise Ontology: A Human-Centric Approach to Understanding the Essence of Organisation*. Springer.

**Organizational Memory & Learning**
- Walsh, J.P., & Ungson, G.R. (1991). Organizational Memory. *Academy of Management Review*, 16(1), 57–91.
- Argyris, C., & Schön, D. (1978). *Organizational Learning: A Theory of Action Perspective*. Addison-Wesley.
- Argyris, C., & Schön, D. (1996). *Organizational Learning II: Theory, Method, and Practice*. Addison-Wesley.
- Nonaka, I., & Takeuchi, H. (1995). *The Knowledge-Creating Company: How Japanese Companies Create the Dynamics of Innovation*. Oxford University Press.
- Weick, K. (1979). *The Social Psychology of Organizing* (2nd ed.). Addison-Wesley.
- Weick, K. (1995). *Sensemaking in Organizations*. Sage Publications.

**Organizations as Information Processors**
- March, J., & Simon, H. (1958). *Organizations*. John Wiley & Sons.
- Simon, H. (1960). *The New Science of Management Decision*. Harper & Row.
- Galbraith, J. (1977). *Organization Design*. Addison-Wesley.

**Cognitive Memory Systems**
- Tulving, E. (1972). Episodic and Semantic Memory. In E. Tulving & W. Donaldson (Eds.), *Organization of Memory*. Academic Press.
- Squire, L.R. (2004). Memory Systems of the Brain: A Brief History and Current Perspective. *Neurobiology of Learning and Memory*, 82(3), 171–177.
- Anderson, J.R. — ACT-R cognitive architecture (procedural/declarative memory distinction), ongoing body of work, act-r.psy.cmu.edu.

**Enterprise Architecture Standards**
- Zachman, J.A. (1987). A Framework for Information Systems Architecture. *IBM Systems Journal*, 26(3), 276–292.
- The Open Group. *TOGAF Standard*, 10th Edition. opengroup.org.

**Knowledge Representation Standards**
- Gruber, T. (1993). A Translation Approach to Portable Ontology Specifications. *Knowledge Acquisition*, 5(2), 199–220.
- W3C. Resource Description Framework (RDF) and Web Ontology Language (OWL) specifications. w3.org.
- Google Cloud (2026). Open Knowledge Format (OKF) v0.1 — open specification, published June 12, 2026. cloud.google.com/blog/products/data-analytics/how-the-open-knowledge-format-can-improve-data-sharing.

**Agent Interoperability & Provenance**
- Anthropic (2024). Model Context Protocol — introduced November 2024; stewarded by the Agentic AI Foundation (Linux Foundation) since December 2025. modelcontextprotocol.io.
- Google. Agent2Agent (A2A) Protocol.
- W3C. PROV-O: The PROV Ontology. w3.org/TR/prov-o/.

**Human-AI Autonomy**
- Human-in-the-loop / human-on-the-loop / human-out-of-loop autonomy-level taxonomy — standard vocabulary in human-AI interaction and human factors literature; apply to Three-Tier Boundary (Always/Ask First/Never) and Human Oversight Authority.

---

## One-Sentence Summary

This phase does not add anything to the Company Brain — it finds the 50 years of prior art already sitting under most of it, cites it, renames what can be renamed, and leaves clearly labeled what genuinely can't, so the team can understand the architecture in one meeting and the technical phase has field-tested ground to build on.
