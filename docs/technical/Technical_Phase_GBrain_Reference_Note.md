# Technical Phase — Working Note: GBrain Reference Strategy & Market Findings

Status: Working note, not a canonical doc. Feeds the technical architecture phase, currently in progress.
Purpose: consolidate everything surfaced in chat + web research this session that's technically actionable, before it gets lost across conversation history.

---

## 1. Decision On The Table

**Strategy set this session: reference and learn from GBrain's architecture, do not fork it. Build Company Brain's own substrate, GBrain-informed, with our governance/reasoning layer on top as the actual product.**

Rationale: GBrain proves the capture/retrieval half of this problem is solvable cheaply and fast, in public, by one person. Forking it directly means inheriting its scope limits (personal-brain-first, siloed team mode, no commitments/drift/trust model) and its stability risk (v0.30, one maintainer, documented breaking changes). Learning its patterns costs nothing and saves real design time.

---

## 2. GBrain — Reverse-Engineered Reference Architecture

Confirmed: MIT-licensed, open source, `github.com/garrytan/gbrain`, TypeScript + PLpgSQL, built and run in production by Garry Tan (President/CEO, Y Combinator). Not a demo — his live instance runs 146,646+ pages, 24,585+ people, 66 autonomous cron jobs.

**Stack:**
- **Storage:** Markdown files in a git repo = source of truth ("brain repo"). Synced into Postgres for retrieval — PGLite (embedded, WASM, zero server, ~2 sec setup) locally, Supabase or self-hosted Postgres at scale.
- **Retrieval:** Hybrid search — vector (HNSW on pgvector) + BM25 keyword + reciprocal-rank fusion (RRF) + knowledge-graph traversal + cross-encoder reranker (ZeroEntropy) + source-tier boosting + alias/synonym hop. Three tunable modes (conservative/balanced/tokenmax) trading cost vs. recall.
- **Graph:** "Self-wiring" — every page write runs regex/string-matching (**zero LLM calls**) against markdown links and wikilinks to extract typed edges: `works_at`, `founded`, `invested_in`, `attended`, `advises`. Deterministic, near-zero marginal cost, but entity vocabulary is fixed to what the rules cover.
- **Design philosophy:** "Thin harness, fat skills" — the runtime is deliberately minimal (message routing, DB connection, signal detection loop); actual behavior lives in ~25-40 markdown skill files with decision trees and error handling.
- **Fact structure:** Each page = current compiled synthesis on top, append-only evidence log underneath. Every claim carries a citation. Analogous in shape to our Memory lifecycle + Current/Superseded provenance model, independently arrived at.
- **Access control:** Per-user scoped slices (personal brain, or a team mount you've joined) — simple visibility permission, not a formal authority/delegation model.
- **Exposure:** MCP server, 30-70+ tools, drop-in with Claude Code / Cursor / OpenClaw.
- **Benchmarked:** P@5 49.1%, R@5 97.9% on their own BrainBench corpus; graph layer alone contributes +31.4 points of precision over graph-disabled retrieval.

**Confirmed limits (from GBrain's own docs and independent reviews), i.e. exactly where our layer starts:**
- No commitment modeling — nothing tracks who owes what, by when, or its fulfillment state.
- No drift detection — no comparison of intended/designed process vs. observed/actual behavior.
- No formal trust or authority model — access control only, no claim/evidence/challenge/approval/delegation structure.
- No memory typing — one undifferentiated page+graph model, not org-specific memory categories.
- Team mode is siloed per-person slices, not a single reasoned org-wide memory with conflict resolution.
- Independent reviewer's summary, worth keeping verbatim: *"gbrain is not memory. It's a library."* Holds pre-sorted facts; doesn't encode why something matters, to whom, or how that changes over time.

---

## 3. Architecture Comparison (for technical mapping reference)

| Layer | GBrain | Company Brain | Implication for build |
|---|---|---|---|
| Knowledge format | Markdown, git-backed | Markdown + YAML (adopted OKF v0.1) | Same instinct — can likely borrow GBrain's git-sync-to-Postgres pattern directly |
| Current vs. history | Synthesis on top / append-only evidence below | Memory lifecycle + Provenance + Current/Superseded | Structurally compatible — build ours as a formalization of this same pattern |
| Relationships | Typed edges via regex, ~5 fixed predicates, zero LLM | Ontology-grounded, open vocabulary | Use GBrain's zero-LLM extraction for the *bulk* layer; reserve reasoning for what it can't reach |
| Memory typing | None | 5 formal types (Factual/Interaction/Commitment/Action/Learning) | Pure Company Brain territory — no reference implementation exists to borrow from |
| Commitments | Not modeled | First-class type, own lifecycle | Build from scratch — this is core differentiated IP |
| Drift detection | Not modeled | Candidate→Pattern→Signal→Severity pipeline | Build from scratch — core differentiated IP |
| Trust/governance | Read-permission scoping only | Full Trust Object Model, three-tier write authority | Build from scratch — this is the "other 60%" the market is missing |
| Retrieval | Hybrid: vector+BM25+RRF+graph+reranker | Not yet specified | **Directly reusable pattern** — adopt this stack rather than reinventing |
| Extraction cost model | Deterministic pattern-matching, near-$0/write | Not yet specified | **Directly reusable pattern** — see cost strategy below |

---

## 4. Key Technical Decisions & Recommendations Surfaced This Session

**4.1 — Layered cost strategy (the single most actionable technical decision from this session).**
Don't run every write through an LLM. Split the pipeline:
- **Cheap deterministic pass** (GBrain-style regex/pattern extraction) on every write, for bulk facts and simple relationships — near-zero marginal cost, scales freely.
- **Reasoning pass** (LLM-based) reserved specifically for what the cheap pass structurally can't do: commitment detection, drift comparison, trust/confidence evaluation, conflict resolution. This is where our actual cost sits, and it should sit only there.
This is the concrete mechanism for the Master Plan's Principle around cost — worth formalizing as an explicit architectural rule in the technical spec.

**4.2 — Reference, don't fork, dependency risk.**
GBrain is v0.30, single-maintainer, README self-documents "frequent breaking changes." Fine to learn from; risky to build production infrastructure directly on top of someone else's personal side project's roadmap. Decision: independent implementation, GBrain-informed.

**4.3 — Retrieval stack: adopt, don't reinvent.**
Vector (pgvector/HNSW) + BM25 + RRF + graph traversal + reranker is a proven, benchmarked pattern (GBrain's own numbers: +31 precision points from adding the graph layer alone). Recommend adopting this combination as the retrieval baseline for Company Brain rather than researching retrieval methods from scratch — this part of the problem is solved, publicly, and doesn't need to be re-derived.

**4.4 — Naming: don't inherit "semantic layer."**
Colrows (an enterprise semantic-layer vendor) frames the winning move as "build a semantic layer." Their structural point (capture commoditizing, governance holding value) is sound; their specific category label isn't quite ours. Semantic layers (Colrows/dbt/Snowflake) solve deterministic metric consistency over structured data ("revenue means the same number everywhere"). Company Brain's governance layer solves trust/provenance over unstructured organizational memory — different problem, potentially complementary product for the same enterprise buyer, not a synonym. Keep our own terms ("governed memory," "trusted context layer") in technical and product docs.

**4.5 — Deployment model constraint, flagged for the technical spec.**
Per the same market analysis: enterprises evaluating this category are expected to want to own their Company Brain — self-hosted or built in-house — rather than buy pure hosted SaaS. If that holds, the technical architecture should design for self-hosted/VPC deployment as a first-class target, not an afterthought retrofitted later. This is a real constraint on infrastructure choices (e.g. Postgres/pgvector over a proprietary managed-only vector DB), not just a business-model question — flagging it here because it affects the stack decision, not only pricing.

**4.6 — OKF adoption (carried over from the grounding phase, technically relevant here too).**
Company Brain adopts Google Cloud's Open Knowledge Format v0.1 (markdown + YAML frontmatter, `type` field required) as the Knowledge Exchange interchange format. Technically compatible with GBrain's markdown-first storage pattern — both converge on the same shape independently. Worth checking directly whether OKF's concept-document format and GBrain's page format are close enough to share tooling.

**4.7 — MCP/A2A — already a settled technical decision, restated for the record.**
Exposure layer standardizes on Model Context Protocol (now under the Agentic AI Foundation / Linux Foundation, Dec 2025) and Agent2Agent. GBrain, Hyper, Savant, and Memory Store all expose over MCP — confirms this is the correct, converged industry standard for this exposure layer, not a risky bet.

---

## 5. Competitor Stack Notes (technically relevant fragments, from the same research pass)

- **Hyper (YC):** claims an "in-house memory system" scoring at/above SOTA on public benchmarks, plus a custom eval suite for precision/recall — no architecture details published, unlike GBrain. Positioned as the ambient connector layer (Docs/Slack/Email/Calendar → any AI tool).
- **Savant (YC):** "operational memory layer" — explicitly serves context to agents "at decision time," framed around undocumented procedures/edge cases/exceptions rather than general knowledge capture. Closer conceptually to our Commitment/Action memory framing than to GBrain's general-purpose graph.
- **Memory Store (YC):** MCP-native, notable feature is "Briefs" — living documents that auto-update whenever new memories are created. Worth a look as a pattern for how Company Brain's Memory Consumption & Delivery layer could surface synthesized state without the user having to query.
- **Cerenovus (YC):** markdown knowledge graph explicitly modeling the company as a system to infer operational inefficiencies — closest conceptual neighbor to Drift Detection found in the whole competitive scan, worth a deeper look if not already done.

---

## 6. Recommended Next Actions

1. Run the technical open-questions/backlog scan across all architecture docs (separately requested, not yet executed) — cross-reference its INFRASTRUCTURE and ALGORITHM/METHOD categories against §4 of this note specifically, since several of those open items likely now have a directional answer from this research.
2. Spike: map Company Brain's five memory types + atomic primitives onto a concrete schema, using GBrain's page+graph model as the structural starting point rather than starting blank.
3. Decide infrastructure baseline explicitly: Postgres + pgvector (GBrain's proven choice, and compatible with the self-hosted/VPC constraint in §4.5) vs. any managed alternative — recommend defaulting to the former unless a specific reason emerges not to.
4. Prototype the two-tier extraction pipeline from §4.1 on a small real dataset, and measure where the cost actually lands, before committing to the full design.
5. Look directly at Cerenovus's approach as the nearest published attempt at something like Drift Detection.

---

## 7. Sources

- github.com/garrytan/gbrain (README, docs/architecture/RETRIEVAL.md, docs/GBRAIN_SKILLPACK.md)
- vectorize.io/articles/gbrain-review — independent technical review
- littlemight.com/g-brain — "it's a library, not memory" critique
- colrows.com/blogs/yc-company-brain-rfs — market structure analysis (read as directionally useful, source has a stake in the semantic-layer framing)
- ycombinator.com/companies/hyper-4, /savant, /hyperspell — YC company pages
- ycombinator.com/launches/QPs-memory-store-your-company-s-brain
- Y Combinator Summer 2026 RFS, "Company Brain" category (Tom Blomfield)
