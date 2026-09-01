# Issues

Leia antes de quebrar um Project em issues. Assume que o Project e o Project Doc já
existem (no Linear ou no texto colado). Se não existirem, ou se houver dois Projects
candidatos, escreva `[FALTA: project]` no draft e não grave; issue sem project certo é
issue perdida.

## O que é uma issue aqui

Uma issue descreve **um comportamento observável** que alguém pode implementar e alguém
pode verificar. Não é uma feature ("Implementar Custom Objects"), não é uma user story
("Como admin, quero…"), não é um capítulo do Doc ("Regras RB-OBJ-001 a 010").

O Linear Method pede issues curtas, em linguagem simples, escritas por quem vai executar.
Quando é o PM que escreve no handoff, a issue é um **ask**: descreve o comportamento
esperado e aponta a regra do contrato; o engenheiro que pegar pode reescrever como
tarefa, quebrar em sub-issues ou renomear. Deixe isso explícito no rodapé do corpo para
que ninguém trate o texto do PM como especificação fechada.

## Quantas issues

No handoff, **poucas e coarse**: uma por linha do índice de jornadas do Doc, mais uma
`Explorar design de X` por DES-*. Não é uma contradição com o Method ("issues as small
as possible"): é uma fase. O PM entrega jornadas; o engenheiro, que sabe como o código
está organizado, quebra em tarefas pequenas. Se você gerar a árvore inteira de
sub-tarefas agora, vai adivinhar a estrutura do código e errar, e a árvore especulativa
vira lixo no backlog.

## Título

Verbo no infinitivo + objeto + a restrição que dá para observar. O título precisa ser
entendido numa lista de 30 issues, sem abrir nenhuma.

- Bom: `Criar Object gera Object + view All records + 4 system attributes`
- Bom: `Rollback ativa versão anterior sem editar histórico`
- Ruim: `Criar Custom Object` (não diz o que se observa)
- Ruim: `Implementar criação de objetos conforme RB-OBJ-001..010` (é capítulo)
- Ruim: `Como admin, quero criar objetos` (é story)

## Corpo

Curto: cabe numa leitura de review sem rolar. Modelo:

```md
**Comportamento esperado**
<2 a 5 linhas do que acontece, do ponto de vista de quem usa. Dado/Quando/Então só se
reduzir ambiguidade.>

**Não faz**
<1 a 3 linhas do que está explicitamente fora, se o Doc disser. Inclua o gancho para a
feature irmã em uma linha, com o id do Project dela, se houver.>

**Contrato**
RB-XXX-001, RB-XXX-003, ENT-001 — ver Project Doc <link>

**Proto**
Paper N-M / link Figma / [FALTA: proto] / — (comportamento sem tela)

**Falha**
<Uma linha: o que acontece se der erro. Padrão: "não deixa estado parcial".>

_Escrita no handoff por <owner>; quem pegar pode reescrever como tarefa._
```

Por que assim:

- **Não cole a regra RB inteira nem o catálogo.** Eles mudam no Doc, e a issue fica
  desatualizada sem ninguém perceber. Id + link envelhece bem.
- **Não escreva critério de aceite subjetivo** ("UX clara", "ficar bom", "rápido"). Não
  dá para verificar, então vira discussão no review.
- **Se o texto original tem fala de cliente**, cole a frase literal entre aspas e linke
  a origem (Attio, Customer Request). O engenheiro entende a dor melhor pela fala do que
  pelo resumo.
- **"Falha não deixa estado parcial"** é a linha mais barata da issue e a que mais evita
  bug: obriga a pensar no rollback antes de codar.
- **Proto "—" não é `[FALTA]`.** Comportamento sem tela (uma regra de deduplicação, um
  job) não tem proto por natureza; escreva "— (sem tela)". `[FALTA: proto]` é para
  jornada com tela cujo desenho não existe.
- **Se o texto lista as regras sem dizer qual issue cobre qual**, cite em cada issue só
  as regras que o comportamento dela claramente exercita, e marque
  `[FALTA: confirmar regras por issue]` nas que ficaram ambíguas. Não cite todas em todas:
  isso anula a rastreabilidade que o id existe para dar.
- **Owner do Project não é assignee da issue.** O rodapé diz quem escreveu; o campo
  assignee fica vazio até alguém pegar, a menos que o texto nomeie o responsável.

## Design indefinido

Se uma jornada depende de decisão de design que ainda não existe, crie **uma** issue
`Explorar design de <jornada>` (corpo: o que precisa ser decidido, 2–3 linhas, sem
critério de aceite de engenharia) e **nenhuma** issue de engenharia para essa jornada até
o proto existir. Não transforme "a definir com Design" em critério de aceite de uma issue
de engenharia: o engenheiro vai implementar uma coisa e o design vai chegar com outra.

## Milestones e relations

Só se o texto tiver fase real ("alpha sem API pública", "v2 com relacionamentos") ou
bloqueio óbvio ("depende da migração X", uma issue que cria a estrutura que a outra usa).
Não invente milestones por padrão nem relations `blocks` especulativas: cada relation
falsa é um engenheiro esperando algo que não precisava esperar.

## Duplicatas

Antes de gravar, busque no Project por título igual ou quase igual (`list_issues` com
filtro de project). Se existir, não crie: aponte a existente no draft e ofereça update ou
pular.

## Formato do draft

```md
**Team:** <nome> · **Project:** <nome> (<existente | [FALTA: project]>) · **Doc:** <link ou —>

### Lote
| id | título | proto | bloqueia |
|---|---|---|---|
| XXX-01 | … | Paper N-M | — |
| DES-01 | Explorar design de … | — | XXX-02 |

### XXX-01 · <título>
<corpo no modelo acima>

### XXX-02 · <título>
…

### DES-01 · Explorar design de <jornada>
<2–3 linhas do que precisa ser decidido>

Posso criar no Linear?
  a) todas (XXX-01, XXX-02, DES-01)
  b) todas menos DES-01
  c) só: <ids>
  d) não gravar
```

A gravação segue o protocolo do SKILL.md: `save_issue` com `project` preenchido, uma por
vez, relations só as confirmadas, recibo com URL por issue e lista do que não gravou.

Veja o exemplo completo em `examples/issues-handoff-studio.md`.
