# Exemplo: Project + Project Doc (Live Chat — roteamento por fila)

Domínio diferente de Custom Objects de propósito: mostra que a estrutura do Doc não
depende de existir matriz de exceção ou catálogo, e mostra o teste de escopo cortando um
pedaço (relatórios) para outro Project.

## Texto colado pelo usuário

> cria o project disso no linear, team Live Chat, initiative "Atendimento híbrido"
>
> ## Roteamento por fila
>
> Owner: Marina.
>
> Hoje toda conversa nova cai numa fila única e o supervisor distribui na mão. Queremos
> que o admin crie filas (ex.: Financeiro, Suporte N1, Vendas) e defina regras de
> entrada: por canal (WhatsApp, webchat, e-mail), por tag da conversa, por horário. A
> conversa entra na primeira fila cuja regra bate, na ordem que o admin definiu. Se
> nenhuma bate, cai na fila "Geral", que não pode ser apagada.
>
> Dentro da fila, atribuição é round-robin entre agentes online com capacidade
> (capacidade = máx de conversas simultâneas por agente, default 5). Agente offline não
> recebe. Se ninguém tem capacidade, a conversa fica esperando na fila e o supervisor vê
> o tempo de espera.
>
> Regras já numeradas no Notion: RB-CHT-010 (primeira fila que bate), RB-CHT-011 (Geral
> é fallback e não deletável), RB-CHT-020 (round-robin só entre online com capacidade),
> RB-CHT-021 (capacidade default 5, configurável por agente).
>
> Fora: transbordo pra agente de IA (isso é outro project, "Agente de IA no atendimento"),
> SLA por fila (depois).
>
> Também queremos um relatório de tempo médio de espera por fila e por agente, com filtro
> de período e export CSV. E um dashboard em tempo real de filas.
>
> Protos no Paper: 2-1 (criar fila e regras), 2-2 (ordem das filas). Tela de capacidade
> por agente ainda não tem desenho. Dashboard e relatório sem desenho.
>
> Stories:
> 1. Como admin, quero criar filas com regras de entrada.
> 2. Como admin, quero ordenar as filas.
> 3. Como admin, quero definir capacidade por agente.
> 4. Como agente, quero receber conversas automaticamente quando tenho capacidade.
> 5. Como supervisor, quero ver o tempo de espera das conversas na fila.
> 6. Como supervisor, quero um relatório de espera por fila/agente.

## Draft devolvido pelo skill

Entendi como Project + Project Doc no team Live Chat, sob a Initiative "Atendimento
híbrido". Antes do Doc, um corte de escopo: relatório histórico + export CSV + dashboard
em tempo real são uma capability separada (dados agregados, período, export), com
proto zero. Deixei fora deste Project e proponho um Project irmão; a story 6 vai para
lá. O que sobra (filas, regras, round-robin, espera) cabe em 2–3 semanas para uma dupla.

---

**Team:** Live Chat · **Initiative:** Atendimento híbrido · **Ação:** create

### Project description

Admin cria filas de atendimento com regras de entrada por canal, tag e horário, e ordena
as filas; a conversa entra na primeira fila cuja regra bate, ou em "Geral". Dentro da
fila, a atribuição é round-robin entre agentes online com capacidade. Supervisor vê o
tempo de espera das conversas na fila. Transbordo para agente de IA, SLA por fila e
relatórios/dashboard de espera são projects separados. Spec completa no Document deste
project.

### Document

# Live Chat — Roteamento por fila
**Owner:** Marina · **Initiative:** Atendimento híbrido

## Resumo
**Por quê.** Toda conversa nova cai numa fila única e o supervisor distribui na mão; isso
não escala e atrasa o primeiro atendimento.
**O quê.** Filas configuráveis pelo admin com regras de entrada ordenadas, fallback
"Geral", e atribuição automática round-robin respeitando capacidade do agente.
**Como.** Avaliação das regras na chegada da conversa, na ordem definida; fila mantém
lista de espera visível ao supervisor; atribuição roda quando um agente online ganha
capacidade.

