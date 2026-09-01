---
name: linear-method
description: >-
  Transforma texto de produto (spec colada do Notion/Productboard, resumo de reunião,
  pedido no chat) em artefatos do Linear seguindo o Linear Method com as convenções da
  Spryx: Initiative, Project + Project Doc, Issues, ou review de prontidão. Use sempre
  que o usuário colar uma spec e pedir para "passar pro Linear", "criar a initiative",
  "quebrar em issues/tickets", "fazer handoff pra eng", "joga isso no Linear", ou
  perguntar "isso tá pronto pra build?", "falta o quê?", "pode ir pra eng?", mesmo sem
  citar a palavra Linear. Também use quando pedirem para revisar uma Initiative,
  Project Doc ou lote de issues já existentes no Linear. Nunca grava no Linear sem
  confirmação explícita do usuário.
---

# Linear Method (Spryx)

Você recebe texto de produto e devolve um rascunho de artefato do Linear no formato
certo, pede confirmação com uma pergunta fechada, e só então grava via MCP oficial da
Linear. Este skill cobre o **método** (o que vai em cada artefato e por quê). Ele não
cobre cycles, triage, planning de sprint nem sync com git.

Leia `references/glossario-spryx.md` antes de produzir qualquer artefato. Os termos
RB-*, DES-*, `[FALTA]`, catálogo, matriz de exceção e System Object têm significado
específico na Spryx, e você vai errar se adivinhar pelo nome.

## 1. Decida qual artefato o texto pede

Leia o texto inteiro antes de decidir; a primeira frase costuma enganar. Se o usuário
pediu um artefato explicitamente ("faz a initiative", "quebra em tickets"), obedeça
sem diagnosticar. Caso contrário, use a tabela:

| O texto tem principalmente… | Artefato | Leia |
|---|---|---|
| Problema, hipótese, outcomes com número, mapa de capabilities, quase nenhuma tela | Initiative | `references/initiative.md` |
| Uma capability: escopo IN/OUT, regras RB-*, jornadas, catálogo de tipos | Project + Project Doc | `references/project-spec.md` |
| Pedido de tickets/handoff, e o Project já existe (no texto ou no Linear) | Issues | `references/issues.md` |
| "Tá pronto?", "falta o quê?", "pode ir pra eng?", ou um link/id de artefato para auditar | Review | `references/review.md` |
| Estratégia + contrato + jornadas misturados no mesmo paste | Nenhum. Veja abaixo. | — |

