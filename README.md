# linear-method

An [Agent Skill](https://agentskills.io/specification) that turns product text (a spec
pasted from Notion or Productboard, meeting notes, a request in chat) into Linear
artifacts — Initiative, Project + Project Doc, Issues, or a readiness review — following
the [Linear Method](https://linear.app/method) with Spryx's own conventions layered on
top.

**What it is:** Linear Method + Spryx conventions. The Method gives the shape (owners,
short project briefs, small concrete issues, design placeholders). Spryx adds a spec
vocabulary the Method does not have: rule IDs (`RB-*`, `ENT-*`), design placeholders
(`DES-*`), an exception matrix, a journey index, and a `[FALTA]` marker for anything the
source text did not say. Both are documented in the skill; nothing is assumed to be
universal.

**What it is not:** it does not cover cycles, triage, sprint planning, or syncing issues
with git. Those are operating concerns, not spec concerns, and other skills cover them.

## Install

```bash
npx skills add Spryx-AI/linear-method
```

Cursor:

```bash
npx skills add Spryx-AI/linear-method --agent cursor
```

Claude Code:

```bash
npx skills add Spryx-AI/linear-method --agent claude-code
```

## Writing to Linear

This pack is **method only**: it ships no MCP server. Install Linear's official MCP
server (or the `linear` plugin from the Claude plugins marketplace) so the agent can
write. The skill maps its steps onto the official server's tools (`save_project`,
`create_document`, `save_issue`, initiative tools, `list_*`) and falls back to "draft
only" when no Linear integration is present.

The skill never writes to Linear on its own. It always drafts first, then ends with a
closed question with lettered options (create everything / create only X / update
`<id>` / don't write). Praise ("looks good") is not a confirmation; picking an option is.
Every write ends with a receipt: URLs for what was created, and an explicit list of what
was **not** written.

## Layout

```
skills/linear-method/
├── SKILL.md                 # decision table, shared principles, write protocol
└── references/
    ├── glossario-spryx.md   # what RB-*, DES-*, [FALTA], catálogo, matriz… mean
    ├── workspace-spryx.md   # teams, issue prefixes, active initiatives, owners
    ├── initiative.md
    ├── project-spec.md
    ├── issues.md
    ├── review.md
    └── examples/            # one complete paste → draft per artifact type
```

The skill body and references are in Brazilian Portuguese, which is the language Spryx
writes specs in. This README is in English because it is the install entry point.

## Status

`references/workspace-spryx.md` and a few glossary entries are marked `[FALTA]` /
`[CONFIRMAR]` — they encode facts about Spryx's Linear workspace that only the team can
fill in. The skill works without them (it resolves teams and projects at runtime and
asks when ambiguous), but it works better with them.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the writing standard used in this repo.

## License

MIT
