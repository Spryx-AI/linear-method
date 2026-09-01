# Exemplos — initiative

## Bom (cabe numa tela)

# Customização de Objetos
Status: revisão conjunta

## Problema
Modelo de dados rígido. Processo vai para planilha.

## Hipótese
Se admin modelar entidades e o time operar Records no contexto do cliente, então workarounds caem ≥30% em 60 dias (baseline vs medição).

## Outcomes
- 5/7 orgs ativam em 14 dias (Object + 3 Attributes + 10 Records + 1 Relationship + 2 usuários).
- ≤2 orgs precisam de Engenharia para configurar.

## Mapa de Projects
- [ ] Estrutura de Custom Objects
- [ ] Records
- [ ] Relationships
- [ ] Lists/Pipelines
- [ ] Contexto Contact/Conversation

## Restrições e não-objetivos
Conversation não tem CRUD genérico nem Pipeline. Sem API pública no v1. Sem exclusão permanente.

## Ruim
Parágrafo de tela “Settings → Dados → Objects”, tabela de tipos de Attribute, RB-ATT-010 no corpo.