## Escopo
**IN**
- Criar, editar e arquivar filas.
- Regras de entrada por canal (WhatsApp, webchat, e-mail), por tag da conversa e por
  horário; ordem das filas definida pelo admin.
- Fila "Geral" como fallback, não deletável.
- Capacidade por agente (máx. de conversas simultâneas), default 5.
- Round-robin entre agentes online com capacidade; conversa espera na fila se ninguém
  tem.
- Supervisor vê tempo de espera de cada conversa na fila.

**OUT**
- Transbordo para agente de IA → project "Agente de IA no atendimento".
- SLA por fila → depois, sem project ainda.
- Relatório histórico de espera (por fila/agente, período, export CSV) e dashboard em
  tempo real → project irmão proposto "Live Chat — Relatórios de fila" [FALTA: confirmar
  corte].

## Decisões
| Decisão | Alternativa descartada | Motivo |
|---|---|---|
| Primeira fila que bate, na ordem do admin | Pontuação/peso por regra | Simples de explicar e prever; o texto define assim |
| Round-robin | Menos ocupado primeiro | O texto define round-robin; "menos ocupado" fica para depois se houver pedido |
| Fila Geral não deletável | Permitir apagar com aviso | Garante que toda conversa tem destino |

## Regras
| ID | Regra |
|---|---|
| RB-CHT-010 | Conversa nova entra na primeira fila, na ordem definida pelo admin, cuja regra de entrada bate. |
| RB-CHT-011 | Se nenhuma regra bate, a conversa entra na fila "Geral"; "Geral" não pode ser apagada. |
| RB-CHT-020 | Atribuição dentro da fila é round-robin apenas entre agentes online com capacidade disponível. |
| RB-CHT-021 | Capacidade é o máximo de conversas simultâneas por agente; default 5, configurável por agente. |
| RB-CHT-022 | Se nenhum agente tem capacidade, a conversa permanece na fila e o tempo de espera fica visível ao supervisor. |

RB-CHT-022 foi atribuída por mim: o texto descreve o comportamento sem id. Renumere se
já existir no Notion.

## Índice de jornadas
| id | título | proto |
|---|---|---|
| CHT-01 | Criar fila com regras de entrada por canal, tag e horário | Paper 2-1 |
| CHT-02 | Ordenar filas e ver qual regra bateu numa conversa | Paper 2-2 |
| CHT-03 | Definir capacidade por agente (default 5) | [FALTA: proto] |
| CHT-04 | Conversa entra na primeira fila que bate ou em Geral | — (sem tela; comportamento) |
| CHT-05 | Round-robin atribui só a agentes online com capacidade | — (sem tela; comportamento) |
| CHT-06 | Supervisor vê tempo de espera das conversas na fila | [FALTA: proto] |
| DES-01 | Explorar design da tela de capacidade por agente | — |
| DES-02 | Explorar design da visão de espera do supervisor | — |

Story 6 (relatório) → índice do project irmão "Relatórios de fila".

---

**Faltas**
- [FALTA: confirmar corte] de relatórios/dashboard para project separado.
- [FALTA: proto] para CHT-03 e CHT-06 (cobertos por DES-01 e DES-02).

Posso gravar no Linear?
  a) criar Project + Doc (só Roteamento; Relatórios fica para depois)
  b) criar só o Project
  c) atualizar <id> em vez de criar
  d) não gravar, só ajustar o draft

## O que observar neste exemplo

- Não há matriz de exceção nem catálogo: as seções foram omitidas, não preenchidas
  com "N/A".
- O teste de escopo cortou relatórios/dashboard **antes** de escrever o Doc e pediu
  confirmação em vez de decidir sozinho.
- RB-CHT-010/011/020/021 preservadas do Notion; RB-CHT-022 criada e sinalizada.
- Stories viraram linhas do índice; duas viraram DES porque não têm desenho.
- CHT-04 e CHT-05 são comportamento sem tela: proto "—" com explicação, não `[FALTA]`.
- Os irmãos foram para OUT com o nome do Project, para que ninguém implemente
  transbordo de IA aqui.
