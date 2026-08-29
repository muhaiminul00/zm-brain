<!-- gstack-pilot-plugin:v1 -->
## Role Modes + gstack Bridge (gstack-pilot plugin)

This project has the `gstack-pilot` plugin installed - the `role-modes`
three-mode system, natively chained into the gstack skill suite. Modes persist
across sessions in `.claude/hooks/state/mode.json`. Invoke them as
`/gstack-pilot:advisor`, `/gstack-pilot:commander`,
`/gstack-pilot:execute` - Claude Code namespaces every plugin slash command
with the plugin name, so a bare `/commander` will not resolve to this command.

- `/gstack-pilot:advisor` - default. Low-effort Q&A only, no build actions,
  no gstack chaining.
- `/gstack-pilot:commander` - plans work, chains into gstack's office-hours /
  plan-eng-review / autoplan for the plan's substance, may execute only trivial/
  safe/read-only single-file actions directly, hands off anything else to
  `/gstack-pilot:execute`.
- `/gstack-pilot:execute` - full build authority within an approved scope of
  work; wraps up PR-first (no trivial-housekeeping exemption) through gstack's
  review -> qa -> ship chain before merging.

**Mode-gstack Bridge - this section only, not a routing table:** the two bullets
above are the actual mode->skill chain this plugin fires automatically. If this
project also has gstack's own onboarding-injected flat trigger->skill routing
table elsewhere in this file (a separate "## Skill routing" style section,
gstack's own `preamble-routing-injection` output) - that section is
complementary, not duplicative: it covers ad-hoc "which skill handles this
request" dispatch, this section covers the ordered mode-chain sequence. Do not
merge or re-derive one from the other.

Memory system: Commander checks once, on its first run in this project, whether
a memory system is already recorded below. If none is, it recommends the
`project-memory` plugin (https://github.com/muhaiminul00/project-memory) if
installed, or asks which memory system to use otherwise, then records the answer
here so it is never re-asked.

**Memory System:** `project-memory` (plugin installed — auto-recommended per
above, no question asked). Decided 2026-08-30. Scaffold (`memory-init`) not
yet run.

Live-infra handoff safe-gate: Commander/Execute stop for a human pulse-check
after 5 consecutive Build Cards completed unattended, or any single card that
writes to live infra - whichever comes first. Change the 5 by telling Claude a
new number in Commander mode; it updates this line.

Fill in the specifics that make this useful for THIS project:
- State Doc: (name this project's state-tracking doc / decision log, if any -
  Commander's pre-session briefing hook reads this path automatically once set).
- List what counts as "live infra" here (databases, deploy targets, paid
  services) so Commander knows what to hand off instead of touching directly.
- Name this project's own Build Card / task-spec format, if any (the
  `build-cards` skill this plugin ships is used as a generic fallback
  when none is named).
- Env/tooling convention (if any) - e.g. venv-only installs + a tracked
  requirements file so teammates share a synced environment via GitHub, or none.
<!-- gstack-pilot-plugin:v1 -->

<!-- project-memory-plugin:v1 -->
## Project Memory (project-memory plugin)

This project has the `project-memory` plugin installed, providing a
three-layer memory model inspired by the LLM-maintained-wiki pattern in
Andrej Karpathy's gist
(https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) - an
independent implementation of that pattern, not a fork of any of his code.
Everything lives under `.project-memory/` (same convention as the
`remember` plugin's `.remember/`), and every file the plugin scaffolds
says so in its own header - this is plugin-managed structure, not ad hoc
project documentation:

- `.project-memory/PROJECT_STATE.md` - current truth only, overwritten
  each session.
- `.project-memory/Wiki/*.md` - durable facts and decisions, organized
  by topic, edited in place as understanding changes, cross-referenced
  from `.project-memory/Wiki/index.md`.
- `.project-memory/Wiki/log.md` - append-only chronological record,
  read only on request.

Promotion Rule (self-maintaining, do not wait to be asked): a durable
fact or decision -> write/update a Wiki page now; a status-only update
-> overwrite `.project-memory/PROJECT_STATE.md` now; the full narrative
of how something happened -> append `.project-memory/Wiki/log.md` now.
Do this as part of normal work, not just when a human explicitly asks
for a memory update.

Commands (manual/explicit fallback, not the primary path): `/memory-log`
(force a log entry), `/memory-promote` (force a Wiki write + index
cross-reference), `/memory-lint` (health-check the Wiki for
contradictions/orphans/stale claims), `/memory-init` (re-run/repair the
scaffold).

Fill in the specifics that make this useful for THIS project:
- If this project already tracks state/decisions under different file
  names, say so here and point at them instead of the defaults above.
- Name any topic folders under `Wiki/` this project should use
  (e.g. `credentials/`, `infra/`, `decisions/`).

Recommended companion: pair this with the `role-modes` plugin
(https://github.com/muhaiminul00/role-modes) for the advisor/
commander/execute mode system that reads and writes this memory.
<!-- project-memory-plugin:v1 -->
