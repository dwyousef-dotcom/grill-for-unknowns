# Writing Great Skills Audit

This note records how `grill-for-unknowns` applies Matt Pocock's `writing-great-skills` guidance.

Source:

- https://github.com/mattpocock/skills/tree/main/skills/productivity/writing-great-skills

## Invocation

`grill-for-unknowns` is intentionally **model-invoked**: it keeps a `description` because the agent should proactively reach for it before complex implementation, long-running subagent work, or plan review. That context load is justified because the user should not have to remember to invoke it every time the agent is about to rush into build mode.

The description uses the leading trigger concepts that should appear in real requests:

- complex implementation,
- docs/source evidence,
- unknown unknowns,
- avoid rushing into build mode,
- map-vs-territory unknowns pass.

## Leading words

The skill deliberately repeats a small set of leading words rather than inventing many new terms:

- **map** — the prompt, plan, assumptions, and current mental model,
- **territory** — real docs, source, tests, constraints, environment, and user taste,
- **unknowns** — the gap between map and territory,
- **grill** — relentless, one-material-question-at-a-time interrogation before building.

These words are meant to anchor both invocation and execution.

## Information hierarchy

The primary `SKILL.md` keeps the runtime-critical steps inline:

1. read the territory,
2. classify unknowns,
3. grill one material decision at a time,
4. preserve domain language,
5. produce a launch packet / verification gates before implementation.

Reference material is progressively disclosed:

- `references/upstream-lineage.md` keeps source-skill lineage and dependency composition out of the main path.
- `references/domain-modeling-add-on.md` keeps `CONTEXT.md` and ADR rules behind a pointer.
- `templates/` contains reusable working documents instead of bloating the skill body.

## Completion criteria

The skill avoids vague "understand the task" completion by requiring checkable outputs before moving from planning to build mode:

- relevant docs/source/tests/config inspected or lack of access stated,
- known knowns / known unknowns / unknown knowns / suspected unknown unknowns listed,
- blocking questions are material and include defaults,
- low-risk unknowns converted into labeled assumptions,
- deviation policy and verification gates defined.

## Pruning and failure modes

The skill tries to avoid these `writing-great-skills` failure modes:

- **Premature completion** — explicit build gate: do not build until shared understanding or approved assumptions.
- **Duplication** — lineage and domain-modeling details are disclosed in references rather than repeated in full.
- **No-op advice** — instructions focus on behavior that changes default agent behavior: read before asking, ask one material question, log deviations, stop on architecture/security/cost/user-facing changes.
- **Negation** — hard prohibitions are paired with positive behavior, e.g. "do not ask what the code can answer" + "inspect docs/source/tests/config first".
- **Sprawl** — the file is still substantial because this is a composition skill. If it grows further, move example prompts, launch packets, or post-implementation reporting details into additional reference files.

## Design trade-off

This skill intentionally pays more body length than a tiny upstream composition skill because Hermes skills are often used as standalone operational playbooks. The current split keeps the high-leverage runtime sequence inline while pushing lineage, ADR/domain rules, and templates behind context pointers.
