# Competitive Landscape (ZM-Brain / ZeroManual)

**Last reviewed:** 2026-09-02, source: founder-supplied `docs/competitors_list.txt`.
Full analysis in `docs/designs/zm-brain-v1-context-sync.md` (Competitive
Landscape section) — this page is the durable summary, that doc is the
session record.

## B2B "Company Brain" players — not v1 competitors

Sentra, Hyper, Hyperspell, Cerenovus, Savant, Aura, Webair AI, Lore, Memory
Store, GBrain (B2B/D2C-ish), Cognee (B2B/developer), Notion AI/Glean-adjacent.
Target org-wide team memory, not the individual-developer D2C wedge ZM-Brain
v1 is scoped to (see [[v1-scope-approach-b]]). Tracked, not competed with,
for two reasons:
1. Several (Hyper especially) validate that the capture-once/deliver-
   everywhere architecture works and is fundable.
2. They become direct competitors again once ZM-Brain broadens back toward
   the canonical enterprise vision — this project's own stated
   narrow-then-broaden strategy.

## D2C / personal memory-sync — the real v1 competitive set

- **Supermemory** — cross-tool MCP second brain, app + browser extension,
  OSS self-host / cloud. Closest match to ZM-Brain's wedge. Differentiation
  not yet decided — open question.
- **Second Brain for AI (Cloudflare, OSS)** — MCP continuity layer bridging
  Claude/ChatGPT/Cursor, self-hosted. Same territory as Supermemory.
- **Mem0** — dev-focused memory API/infra, not consumer-facing. This is the
  "memory storage" category ZM-Brain deliberately avoided competing on
  directly (see the design doc's Wedge section) — watch for them adding
  sync/delivery features.
- **Rewind AI → Limitless → acquired by Meta → shut down Dec 19, 2025** —
  cautionary tale: demand validated enough to get acquired, but the
  standalone product still died. Execution/business-model risk signal, not
  a demand-risk signal.
- Lower proximity: Second Brain – AI Memory (iOS), SecondBrain (voice-first),
  Off Grid AI Desktop, Reflect, Mem.ai, Vellum, Limitless Pendant, Plaud Pin.

## Open question this raises

How ZM-Brain differentiates from Supermemory and Second Brain for AI
specifically — both already ship cross-tool MCP context continuity. Needs an
answer before `/plan-eng-review` locks the build.

## Cross-references

- [[v1-scope-approach-b]] — the v1 scope decision this landscape review
  informs.
- Design doc: `docs/designs/zm-brain-v1-context-sync.md`
