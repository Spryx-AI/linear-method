# Exemplos — project doc

## Description (boa)

Admin cria e arquiva Custom Objects e Attributes. Conversation é System Object: Attributes e Relationships sim, All records e Pipeline não. Records, Relationships e Pipelines são projects irmãos. Spec no document deste project.

## Matriz (obrigatória se houver exceção)

| Capacidade | Conversation | Contrato |
| --- | --- | --- |
| Custom Attributes | Sim | Nativos protegidos |
| All records / CRUD genérico | Não | Inbox |
| Pipelines | Não | Processo durável é Custom Object |

Essa tabela prevalece sobre o resto do doc.

## Índice (bom)

| id | título | proto |
| --- | --- | --- |
| OBJ-01 | Listar System vs Custom Objects | Paper 7-0 |
| OBJ-02 | Criar Object gera só Object + All records + 4 system attrs | Paper 4-0 |
| DES-01 | Campos visíveis na lista de Objects | [FALTA] |

## Ruim no doc
- User stories em prosa
- Métrica “5/7 orgs”
- RB-ATT-010 copiado duas vezes (catálogo e jornada)
