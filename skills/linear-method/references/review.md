# Review de prontidão

Leia quando o usuário perguntar "tá pronto?", "falta o quê?", "pode ir pra eng?", ou
pedir para auditar uma Initiative, um Project Doc ou um lote de issues (colados ou por
id/link do Linear).

O review **aponta buracos, não reescreve**. Reescrever é trabalho dos outros artefatos;
se o usuário quiser, ele pede depois. Um review que devolve a spec inteira reescrita
esconde o que estava errado e tira do autor a chance de aprender o padrão.

## Como ler o artefato

Primeiro identifique o tipo (Initiative, Project Doc, Issues, ou um conjunto deles). Se
o artefato está no Linear, use `get_*` para carregar o conteúdo atual; não avalie de
memória. Depois passe pela checklist do tipo. Não precisa marcar todos os itens: marque
os que falham e os que estão ausentes de forma relevante.

### Initiative

- Owner nomeado.
- Problema diz quem sofre e o que custa.
- Hipótese no formato "se X, então Y, medido por Z".
- Todo outcome tem denominador (cohort concreto) e janela.
- Mapa de Projects é checklist de capabilities, cada uma cabível em 1–3 semanas.
- Nada de tela, slug, RB, catálogo. Exceção de domínio em uma linha, não em matriz.
- Rollout/entitlement só se veio do texto.

### Project Doc

- Owner nomeado; Initiative pai indicada se existe.
- Resumo por quê / o quê / como em ≤10 linhas no topo.
- IN e OUT explícitos; OUT lista os irmãos.
- Exceção de domínio está em matriz (não em prosa) e a matriz não contradiz o resto.
- Toda regra tem id; nenhum id repetido; ids do texto de origem preservados.
- Índice de jornadas com proto ou `[FALTA: proto]` em cada linha.
- Design pendente aparece como DES-*, nunca como critério de aceite.
- Nada de métrica de beta, cohort, pricing, teto de entitlement.
- Cabe em 1–3 semanas; se não, há proposta de corte.

### Issues

- Cada issue é um comportamento observável (não feature, não story, não capítulo).
- Título tem verbo + objeto + restrição observável.
- Contrato por id + link do Doc; nenhuma regra ou catálogo copiado.
- Nenhum critério de aceite subjetivo.
- Project alvo único e correto.
- DES separado das issues de engenharia; nenhuma issue de eng para jornada sem proto.
- Sem título duplicado no Project.
- Milestones/relations só onde há fase ou bloqueio real.

### Cruzado (quando há mais de um artefato)

- A mesma informação não vive em dois lugares (regra na Initiative e no Doc; catálogo no
  Doc e na issue).
- Feature irmã não está especificada no Project errado.
- Entitlement: a regra ENT-* tem id no Doc e o valor/decisão está na Initiative, não o
  contrário.
- Instrumentação/telemetria não coleta PII sem dizer como anonimiza.

## Veredito

Um de três. Escolha o mais severo que se aplica:

- **Não** — há pelo menos um bloqueador (algo que, se for para engenharia assim, vai
  gerar retrabalho ou implementação errada).
- **Pronto para review conjunta** — sem bloqueador, mas há `[FALTA]` que precisa de
  decisão de alguém (owner, cohort, proto). Dá para sentar PM + eng + design e fechar.
- **Pronto para build** — sem bloqueador e sem `[FALTA]` que impeça começar.

## Formato

```md
## Veredito: <Não | Pronto para review conjunta | Pronto para build>
<1–3 linhas de motivo>

## Bloqueadores
- <o que está errado> → <onde deveria estar / o que falta> (cite o trecho ou o id)

## Ajustes menores
- <…>

## Patch sugerido (não gravado)
**Alvo:** <id ou título do artefato>
<diff em prosa ou markdown, curto>

Quer que eu aplique o patch?
  a) atualizar <id> com o patch
  b) não gravar, só o veredito
```

Cite o trecho ou o id ao apontar um problema ("RB-ATT-010 aparece no catálogo e na
jornada OBJ-03"). Apontar sem localizar obriga o autor a procurar, e ele vai discordar
do que não encontrar.

## Gravação

Por padrão, review não grava nada. Se o usuário escolher aplicar o patch, siga o
protocolo do SKILL.md: update por id, só o trecho do patch, recibo com URL. Não aproveite
o update para "melhorar" outras partes do artefato.

Veja o exemplo completo em `examples/review-nao-pronto.md`.
