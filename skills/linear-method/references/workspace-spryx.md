# Workspace Spryx no Linear

Dados do workspace que o skill precisa para resolver "qual team, qual project" sem
adivinhar. Preencha os `[FALTA]` abaixo; enquanto estiverem vazios, o skill resolve
nomes em tempo de execução com `list_teams` / `list_projects` e, se houver dois matches,
pergunta.

Mantenha este arquivo curto. Ele muda quando o workspace muda, e uma informação
desatualizada aqui é pior do que nenhuma (o skill vai gravar no lugar errado com
confiança).

## Teams

| Team no Linear | Prefixo de issue | Superfície do produto | Owner padrão |
|---|---|---|---|
| [FALTA] | [FALTA] | Studio (agentes e flows) | [FALTA] |
| [FALTA] | [FALTA] | Live Chat (inbox, roteamento) | [FALTA] |
| [FALTA] | [FALTA] | CRM / Custom Objects / Records | [FALTA] |
| [FALTA] | [FALTA] | Plataforma / infra | [FALTA] |

Regra de resolução: o usuário diz o team → use. Não diz, mas o texto é claramente de uma
superfície → proponha o team da linha correspondente no draft e deixe o usuário
confirmar na pergunta fechada. Texto ambíguo entre duas superfícies → pergunte antes do
draft.

## Initiatives ativas

| Initiative | Owner | Projects filhos conhecidos |
|---|---|---|
| [FALTA] | [FALTA] | [FALTA] |

Quando um Project novo pertence a uma Initiative listada aqui, linke no draft. Se o
usuário citar uma Initiative que não está aqui, use `list_*` para achar; se não existir,
`[FALTA: initiative pai]`, não crie uma Initiative como efeito colateral de criar um
Project.

## Convenções de nome

- Project: `<Superfície> — <Capability>` (ex.: `Studio — Publicar versão de flow`).
  `[CONFIRMAR]`
- Project Doc: mesmo nome do Project. Um Doc por Project.
- Issue de design: `Explorar design de <jornada>`.
- Labels padrão: [FALTA]

## Fontes de fala de cliente

- Attio (CRM): notas e gravações de call. Linke a URL do registro.
- Linear Customer Requests: linke a request.
- [FALTA: outras fontes]
