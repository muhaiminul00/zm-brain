# Company Brain — Document Index

Canonical architecture documentation for "Company Brain" (ZeroManual, internal). Conceptual architecture only — no technical implementation exists yet, intentionally paused pending Technical Architecture.

Status: **Theoretical Grounding Phase frozen, July 2026.** Eight canonical documents, listed below in dependency order. Each of the six architecture documents is grounded in named theory or industry standards, stated theory-first with an explicit implement/extend/diverge relationship — see `Company_Brain_Theoretical_Foundations_v1.md` for the full field-by-field grounding.

## Working in this repo

This is the document index. For governance, operating instructions, the memory system, and standing rules, see [`CLAUDE.md`](CLAUDE.md) — the actual entry point for anyone (human or AI) doing work here. In short: [gstack](https://github.com/garrytan/gstack) is required for AI-assisted work (enforced by a `PreToolUse` hook that blocks Skill-tool use if it's not found installed — see `CLAUDE.md`'s gstack section), and this project runs on the [`gstack-pilot`](https://github.com/muhaiminul00/gstack-pilot) + [`project-memory`](https://github.com/muhaiminul00/project-memory) plugins.

## Canonical Documents

| # | Document | Version | Defines |
|---|---|---|---|
| 1 | [`COMPANY_BRAIN_Architecture_&_Vision_v2.3.md`](COMPANY_BRAIN_Architecture_&_Vision_v2.3.md) | v2.3 | The seven-layer pipeline, atomic primitives, Primitive Knowledge Objects, memory architecture overview, commitment lifecycle, drift detection, provenance requirements |
| 2 | [`Company_Brain_Ontology_v1.3.md`](Company_Brain_Ontology_v1.3.md) | v1.3 | What first-class objects exist, their composition, Composite Knowledge Objects, their memory homes, their relationships |
| 3 | [`Company_Brain_Memory_Model_v1.3.md`](Company_Brain_Memory_Model_v1.3.md) | v1.3 | How reality becomes memory: Knowledge Representation, formation routing, the five memory types, lifecycle, decay, provenance, write governance, conflict resolution, drift, learning loop, consumption & delivery |
| 4 | [`Company_Brain_Product_Architecture_v2.2.md`](Company_Brain_Product_Architecture_v2.2.md) | v2.2 | How organizational memory reaches humans and AI systems: three exposure modes, Knowledge Exchange, OKF compatibility, Brain-to-Brain interoperability, governance, MVP prioritization |
| 5 | [`Company_Brain_Intelligence_Architecture_v1.1.md`](Company_Brain_Intelligence_Architecture_v1.1.md) | v1.1 | How memory becomes understanding: context assembly, reasoning pipeline, recommendation/risk/opportunity/drift intelligence, Consultant reasoning, agent intelligence, confidence model, adaptive intelligence |
| 6 | [`Company_Brain_Trust_&_Governance_Architecture_v1.1.md`](Company_Brain_Trust_&_Governance_Architecture_v1.1.md) | v1.1 | Authority, accountability, provenance, challenge, approval, delegation, revocation, and oversight mechanisms across humans, agents, and automation |
| 7 | [`Company_Brain_Theoretical_Foundations_v1.md`](Company_Brain_Theoretical_Foundations_v1.md) | v1.0 | The 13 academic fields and industry standards underlying the architecture — each stated theory-first, then bridged to what Company Brain implements, extends, or diverges from; the VSM Compression Test; the vocabulary rename table |
| 8 | [`Bibliography.md`](Bibliography.md) | — | Full verified reference list for every citation used across the document set |

## Reference (not canonical, cited from the documents above)

- [`OKF_Adoption_Mapping.md`](OKF_Adoption_Mapping.md) — Composite Knowledge Object → Open Knowledge Format (OKF) v0.1 field mapping; what Company Brain layers on top (trust, provenance, conflict, decay)
- [`One_Pager.md`](One_Pager.md) — "Company Brain on One Page," a VSM-based summary for a non-technical reader (exec, investor, new hire)
- [`Company_Brain_Foundational_Reasoning_V4.md`](Company_Brain_Foundational_Reasoning_V4.md) — **not canonical, reference only.** The CTO/LLM-context reasoning trail behind every canonical document: why each exists, in what order, and what each fixed in the one before it. If this document conflicts with a canonical document, the canonical document wins. Append-only — never edit existing chapters.
- [`Company_Brain_Theoretical_Grounding_Master_Plan.md`](Company_Brain_Theoretical_Grounding_Master_Plan.md) — the task list, touch-map, and bibliography that scoped the now-complete grounding phase. Historical record of how the eight documents above reached their current state.
- `marked_for_technical_architecture.md` — **does not exist yet** (verified — not a real file in this repo, despite being referenced as one previously). Intended purpose: parking-lot items explicitly deferred to the not-yet-started Technical Architecture phase. Create it when that phase actually starts, or remove this line if the intent changes.

## Archive

`/archive/grounding-phase-2026-07/` preserves the full history of the Theoretical Grounding Phase:

- `pre-grounding-originals/` — the six architecture documents and Foundational Reasoning V4 exactly as they stood before this phase began (v2.2, v1.2, v1.2, v2.1, v1, v1)
- `grounded-drafts/` — the complete working snapshot at freeze: every grounded draft, plus `review/` (the team-review artifacts: `CHANGE_LOG.md`, `COVERAGE_CHECK.md`, `CONSISTENCY_CHECK.md`, `RECOGNIZABILITY_TEST_SHEET.md`, `Team_Review_Package.md`)

Nothing from this phase was discarded — every intermediate state is reconstructable from the archive.

## What's Next

Per Foundational Reasoning V4's roadmap: **Technical Architecture** is next, not yet started. The grounded document set gives it field-tested prior art (VSM, DEMO, Organizational Memory Theory, PROV-O, and others — see `Company_Brain_Theoretical_Foundations_v1.md`) to build against.
