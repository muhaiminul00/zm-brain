# Project State

_This file is maintained by the `project-memory` plugin. It holds current
truth only — it is overwritten each session, not appended to. For durable
facts/decisions see `Wiki/index.md`; for the chronological narrative see
`Wiki/log.md`._

## Status

Theoretical Grounding Phase: complete and frozen (July 2026). Eight canonical
documents merged. Technical Architecture / Building phase in progress.
Architecture locked at `/plan-eng-review` (2026-09-02): D2C (not
B2B/enterprise), individual developers/builders running multiple LLM & agent
tools, wedge = cross-tool context sync, low-cost (pricing itself still
undecided — see Active work). Product name: ZeroManual; ZM-Brain = the
underlying engine; "Company Brain" = the product category, not the
product's name.

## NEXT SESSION: build, or resolve an Unresolved Decision first

`/plan-eng-review` has run (2026-09-02) and locked the v1 architecture — see
`docs/designs/zm-brain-v1-context-sync.md`'s "Technical Architecture
Lock-In" and "GSTACK REVIEW REPORT" sections (last two sections of the
file). Eng Review status is **ISSUES_OPEN, NOT CLEAR** — before `/ship`,
either resolve one of the 4 Unresolved Decisions below or consciously accept
carrying them into build. Two Failure Modes (FM1, FM4 in the design doc) are
flagged CRITICAL — silent-failure risk with no test/error-handling designed
yet; Implementation Tasks T2 and T4 exist for them but the failure-mode
*behavior itself* (what happens on a race, what counts as a secret) is not
yet designed. Start the next session by opening the design doc's last two
sections, not by re-deriving architecture from scratch.

## Active work

- Design doc approved and architecture-locked:
  `docs/designs/zm-brain-v1-context-sync.md` (branch
  `plan/zm-brain-technical-architecture-kickoff`, not yet merged/pushed).
- v1 scope: full "Approach B" core, confirmed a third time at
  `/plan-eng-review` — this time with a stated mitigation (concurrent
  build+test), not a bare preference. See
  `.project-memory/Wiki/decisions/v1-scope-approach-b.md`. **The founder
  chose the fuller/maximal option at every phased-vs-full architecture fork
  in this review (retrieval depth, conflict resolution, hosted relay vs.
  local-only) — flagged by both the reviewer and an independent Codex
  outside-voice pass as a standing pattern to watch, not reversed.**
- 8 architecture decisions locked: Supabase (Postgres+pgvector) as synced
  retrieval index with local git-backed markdown as sole write authority;
  full GBrain retrieval stack (vector+BM25+RRF+graph+reranker); CRDT/
  Automerge conflict resolution; a hosted MCP server for Claude.ai web chat
  delivery. 8 Implementation Tasks (T1-T8) recorded in the design doc, none
  started yet.
- **4 Unresolved Decisions** (design doc, end of file): no kill-rule for The
  Assignment (founder explicitly left this open); pricing/unit economics
  still has no number, now more urgent given real recurring costs (Supabase,
  reranker API, hosted server) the original low-cost default was meant to
  avoid; delivery-surface equivalence (Claude Code/Claude.ai web chat/OpenAI
  named as one v1 target but not individually specced); competitive
  differentiation from Supermemory/Second Brain for AI still open.
- Competitive landscape reviewed — see
  `.project-memory/Wiki/competitive-landscape.md`.
- Outstanding: no external user has been observed/interviewed yet (see the
  design doc's "The Assignment") — now explicitly not load-bearing on scope
  per the founder's own choice this session.
- `TODOS.md` (repo root, new) tracks deferred items: pricing, retrieval-
  quality success criterion, browser extension, enterprise capture sources
  (v2), the kill-rule decision.
