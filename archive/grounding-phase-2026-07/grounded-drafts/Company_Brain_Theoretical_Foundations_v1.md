# Company Brain — Theoretical Foundations

## Version 1.0 — Grounding Phase Deliverable 2 of 6

### Status
Draft — Conceptual grounding only. Not a technical document.

### Depends On
Architecture & Vision v2.3, Ontology v1.3, Memory Model v1.3, Product Architecture v2.2, Intelligence Architecture v1.1, Trust & Governance Architecture v1.1

### Purpose

This document does not add anything to the Company Brain architecture. For each of 13 fields, it states the underlying theory or standard on its own terms first — plainly enough that a reader with zero Company Brain context could understand the theory from that paragraph alone — and only then shows how Company Brain's architecture relates to it: as a direct implementation, as an extension the original theory didn't anticipate, or, in a few cases, as a deliberate divergence. Its job is threefold: replace "here's a citation that relates to this" with "here's the theory, and here's exactly how we stand on it"; give a new hire the actual reasoning chain instead of a reading list; and clearly flag the handful of places where no real parent theory exists, so the team knows exactly where the genuine intellectual property sits.

No architectural decision changes as a result of this document. Only exposition, framing, and (where explicitly marked GROUND in the source touch-map, Master Plan §2) terminology do.

---

## How To Read This Document

Each of the 13 fields below follows the same three-part structure:

1. **The Theory** — stated plainly, standalone, citation attached. No Company Brain vocabulary yet.
2. **The Bridge** — how Company Brain's architecture relates to that theory, mapped to the specific document and section it grounds.
3. **The Relationship** — stated explicitly, one of three shapes: **we implement this directly**, **we extend this to handle something the theory didn't anticipate**, or **we diverge from this, and here's why**. Never left implicit.

A **Fit** rating (Clean / Partial / None) closes each field, carried over from the prior version of this document for continuity with `RECOGNIZABILITY_TEST_SHEET.md` and `COVERAGE_CHECK.md`.

Fields are ordered by explanatory leverage over the architecture, per Master Plan §1 — highest first. Four fields carry the strongest relationship to the architecture and are marked **[Priority]**: Organizational Memory Theory, Enterprise Ontology/DEMO, the Viable System Model, and Organizational Learning Theory. The other nine range from clean extensions to background context — each is stated honestly rather than stretched to match the strongest four.

---

## Field 1 — Management Cybernetics: The Viable System Model **[Priority]**

### The Theory

In 1972, management scientist Stafford Beer proposed the **Viable System Model (VSM)**: any system that must maintain its own existence over time — a company, a body, a nervous system, a country — needs the same five interacting subsystems, regardless of what the system is made of. **System 1 (Operations)** is the units that actually do the work. **System 2 (Coordination)** keeps those units from working against each other. **System 3 (Control)** manages internal resources and day-to-day regulation. **System 4 (Intelligence)** scans the environment and looks forward — what's coming, what should we do about it. **System 5 (Policy)** holds identity and ultimate authority — what the system is, and what it will and won't allow. Beer's further claim, formalized as **Ashby's Law of Requisite Variety**, is that a system survives only if it has enough internal variety (range of possible responses) to absorb the variety of disturbances its environment throws at it — and that viability depends on functioning feedback loops connecting all five subsystems continuously, not on any one subsystem alone. Beer explicitly describes this as making the organization a "living organism," not a metaphor Company Brain invented.

### The Bridge

Company Brain's seven-layer pipeline (Architecture & Vision v2.3 §7: Capture → Understand → Memory → Intelligence → Execution → Exposure → Evolution) is a direct application of VSM's viability logic to an AI-native organization, run through the explicit **VSM Compression Test** below (§14) to check the mapping rather than assert it. Five of the seven layers compress cleanly onto VSM's five subsystems: Capture+Understand implements the System 1/2 sensing function, Execution implements System 1 directly, Intelligence implements System 4 directly, Evolution implements the System 3–4 feedback/audit function, and Trust & Governance (a supporting system, not one of the seven layers) implements System 5. Two layers — Memory and Exposure — have no VSM equivalent at all, because VSM was written for organizations made of people, where memory and delivery happen implicitly through human continuity and informal communication norms. An AI actor gets neither for free.

### The Relationship

**We implement VSM's viability logic directly for five of seven layers, and we extend it for the remaining two.** This is stated as an explicit extension, not a deviation: VSM assumed memory and delivery would stay implicit because it was modeling human organizations; Company Brain makes them first-class, architected layers because it is modeling an AI-native one. The full compression exercise, including where the mapping holds and where it doesn't, is worked through in §14 below.

**Fit:** Clean for the organism framing and the general viability logic; the seven-layer pipeline itself is a direct implementation for five layers and a stated extension for two — see the Compression Test.

---

## Field 2 — Language/Action Perspective

### The Theory

