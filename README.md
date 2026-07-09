# grill-for-unknowns

**An agent skill for finding unknowns, grilling plans, and reaching shared understanding before implementation.**

`grill-for-unknowns` combines docs/source-grounded plan interrogation with the “finding your unknowns” strategy: known knowns, known unknowns, unknown knowns, and unknown unknowns.

The intended behavior is simple:

> Inspect the real territory first, grill the plan and user only where decisions matter, surface blindspots, write down the shared understanding, then build.

## What it does

Use this skill when an agent should **not** rush straight into implementation:

- unfamiliar codebase area,
- unfamiliar API/library/platform docs,
- vague product/design direction,
- long-running subagent or coding-agent launch,
- complex architecture or domain-model decision,
- failed previous attempt due to assumptions,
- or any plan that needs to be pressure-tested before building.

The skill asks the agent to separate:

- **facts** it can discover from docs/source/tests/config,
- **decisions** it needs the user to make,
- **domain language** that should be clarified and recorded,
- and **unknowns** that could materially change implementation.

## Install

### Hermes Agent

Clone the repo and copy the installable skill folder into your Hermes skills directory:

```bash
git clone https://github.com/nicobailon/grill-for-unknowns.git /tmp/grill-for-unknowns
mkdir -p ~/.hermes/skills/software-development
cp -R /tmp/grill-for-unknowns/plugins/grill-for-unknowns ~/.hermes/skills/software-development/grill-for-unknowns
```

Then start a fresh Hermes session or reload skills, and load it explicitly when needed:

```txt
/skill grill-for-unknowns
```

### Manual install from this checkout

```bash
mkdir -p ~/.hermes/skills/software-development
cp -R plugins/grill-for-unknowns ~/.hermes/skills/software-development/grill-for-unknowns
```

## Example prompts

```txt
Use grill-for-unknowns before implementing this. Inspect the relevant docs/source first, then interview me one material question at a time until we have shared understanding.
```

```txt
Grill this plan against the codebase and official docs. Do not build yet. Surface unknown unknowns, challenge domain terms, and produce a launch packet.
```

```txt
I know what I want when I see it. Use grill-for-unknowns to prototype options and extract my unknown knowns before implementation.
```

```txt
Before spawning subagents, use grill-for-unknowns to turn this fuzzy request into a clear launch packet with assumptions, open questions, verification steps, and rollback risks.
```

## Package contents

```txt
grill-for-unknowns/
├── README.md
├── CHANGELOG.md
├── LICENSE
├── NOTICE.md
├── package.json
└── plugins/
    └── grill-for-unknowns/
        ├── SKILL.md
        ├── README.md
        ├── LICENSE
        ├── references/
        │   ├── upstream-lineage.md
        │   ├── domain-modeling-add-on.md
        │   └── writing-great-skills-audit.md
        └── templates/
            ├── ADR.md
            ├── CONTEXT.md
            └── grill-session.md
```

## Credits and lineage

This skill is substantially inspired by, and should be treated as an adaptation/fork of, Matt Pocock’s skill composition around `grill-with-docs`:

- Matt Pocock’s `grill-with-docs` skill:  
  https://github.com/mattpocock/skills/blob/main/skills/engineering/grill-with-docs/SKILL.md
- Matt Pocock’s `domain-modeling` skill:  
  https://github.com/mattpocock/skills/tree/main/skills/engineering/domain-modeling
- Matt Pocock’s `grilling` skill:  
  https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md
- Matt Pocock’s `writing-great-skills` skill-authoring guidance:  
  https://github.com/mattpocock/skills/tree/main/skills/productivity/writing-great-skills

Additional inspiration comes from Thariq’s X article:

- Thariq, “A Field Guide to Fable: Finding Your Unknowns”:  
  https://x.com/trq212/status/2073100352921215386

## License

MIT. See [`LICENSE`](LICENSE).

The upstream `mattpocock/skills` repository is MIT licensed with copyright held by Matt Pocock. Because this skill is an adaptation/fork rather than a totally original work, the license preserves Matt Pocock’s MIT copyright notice and adds Nico Bailon’s copyright notice for the Hermes adaptation.
