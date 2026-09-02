# TODOS

## Technical Architecture (ZM-Brain v1)

### Pricing model for D2C low-cost positioning

**What:** Define an actual price point for ZM-Brain, or an explicit "free
for now" decision with a revisit trigger.

**Why:** The "low-cost" constraint has no number behind it, and is now more
urgent than when the design doc was written — Supabase, the ZeroEntropy
reranker API, and the hosted MCP server (locked at `/plan-eng-review`,
2026-09-02) are all real recurring costs the doc's original "local-only, no
hosted relay" default was specifically written to avoid paying.

**Context:** See `docs/designs/zm-brain-v1-context-sync.md`, Open Questions
and the "Technical Architecture Lock-In" / Unresolved Decisions sections.
Not needed before build starts, but needed before launch — the current
scope cannot be "low-cost" without a number to check it against.

**Effort:** S
**Priority:** P2
**Depends on:** None

---

### Retrieval-quality success criterion

**What:** Write a concrete success criterion for the retrieval stack
(vector+BM25+RRF+graph+reranker), matching the rigor the design doc already
applies to sync ("spike/prototype quality, not production").

**Why:** The full retrieval stack was locked at `/plan-eng-review`
(2026-09-02) with real recurring cost (reranker API) and real build effort,
but the design doc's Success Criteria section has no corresponding
retrieval-quality bar — flagged by the Codex outside voice during that
review.

**Context:** See `docs/designs/zm-brain-v1-context-sync.md`, Success
Criteria section and Implementation Task T8. Needed before v1 is called
"done," not before build starts.

**Effort:** S
**Priority:** P2
**Depends on:** Enough real usage to know what "good retrieval" means for
this product — may need The Assignment or early dogfooding data first.

---

### Browser extension delivery channel

**What:** Add browser-extension-based delivery for closed/non-extensible
tools, per the original wedge (context sync for tools without an MCP/hook
surface).

**Why:** The original Problem Statement's pain point includes tools with no
extensibility surface at all — the current v1 delivery lock (MCP/plugin-
based only: Claude Code, Claude.ai web chat, OpenAI where feasible) doesn't
cover that case. Codex flagged this narrowing as reducing the original
wedge's coverage.

**Context:** See `docs/designs/zm-brain-v1-context-sync.md`, Approach C
(Passive Capture, Browser-First) and the Distribution Plan section. Explicit
founder decision to defer, made at `/plan-eng-review` (2026-09-02).

**Effort:** M
**Priority:** P3
**Depends on:** v1 delivery (T1/T6) shipped and validated first.

---

### Enterprise capture source adapters (v2)

**What:** Add source adapters for the canonical docs' enterprise capture
sources — meetings, email, calendar, Slack — per the original 8-doc vision.

**Why:** This project's own narrow-then-broaden strategy (Problem
Statement) calls for adding these back once the D2C wedge is validated and
shipped. The founder explicitly wants "1-2 of those, or none in v1" now,
with the architecture ready to add them later without a redesign
(Implementation Task T5, source-adapter event model).

**Context:** See `docs/designs/zm-brain-v1-context-sync.md`, "Technical
Architecture Lock-In" section (capture-sources decision, 2026-09-02) and
`docs/architecture/Company_Brain_Memory_Model_v1.3.md` §5-6 for what a full
enterprise capture pipeline eventually needs to produce (Knowledge Objects,
Memory Types).

**Effort:** L
**Priority:** P4
**Depends on:** T5 (source-adapter event model) must exist first; v1 must
be shipped and have real usage before broadening scope, per the narrow-
then-broaden strategy this project has already committed to.

---

### Kill-rule for The Assignment

**What:** Define what result from watching an external developer (The
Assignment, in the design doc) would actually change build scope — or
formally confirm there isn't one.

**Why:** Raised by the Codex outside voice at `/plan-eng-review`
(2026-09-02): with full Approach B already locked regardless of outcome,
The Assignment's observation is not currently load-bearing on any decision,
which risks making it performative rather than a real test.

**Context:** See `docs/designs/zm-brain-v1-context-sync.md`, "Unresolved
decisions that may bite you later." The founder explicitly chose to leave
this unresolved in this review rather than define a rule now — listed here
as a live TODO rather than a closed decision, since it can still be picked
up before or after The Assignment is actually run.

**Effort:** S
**Priority:** P2
**Depends on:** None — this is a decision, not build work.

## Completed
