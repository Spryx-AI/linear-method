# Exemplo: Initiative (Customização de Objetos)

Mostra o caso em que o texto traz problema, hipótese e mapa, mas mistura tela e regra
RB (que o skill corta e lista), e não traz owner (que vira `[FALTA]`).

## Texto colado pelo usuário

> passa isso pro linear como initiative
>
> **Customização de objetos**
>
> Hoje o modelo de dados é fixo: Contact, Company, Conversation. Quando o cliente tem um
> processo próprio (ex.: "Sinistro", "Matrícula", "Ordem de serviço") ele leva pra
> planilha ou pra um CRM paralelo, e a Spryx perde o contexto da conversa. Nas calls de
> discovery com as 7 orgs do beta, 5 citaram planilha paralela espontaneamente.
>
> Aposta: se o admin conseguir modelar as entidades dele e o time operar Records dentro
> do contexto do cliente, os workarounds caem. Queremos ver ≥30% de queda em 60 dias
> (baseline = pesquisa de workaround na semana 0).
>
> Sucesso do v1: 5 das 7 orgs do beta ativam em 14 dias (ativar = criar 1 Object + 3
> Attributes + 10 Records + 1 Relationship, com 2 usuários usando). No máximo 2 orgs
> precisam de engenharia pra configurar.
>
> Capabilities: estrutura de Custom Objects (criar/arquivar Object e Attributes),
> Records (CRUD + import), Relationships (1:N e N:N), Lists/Pipelines, e o contexto do
> Contact/Conversation mostrando os Records ligados.
>
> A tela de criação fica em Settings → Dados → Objects, e criar um Object gera
> automaticamente a view "All records" e 4 system attributes (RB-OBJ-001). Conversation
> é System Object: aceita Attributes mas não tem All records nem Pipeline. Sem API
> pública no v1, sem exclusão permanente (só arquivar). Starter fica limitado a 3
> Objects.
>
> Cliente da Acme na call de 12/08: "a gente tem um Trello só pra saber em que etapa
> tá o sinistro de cada segurado, e ninguém do atendimento olha".

## Draft devolvido pelo skill

Entendi como Initiative: problema, hipótese medida, outcomes com cohort e mapa de
capabilities. Tela, RB-OBJ-001 e o detalhe de Conversation foram movidos (lista no
final).

---

# Customização de Objetos
**Owner:** [FALTA: owner] · **Status:** definição

## Problema
O modelo de dados é fixo (Contact, Company, Conversation). Clientes com processo próprio
(sinistro, matrícula, ordem de serviço) levam a operação para planilha ou CRM paralelo e a
Spryx perde o contexto da conversa. Nas calls de discovery, 5 das 7 orgs do beta citaram
planilha paralela espontaneamente.

> "a gente tem um Trello só pra saber em que etapa tá o sinistro de cada segurado, e
> ninguém do atendimento olha" — Acme, call de 12/08 [FALTA: link da call no Attio]

## Hipótese
Se o admin modelar as próprias entidades e o time operar Records no contexto do cliente,
então os workarounds caem, medido por ≥30% de queda em 60 dias (baseline: pesquisa de
workaround na semana 0).

## Outcomes
- 5/7 orgs do beta ativam em 14 dias. Ativar = 1 Object + 3 Attributes + 10 Records +
  1 Relationship, com 2 usuários usando.
- ≤2/7 orgs precisam de engenharia para configurar.

## Mapa de Projects
- [ ] Estrutura de Custom Objects (criar/arquivar Object e Attributes) — owner: [FALTA]
- [ ] Records (CRUD + import) — owner: [FALTA]
- [ ] Relationships (1:N e N:N) — owner: [FALTA]
- [ ] Lists / Pipelines — owner: [FALTA]
- [ ] Contexto de Contact/Conversation com Records ligados — owner: [FALTA]

## Restrições e não-objetivos
- Conversation é System Object: sem CRUD genérico nem Pipeline (detalhe na matriz do
  Project "Estrutura de Custom Objects").
- Sem API pública no v1.
- Sem exclusão permanente; só arquivar.

## Sucesso e guardrails
- Sucesso: os dois outcomes acima batem na janela.
- Guardrail: se ≥3 orgs precisarem de engenharia para configurar, parar e revisar a
  experiência de setup antes de ampliar o beta.

## Rollout
- Beta com as 7 orgs de discovery.
- Teto de entitlement: plano Starter limitado a 3 Custom Objects (ENT-001).

---

**Movido para Project Doc** (não entra na Initiative):
- Tela "Settings → Dados → Objects" → jornada do Project "Estrutura de Custom Objects".
- RB-OBJ-001 (criar Object gera All records + 4 system attributes) → seção Regras do
  mesmo Project.
- Detalhe de Conversation (Attributes sim, All records e Pipeline não) → matriz de
  exceção do mesmo Project.

**Faltas**
- [FALTA: owner] da Initiative e de cada Project do mapa.
- [FALTA: link da call] da Acme no Attio.

Posso gravar no Linear?
  a) criar a Initiative
  b) atualizar <id> em vez de criar
  c) não gravar, só ajustar o draft

## O que observar neste exemplo

- O skill não inventou owner nem link da call; marcou `[FALTA]` e listou no final.
- A frase do cliente entrou literal, com origem, em vez de "clientes reclamam de
  planilha".
- Rollout e teto de entitlement entraram **porque o texto trouxe** (beta de 7 orgs,
  Starter com 3 Objects). Sem isso a seção seria omitida.
- RB-OBJ-001 e a tela foram cortados, mas listados, para o usuário ver que nada se
  perdeu.
- O mapa de Projects tem 5 itens; cada um parece caber em 1–3 semanas. Se "Records
  (CRUD + import)" fosse maior, o skill teria sugerido separar "Import de Records".
