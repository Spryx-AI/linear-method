# Contributing

The skill is read by a model that has none of your context. Every rule in it is written
for that reader. These are the conventions that keep it that way.

## Writing standard

1. **Imperative + why.** Write "Não copie o catálogo para a issue, porque ele muda e a
   issue fica desatualizada; linke o Doc" rather than "Não recopiar catálogo". A rule
   without its reason gets applied literally in the cases it was meant for and ignored
   in the cases it wasn't.

2. **Every internal term is in the glossary.** If you use `RB-*`, `matriz`, `System
   Object` or any other Spryx term in a skill file, it must have an entry in
   `references/glossario-spryx.md`. If you introduce a new term, add it in the same PR.

3. **An example is input + complete output.** Each file in `references/examples/` shows
   the text the user pasted (shortened is fine) and the full draft the skill returned,
   plus a short "what to observe" list. A description of an example ("good title:
   X; bad title: Y") is not an example.

4. **At least one example per artifact type outside Custom Objects.** Otherwise the
   model learns that "spec" means "Custom Objects" and forces a Conversation matrix
   onto a Live Chat feature.

5. **One language per layer.** Skill body, references and examples in Brazilian
   Portuguese. README and CONTRIBUTING in English. Frontmatter `description` in
   Portuguese, written to trigger: list the concrete phrases users actually say,
   including informal ones.

6. **SKILL.md stays under ~200 lines.** Anything that is only needed for one artifact
   type goes to `references/<artifact>.md`. The SKILL.md decides which reference to
   read; it does not repeat their content.

7. **No magic phrases.** Confirmation is a closed question with lettered options at the
   end of every draft, not a list of accepted strings. If you find yourself adding a
   phrase to an "accepted confirmations" list, the question is not closed enough.

## Before opening a PR

Run the three smoke prompts below against the skill (in Claude Code, Cursor, or with
the `skill-creator` eval loop) and check the expected behavior:

| Prompt | Expected |
|---|---|
| An initiative paste with no owner and no metric | Draft with `[FALTA: owner]`, `[FALTA: cohort]`; nothing invented |
| A paste mixing initiative + spec + tickets | No artifact generated; three-line diagnosis and a question |
| "manda ver" before the closed question was asked | Skill asks the closed question; nothing written |

Also check: frontmatter is valid YAML, every `references/*.md` linked from SKILL.md
exists, and no `[CONFIRMAR]` was added without a note in the PR saying who should
confirm it.
