# Company Brain — Project Context

## What this repo is
Canonical architecture docs for "Company Brain" (ZeroManual, internal). Conceptual
architecture only — no technical implementation exists yet, intentionally paused.

## Canonical documents
The Theoretical Grounding Phase (see `Company_Brain_Theoretical_Grounding_Master_Plan.md`
and Foundational Reasoning §25) is **frozen** as of July 2026. Eight canonical documents
now define the Company Brain, each grounded in named theory/standards with the
relationship stated explicitly (implement / extend / diverge) rather than just cited:

- COMPANY_BRAIN_Architecture_&_Vision_v2.3.md
- Company_Brain_Ontology_v1.3.md
- Company_Brain_Memory_Model_v1.3.md
- Company_Brain_Product_Architecture_v2.2.md
- Company_Brain_Intelligence_Architecture_v1.1.md
- Company_Brain_Trust_&_Governance_Architecture_v1.1.md
- Company_Brain_Theoretical_Foundations_v1.md — the 13 grounding fields, theory-first, with an explicit implement/extend/diverge relationship for each
- Bibliography.md — full verified reference list
- Company_Brain_Foundational_Reasoning_V4.md ← APPEND ONLY, never edit existing text (Chapter 0's status table is the sole exception, kept current at each phase freeze)

Supporting reference (not canonical, but cited from the canonical set): `OKF_Adoption_Mapping.md`,
`One_Pager.md`. See `README.md` for the full document index.

Full history of this phase — every intermediate draft, the pre-grounding original
document versions, and the team-review artifacts (change log, coverage check,
consistency check, recognizability sheet) — is preserved in
`/archive/grounding-phase-2026-07/`, not discarded.

## Current task
None active. The Theoretical Grounding Phase is complete and frozen. Next phase per
Foundational Reasoning's roadmap: Technical Architecture (not yet started).

## Hard rules (apply to any future phase touching these documents)
1. Conceptual grounding only. No databases, APIs, schemas, models, code. If you
   catch yourself about to design an implementation, stop — out of scope, belongs
   to Technical Architecture.
2. Never invent a citation. Every source in the bibliography must be verified by
   web search before use. If you can't verify a claim about a source, mark it
   `[UNVERIFIED — needs check]` inline rather than asserting it.
3. Any future revision to a canonical document should follow the same discipline
   this phase used: draft to a working folder, get explicit review/freeze approval,
   then merge — don't edit a canonical doc in place without that cycle.
4. Preserve every original architectural decision unless a human explicitly
   approves a real architectural change. Grounding/vocabulary work changes what
   something is called and what it's compared to — not what any layer does.
5. OKF: Company Brain has adopted Google Cloud's real Open Knowledge Format v0.1
   (June 2026) as its Knowledge Exchange interchange format. This is decided, not
   open — see `OKF_Adoption_Mapping.md`. Do not re-litigate it.
6. Stop and flag rather than guess when a source doesn't clearly support a concept
   — a forced-fit citation is worse than none.

## Definition of done for the Theoretical Grounding Phase (complete)
All deliverables merged into the canonical set above, per master plan §7 and the
freeze instruction of July 2026. Pre-freeze history archived, not deleted.

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
