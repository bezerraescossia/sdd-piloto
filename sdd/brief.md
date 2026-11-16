# Brief: CTL DocAnswer

| Campo | Valor |
| --- | --- |
| Versão | 0.3 |
| Templates | v1.1 |
| Data | 2026-11-16 |
| Dono (PO) | Guilherme |
| Cliente / Sponsor | Lucas (cliente e Sponsor) |
| Tech Lead, Engenheiro de IA/ML, QA e Dev | Rafael (acúmulo de papéis: ver P26) |
| Segurança e Compliance | Pergunta em aberto (P21) |
| Status | rascunho |

## 1. Problema e objetivo

<!-- Gate: G0 · Preenche: PO -->

Hoje, para responder a perguntas sobre o conteúdo de um conjunto de documentos, o cliente precisa fazer uma análise manual: acessar repositórios, abrir pastas e documentos e consolidar a informação. Exemplo: para saber "Quantos projetos foram realizados em 2025?", é preciso abrir os documentos e contar os projetos à mão. Outro exemplo: para saber quais riscos um projeto levantou, é preciso localizar e ler os documentos desse projeto.

Para quem: o cliente, que é leigo em tecnologia e precisa de uma solução simples e direta. O desenvolvedor também é usuário: ele baixa as métricas de performance da solução.

**Objetivo:** permitir que o cliente envie documentos e obtenha, de forma simples, respostas às suas perguntas baseadas apenas nesses documentos e acompanhadas da referência de origem, em texto ou como documento gerado (Word, PowerPoint ou Excel), usando um modelo de IA executado localmente no hardware do usuário.

## 2. Usuários e casos de uso prioritários

<!-- Gate: G0 e G1 (alimenta o golden dataset) · Preenche: PO -->

| # | Usuário | Situação | Entrada de exemplo | Saída esperada |
| --- | --- | --- | --- | --- |
| 1 | Cliente (leigo em tecnologia) | Quer saber quantos projetos foram feitos em um ano, sem contar à mão | Envia a pasta com os documentos dos projetos e pergunta: "me diga quantos projetos foram feitos no ano de 2025" | Resposta em texto (linguagem natural) com a quantidade de projetos feitos em 2025, baseada apenas nos documentos enviados, com as referências usadas (ver regra de referência abaixo) |
| 2 | Cliente (leigo em tecnologia) | Quer detalhes sobre um projeto específico | "Quais foram os riscos levantados pelo projeto XYZ?" | Resposta em texto com os riscos do projeto XYZ que constam nos documentos enviados, com as referências usadas |
| 3 | Cliente (leigo em tecnologia) | Faz uma pergunta cuja resposta não está nos documentos enviados | Pergunta sobre informação ausente dos documentos | Resposta pré-cadastrada: "Desculpe, não consegui encontrar as informações para responder sua pergunta." O texto das respostas pré-cadastradas deve ser simples de editar, pois vai mudar durante o desenvolvimento |
| 4 | Cliente (leigo em tecnologia) | Quer o resultado como documento em vez de texto | "Gere um documento word a partir do que você me respondeu" ou "Apresente a resposta em powerpoint" | Documento no formato pedido (Word, PowerPoint ou Excel) com o conteúdo da resposta, baseado apenas nos documentos enviados |
| 5 | Desenvolvedor | Quer comparar a performance desta solução (modelo local) com soluções que usam modelos em nuvem. A comparação é feita por ele, fora do sistema | Acessa os dados de performance direto pela interface, não pelo chat, e escolhe o formato do download (CSV ou JSON). Os dados ficam visíveis para qualquer usuário: não há autenticação, pois a aplicação roda apenas localmente | Arquivo CSV ou JSON com, no mínimo: tempo de processamento, tempo de resposta e acerto (a partir do feedback dado a cada resposta). A lista final de métricas ainda será acordada com o cliente |

**Regra de referência (casos 1, 2 e 4):** toda resposta vem acompanhada da referência usada para respondê-la.

- Documento (PDF, Word): nome do arquivo e página, quando possível.
- Planilha: apenas o nome da planilha.
- Apresentação: nome do arquivo e página (slide).

**Feedback:** o usuário pode dar feedback sobre cada resposta recebida. Esse feedback alimenta a métrica de acerto. O formato do feedback será definido com o cliente (P22).

