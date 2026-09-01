---
name: linear-feature-spec
description: >-
  Use ao especificar uma feature: escopo, IN/OUT, regras RB-*, catálogo, jornadas,
  Project Doc no Linear. Um Project = uma capability. Contrato no Document. Não cria
  issues a menos que peçam também linear-issues.
---
# Linear feature spec

Um Project = uma capability. Description curta no Project. Contrato no Document. Siga `linear-write-protocol`. Não cria issues a menos que peçam também `linear-issues`.

Obrigatório: qual capability, IN e OUT. Resto [FALTA].

## Project
Description ≤8 linhas.

## Doc
- Contexto 1 parágrafo
- IN/OUT
- Matriz de exceção só se entidade não herda o genérico
- Decisões
- Regras com ID (preservar IDs do texto)
- Índice de jornadas → candidatos de issue + proto ou [FALTA]
- Catálogo como apêndice se o texto trouxer

Sem beta/cohort/pricing da initiative. User story vira linha no índice. Design indefinido = DES-* no índice, nunca AC.

IDs locais PREFIXO-##. Não inventar ABC-123.

## Write
Project → Document. Ligar à Initiative se o usuário deu. Update: não duplicar doc com o mesmo título. Sem milestone default.

## Output (fase 1)
Draft com Team, Project existente, Document existente, Ação create|update, description, seções Contexto/IN-OUT/Matriz/Decisões/Regras/Índice/Catálogo, Faltas.

Pedir: `pode criar` | `pode atualizar <id>` | `cria só o project e o doc` | `não grava`.
