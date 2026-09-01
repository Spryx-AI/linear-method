# Exemplo: handoff de issues (Studio — Publicar versão de flow)

Mostra o handoff a partir de um índice de jornadas existente: uma issue por jornada, uma
DES separada, contrato por id, e a relação `bloqueia` só onde é óbvia.

## Texto colado pelo usuário

> quebra em tickets no project "Studio — Publicar versão de flow" (já existe no linear,
> doc tá lá). Índice do doc:
>
> | id | título | proto |
> |---|---|---|
> | FLW-01 | Publicar draft cria versão imutável e ativa | Paper 3-1 |
> | FLW-02 | Rollback ativa versão anterior sem editar histórico | [FALTA] |
> | DES-01 | Lista de versões (colunas e ordenação a definir) | — |
>
> Regras: RB-FLW-010 (publicar congela o draft numa versão numerada), RB-FLW-011 (só uma
> versão ativa por flow), RB-FLW-020 (rollback cria uma nova versão ativa igual à
> anterior; não apaga nada).
>
> O Bruno (eng) comentou na review: "se a publicação falhar no meio, não pode ficar
> versão meio criada". Owner do project sou eu (Pedro).

## Draft devolvido pelo skill

Entendi como handoff de issues para um Project existente. Busquei no Project por títulos
iguais e não achei duplicatas. Duas issues de engenharia e uma de design; FLW-02 depende
da lista de versões existir (DES-01), então marquei o bloqueio.

---

**Team:** Studio · **Project:** Studio — Publicar versão de flow (existente) · **Doc:** [link do Project Doc]

### Lote
| id | título | proto | bloqueia |
|---|---|---|---|
| FLW-01 | Publicar draft cria versão imutável e ativa | Paper 3-1 | — |
| FLW-02 | Rollback ativa versão anterior sem editar histórico | [FALTA: proto] | — |
| DES-01 | Explorar design da lista de versões | — | FLW-02 |

### FLW-01 · Publicar draft cria versão imutável e ativa

**Comportamento esperado**
Ao publicar um flow em draft, o sistema cria uma versão numerada (n+1), imutável, e a
marca como ativa. O draft continua editável e passa a apontar para a nova versão como
base. Só existe uma versão ativa por flow.

**Não faz**
Não permite editar uma versão publicada. Não apaga versões anteriores. Não trata rollback
(FLW-02).

**Contrato**
RB-FLW-010, RB-FLW-011 — ver Project Doc [link]

**Proto**
Paper 3-1

**Falha**
Publicação que falha no meio não deixa versão parcial: ou a versão existe completa e
ativa, ou nada muda. ("se a publicação falhar no meio, não pode ficar versão meio
criada" — Bruno, review)

_Escrita no handoff por Pedro; quem pegar pode reescrever como tarefa._

### FLW-02 · Rollback ativa versão anterior sem editar histórico

**Comportamento esperado**
A partir da lista de versões, o usuário escolhe uma versão anterior e faz rollback. O
sistema cria uma nova versão (n+1) com o conteúdo idêntico à escolhida e a marca como
ativa. A versão que estava ativa continua no histórico.

**Não faz**
Não edita nem apaga nenhuma versão existente. Não altera o draft.

**Contrato**
RB-FLW-011, RB-FLW-020 — ver Project Doc [link]

**Proto**
[FALTA: proto] — depende de DES-01

**Falha**
Rollback que falha não deixa versão parcial nem muda a versão ativa.

_Escrita no handoff por Pedro; quem pegar pode reescrever como tarefa._

### DES-01 · Explorar design da lista de versões

Decidir colunas (número, data, autor, ativa?), ordenação padrão e onde fica a ação de
rollback. FLW-02 depende deste desenho para ter proto. Sem critério de aceite de
engenharia até o proto existir.

---

**Faltas**
- [FALTA: proto] em FLW-02 (coberto por DES-01).

Posso criar no Linear?
  a) todas (FLW-01, FLW-02, DES-01)
  b) todas menos DES-01
  c) só: <ids>
  d) não gravar

## Depois da confirmação

Usuário: `a`

Recibo devolvido pelo skill:

```
Criadas no project Studio — Publicar versão de flow:
- FLW-01 → SPR-482 https://linear.app/spryx/issue/SPR-482
- FLW-02 → SPR-483 https://linear.app/spryx/issue/SPR-483
- DES-01 → SPR-484 https://linear.app/spryx/issue/SPR-484
- Relation: SPR-484 blocks SPR-483

Não gravado: nada pendente.
```

## O que observar neste exemplo

- A fala do Bruno virou a linha "Falha" da FLW-01, literal e com origem.
- Contrato cita ids e linka o Doc; nenhuma regra RB copiada por inteiro.
- Só uma relation, e óbvia (rollback precisa da lista de versões). Nenhum milestone.
- O rodapé "quem pegar pode reescrever" está em cada issue de engenharia, não na DES.
- O recibo lista o que **não** gravou mesmo quando é "nada", para o usuário não
  precisar deduzir.
