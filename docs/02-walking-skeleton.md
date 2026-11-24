# Walking skeleton: sdd-piloto (CTL DocAnswer)

> Proposta do Tech Lead, a confirmar com o PO (Guilherme). Baseada em `docs/01-story-map.md`.

## Caminho escolhido

**Perguntar sobre um projeto e receber resposta em texto com referência, usando LLM local em CPU (caso de uso 2).**

1. Cliente envia 3–5 documentos PDF pela interface web local.
2. O sistema extrai o texto por página e indexa.
3. Cliente pergunta, por exemplo, "Quais foram os riscos levantados pelo projeto XYZ?".
4. O sistema recupera os trechos relevantes e o LLM local gera a resposta usando só esses trechos.
5. A interface mostra a resposta com a referência (nome do arquivo e página).
6. Se a informação não está nos documentos, mostra a resposta pré-cadastrada ("Desculpe, não consegui encontrar as informações para responder sua pergunta.").
7. O tempo de resposta é medido e registrado.

## Componentes atravessados e riscos cobertos

| Componente | Risco que o esqueleto expõe |
|---|---|
| LLM local (CPU) | Latência real vs. meta de 60 s; qualidade da resposta só em CPU |
| Recuperação e indexação | Se os trechos certos são encontrados em documentos sintéticos de exemplo |
| Ingestão e extração (PDF) | Extração fiel com número de página |
| Referências/citações | Referência vir do dado e não do modelo |
| Resposta pré-cadastrada (caso 3) | Se o sistema responde só com base nos documentos |
| Interface web local | Fluxo mínimo de upload, pergunta e resposta |
| Métricas (só tempo de resposta) | Base para medir a latência durante todo o projeto |

## Dentro do escopo

- Upload de PDF, indexação, uma pergunta por vez, resposta em texto com referência arquivo + página.
- Mensagem pré-cadastrada para informação ausente, lida de um arquivo de configuração editável.
- Registro do tempo de resposta de cada pergunta.
- Execução 100% local, sem chamada a modelo em nuvem.

## Fora do escopo (adiado de propósito)

- Word, Excel, PowerPoint e Markdown (só PDF por ora).
- Perguntas de contagem agregada (caso 1), por serem mais difíceis e dependerem de mais documentos.
- Guardrails G-1 a G-3.
- Feedback por resposta e métrica de acerto.
- Geração de documentos (Word, PowerPoint, Excel).
- Exportação CSV/JSON e tela de métricas.
- Estilo da interface, tratamento de muitos arquivos e otimizações de performance.
- Autenticação (fora de escopo do projeto).

## Prova de vida

No ambiente de desenvolvimento, o PO envia de 3 a 5 PDFs, pergunta algo que consta neles e recebe a resposta em texto com arquivo e página corretos, em até 60 s na máquina de referência (Intel Core Ultra 9 185H, 62 GB de RAM, só CPU). Uma pergunta que não está nos documentos devolve a mensagem pré-cadastrada. O tempo de resposta fica registrado.

## Entregas de engenharia junto

- Script único para subir a aplicação local, com instruções no repositório.
- Testes automatizados desde o início (ao menos extração com página, referência e mensagem de informação ausente).
- Pipeline de CI com testes e lint.
- Execução no ambiente de produção (aplicação local) além do de desenvolvimento, para validar o caminho de instalação.
- Pequeno conjunto de perguntas de desenvolvimento com resposta esperada, sobre documentos sintéticos de exemplo (quem os cria está em aberto, PEND-16).

## Decisões em que o esqueleto se apoia

| ADR | Decisão | Status |
|---|---|---|
| [0001](adr/0001-modelo-de-ia-somente-local.md) | Só modelos de IA locais | aceito |
| [0002](adr/0002-aplicacao-web-local-sem-autenticacao.md) | Aplicação web local, sem autenticação | aceito |
| [0003](adr/0003-execucao-so-em-cpu-primeiro.md) | CPU primeiro, GPU opcional | aceito |
| [0004](adr/0004-linguagem-e-framework.md) | Python + FastAPI (interface a decidir no card #2) | proposto |
| [0005](adr/0005-runtime-e-modelo-de-linguagem-local.md) | Runtime e modelo local | proposto, confirmado pelo spike #1 |
| [0006](adr/0006-extracao-indexacao-recuperacao-e-referencia.md) | Extração, recuperação e referência vinda dos trechos | proposto, confirmado pelo spike #1 |
| [0007](adr/0007-armazenamento-metricas-e-mensagens.md) | SQLite para métricas; configuração para mensagens | proposto |
| [0008](adr/0008-empacotamento-e-instalacao.md) | Script de instalação com ambiente virtual | proposto |

Como os ADRs 0005 e 0006 só são aceitos depois do spike #1, ele é o primeiro passo do esqueleto, antes de qualquer card de Story.

## Alternativas descartadas

- **Caso 1 (contagem agregada):** é o mais arriscado para recuperação, mas exige um conjunto maior de documentos e uma definição de "projeto" que ainda não existe. Entra logo depois, como fatia.
- **Avaliação primeiro, sem interface:** mede latência e qualidade cedo, mas não tem nada que o usuário veja, o que viola a regra do esqueleto que anda. A medição de latência entra pelo registro do tempo de resposta.

## Dependências e pontos a confirmar

- O PO confirma que o caso 2 é o primeiro ponta a ponta (pergunta aberta no story map).
- Documentos de teste: o Lucas confirmou que não enviará os documentos dele, por serem privados. Usaremos documentos sintéticos de exemplo.
- Escolha do modelo local e da biblioteca de recuperação fica para a Elaboration do primeiro card ou para um spike.
