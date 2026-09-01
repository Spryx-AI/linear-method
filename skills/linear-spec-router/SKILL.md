---
name: linear-spec-router
description: >-
  Decide se o texto vira Initiative, Project Doc, Issues ou review. Use ao colar
  spec do Productboard/Notion/chat, pedir Linear, issues ou review. Não grava no
  Linear.
---
# Linear spec router

Classifique e aponte a skill. Não grava no Linear.

Siga `linear-write-protocol` só na skill seguinte.

Leia `examples.md` nesta pasta se o tipo não estiver óbvio.

## Quando

Cola de spec, “passar pro Linear”, “quebrar em issues”, “está pronto?”, “por onde começo”.

## Rota

| Sinal | Skill |
| --- | --- |
| Problema, outcomes, hipótese, beta, mapa de capabilities, quase sem tela | `linear-initiative` |
| Uma feature: escopo, regras, catálogo, jornadas | `linear-feature-spec` |
| Pedido explícito de tickets / handoff | `linear-issues` |
| “Está pronto?”, “falta o quê?” | `linear-spec-review` |
| Estratégia + contrato + jornadas no mesmo paste | Split: 3 rascunhos curtos e esperar escolha |

Pedido explícito de artefato = confiança alta. Diagnóstico curto. Não perguntar de novo.

## Regras

- Initiative ≠ tela, slug, RB, catálogo.
- Project Doc ≠ métrica de beta / cohort / pricing da initiative.
- Issue cita ID da regra; não recopia catálogo.
- “Como [persona], quero…” vira candidato de issue, não prosa aqui.
- Exceção de domínio (ex. Conversation) = matriz no Doc, não issue-ensaio.
- “A definir com Design” = candidato DES-*, nunca AC de engenharia.
- Só o texto desta tarefa. [FALTA] em vez de inventar.

## Output

```md
## Diagnóstico
- Tipo: Initiative | Project Doc | Issues | Review | Blob
- Confiança: alta | média | baixa
- Por quê: 1–3 linhas

## Próximo passo
- Skill: linear-initiative | linear-feature-spec | linear-issues | linear-spec-review
- Esta skill não grava.

## Faltas
- [FALTA]   # omitir se vazio
```

Se confiança ≠ alta, no máximo 1 pergunta. Se blob, não gerar artefato final.
