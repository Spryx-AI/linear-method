# Linear Method skills

Portable Agent Skills pack for the Linear Method: **router → initiative → feature spec → issues → review**, with a shared **write protocol**.

Install with the [Vercel skills CLI](https://github.com/vercel-labs/skills). Skills follow the [Agent Skills spec](https://agentskills.io/specification).

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

List skills without installing:

```bash
npx skills add Spryx-AI/linear-method --list
```

## Skills

| Skill | Role |
| --- | --- |
| `linear-spec-router` | Classify a paste and point to the next skill. Does not write Linear. |
| `linear-initiative` | One investment page. Not a spec or backlog. |
| `linear-feature-spec` | One Project = one capability. Short Project description; contract in the Document. |
| `linear-issues` | One issue = one observable behavior. Contract stays in the Project Doc. |
| `linear-spec-review` | Point at holes. Do not rewrite the spec. |
| `linear-write-protocol` | Draft → explicit ok → write → URLs. Shared by the write skills. |

## Linear writes

This pack is **method only**. It does not include a Linear MCP/plugin.

Install the official Linear MCP or plugin separately if the agent should write to Linear. This pack does not write Linear until the user says an explicit phrase listed in `linear-write-protocol` (for example `pode criar`, `ok`, `grava`, `cria só o project e o doc`, `pode atualizar <id>`, `não grava`). Vague praise such as `fica bom` / `legal` / `segue` is not confirmation.

## License

MIT
