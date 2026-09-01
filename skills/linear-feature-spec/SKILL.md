---
name: linear-feature-spec
description: >-
  Escreve o Project Doc de UMA feature e, após ok explícito, grava Project +
  Document. Use para spec de comportamento. Não cria issues salvo pedido
  conjunto de linear-issues.
---
# Linear feature spec

Um Project = uma capability. Description curta no Project. Contrato no Document.

Siga `linear-write-protocol`. Não cria issues a menos que o usuário peça também `linear-issues`.

Leia `examples.md` nesta pasta antes de redigir.

## Quando

Uma feature com contexto, escopo, regras e/ou jornadas.

## Obrigatório

Qual capability, IN e OUT. Resto: [FALTA].

## Project description (≤8 linhas)

O que dá para fazer, exceção de domínio numa frase se houver, irmãos no Fora, pointer do doc.

## Doc

1. Contexto (1 parágrafo)
2. IN / OUT
3. Matriz de exceção — só se o texto tiver entidade que não herda o genérico
4. Decisões (tabela curta)
5. Regras com ID (preservar IDs do texto)
6. Índice de jornadas → candidatos de issue + proto ou [FALTA]
7. Catálogo (tipos/campos) como apêndice, se o texto trouxer

Sem beta, cohort, pricing da initiative. “Como persona, quero…” vira linha no índice. “A definir com Design” = DES-* no índice, nunca AC.

IDs locais de issue: PREFIXO-##. Não inventar ABC-123.

## Write

Ordem: Project → Document. Ligar à Initiative se o usuário deu. Update: não duplicar doc com o mesmo título. Sem milestone default.

## Output fase 1

```md
## Draft Linear (fase 1)
- Team:
- Initiative pai:
- Project existente: [FALTA se create]
- Ação: create | update

### Project description
<≤8 linhas>

### Document
# <feature>
## Contexto
## Escopo (IN / OUT)
## Matriz de exceção   # omitir se vazia
## Decisões
## Regras
| ID | Regra |
| --- | --- |
## Índice
| id | título | proto |
| --- | --- | --- |
## Catálogo   # omitir se vazio

Responda: pode criar | pode atualizar <id> | cria só o project e o doc | cria só o doc | não grava
```
