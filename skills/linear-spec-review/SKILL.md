---
name: linear-spec-review
description: >-
  Audita Initiative, Project Doc ou issues (separação, IDs, ACs, prontidão para
  engenharia). Use quando perguntarem se está pronto ou o que falta. Não grava
  salvo patch pontual confirmado.
---
# Linear spec review

Aponte buracos. Não reescreva a spec (isso é initiative / feature-spec / issues).

Não grava por padrão. Patch pontual só com ok explícito, via `linear-write-protocol`.

Leia `examples.md` nesta pasta.

## Quando

“Está pronto?”, “falta o quê?”, “pode ir pra engenharia?”, draft ou ids Linear na mesa.

## Olhar (não precisa marcar todos)

- Initiative: hipótese falsificável, outcomes com denominador, mapa sem tela, sem RB.
- Doc: IN/OUT, exceção em matriz, regras com ID, índice + proto, sem beta da initiative, Design ≠ AC.
- Issues: um comportamento, título com restrição, contrato por ID, sem catálogo copiado, project alvo.
- Cruzado: irmã especificada no lugar errado, entitlement atômico, PII na instrumentação, título duplicado.

## Veredito

Pronto para review conjunta | Pronto para build | Não.

## Output

```md
## Veredito
<um dos três>
- Motivo: 1–3 linhas

## Bloqueadores
-

## Ajustes menores
-

## Patch sugerido (não gravado)
- Alvo:
- Diff:

Para gravar o patch: pode atualizar <id> | não grava
```
