# Company Brain — Project Context & Operating Instructions

Project:   Company Brain (ZeroManual, internal)
Document:  CLAUDE.md v1.0 — governance for the Theoretical Grounding →
           Technical Architecture transition


---

## Project Summary

Company Brain is a memory and intelligence layer for organizations.
It automatically captures meetings, emails, and decisions, understands
what happened, and stores it as structured knowledge — facts,
commitments, decisions, and lessons learned — then delivers the right
piece of knowledge to the right person (or AI agent) at the right time.
The problem it solves: AI agents at work currently have no company
context (no relationship history, no flagged risks, no prior
commitments), so they produce generic, unusable output — the same
organizational-memory problem companies already have with people,
now more urgent because more work is shifting to agents that guess
without it.

**Current stage, stated plainly:** conceptual architecture only — no
technical implementation exists yet, intentionally paused. The
Theoretical Grounding Phase is complete and frozen (July 2026): eight
canonical documents now define the system, each grounded in named
theory/industry standards with an explicit implement/extend/diverge
relationship stated per source, not just cited. Per Foundational
Reasoning V4's own roadmap, **Technical Architecture is next, not yet
started** — do not treat this project as further along than that.

---

## Session Start — read in this order, nothing else by default

1. **`.project-memory/PROJECT_STATE.md`** — current status, active
   work, in full, every session.
2. **`.project-memory/Wiki/index.md`** — catalog of durable facts/
   decisions. Read the index only; drill into a specific
   `.project-memory/Wiki/*.md` page only when the current task
   actually touches that topic.
3. **This file (CLAUDE.md)** — you're reading it now.
4. Any specific canonical document a task actually names — not the
   full eight-document set by default (see Canonical Documents below
   for what each one covers, so you know which one to open).

---

## Modes

