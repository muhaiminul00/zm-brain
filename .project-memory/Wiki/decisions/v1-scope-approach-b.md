# Decision: ZM-Brain v1 scope = full core (Approach B), not a narrow MVP

**Status:** Locked at `/plan-eng-review` (2026-09-02) with a stated
mitigation (concurrent build+test) — see "What resolved this" below. The
underlying zero-external-demand-validation risk is accepted, not resolved;
it's tracked as a standing risk in the design doc's Unresolved Decisions.
**gstack decision-log id:** `f2a20996-c92a-4444-a1e6-07a0e8147ea4` →
superseded by `b3cf7b56-372d-436e-8e45-471d0abc3201` (2026-09-02, adds the
justification this page originally flagged as missing) → architecture
lock-in itself logged as `f099b419-fb83-49f2-9588-261bf7ff5697`.
**Design doc:** `docs/designs/zm-brain-v1-context-sync.md` (see its
"Technical Architecture Lock-In" section for the full set of 8 locked
architecture decisions built on top of this scope choice).

## What was decided

For the ZM-Brain v1 build (D2C, individual developers, the "context sync
across tools" wedge — see the design doc above for full framing; no
separate `zm-brain-technical-architecture-scope` Wiki page was ever
created), the founder chose
**Approach B**: a full local-first core (wiki/files-based store + sync
across devices + light hybrid retrieval + provenance/write-governance
concepts scoped down from the canonical Memory Model doc), over Approach A
(a minimal wiki-store packer with no sync/retrieval/governance) or a
scoped-down "A-shaped v1 on B's data model."

## Why this is flagged as a live tension, not settled fact

This directly contradicts the narrow-first strategy the same office-hours
session agreed to (ship the narrow wedge, get real paying users, then
broaden). The assistant recommended Approach A twice, including one explicit
pushback naming the contradiction. The founder held Approach B both times;
no specific technical reason was given for why the full core can't be faked
with a thinner v1 on the second pushback — this is recorded as a stated
preference, not a defended technical premise (contrast with Premise 3 in the
design doc, which the founder did defend with reasoning against a
cross-model challenge).

An independent adversarial review of the design doc (score 6/10) named this
exact scope choice as its top Scope-dimension finding and recommended either
reverting to Approach A or requiring a written technical justification
before Technical Architecture planning locks it in.

## What resolved this

At `/plan-eng-review` (2026-09-02), the reviewer's Step 0 Scope Challenge
proposed descoping to Approach A a third time, citing this project's own
prior spike-philosophy doc (`docs/technical/Technical_Build_Master_Plan_v1.2.md`).
The founder held Approach B again, but this time gave the justification this
page previously flagged as missing: build and test concurrently (dogfood by
founder + invited users live during build, not gated behind a post-build
validation phase), plus concrete narrowing on delivery (MCP/plugin-based
only for v1) and capture sources (0-2 dev-tool-native sources, not
enterprise ones). See the design doc's "Technical Architecture Lock-In"
section for the 8 architecture decisions made on top of this (store
backend, retrieval depth, conflict resolution, hosted MCP server, write-path
authority).

**The Assignment (watch one external developer) remains outstanding and is
now explicitly NOT load-bearing on scope** — the founder chose, during the
same review, to leave undefined what result would trigger a descope
(see the design doc's Unresolved Decisions and [[competitive-landscape]]
for the related differentiation risk). This is a standing risk, not a
closed question.

## Cross-references

- Design doc: `docs/designs/zm-brain-v1-context-sync.md`
- `.project-memory/PROJECT_STATE.md` — reflects "Technical Architecture in
  progress, architecture locked at /plan-eng-review, several unresolved
  decisions tracked" as current status. (Plain path, not a `[[ ]]` Wiki
  link — PROJECT_STATE.md is the state doc, not a Wiki page.)