**Guardrails:** a solução deve ter guardrails. No mínimo, deve tratar as três categorias abaixo. Os demais guardrails serão definidos depois (P27). Em cada guardrail, o sistema responde com uma resposta pré-cadastrada e simples de editar, como no caso 3. O texto de cada resposta está em aberto (P29).

| # | Categoria | Entrada de exemplo | Saída esperada |
| --- | --- | --- | --- |
| G-1 | Pergunta imprópria | Pergunta contendo palavrão | Resposta pré-cadastrada e editável; texto em aberto (P29) |
| G-2 | Pergunta genérica, não ligada aos documentos | "Quem é o presidente do Brasil?" | Resposta pré-cadastrada e editável; texto em aberto (P29) |
| G-3 | Pergunta sobre a própria IA | "Qual modelo você usa?", "Quem te criou?" | Resposta pré-cadastrada e editável; texto em aberto (P29) |

## 3. Critérios de sucesso

<!-- Gate: G0 · Preenche: PO com o cliente · QA confirma os critérios do sistema; Engenheiro de IA/ML confirma os critérios de modelo -->

Nenhum critério tem forma de medir nem limiar definidos ainda (P9).

| Critério | Como se mede | Limiar | Quem valida |
| --- | --- | --- | --- |
| Respostas baseadas apenas nos documentos enviados | Pergunta em aberto (P9) | Pergunta em aberto (P9) | Engenheiro de IA/ML |
| Respostas corretas quando a informação está nos documentos (ex.: contagem de projetos de 2025, riscos do projeto XYZ) | Pergunta em aberto (P9) | Pergunta em aberto (P9) | Engenheiro de IA/ML |
| Resposta pré-cadastrada quando a informação não está nos documentos | Pergunta em aberto (P9) | Pergunta em aberto (P9) | Engenheiro de IA/ML |
| Guardrails G-1, G-2 e G-3 acionados nas perguntas impróprias, genéricas e sobre a IA | Pergunta em aberto (P9) | Pergunta em aberto (P9) | Engenheiro de IA/ML |
| Toda resposta acompanhada da referência, conforme a regra da seção 2 | Pergunta em aberto (P9) | Pergunta em aberto (P9) | QA |
| Nenhuma chamada a modelo hospedado em nuvem | Pergunta em aberto (P9) | Pergunta em aberto (P9) | QA |
| Geração de documentos Word, PowerPoint e Excel a partir da resposta | Pergunta em aberto (P9) | Pergunta em aberto (P9) | QA |
| Exportação das métricas em CSV e em JSON | Pergunta em aberto (P9) | Pergunta em aberto (P9) | QA |
| Uso simples e direto por um cliente leigo em tecnologia | Pergunta em aberto (P9) | Pergunta em aberto (P9) | PO com o cliente |

## 4. Fora de escopo

<!-- Gate: G0 · Preenche: PO -->

- Uso de qualquer modelo de IA hospedado em nuvem.
- Respostas baseadas em informação que não esteja nos documentos enviados.
- Comparação automática com soluções em nuvem. O sistema só exporta as métricas; a comparação é feita pelo desenvolvedor.
- Processamento de imagens e vídeos.
- Perguntas por voz.
- Respostas da IA por voz.
- Integração com WhatsApp, Teams e Outlook.
- Autenticação. A aplicação roda apenas localmente, e as métricas de performance ficam visíveis para qualquer usuário.

## 5. Dados e data contracts

<!-- Gate: G0 · Preenche: PO (lista), Data Owner (contratos) -->

| Fonte | Data Owner | Contrato assinado? | Dados pessoais? | Link para o contrato |
| --- | --- | --- | --- | --- |
| Documentos enviados pelo cliente (pastas e arquivos; ex.: documentos de projetos) | Lucas (cliente) | não | Pergunta em aberto (P12) | Não existe ainda (`sdd/data-contracts/DC-001-<fonte>.md`) |

Formatos aceitos no envio: PDF, Word, Excel, PowerPoint e Markdown. A validar com o cliente se há outro formato desejado (P13).

Idiomas dos documentos: português e inglês. Idioma das perguntas e das respostas: a validar com o cliente (P19).

