# Exemplo: review com veredito "Não" (CRM — Import de contatos)

Domínio de CRM, fora de Custom Objects. Mostra um Doc que parece completo mas tem três
bloqueadores clássicos: métrica de Initiative dentro do Doc, design pendente virando
critério de aceite, e regra copiada em dois lugares.

## Texto colado pelo usuário

> isso tá pronto pra ir pra eng?
>
> # CRM — Import de contatos via CSV
> Owner: Júlia
>
> ## Contexto
> Clientes migrando de outra ferramenta precisam trazer a base. Meta: 80% das orgs do
> beta importam ≥100 contatos na primeira semana.
>
> ## Escopo
> IN: upload CSV até 10 MB, mapeamento de colunas para atributos de Contact,
> deduplicação por e-mail, relatório de erros por linha.
> OUT: import de Company (project separado), import agendado/recorrente.
>
> ## Regras
> | ID | Regra |
> |---|---|
> | RB-IMP-001 | Arquivo acima de 10 MB é rejeitado antes do upload terminar. |
> | RB-IMP-002 | Linha com e-mail já existente atualiza o Contact em vez de duplicar. |
> | RB-IMP-003 | Linha inválida não impede o import das demais; vai para o relatório de erros. |
>
> ## Jornadas
> | id | título | proto |
> |---|---|---|
> | IMP-01 | Subir CSV e mapear colunas | Paper 5-0 |
> | IMP-02 | Ver relatório de erros por linha e baixar CSV só com as linhas com erro | a definir com Design |
> | IMP-03 | Linha com e-mail existente atualiza o Contact em vez de duplicar (RB-IMP-002) | — |
>
> Critérios de aceite da IMP-02: a tela de erros deve ser clara e fácil de entender; o
> download deve funcionar.

## Resposta devolvida pelo skill

## Veredito: Não
O Doc tem estrutura certa e regras com id, mas três pontos vão gerar retrabalho se forem
para engenharia assim: uma métrica de Initiative no Doc, uma jornada sem desenho com
critério de aceite subjetivo, e uma regra duplicada entre Regras e Jornadas.

## Bloqueadores
- **Métrica de Initiative no Doc.** "80% das orgs do beta importam ≥100 contatos na
  primeira semana" (Contexto) é outcome; pertence à Initiative pai. No Doc vira um
  número que engenharia não controla e QA não verifica. → Mover para a Initiative
  ([FALTA: qual initiative]); no Contexto deixar só o por quê.
- **Design pendente como critério de aceite.** IMP-02 tem proto "a definir com Design" e
  critério "tela clara e fácil de entender". Não dá para implementar nem verificar. →
  Criar `DES-01 · Explorar design do relatório de erros` no índice; IMP-02 fica sem
  issue de engenharia até o proto existir; remover o critério subjetivo.
- **Regra copiada na jornada.** IMP-03 repete o texto de RB-IMP-002 no título. Quando a
  regra mudar, o índice fica velho. → Título observável ("Reimportar CSV com e-mails
  existentes não cria Contact duplicado") e a coluna proto com "—" (comportamento sem
  tela), contrato por id.

## Ajustes menores
- Falta o **Resumo** (por quê / o quê / como) no topo; o Contexto faz parte do papel, mas
  não diz o "como" em alto nível.
- Falta a **Initiative pai** no cabeçalho.
- IMP-01 cobre duas coisas (upload e mapeamento). Cabe numa issue, mas o título deveria
  dizer a restrição observável: "Subir CSV até 10 MB e mapear colunas para atributos de
  Contact".
- OUT menciona "import de Company (project separado)" sem nome do Project. Se já existe,
  nomeie; se não, `[FALTA: project irmão]`.

## Patch sugerido (não gravado)
**Alvo:** Project Doc "CRM — Import de contatos via CSV"

- Contexto: remover a frase "Meta: 80% das orgs…"; adicionar linha "Outcome na
  Initiative [FALTA: nome]".
- Índice: substituir a linha IMP-02 por
  `IMP-02 | Ver relatório de erros por linha e baixar CSV só com erros | [FALTA: proto] — depende de DES-01`
  e adicionar `DES-01 | Explorar design do relatório de erros | —`.
- Índice: renomear IMP-03 para "Reimportar CSV com e-mails existentes não cria Contact
  duplicado", proto "—".
- Remover o parágrafo "Critérios de aceite da IMP-02".
- Adicionar seção Resumo no topo com o por quê / o quê / como em ≤10 linhas.

Quer que eu aplique o patch?
  a) atualizar o Doc com o patch
  b) não gravar, só o veredito

## O que observar neste exemplo

- O veredito veio primeiro, com motivo em três linhas, para quem só lê o topo.
- Cada bloqueador cita o trecho ou o id e diz **para onde** a informação vai, não só
  que está errada.
- O skill não reescreveu o Doc; propôs um patch localizado e perguntou.
- "Ajustes menores" separa o que não impede a engenharia de começar.
- O skill não inventou o nome da Initiative nem do Project irmão: `[FALTA]`.