Terry Winograd and Fernando Flores, in *Understanding Computers and Cognition* (1986), argue that organizational coordination is not fundamentally about information moving between people — it's linguistic. Work gets done through a recurring conversational structure they call the "conversation for action": one party makes a **Request**, another makes a **Promise** to fulfill it, the work happens, the responsible party gives a **Report**, and the requester gives an **Accept**. The commitment created at the Promise step isn't incidental to this conversation — it is the atomic unit the whole conversation exists to create and track. On this view, an organization is best understood as a network of commitments between people, not a network of documents or information flows.

### The Bridge

Company Brain's Commitment primitive and Commitment Memory lifecycle (Architecture & Vision v2.3 §5, §10) implement Winograd & Flores's Request→Promise→Report→Accept loop directly as their core shape: Requested maps to Request, Promised maps to Promise, and Fulfilled maps to Accept following a Report. But the eight-state lifecycle doesn't stop there — it adds Delegated, Renegotiated, Cancelled, and Breached, four real-world exit paths the original four-part conversational loop has no name for. Winograd & Flores modeled a single conversation happening once; Company Brain needed a persistent record that survives across days or months, gets handed off between people, changes scope mid-flight, or simply expires unresolved.

### The Relationship

**We implement the conversation-for-action loop directly for the core three states, and we extend it with four additional states the original theory has no equivalent for.** The extension exists because Winograd & Flores were describing a live conversation, not a stored, stateful record — Commitment Memory as a persistent memory type with its own lifecycle is Company Brain's addition on top of their model, not a restatement of it (see Master Plan §5).

**Fit:** Clean for the coordination-as-commitment framing and the conversational loop as the direct ancestor of the first three lifecycle states; the four additional states are an explicit, named extension.

---

## Field 3 — Speech Act Theory

### The Theory

J.L. Austin's *How to Do Things with Words* (1962) makes the case that some utterances don't describe the world — they act on it. Saying "I promise" under the right conditions doesn't report an obligation, it creates one; Austin calls these **performatives**. John Searle's *Speech Acts* (1969) formalizes this into a taxonomy: **commissives** commit the speaker to a future action (a promise), **directives** attempt to get someone else to act (a request), and there are several other categories besides. This is the philosophy-of-language foundation underneath Field 2 — Winograd & Flores's conversation-for-action loop is, formally, a sequence of commissive and directive speech acts.

### The Bridge

Every Commitment created in Company Brain is, in Searle's terms, the product of a commissive speech act (someone promising) or a directive one (someone requesting a promise). This isn't a separate mechanism from Field 2 — it's the formal layer underneath it, cited here so the Commitment/Communication primitives (Architecture & Vision v2.3 §5) aren't resting on an ad hoc distinction between "asking" and "committing."

### The Relationship

**We implement this directly, one level below Field 2** — Company Brain doesn't add anything Austin and Searle didn't already formalize; it applies their categories to organizational Communication and Commitment records.

**Fit:** Clean, as the formal underpinning of Field 2 — not an independent grounding point in its own right.

---

## Field 4 — Enterprise Ontology / DEMO **[Priority]**

### The Theory

Jan Dietz's **DEMO** (Design & Engineering Methodology for Organizations), formalized in *Enterprise Ontology: Theory and Methodology* (2006) and extended in Dietz & Mulder (2020), models an organization as a network of **transactions** between an initiator and an executor. Every transaction follows the same fixed pattern: a sequence of **coordination-acts** (request, promise, accept — the talking) that wraps a single **production-act** (the actual work). Dietz's central and most load-bearing claim is methodological: an organization's essential model — what it fundamentally is — should be described completely independent of how it happens to be implemented. DEMO calls this the separation of the "essential" layer (coordination and production acts) from the "informational" and "documental" layers (the systems and paperwork that happen to support it today). An organization's essence doesn't change when you swap out its software.

### The Bridge

Company Brain's Ontology document is, in its entirety, a direct application of Dietz's essential-layer principle: Ontology v1.3 §2 states plainly that the Company Brain "does not model documents, software, databases, or dashboards as primary concepts" — those are representations, exactly Dietz's point about the informational/documental layers being secondary to the essential one. Ontology's four-layer structure (Atomic Primitives → Core Objects → Organizational Structures → Operational Constructs, §3) is Company Brain's own decomposition, arrived at independently (Foundational Reasoning V4, Chapter 10), but it lands on the same shape as DEMO's Cooperation-act/Production-act/Process/Fact Model split: a small set of atomic coordination units composing upward into the concrete objects an organization actually reasons about. And DEMO's coordination-act/production-act split is the direct ancestor of Ontology's own Policy/SOP/Workflow disambiguation (§3): Policy is the constraint, SOP is the designed sequence of coordination and production, Workflow is what was actually produced — DEMO's performa/informa/forma distinction, applied.

### The Relationship

**We implement Dietz's implementation-independence principle directly, and the four-layer structure is an independently-derived parallel to DEMO's own layering, not an exact copy of it.** Company Brain's ten atomic primitives were discovered through separate literature research and product reasoning (Foundational Reasoning V4, Chapter 10) that converged on DEMO's shape rather than starting from it — worth stating honestly rather than claiming Company Brain built directly on top of DEMO's specific transaction pattern. Where the parallel is closest — coordination-acts vs. production-acts — Company Brain implements it directly in the Policy/SOP/Workflow split.

