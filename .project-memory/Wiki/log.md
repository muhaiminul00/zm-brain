# Wiki Log

_Append-only chronological record. Read only on request._

## 2026-08-30

- `project-memory` plugin scaffolded (PROJECT_STATE.md, Wiki/index.md,
  Wiki/log.md created) via `/gstack-pilot:commander`'s verification pass.

## 2026-09-02

- Ran `/office-hours` to kick off the Technical Architecture/Building phase.
  Clarified naming (ZeroManual = product, ZM-Brain = engine, "Company Brain"
  = category, not the product's name). Narrowed scope to D2C individual
  developers, wedge = cross-tool context sync. Six forcing questions run;
  demand evidence stayed at "founder's own pain + informal signal," no
  external user validated yet. Landscape search found the "AI memory"
  category crowded (196+ MCP memory servers, Anthropic's own native memory
  beta) but a distinct gap in cross-tool portability for non-extensible
  tools — reframed the wedge accordingly. Codex second opinion agreed on
  the core signal but challenged the central-store premise; founder
  defended it with reasoning (files/wiki-based, not vector-RAG). Founder
  then selected the full "Approach B" core over the assistant's
  narrow-MVP recommendation, twice, without technical justification the
  second time — logged as decision `f2a20996-c92a-4444-a1e6-07a0e8147ea4`
  and promoted to `.project-memory/Wiki/decisions/v1-scope-approach-b.md`.
  Design doc written (`docs/designs/zm-brain-v1-context-sync.md`),
  adversarial-reviewed twice (6/10 both rounds; 19 issues found across both
  passes, 15 fixed directly — conflict-resolution/security Open Questions,
  Premise-5-vs-scope contradiction flagged inline, undefined jargon marked
  BLOCKING, per-subsystem effort breakdown, write-governance deferred out
  of v1, Wiki cross-reference added; 1 issue persisted on purpose as a
  "Reviewer Concerns" section — no technical justification given for full
  Approach B scope over a narrower MVP, per the convergence guard). Founder
  approved the doc, adding a Competitive Landscape section from a supplied
  competitor list: B2B "Company Brain" players (Sentra, Hyper, Hyperspell,
  Cerenovus, Savant, Aura, Webair AI, Lore, Memory Store, GBrain, Cognee)
  judged NOT v1 competitors given the D2C narrowing, but tracked for the
  later broaden-back phase; D2C players (Supermemory, Second Brain for AI/
  Cloudflare, Mem0, the dead Rewind/Limitless) are the real v1 competitive
  set, with Supermemory and Second Brain for AI flagged as closest/
  undifferentiated. Promoted to
  `.project-memory/Wiki/competitive-landscape.md`. Work is on branch
  `plan/zm-brain-technical-architecture-kickoff`, not yet merged.
  Session ended on low usage credit — founder set a standing instruction
  that the next session must start with `/plan-eng-review` against the
  eight canonical docs + this approved design doc (see PROJECT_STATE.md's
  "NEXT SESSION MUST START WITH" line).

- Ran `/plan-eng-review` (via `/gstack-pilot:commander`) against the eight
  canonical docs and the approved design doc, per the standing instruction
  above. Step 0 Scope Challenge fired (Approach B triggers the >2-new-
  services complexity gate); reviewer proposed descoping to Approach A,
  citing `docs/technical/Technical_Build_Master_Plan_v1.2.md`'s spike-only
  philosophy ("No Retrieval. No Search."). Founder rejected the descope a
  third time, this time with reasoning: concurrent build+test (dogfood live
  during build), delivery narrowed to MCP/plugin-based (Claude Code +
  Claude.ai web chat + OpenAI where feasible, browser extension deferred),
  capture sources narrowed to 0-2 dev-tool-native sources with a pluggable
  adapter requirement for v2 enterprise sources, and explicit rejection of
  the spike-doc's applicability (it targeted a different, pre-pivot
  pipeline). Logged as decision `b3cf7b56-372d-436e-8e45-471d0abc3201`,
  superseding the earlier unjustified `f2a20996`.

  Four Architecture findings resolved the design doc's BLOCKING/TBD items:
  (1) Claude.ai web chat needs a reachable-from-cloud MCP server, ruling out
  pure local-only; (2) store backend locked to Supabase (Postgres+pgvector)
  as a synced retrieval index with local git-backed markdown as source of
  truth, directly reusing GBrain's own proven split (researched pre-pivot in
  `docs/technical/Technical_Phase_GBrain_Reference_Note.md`) — a Hostinger
  VPS relay and Pinecone/Notion alternatives were considered and rejected;
  (3) retrieval depth locked to the full GBrain stack (vector+BM25+RRF+
  graph+reranker) — reviewer's phased vector+BM25+RRF-first recommendation
  was rejected; (4) conflict resolution locked to CRDT/Automerge —
  reviewer's boring-by-default git-merge-conflicts recommendation was
  rejected; follow-up research found Automerge specifically fits "git-for-
  documents" products, correcting the reviewer's own overstated initial
  immaturity claim.

  Ran the mandatory Codex outside-voice pass (gpt-5.5, high reasoning) — 25
  problems named. Two were put to the founder as Cross-Model Tensions and
  locked: (1) Supabase is storage, not a hosted MCP connector service — a
  real gap this review's own Architecture section had missed, now resolved
  by adding a compute-only hosted MCP server; (2) write-path authority was
  underspecified across git/Supabase/CRDT — resolved as local git markdown
  being the sole write surface, Supabase always a read-only derived view,
  with the git-to-Supabase sync required to be part of the same write
  operation. A third tension (no kill-rule for The Assignment given scope
  already locked regardless of outcome) was raised and the founder
  explicitly chose to leave it unresolved. Both reviewers independently
  converged on naming the same standing risk: every phased-vs-full choice
  this session was resolved toward the fuller option (Approach B, full
  retrieval, CRDT, hosted relay) — recorded as an accepted, unreversed risk,
  not litigated further per the review's own rules once a founder decision
  was made.

  8 Implementation Tasks (T1-T8, P1/P2) and 2 critical failure-mode gaps
  (FM1: a race between the hosted MCP server reading Supabase and an
  in-flight git-to-Supabase sync; FM4: a captured secret reaching Supabase
  before a redaction pass exists) were written into the design doc, along
  with a data-flow diagram, a worktree parallelization plan, and 4
  Unresolved Decisions (kill-rule, pricing, delivery-surface equivalence,
  competitive differentiation). All appended to
  `docs/designs/zm-brain-v1-context-sync.md` under "Technical Architecture
  Lock-In" and a closing `## GSTACK REVIEW REPORT` section (Eng Review
  status: ISSUES_OPEN / NOT CLEAR — required before `/ship`). The stale
  "Reviewer Concerns" section was updated in place to point at this
  resolution rather than left contradicting it. Deferred items (pricing,
  retrieval-quality criterion, browser extension, enterprise sources, the
  kill-rule decision) were written to a new repo-root `TODOS.md`.
  `.project-memory/Wiki/decisions/v1-scope-approach-b.md` and
  `PROJECT_STATE.md` updated to match. Architecture decision logged as
  gstack decision `f099b419-fb83-49f2-9588-261bf7ff5697`. `jq` is not
  installed in this environment, so the Implementation Tasks JSONL artifact
  for `/autoplan` could not be written (learning logged) — the markdown
  section in the design doc has the same content. Work remains on branch
  `plan/zm-brain-technical-architecture-kickoff`, not yet committed, pushed,
  or merged.
