# Pendências e perguntas em aberto: sdd-piloto (CTL DocAnswer)

Documento único para tudo o que ainda não está esclarecido no projeto. Atualize aqui, e só aqui, ao longo do trabalho.

**Última atualização:** 2026-11-24

## Como usar

- Toda dúvida, premissa não confirmada ou dependência de terceiros entra em **Em aberto**, com dono e com os cards do Jira que ela bloqueia.
- Quando for respondida, mova a linha para **Resolvidas**, com a data e a resposta. Não apague.
- Nos cards do Jira, descreva a pendência em palavras e cite o ID desta tabela (`PEND-NN`) em vez de repetir a explicação.
- Os IDs são `PEND-NN`; os códigos P-numéricos antigos não são mais usados.

## Em aberto

### Cliente e produto (dono: PO com o cliente, salvo indicação)

| ID | Pendência ou pergunta | Dono | Bloqueia | Origem |
|---|---|---|---|---|
| PEND-01 | Para cada critério de sucesso: como se mede e qual o limiar aceito? (inclui o valor de "acerto ≥ X") | PO com o cliente | CTM-14, CTM-17 | levantamento inicial, critérios de sucesso |
| PEND-02 | Lista final de métricas de performance, além das mínimas (tempo de processamento, tempo de resposta e acerto). | PO com o cliente | CTM-28 (e CTM-29, CTM-30) | levantamento inicial |
| PEND-03 | Há outro formato de documento desejado além de PDF, Word, Excel, PowerPoint e Markdown? Há limite de tamanho ou de quantidade de arquivos? | PO com o cliente | CTM-25, CTM-21 a CTM-24 | levantamento inicial |
| PEND-04 | Em que idioma(s) o cliente fará as perguntas e receberá as respostas? Hoje só os documentos estão definidos (português e inglês). | PO com o cliente | CTM-34 | levantamento inicial |
| PEND-05 | Formato do feedback de cada resposta (ex.: certo/errado ou nota). | PO com o cliente | CTM-26, CTM-27 | levantamento inicial |
| PEND-06 | Além da mensagem de informação não encontrada, há outras respostas pré-cadastradas previstas? | PO | CTM-11 | levantamento inicial |
| PEND-07 | Qual o texto da resposta pré-cadastrada de cada guardrail (G-1, G-2, G-3)? | PO | CTM-18, CTM-19, CTM-20 | levantamento inicial |
| PEND-08 | Quais são os demais guardrails, além de G-1 a G-3? | PO e Segurança e Compliance | CTM-18 a CTM-20 | levantamento inicial |
| PEND-09 | Layout esperado dos documentos gerados (Word, PowerPoint, Excel). | PO | CTM-31 (e CTM-32, CTM-33) | cards de geração de documento |
| PEND-10 | Definição de "projeto" e de ano nos documentos de exemplo, para a contagem de projetos por ano. | PO (via CTM-15) | CTM-15, CTM-16 | levantamento inicial |

### Segurança, conformidade e papéis

| ID | Pendência ou pergunta | Dono | Bloqueia | Origem |
|---|---|---|---|---|
| PEND-11 | Quem ocupa o papel de Segurança e Compliance (veto sobre guardrails e permissões dos agentes)? Hoje o papel não tem responsável. | PO | CTM-18 a CTM-20; parecer de Segurança e Compliance sobre a viabilidade | levantamento inicial |
| PEND-12 | Requisitos de conformidade aplicáveis ao projeto: a definir. | Segurança e Compliance | nenhum card direto | levantamento inicial |
| PEND-13 | Quem assina a aceitação final dos critérios de sucesso (sugestão: o PO)? | PO e Tech Lead | fechamento do projeto | levantamento inicial, acúmulo de papéis |
| PEND-14 | O Guilherme concorda com a exceção de projeto que deixa um só desenvolvedor acumulando Dev, Tech Lead, QA e Engenharia de IA/ML? | PO | nenhum card direto | levantamento inicial, acúmulo de papéis |
| PEND-15 | Há alguma exigência de privacidade (LGPD) para o uso final do sistema, já que o desenvolvimento usa só documentos sintéticos? | Segurança e Compliance | nenhum card direto | decisão de 2026-11-24 |

