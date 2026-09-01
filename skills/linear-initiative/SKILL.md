---
name: linear-initiative
description: >-
  Escreve e, após ok explícito, grava uma Initiative no Linear. Use para texto
  estratégico (problema, hipótese, outcomes, mapa de projects). Não cria
  projects nem issues.
---
# Linear initiative

Uma página de investimento. Não é spec nem backlog.

Siga `linear-write-protocol`. Não cria Project nem Issue.

Leia `examples.md` nesta pasta antes de redigir o payload.

## Quando

Router = Initiative, ou o texto é problema / para quem / o que o v1 valida, quase sem tela.

## Cabeça

Problema, para quem, o que o v1 valida. Se faltar: [FALTA].

## Corpo (cabe numa tela)

1. Status: definição | revisão | pronto para build
2. Problema (≤5 linhas)
3. Hipótese: se X então Y medido por Z
4. Outcomes com denominador se houver cohort (5/7, não “a maioria”)
5. Mapa de Projects (checklist de capabilities, sem tela)
6. Restrições + não-objetivos (curto)
7. Sucesso / guardrails
8. Beta/rollout e teto de entitlement só se o texto trouxe

Cortar jornada, slug, RB, catálogo. Conversation: no máximo uma linha de restrição.

## Write

Create/update só da Initiative. Ligar projects existentes se o usuário der os nomes; não criar filhos.

## Output fase 1

```md
## Draft Linear (fase 1)
- Team:
- Initiative existente: [FALTA se create]
- Ação: create | update

# <nome>
Status:

## Problema
## Hipótese
## Outcomes
## Mapa de Projects
- [ ]
## Restrições e não-objetivos
## Sucesso e guardrails

## Faltas
- [FALTA]

Responda: pode criar | pode atualizar <id> | cria só a initiative | não grava
```
