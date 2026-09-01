# Project + Project Doc

Leia antes de escrever a spec de uma capability. Um **Project** é uma capability
entregável em 1–3 semanas por 1–3 pessoas, com owner. Ele tem uma **description curta**
(o que dá para fazer, em ≤8 linhas) e um **Project Doc** onde vive o contrato: IN/OUT,
regras, exceções, jornadas.

## Antes de escrever: teste de escopo

Responda para si mesmo, com o texto na mão:

1. Dá para descrever a capability em uma frase com um verbo? ("Admin cria e arquiva
   Custom Objects e Attributes.")
2. Uma dupla entrega isso em até três semanas?
3. Há um owner nomeado?

Se (1) falha, o texto provavelmente descreve uma Initiative ou dois Projects; volte para
a tabela de decisão do SKILL.md. Se (2) falha, proponha o corte **antes** do Doc: liste
2–4 Projects candidatos (ou Milestones dentro de um Project, se as fases dependem uma
da outra) e pergunte qual escrever primeiro. Escrever o Doc de um Project de três meses
produz um documento que ninguém consegue verificar contra a entrega. Se (3) falha,
`[FALTA: owner]` e siga.

## Obrigatório

Qual capability, o que está IN, o que está OUT. Todo o resto pode ser `[FALTA]`.

## Project description (≤8 linhas)

É o que aparece na lista de Projects do Linear, então precisa funcionar sem abrir o Doc:

- O que dá para fazer (uma ou duas frases).
- A exceção de domínio mais importante, em uma frase, se houver.
- Os Projects irmãos que estão fora ("Records, Relationships e Pipelines são projects
  separados"), para ninguém implementar a feature vizinha aqui.
- "Spec completa no Document deste project."

## Project Doc

Abra com **por quê / o quê / como** em até 10 linhas: é o que o Linear Method pede
("briefly communicate the why, what and how") e é o que a maior parte dos leitores vai
ler. As seções seguintes são o contrato, e as duas últimas são apêndice.

```md
# <Nome do Project>
**Owner:** <nome ou [FALTA: owner]> · **Initiative:** <nome ou —>

## Resumo
<Por quê (1–3 linhas), o quê (1–3 linhas), como em alto nível (1–3 linhas).>

## Escopo
**IN**
- <…>
**OUT**
- <…, incluindo irmãos>

## Matriz de exceção   # omitir se nenhuma entidade foge do genérico
| Capacidade | <Entidade> | Contrato |
|---|---|---|

## Decisões
| Decisão | Alternativa descartada | Motivo |
|---|---|---|

## Regras
| ID | Regra |
|---|---|
| RB-XXX-001 | <frase verificável> |

## Índice de jornadas
| id | título | proto |
|---|---|---|
| XXX-01 | <verbo + objeto + restrição observável> | Paper N-M / [FALTA: proto] |
| DES-01 | Explorar design de <jornada> | — |

## Catálogo   # apêndice; omitir se o texto não trouxer
<tipos, campos, opções>
```

## Regras de conteúdo

**A matriz prevalece.** Se uma entidade (Conversation é o caso recorrente) não herda o
comportamento genérico, isso vai em tabela, capacidade por capacidade, e a tabela vence
qualquer parágrafo que diga o contrário. Exceção em prosa se perde; em tabela, o
engenheiro consulta.

**Regras têm id, e o id vem do texto.** Se o texto traz RB-OBJ-001, preserve. Se o texto
descreve regras sem id, atribua ids sequenciais com o prefixo da área e diga que fez isso.
Não copie a mesma regra em dois lugares (catálogo e jornada, por exemplo); uma regra, um
id, um lugar.

**User story vira linha do índice.** "Como admin, quero ver a lista de objetos" vira
`OBJ-01 | Listar System vs Custom Objects | Paper 7-0`. Não escreva a story em prosa
no Doc: ela não é verificável e vai virar issue de qualquer jeito.

**"A definir com Design" vira DES-\*.** Uma linha no índice, `Explorar design de X`.
Nunca um critério de aceite ("UX deve ficar clara") nem uma issue de engenharia sem
proto.

**Nada de Initiative aqui.** Métrica de beta, cohort, pricing, teto de entitlement:
cite o id ENT-* se a regra existe, mas o valor e a decisão ficam na Initiative. Se o
texto mistura, mova e liste sob "Movido para Initiative" no final do draft.

**Não invente milestones.** Só se o texto tem fase real ("v1 sem API pública, v2 com").

## Gravação

Ordem: Project (`save_project`, com team e, se houver, initiative) → Document
(`create_document`, linkado ao Project). Antes de criar, busque Project com título
igual no team; se existir, ofereça update e verifique se já tem Doc (não duplique Doc
com o mesmo título). Não crie issues aqui, a menos que o usuário tenha pedido o handoff
junto; nesse caso, leia `issues.md` e faça um segundo draft depois de gravar o Doc.

Pergunta fechada típica:

```
Posso gravar no Linear?
  a) criar Project + Doc
  b) criar só o Project (Doc depois)
  c) atualizar <id> e o Doc dele em vez de criar
  d) não gravar, só ajustar o draft
```

Veja o exemplo completo em `examples/project-spec-live-chat-routing.md`.
