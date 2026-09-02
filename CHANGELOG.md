# Changelog

All notable changes to this project are documented here. Format loosely
follows [Keep a Changelog](https://keepachangelog.com/).

## [0.1.0.0] - 2026-09-02

### Added

- Started the Technical Architecture / Building phase for ZM-Brain v1
  (product: ZeroManual), narrowed to a D2C wedge for individual developers:
  cross-tool context sync, project/entity awareness, low-cost.
- Wrote and locked the v1 design doc
  (`docs/designs/zm-brain-v1-context-sync.md`): problem statement, demand
  evidence, target user, constraints, competitive landscape (Supermemory
  and Second Brain for AI as the closest D2C competitors), and 9 locked
  architecture decisions — Supabase (Postgres + pgvector) as a synced
  retrieval index with local git-backed markdown as the sole source of
  truth and write surface, the full GBrain hybrid retrieval stack
  (vector + BM25 + RRF + graph traversal + reranker), CRDT/Automerge
  conflict resolution, and a hosted MCP server for Claude.ai web chat
  delivery.
- Added 8 Implementation Tasks (T1-T8) and a data-flow diagram scoping the
  actual build, none started yet.
- Added `TODOS.md` tracking deferred work: pricing, a retrieval-quality
  success criterion, browser-extension delivery, enterprise capture
  sources for v2, and a kill-rule decision for the founder's own
  external-user observation ("The Assignment").
- Documented 8 failure modes (4 flagged critical: a sync race condition,
  secret leakage before redaction exists, prompt-injection/content-
  poisoning risk with no trust boundary, and the reranker as an
  unacknowledged third-party exfiltration path) and 9 unresolved decisions
  — surfaced by independent architecture review and two adversarial review
  passes, recorded as tracked risk rather than resolved.

### Changed

- Updated `README.md`'s project-status framing: the repo is no longer
  "Technical Architecture not yet started" — it's in progress, with v1
  scope and architecture locked, unresolved risk items tracked explicitly
  rather than implied resolved.

## [Unreleased]

Nothing yet.