**Fit:** Clean for the implementation-independence philosophy (direct implementation) and for the coordination/production-act split underlying Policy/SOP/Workflow (direct implementation); Partial for the four-layer structure as a whole (independently-derived parallel, not an exact copy).

---

## Field 5 — Organizational Memory Theory **[Priority]**

### The Theory

J.P. Walsh and G.R. Ungson, in "Organizational Memory" (*Academy of Management Review*, 1991), give the first formal academic definition and taxonomy of what it means for an organization to remember. Their core claim: organizations retain stored information from their own history that can be brought to bear on present decisions, and that information is retained through five **retention facilities** — **individuals** (what people personally remember), **culture** (shared norms and stories), **transformations** (standard procedures for converting inputs to outputs), **structures** (roles and formal relationships), and **external archives** (records kept outside the organization, e.g. by regulators or the press). Organizational memory, on this account, moves through three processes: **acquisition** (information enters one or more facilities), **retention** (it persists there), and **retrieval** (it's brought back out when needed).

### The Bridge

Company Brain's Memory Model implements Walsh & Ungson's core claim directly: Memory Model v1.3 §3's definition — "a persistent, structured representation of organizational reality through time" — is the same claim their 1991 paper formalized, not a novel one. But Company Brain does not adopt their five-facility taxonomy; it uses a different, more operational five-type taxonomy instead (Factual, Interaction, Commitment, Action, Learning), organized around *what kind of thing is being remembered* rather than *where it physically lives*. The two taxonomies are compatible, not identical, and it's worth being precise about why they diverge here rather than papering over it: Walsh & Ungson were describing how human organizations retain memory informally, across people, culture, and paper archives that pre-existed any attempt to architect them. Company Brain is *building* the retention facility, not describing an existing informal one — so it organizes memory by the questions the organization needs answered (what do we know, why do we know it, who owes what to whom, what happened, what did we learn) rather than by where the memory happens to sit. Two of the five Company Brain types have no Walsh & Ungson facility to map onto at all: **Commitment Memory** (future-oriented — no retention facility describes an obligation that hasn't happened yet) and **Learning Memory** (Walsh & Ungson's facilities describe static retention, not the update-the-rule loop Company Brain's Learning Memory performs — that mechanism is grounded separately in Field 7, Argyris & Schön).

### The Relationship

**We implement Walsh & Ungson's definition of organizational memory directly, and we diverge from their five-facility taxonomy by design**, replacing it with a taxonomy organized by question-answered rather than location-of-retention — because Company Brain is architecting the retention mechanism from scratch rather than describing one that already exists informally. Two of five memory types (Commitment, Learning) further **extend** beyond anything the 1991 theory anticipated, since it was written before "obligation as a first-class, stateful memory record" or "organizational rule-correction as a memory type" were questions that needed answering.

**Fit:** Clean for the core definition (direct implementation). Deliberate divergence, not a gap, on the five-type taxonomy — three of five types happen to also map cleanly onto a *different* body of theory (cognitive memory systems, Field 10); two do not map onto anything and are Company Brain's own contribution.

---

## Field 6 — Knowledge Creation Theory (SECI)

### The Theory

Ikujiro Nonaka and Hirotaka Takeuchi, in *The Knowledge-Creating Company* (1995), describe organizational knowledge creation as a continuous conversion cycle between **tacit knowledge** (know-how and experience, hard to write down) and **explicit knowledge** (codified, transferable, written). The cycle has four modes: **Socialization** (tacit to tacit, through shared experience — an apprentice watching a master), **Externalization** (tacit to explicit, through articulation — writing down what was previously just known), **Combination** (explicit to explicit, through recombining existing documented knowledge into something new), and **Internalization** (explicit to tacit, through practice — a written procedure becoming second nature). The cycle repeats, and each pass spirals organizational knowledge to a higher level.

### The Bridge

Company Brain's Capture → Understanding transition (Architecture & Vision v2.3 §8–9) is a narrow, specific instance of Nonaka & Takeuchi's Externalization mode: raw organizational activity — meetings, emails, decisions that exist only as lived experience — gets converted into structured Knowledge Objects, the explicit, codified form. Company Brain does not implement the full four-mode cycle; there's no architectural component that does Socialization (tacit-to-tacit) or Internalization (explicit-to-tacit) — those remain human processes the architecture doesn't touch.

### The Relationship

**We implement one mode (Externalization) of a four-mode theory directly, and we do not attempt the other three.** This is a partial application by design, not an oversight: Capture and Understanding are specifically about turning lived organizational activity into codified memory, which is exactly Externalization's job description — extending SECI to cover Socialization or Internalization would mean architecting something about how humans learn from each other directly, which is out of scope for a memory-and-intelligence system.

**Fit:** Partial — clean for the Externalization mapping specifically, not a claim about the full SECI cycle.

---

## Field 7 — Organizational Learning Theory **[Priority]**

### The Theory

Chris Argyris and Donald Schön, in *Organizational Learning: A Theory of Action Perspective* (1978) and *Organizational Learning II* (1996), distinguish two levels at which an organization can learn from error. **Single-loop learning** detects an error and corrects the action — the underlying rule or assumption that produced the error stays unquestioned. **Double-loop learning** goes a level deeper: it questions and revises the governing rule itself once errors recur, rather than just patching the latest instance. A thermostat that turns the heat on when it's cold is doing single-loop correction; a person who decides the target temperature itself is wrong is doing double-loop learning.

### The Bridge

Company Brain's Drift → Learning Memory pipeline implements this distinction directly, and the mapping is close to exact rather than approximate. When Intelligence Architecture v1.1 Part 10 detects a single Drift Candidate — one instance of executed reality diverging from designed policy — and it gets corrected in place, that is single-loop learning: the instance is fixed, the rule (the SOP or Policy) is untouched. When that divergence repeats often enough to become a confirmed Drift Pattern, and Memory Model v1.3 §13's Organizational Learning process routes it into Learning Memory as a policy-improvement candidate — which, through Memory Model's Write Governance, can actually change the Policy or SOP itself — that is double-loop learning, happening exactly as Argyris & Schön described it: the rule changes because the error recurred, not because any single instance demanded it.

### The Relationship

**We implement Argyris & Schön's single-loop/double-loop distinction directly**, using it as the literal mechanism distinguishing "fix this one Drift Candidate" from "change the Policy because the Drift Pattern keeps recurring" — not just an analogy layered on afterward. Company Brain's specific pipeline shape (Drift Candidate → Pattern → Signal → Severity, and the Learning Memory write-governance gate) is Company Brain's own engineering of *how* double-loop learning gets triggered and approved — Argyris & Schön describe the phenomenon, not a four-stage evidence-threshold pipeline or a governance gate on rule changes, so that mechanical detail is a genuine extension, not something borrowed.

**Fit:** Clean — one of the two or three strongest fits in the entire document. The distinction does real explanatory work for the Drift/Learning Memory pipeline, not decorative work.

---

## Field 8 — Sensemaking Theory

### The Theory

Karl Weick, across *The Social Psychology of Organizing* (1979) and *Sensemaking in Organizations* (1995), argues that organizations don't perceive a pre-existing, objective environment and then react to it. Instead, people act first — often on ambiguous, incomplete information — and only afterward retrospectively construct a shared, meaningful account of what happened and why. Weick calls the acting-first part **enactment**: the environment an organization responds to is partly one it created through its own prior actions, not a fixed backdrop that existed independently. Meaning, on this account, is made after the fact, socially, not read directly off reality.

### The Bridge

Company Brain's Understanding Layer (Architecture & Vision v2.3 §9) implements this directly: its whole job is turning raw, ambiguous captured activity into "what does this mean?" — a sensemaking operation in Weick's precise sense, not a lookup or extraction operation. Ontology v1.3 §4's Context Model implements the same idea at the data-modeling level: Context is explicitly **not** a stored primitive — it's generated on demand from Goals, Rules, Relationships, History, Actions, Commitments, Time, and Resources, exactly matching Weick's claim that meaning is constructed from surrounding conditions rather than filed away as a fact. Memory Model v1.3 §12's Memory Drift concept also depends on Weick's enactment idea for its explanatory power on the *why*-side: the gap between designed and executed reality exists because organizational actors enact their environment moment to moment rather than simply following the design — Argyris & Schön (Field 7) explains how that gap gets corrected, but Weick explains why it opens up in the first place.

### The Relationship

**We implement Weick's sensemaking framing directly for the Understanding Layer and the Context Model** — these aren't loosely inspired by sensemaking, they're built to do exactly what Weick describes meaning-making as being. For Memory Drift, **we rely on Weick to explain the cause and on Argyris & Schön to explain the correction** — two different theories doing two different jobs in the same mechanism, stated explicitly so neither is stretched to cover the other's part.

**Fit:** Clean for the Understanding Layer and Context Model (direct implementation). For Memory Drift, Weick explains the cause-side only; Field 7 covers the correction-side — together, not interchangeably.

---

## Field 9 — Information-Processing View of Organizations

### The Theory

James March and Herbert Simon, in *Organizations* (1958), and Jay Galbraith, in *Organization Design* (1977), model organizations as **bounded-rational information processors**: no individual or organization can process unlimited information, so organizations build structure, hierarchy, and standard routines specifically to manage that limit and reduce uncertainty. Structure isn't there for its own sake — it exists because information-processing capacity is finite and uncertainty has to go somewhere.

### The Bridge

Company Brain's founding problem statement (Architecture & Vision v2.3 §2: "Organizations Do Not Have Reliable Memory") implements this framing directly rather than asserting it as a novel observation. The claim that organizations compensate for fragmented knowledge through human continuity — people remembering who knows what, why decisions were made, how exceptions get handled — is a specific, applied instance of the bounded-rational information-processing problem March, Simon, and Galbraith formalized decades ago: humans are the organization's fallback information-processing mechanism precisely because no other mechanism exists to absorb that uncertainty. Company Brain doesn't extend this theory technically; it uses it to establish that the problem being solved is a real, well-studied one, not a Company Brain invention.

### The Relationship

**We implement this framing directly as the problem statement's theoretical grounding** — no extension or divergence to note; this field's job is establishing that "organizations struggle to retain and use their own knowledge" is an old, well-documented finding, which is exactly what it's cited for.

**Fit:** Clean for the problem framing. This is background-establishing grounding, not mechanism-level grounding — it explains why the problem exists, not how any specific layer works.

---

## Field 10 — Cognitive Memory Systems Taxonomy

### The Theory

Endel Tulving's "Episodic and Semantic Memory" (1972) distinguishes **semantic memory** (general facts about the world, no personal or temporal anchor — "Paris is the capital of France") from **episodic memory** (memories of specific events anchored in time and place — "the meeting where we decided to launch in Paris"). Larry Squire's later survey work (2004) extends this into a broader taxonomy that adds **procedural memory** — skills and "how to" knowledge, often not consciously articulable. John Anderson's ACT-R cognitive architecture operationalizes a closely related procedural/declarative split computationally.

### The Bridge

Three of Company Brain's five memory types implement this taxonomy directly, term-for-term: **Factual Memory** (people, resources, policies — no personal/temporal anchor) is semantic memory; **Interaction Memory** (discussions, decisions, negotiations — anchored in a specific time and context) is episodic memory; **Action Memory** (what was actually executed) is procedural memory. Two types have no equivalent here at all: **Commitment Memory** and **Learning Memory**. No individual human's cognitive architecture has a memory system for "an obligation another person owes me" or "what this organization, as a collective, has learned" — those aren't things a single brain needs to track, but an organization does.

### The Relationship

**We implement this taxonomy directly for three of five memory types, and we diverge from it entirely for the other two** — not because the theory is incomplete, but because it describes individual cognition and Company Brain is modeling organizational-level memory, where two genuinely new categories exist that no individual mind needs. This divergence is the clearest single piece of evidence in this document for where Company Brain's real intellectual property sits (Master Plan §5): the two memory types with no cognitive-science parent are original.

**Fit:** Clean for 3 of 5 types (direct implementation). Deliberate divergence — not a gap — for Commitment and Learning Memory, which are organizational-level constructs, grounded instead in Fields 2 and 7 respectively.

---

## Field 11 — Enterprise Architecture Standards

### The Theory

John Zachman's "A Framework for Information Systems Architecture" (1987) organizes everything that can be said about an enterprise along six interrogatives — **Who, What, Where, When, Why, How** — crossed against several levels of abstraction from high-level scope down to working implementation. The Open Group's TOGAF standard operationalizes a similar comprehensive-coverage philosophy into a full, widely-used enterprise-architecture development method.

### The Bridge

Company Brain's ten Atomic Primitives (Architecture & Vision v2.3 §5) implement Zachman's interrogative-based naming convention directly at the "Key Question" column: Actor answers Who, Communication answers What-was-communicated, Commitment answers Who-owes-what-to-whom, Time answers When, Goal answers Why. Two of Company Brain's ten primitives — State and Relationship — extend past Zachman's six interrogatives, which don't include a dedicated question for "what condition is this in" or "how is this connected to that."

### The Relationship

**We implement Zachman's interrogative convention directly for eight of ten primitives, and we extend it with two questions (State, Relationship) Zachman's six-cell grid doesn't ask.** Company Brain does not adopt Zachman's abstraction-level rows or TOGAF's full development method — only the interrogative-question convention at the primitive-naming level.

**Fit:** Clean for the interrogative-based naming convention (direct implementation, mostly); Partial for the framework as a whole (Company Brain uses one dimension of Zachman's two-dimensional grid, not the full framework).

---

## Field 12 — Formal Ontology / Knowledge Representation Standards

### The Theory

Tom Gruber's 1993 paper gives the definition still cited as canonical today: an **ontology** is "an explicit specification of a conceptualization" — a formal, shareable statement of what categories of thing exist in a domain and how they relate. The W3C's **RDF** and **OWL** specifications operationalize this into a concrete graph-based convention: knowledge is expressed as **subject–predicate–object triples** (e.g., "Person — belongs to — Team"), with formally typed relationships connecting them into a traversable graph. Separately and much more recently, Google Cloud's **Open Knowledge Format (OKF) v0.1** (published June 12, 2026, verified real via web search) is a narrow, portability-only interchange format: knowledge bundles as directories of markdown files with a small YAML frontmatter (only `type` required), designed so any producer can write a bundle and any consumer can read it without a shared SDK.

### The Bridge

Company Brain's Ontology document implements Gruber's definition directly — it exists precisely to give an explicit, shared specification of what exists in organizational reality (Ontology v1.3 §1). The Relationship Model's From/Relationship/To structure (Ontology v1.3 §6, Memory Model v1.3 §11) implements RDF's subject-predicate-object triple convention directly, just under plainer column names. OKF is a different kind of relationship entirely: rather than citing it as an analogy, Company Brain has **adopted it directly** as its Knowledge Exchange interchange format (Master Plan §6) — Composite Knowledge Objects export as OKF concept documents, full field mapping in the companion `OKF_Adoption_Mapping.md`.

### The Relationship

**We implement Gruber's ontology definition directly, we implement RDF's triple convention directly (with plainer labels), and we have adopted OKF wholesale as external infrastructure rather than grounding it as a theory Company Brain merely resembles.** OKF explicitly leaves trust, provenance, conflict, and decay as open design space; Company Brain's own layers fill that space without needing to modify or fork the spec.

**Fit:** Clean for Gruber's definition and the RDF-style relationship convention (both direct implementations). OKF is an adoption, not a fit rating — see `OKF_Adoption_Mapping.md` for the concrete division of labor between what OKF covers (portability) and what Company Brain covers (trust, provenance, conflict, decay).

---

## Field 13 — Agent Interoperability & Provenance Standards

### The Theory

The **Model Context Protocol (MCP)**, introduced by Anthropic in November 2024, standardizes how AI applications connect to external tools, data sources, and context — verified via web search to now be stewarded by the **Agentic AI Foundation**, a Linux Foundation directed fund co-founded by Anthropic, Block, and OpenAI, since December 2025. Google's **Agent2Agent (A2A) protocol**, donated to the Linux Foundation in June 2025, standardizes discovery and communication between AI agents built by different vendors. Separately, the W3C's **PROV-O** is a formal vocabulary for describing provenance — where a piece of information came from and who's responsible for it — built on three core relations: `wasGeneratedBy` (an entity was produced by a specific activity), `wasAttributedTo` (an entity is the responsibility of a specific agent), and `wasDerivedFrom` (an entity was derived from another entity).

### The Bridge

Company Brain has **adopted MCP and A2A directly** as its Agent Access exposure layer (Product Architecture v2.2 §5) — the Company Brain is built as an MCP provider, not merely a consumer, and is A2A-discoverable; this is infrastructure Company Brain runs on, not a theory it merely resembles. PROV-O is grounded differently: Company Brain's provenance fields **implement** its three-relation structure directly, mapped by *question* rather than loosely borrowed — `wasAttributedTo` answers who asserted a Memory record or who approved/acted in Execution; `wasGeneratedBy` answers when and by what activity, across Memory, Intelligence, and Execution; `wasDerivedFrom` answers what source or evidence a record traces back to. This same three-way mapping appears identically in Memory Model v1.3 §8 and Trust & Governance v1.1 Part 4.

### The Relationship

**We have adopted MCP and A2A directly as exposure infrastructure, and we implement PROV-O's three-relation vocabulary directly, mapped per-question rather than per-layer**, so the same term means the same thing everywhere Provenance is discussed across the document set.

**Fit:** Clean for MCP/A2A (adopted infrastructure, not analogy) and for PROV-O (direct implementation) — the strongest single implementation in Trust & Governance Architecture v1.1, per Master Plan §2.6.

---

## VSM Compression Test

Per Master Plan §4, this is the required exercise before finalizing any VSM-related claims: attempt to re-derive Company Brain's seven-layer pipeline as a specialization of Beer's five VSM subsystems, and state plainly what does and doesn't fit — this is where Field 1's "we implement / we extend" claim gets checked, not just asserted.

**Beer's five subsystems:** System 1 (Operations), System 2 (Coordination), System 3 (Control), System 4 (Intelligence), System 5 (Policy).

**Company Brain's seven layers:** Capture → Understand → Memory → Intelligence → Execution → Exposure → Evolution.

**Attempted re-derivation:**

- **Capture + Understand implement System 1/2's sensing function.** VSM's Operations units and their coordinating channels are where an organization senses its own activity; Company Brain's Capture and Understand layers do the same sensing work, made explicit and continuous rather than left implicit in day-to-day operational channels.
- **Execution implements System 1 directly.** The units that do the organization's actual work.
- **Intelligence implements System 4 directly.** System 4's job is environmental scanning and future-facing awareness — exactly what Company Brain's Intelligence layer does over memory (Intelligence Architecture v1.1 Parts 7–10).
- **Trust & Governance implements System 5 directly**, sitting outside the pipeline the same way System 5 sits above, not inside, Systems 1–4. System 5 is policy, identity, and ultimate authority; Trust & Governance Architecture v1.1 plays that exact role.
- **Evolution implements a partial version of the System 3–4 feedback loop.** Comparing designed-vs-executed process and routing confirmed divergence back into Learning Memory (Memory Model v1.3 §13) resembles the System 3–4 audit/feedback channel, but VSM doesn't name a discrete layer for this the way Company Brain does — a partial, not exact, implementation.

**Where the re-derivation breaks down — Memory and Exposure:**

Memory and Exposure, as first-class, independently named layers, have no direct VSM equivalent. VSM assumes memory and delivery implicitly inside its channels — Beer never treats "what the organization remembers" or "how information reaches the right actor" as subsystems in their own right, because in a human organization those functions are diffused across people, culture, and ad hoc communication, not architected.

This is where Company Brain genuinely extends VSM for an AI-native context, stated explicitly in the exact form the exercise is meant to produce:

> **We adopt VSM's viability logic, and we extend it with two layers VSM left implicit — Memory and Exposure — because in an AI-native organization, those can no longer stay implicit.** A human organization's memory lives in people who move between roles and retain context informally; an AI actor has no such implicit continuity unless memory is made an explicit, architected layer. Likewise, a human organization's "delivery" of the right information to the right person happens through ambient human communication norms that no one designs directly; an AI actor requires exposure to be a first-class, engineered responsibility, because nothing else will surface the right memory at the right moment on its behalf.

This one paragraph, cited to Beer's 50-year-old model, is intended to do more for the team's "too complex" complaint than any glossary: it gives a recognizable mental model to hang the seven-layer pipeline on, and a one-sentence, principled reason for the two layers that don't come from that model — rather than leaving Memory and Exposure looking like arbitrary additions.

**Conclusion:** 5 of 7 layers (Capture/Understand, Execution, Intelligence, Evolution, and Trust & Governance as System 5 outside the pipeline proper) are direct or partial implementations of VSM's 5 subsystems. Memory and Exposure are not, and are the correct places to say "this is genuinely new," not the correct places to force a citation.

---

## Appendix — Vocabulary Rename Table

Per Master Plan §7.2, and updated per the team review's vocabulary pass. Legend: **IMPLEMENT** = Company Brain's term is a direct application of the source vocabulary; **EXTEND** = Company Brain's term builds on the source but adds something the theory didn't cover; **KEEP-JUSTIFIED** = a plainer or more conventional alternative exists and was considered, but Company Brain's own term is retained because it is at least as clear (reason given); **KEEP-ORIGINAL** = no external parent exists, not applicable.

| Old / Internal Term | Disposition | Source | Document(s) Affected |
|---|---|---|---|
| "Living organism" framing | IMPLEMENT | Beer (1972) | Architecture & Vision §3 |
| Seven-Layer Pipeline (as a whole) | IMPLEMENT (5 of 7 layers) + EXTEND (Memory, Exposure) | Beer (1972, 1979, 1985) | Architecture & Vision §7 |
| "Coordination Systems" | IMPLEMENT | Winograd & Flores (1986) | Architecture & Vision §4 |
| Commitment primitive / Commitment lifecycle | IMPLEMENT (core 3 states) + EXTEND (4 additional states) | Winograd & Flores (1986); Austin (1962); Searle (1969) | Architecture & Vision §5, §10 |
| "Ostensive-versus-performative gap" | **SWAPPED** → "designed-versus-executed gap," matching the plain-language term Company Brain already uses consistently in Ontology (SOP vs. Workflow) and Product Architecture (Drift Experience) | Dietz/DEMO's coordination-act/production-act split | Architecture & Vision §11 |
| Ontology philosophy ("abstracted from implementation") | IMPLEMENT | Dietz (2006, 2020) | Ontology §2 |
| Ontology four-layer structure | PARTIAL — independently-derived parallel, not a copy | Dietz (2006, 2020) | Ontology §3 |
| "Memory" (general definition) | IMPLEMENT | Walsh & Ungson (1991) | Memory Model §3 |
| Five Memory Types (Factual/Interaction/Commitment/Action/Learning) | KEEP-JUSTIFIED — plain, question-answering names read more clearly to a non-specialist than Walsh & Ungson's five retention facilities (individuals/culture/transformations/structures/archives) or cognitive science's semantic/episodic/procedural labels; the underlying concepts are cited (Fields 5, 10), the names stay Company Brain's own | Walsh & Ungson (1991); Tulving (1972); Squire (2004) | Memory Model §6 |
| Capture → Understanding transition | IMPLEMENT (Externalization only, of SECI's 4 modes) | Nonaka & Takeuchi (1995) | Architecture & Vision §8–9 |
| Drift → Learning Memory pipeline | IMPLEMENT (single/double-loop distinction) + EXTEND (the specific 4-stage pipeline and write-governance gate) | Argyris & Schön (1978, 1996) | Memory Model §12–13, Architecture & Vision §14, §16 |
| Understanding Layer / Context Model | IMPLEMENT | Weick (1979, 1995) | Architecture & Vision §9, Ontology §4 |
| "The Problem" (fragmented memory) | IMPLEMENT | March & Simon (1958); Galbraith (1977) | Architecture & Vision §2 |
| Primitive "Key Question" column | IMPLEMENT (8 of 10) + EXTEND (State, Relationship) | Zachman (1987); TOGAF 10th Ed. | Architecture & Vision §5 |
| "Ontology" (the word itself) | IMPLEMENT | Gruber (1993) | Ontology §1 |
| Relationship Model — "From / Relationship / To" columns | KEEP-JUSTIFIED — structurally identical to RDF's Subject/Predicate/Object triple, but plainer column labels read more naturally for non-technical stakeholders; noted explicitly rather than silently renamed | W3C RDF/OWL | Ontology §6, Memory Model §11 |
| Open Knowledge Format (OKF) | **Adopted directly** — no longer an internal placeholder term | Google Cloud OKF v0.1 (2026) | Architecture & Vision §9, Ontology §2, Memory Model §4, Product Architecture §5 |
| MCP governance language | Updated to reflect Agentic AI Foundation (Linux Foundation) stewardship since Dec 2025 | Anthropic/MCP; Agentic AI Foundation | Product Architecture §5 |
| Provenance fields (who asserted, when, from what source) | IMPLEMENT — mapped per-question: `wasAttributedTo`=who, `wasGeneratedBy`=when, `wasDerivedFrom`=source | W3C PROV-O | Memory Model §8, Trust & Governance Part 4 |
| Three-Tier Boundary (Always / Ask First / Never) | KEEP-JUSTIFIED — "Always/Ask First/Never" is a direct, plain-language instruction a product user acts on immediately; "human-in-the-loop/on-the-loop/out-of-loop" is the correct academic mapping (cited, and used to align this document with Trust & Governance's Human Oversight Authority) but reads as jargon in a product surface, so the plain names stay and the taxonomy is cited alongside them, not substituted in | Human-AI interaction literature (standard vocabulary, no single source) | Product Architecture §15, Trust & Governance Part 8 |
| Write Governance | KEEP-JUSTIFIED — more precise than the conventional "Access Control" (RBAC/ABAC's own term), since it names the specific concern (who may write memory) rather than access generally | RBAC / Zero Trust literature | Memory Model §9 |
| Governance Lifecycle (Proposed→Reviewed→Approved→Executed→Audited) | KEEP-JUSTIFIED — simpler than ITIL's own multi-stage change-management vocabulary (RFC, CAB approval, build, test, implement, review), same general shape, plainer labels | Generic ITIL-style change management | Trust & Governance Part 6 |
| Commitment Memory, Learning Memory | KEEP-ORIGINAL — no individual-cognition analog exists | — | Memory Model §6 |
| Drift Detection pipeline (Candidate→Pattern→Signal→Severity) | KEEP-ORIGINAL — no academic or industry equivalent found | — | Intelligence Architecture Part 10 |
| Brain Score, Agent Readiness | KEEP-ORIGINAL — original output types | — | Intelligence Architecture Part 15 |
| Right Memory, Right Moment (Principle 8), Exposure Layer | KEEP-ORIGINAL — no VSM or other equivalent; the explicit extension identified in the Compression Test | — | Architecture & Vision §6, §13 |
| Knowledge Exchange / Brain-to-Brain Interoperability | KEEP-ORIGINAL — strategic direction, not a format-compatibility claim | — | Product Architecture §5 |

Full source list with complete bibliographic detail: see the companion `Bibliography.md`.

---

## Field Strength Summary — Where "We Implement/Extend" Holds vs. Where It's Weaker

Honest accounting, since not every field earns the same strength of claim:

**Strong — supports "we implement this theory directly" for at least part of the mapping:** Field 1 (VSM — 5 of 7 layers), Field 2 (Language/Action Perspective — core 3 lifecycle states), Field 3 (Speech Act Theory — full), Field 4 (DEMO — implementation-independence and coordination/production-act split), Field 5 (Organizational Memory Theory — core definition), Field 7 (Argyris & Schön — the single/double-loop mechanism itself), Field 8 (Weick — Understanding Layer and Context Model), Field 9 (March/Simon/Galbraith — problem framing), Field 10 (cognitive memory taxonomy — 3 of 5 types), Field 11 (Zachman — 8 of 10 primitives), Field 12 (Gruber and RDF — both direct), Field 13 (PROV-O direct; MCP/A2A adopted as infrastructure, not merely theory).

**Weaker — supports only "we are consistent with this," not "we implement or extend it":** Field 6 (SECI) supports only a narrow, single-mode claim (Externalization) — Company Brain doesn't implement or extend the other three-quarters of Nonaka & Takeuchi's cycle, and shouldn't claim to. This is the one field in the document where "consistent with" is the honest ceiling, not "implements" or "extends."

**Sections with no theoretical claim at all, by design:** Intelligence Architecture's Parts 7–10 and 15 (Recommendation/Risk/Opportunity/Drift Intelligence, Brain Score, Agent Readiness) and the KEEP-ORIGINAL rows above carry no field mapping because none was found — these are Company Brain's actual original contribution, not a weak version of a strong field.

---

## What This Document Does Not Do

Consistent with the Master Plan's scope boundary: this document does not introduce any new architectural layer, primitive, memory type, or mechanism. Every field above states a real theory on its own terms and then says explicitly how Company Brain relates to it — implement, extend, or diverge — never leaving the relationship for the reader to infer. Where Master Plan §5 says KEEP, this document does not force a citation onto it — Drift Detection, Commitment Memory, Learning Memory, Brain Score, Agent Readiness, Right Memory/Right Moment, and Knowledge Exchange as a strategic direction remain exactly what they were: Company Brain's own contribution, not a renamed version of someone else's.
