---
name: linear-write-protocol
description: >-
  Use this whenever a Linear Initiative, Project Doc, Issue, or spec review
  patch is about to be written. Draft first, wait for an explicit create/update
  ok, then write, then return URLs. Never skip confirmation.
---
# Linear write protocol

Draft → ok explícito → write → recibo. Vale para initiative, project/doc, issues e patch de review.

## Fase 1
Montar markdown. Sem MCP/CLI de create/update/delete.

## Fase 2
Esperar confirmação explícita.

Válida: `pode criar`, `ok`, `grava`, `cria só o project e o doc`, `cria só: OBJ-01`, `pode atualizar <id>`, `não grava`.

Inválida: `fica bom`, `legal`, `segue`. Perguntar de novo em uma linha.

## Fase 3
MCP preferido. Resolver team/project por nome; 2 matches = parar. Só o recorte autorizado.

## Fase 4
URLs + o que não gravou.

Integração falhou: reportar e deixar o draft. Não afirmar que gravou.
