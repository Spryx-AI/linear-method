# Initiative

Leia antes de escrever uma Initiative. Uma Initiative é **uma página de investimento**:
diz qual problema vale atacar, para quem, o que o v1 precisa provar, e em quais
capabilities (Projects) isso se decompõe. Não é spec, não é backlog, não é roadmap
detalhado.

## Por que ela é curta

A Initiative é o documento que lideranças e outros times leem para decidir se o
investimento faz sentido. Quanto mais detalhe de implementação entra nela (telas, regras
RB, catálogo de campos), menos gente lê até o fim e mais ela diverge do Project Doc, que
é onde esse detalhe vive de verdade. Se um trecho do texto descreve **como** o sistema se
comporta, ele é candidato a Project Doc; anote isso na lista de Projects e siga.

## Obrigatório

Sem estas três coisas não existe Initiative, só uma ideia. Se o texto não traz, escreva
`[FALTA]` no lugar e siga, mas destaque na lista de faltas:

- **Problema**: o que está errado hoje e para quem.
- **Hipótese falsificável**: "se X, então Y, medido por Z".
- **Owner**: quem responde pelo brief e pela entrega.

## Estrutura

Cabe numa tela (algo entre 25 e 40 linhas de markdown). Preserve a ordem para que quem
lê várias Initiatives encontre a mesma coisa no mesmo lugar.

```md
# <Nome da Initiative>
**Owner:** <nome ou [FALTA: owner]> · **Status:** definição | revisão | pronto para build

## Problema
<≤5 linhas. Quem sofre, o que faz hoje como workaround, o que isso custa.>

## Hipótese
Se <mudança>, então <efeito>, medido por <métrica e janela>.

## Outcomes
- <fração do cohort + comportamento + janela: "5/7 orgs do beta ativam em 14 dias">
- <…>

## Mapa de Projects
- [ ] <Capability 1> — owner: <nome ou [FALTA]>
- [ ] <Capability 2>
- [ ] <…>

## Restrições e não-objetivos
<≤5 linhas. O que fica fora do v1 e por quê.>

## Sucesso e guardrails
<Sinais de que deu certo; sinais de que deve parar.>

## Rollout   # só se o texto trouxer
<Beta, cohort, critério de ampliação, teto de entitlement.>
```

## Regras de conteúdo

**Outcome tem denominador.** "A maioria das orgs ativa" não é outcome; "5/7 orgs do beta
ativam em 14 dias" é. Sem cohort no texto, escreva o comportamento esperado e
`[FALTA: cohort]`. Denominador vago faz a Initiative ser "bem-sucedida" para sempre.

**Mapa de Projects é uma checklist de capabilities, sem tela.** "Estrutura de Custom
Objects", "Records", "Relationships" são capabilities. "Tela de listagem de objetos em
Settings → Dados" é tela e pertence ao Doc. Se um item do mapa não cabe em 1–3 semanas,
divida-o em dois itens.

**Rollout e entitlement só se o texto trouxe.** Beta, cohort e teto de plano são decisões
de negócio; inventá-las aqui cria um compromisso que ninguém tomou. Se o texto não fala
disso, omita a seção inteira (não escreva `[FALTA: rollout]`; rollout indefinido é normal
em fase de definição).

**Exceção de domínio vira uma linha, não uma tabela.** Se Conversation não participa de
algo, escreva uma linha em Restrições ("Conversation não tem CRUD genérico nem
Pipeline"). A matriz completa vai para o Project Doc.

## O que cortar (e para onde vai)

| Se o texto tem… | Não entra na Initiative porque… | Vai para |
|---|---|---|
| Jornadas, "como admin, quero…" | É comportamento, não investimento | Índice de jornadas do Project Doc |
| Slug, nome de rota, tela | É implementação | Project Doc ou issue |
| Regras RB-*, ENT-* | É contrato | Seção Regras do Project Doc |
| Catálogo de tipos/campos | Muda com frequência | Apêndice do Project Doc |
| Critério de aceite | É verificação de issue | Issue |

Ao cortar, não jogue fora: liste no final do draft, sob "Movido para Project Doc", em
uma linha por item, para o usuário ver que você viu.

## Gravação

Crie ou atualize só a Initiative. Se o usuário citar Projects existentes pelo nome,
linke-os; não crie Projects filhos como efeito colateral. Antes de criar, busque
Initiative com título igual ou muito parecido; se existir, ofereça update.

Pergunta fechada típica:

```
Posso gravar no Linear?
  a) criar a Initiative
  b) atualizar <id> em vez de criar
  c) não gravar, só ajustar o draft
```

Veja o exemplo completo em `examples/initiative-custom-objects.md`.