Há dados para montar o golden dataset? **Não.** Não existe hoje conjunto de documentos com perguntas e respostas corretas (P24).

**Insumo opcional:** nenhuma avaliação de prontidão dos dados foi informada.

## 6. Restrições e riscos

<!-- Gate: G0 · Preenche: PO · Segurança e Compliance sinaliza o que é seu -->

| Tema | Restrição ou risco | Responsável |
| --- | --- | --- |
| Privacidade e LGPD | Pergunta em aberto (P12) | Segurança e Compliance |
| Conformidade | A definir (P15) | Segurança e Compliance |
| Guardrails | A solução deve ter guardrails; o mínimo está na seção 2 (G-1 a G-3). Guardrails são item de veto de Segurança e Compliance, papel ainda sem nome (P21) | Segurança e Compliance |
| Custo esperado | Pergunta em aberto (P16) | Tech Lead |
| Latência esperada | Pergunta em aberto (P16) | Tech Lead |
| Técnico | O modelo de IA deve ser executado localmente, no hardware do usuário; nenhum modelo hospedado em nuvem pode ser usado. A solução é uma aplicação web local. Especificação mínima do hardware em aberto (P17) | Tech Lead |
| Técnico (avaliação) | Não existe golden dataset. Sem ele, os critérios de modelo não podem ser medidos (P24) | Engenheiro de IA/ML |
| Cliente (disponibilidade, escopo) | Cliente leigo em tecnologia: a interface precisa ser simples e direta. Pontos ainda a validar com o cliente: métricas (P7), formatos (P13), idioma (P19) | PO |
| Papéis | Rafael acumula Dev, Tech Lead, QA e Engenheiro de IA/ML, o que conflita com a regra "quem implementa nunca é quem mede nem quem aceita" (P26). Segurança e Compliance ainda sem nome (P21) | PO |

## 7. Parecer de viabilidade

<!-- Gate: G0 · Preenche: Tech Lead, QA, Engenheiro de IA/ML, Segurança e Compliance -->

- **Tech Lead:** pendente.
- **QA:** pendente.
- **Engenheiro de IA/ML:** pendente.
- **Segurança e Compliance:** pendente.

## 8. Premissas e perguntas em aberto

<!-- Gate: G0 · Preenche: qualquer papel -->

| # | Premissa ou pergunta | Dono | Prazo |
| --- | --- | --- | --- |
| P7 | Lista final de métricas de performance, além das mínimas (tempo de processamento, tempo de resposta, acerto): acordar com o cliente. | PO com o cliente | |
| P9 | Para cada critério de sucesso: como se mede e qual o limiar aceito? | PO com o cliente | |
| P12 | Os documentos enviados podem conter dados pessoais? | Segurança e Compliance | |
| P13 | Há outro formato de documento desejado além de PDF, Word, Excel, PowerPoint e Markdown? Há limite de tamanho ou de quantidade? | PO com o cliente | |
| P15 | Requisitos de conformidade aplicáveis: a definir. | Segurança e Compliance | |
| P16 | Quais são as expectativas de custo e de tempo de resposta? | Tech Lead | |
| P17 | Qual é o hardware disponível no computador do usuário (CPU, GPU, memória)? Qual a configuração mínima a suportar? | Tech Lead | |
| P19 | Em que idioma(s) o cliente fará as perguntas e receberá as respostas? | PO com o cliente | |
| P21 | Quem ocupa o papel de Segurança e Compliance (veto sobre guardrails, dados pessoais e permissões dos agentes)? | PO | |
| P22 | Formato do feedback de cada resposta (ex.: certo/errado, nota): a definir com o cliente. | PO com o cliente | |
| P24 | O golden dataset não existe. Quem o monta, com quais documentos, e quem rotula as respostas corretas? | PO, Engenheiro de IA/ML | |
| P25 | Além da mensagem de informação não encontrada, há outras respostas pré-cadastradas previstas? | PO | |
| P26 | Rafael acumula Dev, Tech Lead, QA e Engenheiro de IA/ML. A metodologia exige que quem implementa não seja quem mede nem quem aceita, e que o Tech Lead audite o evidence pack do Dev. Quem mede e audita, ou como essa regra é adaptada neste projeto? Mudança na metodologia exige commit `framework:` aprovado pelo Tech Lead | PO, Tech Lead | |
| P27 | Quais são os demais guardrails, além de G-1 a G-3? | PO, Segurança e Compliance | |
| P29 | Qual é o texto da resposta pré-cadastrada de cada guardrail (G-1, G-2, G-3)? | PO | |