**Caso misto.** Não gere artefato. Diga em três linhas o que você vê de cada tipo no
texto ("as seções 1–2 são initiative, 3–6 são spec de Custom Objects, o final é uma
lista de tickets") e pergunte qual fazer primeiro. Um paste misto quase sempre vem de
um doc que ainda não foi fatiado; gerar os três de uma vez produz três artefatos ruins e
tira do usuário a chance de decidir o corte.

Depois de decidir, leia o arquivo de referência indicado e o exemplo correspondente em
`references/examples/`. Cada exemplo mostra o texto colado e o draft completo devolvido.

## 2. Princípios que valem para todos os artefatos

**Só o que está no texto.** Se falta owner, métrica, time, proto ou decisão, escreva
`[FALTA: o quê]` no lugar. Nunca invente um número de métrica, um nome de time, um id
de regra ou um link de proto. Um `[FALTA]` visível custa dez segundos para resolver;
um dado inventado vira compromisso que alguém vai cobrar.

**Owner nomeado.** Toda Initiative e todo Project têm um owner responsável pelo brief
e pela entrega (Linear Method). Se o texto não diz quem é, `[FALTA: owner]`. Issues
herdam o owner do Project até serem assumidas por alguém.

**Escopo de Project = 1 a 3 semanas, 1 a 3 pessoas.** Se a capability descrita não
cabe nisso, proponha o corte em Projects menores ou em Milestones antes de escrever o
Doc, e pergunte. Um Project de três meses vira um lugar onde issues se acumulam sem
que ninguém consiga dizer se está indo bem.

**Cada camada tem o seu conteúdo, e só ele.** Quando a mesma informação vive em dois
lugares, um deles fica errado.

- Initiative fala de problema, hipótese, outcomes e mapa de capabilities. Não tem tela,
  slug, regra RB nem catálogo.
- Project Doc tem o contrato (IN/OUT, RB-*, matriz de exceção, índice de jornadas).
  Não tem métrica de beta, cohort nem pricing; isso é da Initiative.
- Issue cita o id da regra e linka o Doc. Não recopia catálogo nem regra.

**User story vira candidato de issue, não prosa.** "Como admin, quero criar objeto" é
uma linha no índice de jornadas do Doc, e depois uma issue. Não vai para o corpo do Doc
como parágrafo, porque prosa de user story não é verificável e infla o documento.

**Design indefinido vira issue `Explorar design de X`.** Nunca vira critério de aceite
de engenharia. É o padrão do Linear Method para projetos com design pendente: uma issue
placeholder que se quebra depois, e nenhuma issue de engenharia para aquela jornada até
o proto existir.

**Fala de cliente entra literal.** Se o texto tem citação de cliente (call, ticket,
Attio, Customer Request do Linear), cole a frase entre aspas e linke a origem, em vez
de resumir. O cliente descreve a dor melhor do que o resumo dele.

**Preserve os ids do texto.** Se o paste já traz RB-OBJ-001, use RB-OBJ-001. Renumerar
quebra a rastreabilidade com o doc de origem.

## 3. Protocolo de gravação

Vale para tudo que escreve no Linear: Initiative, Project, Document, Issues e patch de
review.

1. **Draft primeiro.** Monte o artefato completo em markdown, no formato do arquivo de
   referência. Nesta fase não chame nenhuma tool de create/update/delete. Tools de
   leitura (`list_*`, `get_*`) podem ser usadas para checar se algo já existe.

2. **Termine com uma pergunta fechada e opções literais.** Por exemplo:

   ```
   Posso gravar no Linear?
     a) criar Project + Doc
     b) criar só o Project
     c) atualizar <id> em vez de criar
     d) não gravar, só ajustar o draft
   ```

   Aceite qualquer resposta que escolha uma opção sem ambiguidade ("a", "cria tudo",
   "só o project", "manda ver" depois desta pergunta é claramente (a)). Se a resposta
   não escolhe ("fica bom", "legal", "segue"), repita a pergunta em uma linha e não
   grave. Elogio não é autorização, e é mais barato perguntar de novo do que apagar
   um Project criado por engano. Se o usuário responder "manda ver" **antes** de você
   ter feito a pergunta, faça a pergunta.

3. **Antes de criar, procure duplicata.** Busque por título igual ou quase igual no
   mesmo team/project. Se existir, ofereça update em vez de criar. Resolva team e
   project por nome usando `references/workspace-spryx.md` e as tools `list_teams` /
   `list_projects`; se houver dois matches plausíveis, pare e pergunte qual.

4. **Grave só o recorte autorizado**, nesta ordem: Initiative → Project → Document
   (linkado ao Project) → Issues (com `project` preenchido) → Milestones e relations
   confirmadas. Update é sempre por id, nunca por "o project que tem esse nome".

5. **Devolva um recibo**: URL de cada objeto criado ou atualizado, e uma lista
   explícita do que **não** gravou (por exemplo "issues: não gravadas, aguardando").
   Se o MCP falhar, diga que falhou, mostre o erro e mantenha o draft disponível. Nunca
   afirme que gravou sem ter a URL na mão.

### Mapeamento para o MCP oficial da Linear

Os nomes de tool mudam entre versões do servidor. Use a lista de tools carregada na
sessão como fonte de verdade; os nomes abaixo são os da versão corrente e servem de
orientação.

| Ação | Tool (MCP oficial) | Observação |
|---|---|---|
| Criar/atualizar Initiative | tool de initiative (`save_initiative` ou equivalente) | Disponível desde fev/2026. Se a sessão não tiver, devolva o draft e diga que o servidor não expõe initiatives. |
| Criar/atualizar Project | `save_project` | Passe `team`; para update, passe o id. |
| Criar Project Doc | `create_document` / `update_document` | Linke ao Project. Um Doc por Project; não duplique título. |
| Criar/atualizar Issue | `save_issue` | Sempre com `project`. Não crie issue solta no team. |
| Milestone | `save_milestone` | Só quando o texto tem fase real. |
| Resolver nomes | `list_teams`, `list_projects`, `list_issues`, `list_documents` | Use antes de qualquer create. |

Se o servidor disponível não for o oficial (um MCP da comunidade, ou a CLI), mantenha o
protocolo e adapte os nomes. Se não houver nenhuma integração com Linear na sessão,
entregue o draft e diga que não tem como gravar.

## 4. Formato da resposta

Sempre nesta ordem, para que o usuário encontre a mesma coisa no mesmo lugar:

1. Uma linha dizendo o que você entendeu que o texto pede (ou a pergunta do caso misto).
2. O draft completo, no formato do arquivo de referência.
3. A lista de `[FALTA]`, se houver.
4. A pergunta fechada de gravação.

Depois da confirmação: o recibo.

## 5. Arquivos de referência

- `references/glossario-spryx.md` — o que significa cada termo interno. Leia sempre.
- `references/workspace-spryx.md` — teams, prefixos de issue, initiatives ativas, owners.
- `references/initiative.md`, `references/project-spec.md`, `references/issues.md`,
  `references/review.md` — estrutura, regras e o que cortar em cada artefato.
- `references/examples/` — um exemplo completo (paste → draft) por artefato.
