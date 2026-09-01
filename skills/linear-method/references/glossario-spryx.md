# Glossário (convenções Spryx)

Termos que aparecem nas specs da Spryx e nos artefatos do Linear. O Linear Method pede
para não inventar termos; estes já existem, então o trabalho é usá-los sempre com o
mesmo sentido. Se um termo do texto do usuário não estiver aqui, use-o como está e não
crie um sinônimo.

Itens marcados `[CONFIRMAR]` foram inferidos do uso nas specs existentes e precisam de
validação do time de produto. Ao confirmar, remova a marca.

## Ids e marcadores

**RB-\<ÁREA\>-\<NNN\>** — Regra de negócio. Uma frase verificável sobre comportamento do
sistema, com id estável. Ex.: `RB-OBJ-001 Criar Object gera automaticamente a view All
records`. Vive na seção "Regras" do Project Doc; issues citam o id, não o texto. A
`<ÁREA>` é um prefixo de 3 letras da capability (OBJ, ATT, FLW, CHT…). `[CONFIRMAR: lista
oficial de áreas]`

**DES-\<NN\>** — Decisão de design pendente. Marca uma jornada ou tela cujo desenho ainda
não existe. Vira uma issue `Explorar design de X` no handoff, e nunca vira critério de
aceite de engenharia. O `NN` é local ao Project.

**ENT-\<NNN\>** — Regra de entitlement (o que cada plano/tier pode fazer, limites,
tetos). Ex.: `ENT-001 Plano Starter cria até 3 Custom Objects`. Referenciada por issues
como qualquer RB. O **teto de entitlement** (o valor numérico do limite) é decisão de
negócio da Initiative; o Project Doc só cita o id. `[CONFIRMAR]`

**\<PREFIXO\>-\<NN\>** (ex.: OBJ-01, FLW-02) — Id local de candidato a issue, usado no
índice de jornadas do Doc e no draft de issues. Existe para o usuário poder dizer "cria
só OBJ-01 e OBJ-03" antes de existir id do Linear. Não é o identificador do Linear
(esse aparece só no recibo, ex.: SPR-123).

**[FALTA: o quê]** — Marcador de informação ausente no texto de origem. Sempre com o
complemento ("[FALTA: owner]", "[FALTA: proto]"). É a alternativa a inventar. Um
artefato pode ser gravado com `[FALTA]` dentro se o usuário autorizar; um artefato não
pode ser gravado com dado inventado.

## Estruturas do Project Doc

**Contrato** — O conjunto IN/OUT + regras RB/ENT + matriz de exceção de um Project. É o
que engenharia implementa e QA verifica. Vive só no Project Doc; issues apontam para ele.

**IN / OUT** — O que a capability faz e o que explicitamente não faz. "OUT" inclui os
irmãos (outros Projects da mesma Initiative) para que ninguém implemente a feature
vizinha por engano.

**Matriz de exceção** — Tabela que lista entidades que **não herdam o comportamento
genérico** da capability, capacidade por capacidade. Ex.: Conversation aceita Custom
Attributes mas não tem view All records nem Pipeline. Só existe se houver exceção. Quando
existe, prevalece sobre a prosa do Doc.

**Índice de jornadas** — Tabela `id | título | proto` que lista os candidatos a issue de
um Project. Cada user story do texto de origem vira uma linha aqui. É a ponte entre Doc
e handoff.

**Catálogo** — Lista de tipos, campos ou opções que a capability suporta (ex.: os tipos
de Custom Attribute: texto, número, data, seleção…). Vai como apêndice do Doc porque
muda com frequência; nunca é copiado para issue.

**Decisões** — Tabela curta de escolhas já tomadas com a alternativa descartada
("soft delete, não exclusão permanente"). Serve para o engenheiro não reabrir a discussão.

## Entidades do produto Spryx

**System Object** — Entidade nativa do produto (Contact, Company, Conversation…) que
existe independentemente de configuração do admin. Contrasta com **Custom Object**,
criado pelo admin. `[CONFIRMAR: lista oficial de System Objects]`

**Conversation** — System Object que representa uma conversa no Live Chat. É a exceção
mais frequente na matriz: aceita atributos e relacionamentos, mas não tem CRUD genérico
nem Pipeline, porque sua listagem é o Inbox. `[CONFIRMAR]`

**Records / Relationships / Pipelines / Lists** — Capabilities irmãs de Custom Objects
(instâncias, ligações entre objetos, processos com estágios, visões filtradas). Cada uma
é um Project separado. `[CONFIRMAR]`

**Studio** — Superfície de construção de agentes e flows. **Flow** tem draft e versões
publicadas. `[CONFIRMAR: nomenclatura de versão]`

**Live Chat** — Inbox omnichannel com colaboração humano-agente. Termos: fila, roteamento,
atribuição, transbordo (handoff humano). `[CONFIRMAR]`

## Artefatos e prototipagem

**Proto** — Protótipo navegável ou tela de referência. Na Spryx vem como "Paper N-M"
(ex.: Paper 4-0) ou link do Figma. Cada linha do índice de jornadas tem um proto ou
`[FALTA: proto]`. `[CONFIRMAR: o que é "Paper"]`

**Beta / rollout / cohort** — Plano de liberação (para quais orgs, em que ordem, com
que critério). É conteúdo da Initiative. Nunca vai para o Project Doc nem para issue.

**Outcome com denominador** — Métrica de resultado escrita como fração de um cohort
concreto ("5/7 orgs do beta ativam em 14 dias"), não como proporção vaga ("a maioria").
Sem cohort no texto, `[FALTA: cohort]`.

**Hipótese falsificável** — Frase no formato "se X, então Y, medido por Z". Sem o
"medido por", não dá para saber se a Initiative deu certo.

## Linear (vocabulário do Method)

**Initiative** — Agrupador estratégico de Projects. Uma página: problema, hipótese,
outcomes, mapa de Projects.

**Project** — Uma capability entregável em 1–3 semanas por 1–3 pessoas, com owner. Tem
description curta e um Project Doc.

**Project Doc (Document)** — Documento anexado ao Project onde vive o contrato.

**Milestone** — Fase dentro de um Project. Só quando o texto tem fase real.

**Issue** — Uma tarefa concreta: um comportamento observável. No handoff é escrita pelo
PM como *ask*; quem pega pode reescrever como tarefa.
