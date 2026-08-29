# Company Brain — Open Knowledge Format (OKF) Adoption Mapping

Status: Draft — Grounding Phase Deliverable 1 of 6
Depends on: Architecture & Vision v2.3 §9, Ontology v1.3 §2–3, Memory Model v1.3 §4, Product Architecture v2.2 §5
Decision basis: Master Plan §6 (decided — Google Cloud's Open Knowledge Format v0.1 adopted as Company Brain's Knowledge Exchange interchange format, not re-litigated here)

---

## 1. What OKF v0.1 Actually Is

Verified via web search (June 2026 release, Google Cloud):

- Published by Google Cloud, June 12, 2026, as an open specification (Apache 2.0).
- An OKF **bundle** is a directory of markdown files, each representing one **concept document**.
- Structure: YAML frontmatter + free-form markdown body.
- Only **`type`** is a required frontmatter field. Other conventional fields observed in the spec and reference bundles: `title`, `description`, `resource`, `tags`, `timestamp`.
- Relationships between concepts are expressed as ordinary markdown links between files — no separate relationship schema.
- OKF deliberately defines portability only: "any producer can write it, any consumer can read it, no SDK required." It explicitly leaves trust, provenance, conflict semantics, and confidence/decay as open design space — it does not compete with those concerns, it has no opinion on them.

This is a narrow, minimal spec by design. That narrowness is exactly why it's adoptable without compromising anything Company Brain already owns.

## 2. Field Mapping — Composite Knowledge Object → OKF Concept Document

Composite Knowledge Objects (Ontology v1.3 §3; combine Primitive Knowledge Objects per Architecture & Vision v2.3 §9) are the tier that exports as OKF concept documents. Primitive Knowledge Objects remain Company Brain's internal representation layer — they are not individually exported; they compose into the Composite before crossing the OKF boundary.

| Composite Knowledge Object Field | OKF v0.1 Field | Notes |
|---|---|---|
| Ontology object type (Person, Team, Commitment, Policy, Meeting, etc. — Ontology v1.3 §3) | `type` (frontmatter, required) | Direct mapping. This is the only field OKF requires, and Company Brain already has a canonical type for every Composite Knowledge Object. |
| Object canonical name/identifier | `title` | e.g. a Policy Object's policy name, a Person Object's canonical name. |
| Object summary (human-readable, derived from the object's substantive content) | `description` | Short-form; the full content lives in the markdown body, not this field. |
| Source reference (what produced this object — Memory Model v1.3 §7 Provenance) | `resource` | OKF's `resource` field is the closest native slot for "what this concept is about/derived from." Company Brain's fuller provenance record (§3 below) does not fit here and is not forced into it. |
| Relationships (Ontology v1.3 §6 Relationship Model) | Markdown links between concept files | Matches §6's own description almost exactly: "without relationships, the Brain becomes storage." OKF's link-graph convention is a native fit, not a stretch. |
| Object substantive content (the composed Primitive Knowledge Objects' data) | Markdown body | Free-form; Company Brain writes its own internal structure into this body. OKF does not constrain body structure beyond "markdown." |
| Last updated / lifecycle timestamp (Memory Model v1.3 §7 Memory Lifecycle) | `timestamp` | One-way: OKF's `timestamp` is a single point-in-time field. It does not carry Company Brain's multi-stage lifecycle (Observed → Interpreted → Recorded → Linked → Used → Updated) — that stays internal; only the current timestamp crosses the boundary. |
| Cross-object categorization (e.g. memory type, ontology layer) | `tags` | Optional, non-load-bearing on either side — useful for filtering an exported bundle but not a field either format depends on structurally. |

**What does not map, by design:** Primitive Knowledge Objects (the 8 atomic types) have no OKF representation of their own — they are pre-export internal structure. Commitment Memory's eight-state lifecycle, Memory Drift, and Learning Memory have no OKF field at all; they are Company Brain concepts that live entirely on the Company Brain side of the boundary and are simply not present in an exported concept document unless summarized into the markdown body at export time.

## 3. What Company Brain Layers On Top (OKF Leaves This Open By Design)

Per master plan §6, OKF v0.1 explicitly states trust/provenance/conflict/confidence semantics are open design space it does not address. Company Brain's Trust & Governance Architecture v1.1 and Memory Model v1.3 fill exactly that space, and none of it requires modifying or extending the OKF spec itself — it wraps around the outside of an OKF bundle.

| Company Brain Layer | What It Adds | Canonical Owner |
|---|---|---|
| **Trust** | Trust tiers (Always / Ask First / Never), Trust Cards (Source, Confidence, Authority, Last Updated, Challenge Status) | Product Architecture v2.2 §15; Trust & Governance Architecture v1.1 Part 2–3 |
| **Provenance** | Who asserted it, when, from what source, under which rule version, confidence, challenge status | Memory Model v1.3 §8; Trust & Governance Architecture v1.1 Part 4 |
| **Conflict / Contradiction** | Current vs. Superseded marking; never silently overwritten; tie-break rules | Memory Model v1.3 §10; Trust & Governance Architecture v1.1 Part 3 (Challenge object) |
| **Confidence & Decay** | Confidence levels (Very Low → Very High); decay applies to active/open states only, not terminal states | Intelligence Architecture v1.1 Part 13, Part 15.1; Memory Model v1.3 §7 (Decay Path) |
| **Governance / Authority** | Who may write, approve, challenge, delegate | Trust & Governance Architecture v1.1 Parts 5–9 |

None of these require a fork of OKF or a competing "internal OKF." They travel as a wrapper — metadata Company Brain attaches to an OKF bundle at export/import time, not fields inserted into the OKF frontmatter itself. This preserves OKF's stated minimalism (a non-Company-Brain consumer can still read the bundle with zero knowledge of Company Brain's trust/governance layer) while Company Brain-to-Company Brain exchange uses the full wrapper.

## 4. Division of Labor (restated from Master Plan §6)

**OKF solves portability.** Any producer, any consumer, no SDK required.

**Company Brain solves governance.** Trust, provenance, conflict resolution, confidence, and decay — a problem OKF v0.1 explicitly leaves open.

**Brain-to-Brain Interoperability** (Product Architecture v2.2 §5) becomes concrete under this mapping: two Company Brain instances exchange OKF-formatted Composite Knowledge Objects, each wrapped in its own instance's provenance and trust metadata. A non-Company-Brain OKF consumer (e.g. Google's reference visualizer) can still read the bundle's markdown/frontmatter; it simply doesn't see the trust/provenance wrapper, which is the correct behavior — that wrapper is a Company Brain-to-Company Brain concern, not a portability requirement.

## 5. What This Deliverable Does Not Change

This is a mapping document, not a re-architecture. It does not alter:
- The Primitive/Composite Knowledge Object split (Architecture & Vision v2.3 §9, Ontology v1.3 §3) — owned as-is.
- Memory Model v1.3's five memory types, lifecycle, or write governance — untouched.
- Trust & Governance Architecture v1.1's Trust Object Model — untouched.

It formalizes what was already decided in principle (Master Plan §6) into a field-level mapping so that Memory Model and Product Architecture's existing "OKF-compatible" language has a concrete referent instead of a placeholder.

---

*Feeds into: Memory Model v1.3 §4 (Knowledge Representation), Product Architecture v2.2 §5 (Knowledge Exchange) — both referenced in the rename-pass drafts.*
