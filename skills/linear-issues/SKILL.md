---
name: linear-issues
description: >-
  Quebra um Project Doc em issues do Linear, uma por comportamento observável.
  Após ok explícito, grava no Project. Use para tickets, issues ou handoff de
  engenharia.
---
# Linear issues

Uma issue = um comportamento observável. Contrato fica no Project Doc.

Siga `linear-write-protocol`. Não cria Initiative nem Project Doc.

Leia `examples.md` nesta pasta. Prefira poucas issues boas. O engenheiro pode reescrever a issue ao pegar.

## Quando

Pedido de tickets / handoff, e já existe Project/Doc (no texto ou no Linear). Sem project unívoco: [FALTA], não gravar.

## Forma

Título: verbo + objeto + restrição visível.

Corpo, curto (cabe num review):

- O que acontece (linguagem simples; Dado/Quando/Então só se reduzir ambiguidade)
- Não faz (1–3 linhas)
- Contrato: IDs do doc, não a regra inteira
- Proto ou [FALTA]
- Falha não deixa estado parcial

Não: user story, “implementar a feature”, recopiar catálogo, AC “bom UX”.
Gancho para feature irmã: uma linha + ID.
Design indefinido: DES-*, issue separada.
Duplicata de título no mesmo project: não criar, avisar.

IDs locais PREFIXO-##. Linear ID só no recibo.

## Milestone / relation

Só se o texto tiver fase real (ex. alpha) ou bloqueio óbvio. Sem os 5 defaults. Sem árvore especulativa.

## Write

Ordem: issues → relations só as confirmadas. Antes de create, buscar título igual no project.

Confirmação válida também: `cria todas`, `cria todas menos DES-01`, `cria só: OBJ-01, OBJ-02`.

## Output fase 1

```md
## Draft Linear (fase 1)
- Team:
- Project:
- Ação: create

### Lote
| id | título | bloqueia | proto |
| --- | --- | --- | --- |

### OBJ-01 — <título>
Faz: …
Não faz: …
Contrato: [RB-…]
Proto: …
Bloqueia: —

Responda: pode criar | cria todas | cria só: <lista> | não grava
```