### Dados de avaliação

| ID | Pendência ou pergunta | Dono | Bloqueia | Origem |
|---|---|---|---|---|
| PEND-16 | Quem cria os documentos sintéticos de exemplo e escreve as perguntas, respostas corretas e referências esperadas (5 a 10 por categoria, em português e inglês)? Os documentos devem imitar a estrutura dos reais, senão a avaliação de recuperação e contagem perde valor. | PO e Tech Lead | CTM-14, CTM-15, CTM-16 | decisão de 2026-11-24 |
| PEND-17 | Pendência herdada do processo antigo: se alguém audita o resultado das avaliações ou se o acúmulo de papéis é total. Confirmar se ainda se aplica, já que o processo antigo foi removido. | PO e Tech Lead | nenhum card direto | levantamento inicial, acúmulo de papéis |

### Técnicas

| ID | Pendência ou pergunta | Dono | Bloqueia | Origem |
|---|---|---|---|---|
| PEND-18 | Qual modelo local e qual biblioteca de recuperação respondem dentro de 60 s só em CPU? A GPU continua opcional? | Tech Lead (via CTM-7) | CTM-9 e demais; ADRs 0005 e 0006 | walking skeleton |
| PEND-19 | As metas de latência (60 s para texto, 120 s para documento) são provisórias e precisam ser ajustadas depois de medir o modelo escolhido. | Tech Lead | CTM-35 | levantamento inicial, restrições |
| PEND-20 | O PO confirma que o caso 2 (perguntar sobre um projeto e receber resposta com referência) é o primeiro ponta a ponta? | PO | CTM-2 | levantamento inicial |
| PEND-21 | A interface web usará qual tecnologia? O ADR 0004 fixa Python e FastAPI e deixa a interface a decidir. | Tech Lead | CTM-9 | ADR 0004 |

### Organização do Jira

| ID | Pendência ou pergunta | Dono | Bloqueia | Origem |
|---|---|---|---|---|
| PEND-22 | O tipo de issue "Spike" existe no projeto CTM? Se existir, trocar CTM-7 e CTM-15 para Spike e remover o label `spike`. Não foi possível confirmar pela API. | Tech Lead | CTM-7, CTM-15 | conversa de 2026-11-24 |
| PEND-23 | O CTM-3 ("Épico 2") está vazio e sem nome. Definir o tema e ligar os cards do backlog que não são do esqueleto. | Tech Lead e PO | CTM-14 a CTM-35 | conversa de 2026-11-24 |
| PEND-24 | Os story points estão só no texto das descrições. Preencher o campo de story points do Jira. | Tech Lead | CTM-7 a CTM-35 | conversa de 2026-11-24 |
| PEND-25 | Criar os links de dependência entre as issues, hoje só descritos nas descrições. | Tech Lead | CTM-7 a CTM-35 | conversa de 2026-11-24 |

## Resolvidas

| ID | Pergunta | Resposta | Data |
|---|---|---|---|
| PEND-R01 | Os documentos reais do Lucas serão usados no desenvolvimento e na avaliação? | Não. O Lucas confirmou que não enviará os documentos dele, por serem privados. Usaremos documentos sintéticos de exemplo. | 2026-11-24 |
| PEND-R02 | Os documentos enviados podem conter dados pessoais? (para o desenvolvimento) | Superada: sem documentos reais, não há dados pessoais no desenvolvimento. Ver PEND-15 para o uso final. | 2026-11-24 |
| PEND-R03 | O Lucas libera os documentos reais para o conjunto de avaliação? | Superada pela decisão de usar documentos sintéticos. Ver PEND-16. | 2026-11-24 |

## Histórico de decisões

- **2026-11-24:** documentos de desenvolvimento e avaliação serão sintéticos; o Lucas não enviará os dele (PEND-R01).
- **2026-11-24:** o documento de partida do projeto foi aposentado. Só o problema e o objetivo foram mantidos, na seção Problema e Contexto de `docs/01-story-map.md`, que passa a ser a raiz do fluxo. Casos de uso, fora de escopo, critérios de sucesso e restrições não foram migrados.
- **2026-11-24:** este documento passa a ser o único lugar das pendências; os códigos P-numéricos antigos deixam de ser usados.