### Respostas registradas

Respondidas pelo PO (Guilherme) em 2026-11-16.

| # | Pergunta | Resposta |
| --- | --- | --- |
| P1 | Nome do projeto | CTL DocAnswer |
| P2 | PO, cliente e Sponsor | PO: Guilherme. Desenvolvedor: Rafael. Cliente: Lucas. Não há Sponsor (consequências em P20) |
| P3 | Perfil do usuário | Cliente leigo em tecnologia; a solução deve ser simples e direta. O download das métricas é necessidade do desenvolvedor |
| P4 | Resposta quando a informação não está nos documentos | Resposta pré-cadastrada: "Desculpe, não consegui encontrar as informações para responder sua pergunta." Respostas pré-cadastradas devem ser simples de editar |
| P5 | Exemplos de pedido de documento | "Gere um documento word a partir do que você me respondeu"; "Apresente a resposta em powerpoint" |
| P6 | Referência nas respostas | Toda resposta traz a referência: nome do arquivo e página quando possível; planilha, apenas a planilha; apresentação, a página |
| P7 | Métricas e formato | Mínimas: tempo de processamento, tempo de resposta e acerto (feedback do usuário por resposta); lista final a acordar com o cliente. Exportação em CSV ou JSON, à escolha. A comparação com soluções em nuvem é feita pelo usuário, não automaticamente |
| P8 | Outros casos de uso | Detalhes de um projeto específico, ex.: "Quais foram os riscos levantados pelo projeto XYZ?" |
| P10 | Fora de escopo | Processamento de imagens e vídeos, perguntas por voz, integração com WhatsApp, Teams e Outlook, autenticação |
| P11 | Data Owner | O próprio cliente (Lucas) |
| P13 | Formatos aceitos | PDF, Word, Excel, PowerPoint e Markdown; outros formatos a validar com o cliente |
| P14 | Golden dataset | Não existe (desdobramento em P24) |
| P15 | Conformidade | A definir |
| P18 | Forma de acesso | Aplicação web local |
| P19 | Idiomas | Documentos em português e inglês; idioma de perguntas e respostas a validar com o cliente |
| P20 | Sponsor | Lucas é o Sponsor, além de cliente |
| P21 (parcial) | Papéis | Tech Lead, Engenheiro de IA/ML e QA: Rafael. Segurança e Compliance segue em aberto |
| P22 | Formato do feedback | A definir com o cliente |
| P23 | Tempo de processamento | Sim: é o tempo de processamento dos documentos enviados |
| P4 (complemento) | Guardrails | A solução deve ter guardrails, no mínimo para perguntas impróprias (ex.: com palavrão), genéricas (ex.: "quem é o presidente do Brasil") e sobre a IA (ex.: "qual modelo você usa", "quem te criou"). Os demais serão definidos depois |
| Correção do caso 5 | Acesso às métricas | O desenvolvedor encontra os dados de performance direto na interface; não os pede pelo chat |
| Complemento P10 | Fora de escopo | Respostas da IA por voz |
| P30 | Visibilidade das métricas | Os dados de performance ficam visíveis na interface para qualquer usuário. Não há autenticação porque a aplicação roda apenas localmente |
| P28 | Resposta dos guardrails | Resposta pré-cadastrada e editável em cada guardrail, como no caso 3 |

## 9. Aprovação (G0)

<!-- Gate: G0 · O cliente e o Sponsor validam; os demais assinam o que é seu -->

| Papel | Nome | Aprova | Data |
| --- | --- | --- | --- |
| Cliente | Lucas | critérios de sucesso | |
| Sponsor | Lucas | escopo e orçamento | |
| PO | Guilherme | brief | |
| Tech Lead | Rafael | viabilidade | |
| QA | Rafael | mensurabilidade dos critérios do sistema | |
| Engenheiro de IA/ML | Rafael | mensurabilidade dos critérios de modelo | |
| Data Owner | Lucas | data contracts | |