This project runs on the `gstack-pilot` plugin's three-mode system
(Advisor/Commander/Execute) — the same portable mode system
[Zenny](https://github.com/muhaiminul00/role-modes) uses, natively
chained into gstack. **The mode-switch mechanics and the gstack
chain itself are documented in `.claude/CLAUDE.md`** (seeded by the
plugin, not this file) — read there for exactly which gstack skill
each mode chains into and why. This file deliberately does not
re-explain that mechanism: `gstack-pilot` already handles the routing,
and duplicating its own documentation here would just be a second,
driftable copy of the same information.

In short: `/gstack-pilot:advisor` for low-effort Q&A (default),
`/gstack-pilot:commander` to plan, `/gstack-pilot:execute` to build.

---

## Memory System

This project uses the `project-memory` plugin's three-layer model,
scaffolded under `.project-memory/`:

- **`.project-memory/PROJECT_STATE.md`** — current truth only,
  overwritten each session, never appended to.
- **`.project-memory/Wiki/*.md`** — durable facts and decisions,
  cross-referenced from `.project-memory/Wiki/index.md`, edited in
  place as understanding changes.
- **`.project-memory/Wiki/log.md`** — append-only chronological
  record, read only on request (historical/audit purposes).

**Promotion Rule**, applied continuously, not just when asked: a
durable fact or decision → write/update a Wiki page now; a status-only
update → overwrite `PROJECT_STATE.md` now; the full narrative of how
something happened → append `Wiki/log.md` now.

---

## Canonical Documents

The Theoretical Grounding Phase (see
`docs/architecture/Company_Brain_Theoretical_Grounding_Master_Plan.md`
and Foundational Reasoning §25) is **frozen** as of July 2026. Eight
canonical documents now define Company Brain, each grounded in named
theory/standards with the relationship stated explicitly
(implement / extend / diverge) rather than just cited:

- `COMPANY_BRAIN_Architecture_&_Vision_v2.3.md` — the seven-layer
  pipeline, atomic primitives, Primitive Knowledge Objects, memory
  architecture overview, commitment lifecycle, drift detection,
  provenance requirements
- `Company_Brain_Ontology_v1.3.md` — first-class objects, their
  composition, Composite Knowledge Objects, memory homes,
  relationships
- `Company_Brain_Memory_Model_v1.3.md` — how reality becomes memory:
  formation routing, the five memory types, lifecycle, decay,
  provenance, write governance, conflict resolution, drift, the
  learning loop
- `Company_Brain_Product_Architecture_v2.2.md` — how organizational
  memory reaches humans/AI systems: exposure modes, Knowledge
  Exchange, OKF compatibility, Brain-to-Brain interoperability,
  governance, MVP prioritization
- `Company_Brain_Intelligence_Architecture_v1.1.md` — how memory
  becomes understanding: context assembly, reasoning pipeline,
  recommendation/risk/opportunity/drift intelligence, Consultant
  reasoning, agent intelligence, confidence model
- `Company_Brain_Trust_&_Governance_Architecture_v1.1.md` — authority,
  accountability, provenance, challenge, approval, delegation,
  revocation, oversight across humans, agents, and automation
- `Company_Brain_Theoretical_Foundations_v1.md` — the 13 grounding
  fields, theory-first, with an explicit implement/extend/diverge
  relationship for each; the VSM Compression Test; the vocabulary
  rename table
- `Bibliography.md` — full verified reference list

Supporting reference (not canonical, but cited from the canonical
set): `OKF_Adoption_Mapping.md`, `One_Pager.md`,
`Company_Brain_Foundational_Reasoning_V4.md` (the CTO/LLM-context
reasoning trail — **if this conflicts with a canonical document, the
canonical document wins**; append-only, never edit existing chapters),
`marked_for_technical_architecture.md` (parking-lot items deferred to
the next phase). See `README.md` for the full document index with
per-document dependency order.

Full history of this phase — every intermediate draft, the
pre-grounding original document versions, and the team-review
artifacts (change log, coverage check, consistency check,
recognizability sheet) — is preserved in
`/archive/grounding-phase-2026-07/`, not discarded.

---

## Standing Rule — Document Resolution Authority

When a conflict, gap, or apparent error surfaces mid-session across
the canonical set:

1. **The canonical document wins over any reference/supporting
   document** — `Company_Brain_Foundational_Reasoning_V4.md`
   explicitly defers to the canonical set if the two ever disagree;
   the same precedence applies to `OKF_Adoption_Mapping.md`/
   `One_Pager.md` against whichever canonical document they cite.
2. Between canonical documents, check whether one already states its
   own implement/extend/diverge relationship to the theory in question
   (`Company_Brain_Theoretical_Foundations_v1.md` is the field-by-field
   source of truth for this) — that stated relationship resolves most
   apparent conflicts, since it's the explicit design intent, not an
   accident.
3. If a real search finds no answer: resolve it yourself only if it's
   a mechanical/structural fact with one obviously correct answer given
   everything already established. Otherwise — stop and ask. Never
   invent a citation or a plausible-sounding resolution to fill a gap
   (this project's own grounding discipline already treats a
   forced-fit citation as worse than none).
4. **Log any self-resolved item** as a new/updated page under
   `.project-memory/Wiki/` and an entry in `.project-memory/Wiki/
   log.md` — state the conflict, documents checked, what it resolved
   to, and why. This mirrors the review artifacts already kept for the
   grounding phase (`CHANGE_LOG.md`, `CONSISTENCY_CHECK.md` in the
   archive) — the same discipline, just live instead of end-of-phase.

---

## Standing Rule — Branch/PR Workflow

`gstack-pilot`'s own default wrap-up — feature branch → PR → gstack's
`review` → `qa` → `ship` chain → merge, for **every** change, with no
trivial-housekeeping exemption — is this project's actual rule, not
just an inherited plugin default. Stated here explicitly so it's
discoverable by reading this file, without already knowing
`gstack-pilot`'s internals. This applies even to pure documentation
changes (like this file) — the plugin's own design reasoning for the
"no exemption" choice is that using gstack's real pipeline consistently
matters more than saving a little overhead on small edits.

---

## Build Cards

This project has not defined its own Build Card / task-spec format.
Use `gstack-pilot`'s generic `build-cards` skill as the fallback until
one is defined — do not invent a numbering scheme or ceremony beyond
what that skill already provides.

---

## Repo Notes

- `docs/architecture/` — the eight canonical documents plus supporting
  reference docs.
- `docs/technical/` — early technical-phase scaffolding (`MVP_Build_
  Plan.md`, `Open_Questions_Technical_Backlog.md`, a GBrain reference
  note) — **not yet the Technical Architecture phase itself**; read
  these as pre-work/parking-lot material, not as a started or approved
  plan.
- `docs/deck & proposal/` — pitch-deck and proposal materials, not
  architecture — don't treat these as a source of technical fact.
- `archive/grounding-phase-2026-07/` — full history of the grounding
  phase (see Canonical Documents above); nothing from that phase was
  discarded.
- `.claude/hooks/check-gstack.sh` + the PreToolUse hook in
  `.claude/settings.json` block Skill-tool use if gstack isn't found
  installed globally — this is `gstack-team-init`'s own enforcement,
  not something this file manages.

---

## gstack (REQUIRED — global install)

**Before doing ANY work, verify gstack is installed:**

```bash
_GS=""
for _D in "${GSTACK_ROOT:-}" "$HOME/.claude/skills/gstack" "$HOME/.codex/skills/gstack" "$HOME/.factory/skills/gstack" "$HOME/.kiro/skills/gstack" "$HOME/.config/opencode/skills/gstack" "$HOME/.slate/skills/gstack" "$HOME/.cursor/skills/gstack" "$HOME/.openclaw/skills/gstack" "$HOME/.hermes/skills/gstack" "$HOME/.gbrain/skills/gstack" "$HOME/.gstack/repos/gstack"; do
  [ -z "$_GS" ] && [ -n "$_D" ] && [ -d "$_D/bin" ] && _GS="$_D"
done
[ -n "$_GS" ] && echo "GSTACK_OK: $_GS" || echo "GSTACK_MISSING"
```

If GSTACK_MISSING: STOP. Do not proceed. Tell the user:

> gstack is required for all AI-assisted work in this repo.
> Install it:
> ```bash
> git clone --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
> cd ~/.claude/skills/gstack && ./setup --team
> ```
> Then restart your AI coding tool.

Do not skip skills, ignore gstack errors, or work around missing gstack.

Using gstack skills: After install, skills like /qa, /ship, /review, /investigate,
and /browse are available. Use /browse for all web browsing.
Use the resolved install path above for gstack file paths
(default: ~/.claude/skills/gstack).

## Skill routing

When the user's request matches an available skill, invoke it via the Skill tool. When in doubt, invoke the skill.

Key routing rules:
- Product ideas/brainstorming → invoke /office-hours
- Strategy/scope → invoke /plan-ceo-review
- Architecture → invoke /plan-eng-review
- Design system/plan review → invoke /design-consultation or /plan-design-review
- Full review pipeline → invoke /autoplan
- Bugs/errors → invoke /investigate
- QA/testing site behavior → invoke /qa or /qa-only
- Code review/diff check → invoke /review
- Visual polish → invoke /design-review
- Ship/deploy/PR → invoke /ship or /land-and-deploy
- Save progress → invoke /context-save
- Resume context → invoke /context-restore
- Author a backlog-ready spec/issue → invoke /spec
