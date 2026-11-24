# Story map: sdd-piloto (CTL DocAnswer)

> Raiz do fluxo de documentos do projeto. A seção **Problema e Contexto** traz o problema e o objetivo do projeto. O mapa da jornada, os componentes e os riscos marcados como *hipótese* são proposta do Tech Lead e precisam ser validados com o PO no workshop. Pendências e perguntas em aberto ficam em `docs/pendencias.md`.

## Problema e Contexto

Hoje, para responder a perguntas sobre o conteúdo de um conjunto de documentos, o cliente precisa fazer uma análise manual: acessar repositórios, abrir pastas e documentos e consolidar a informação. Exemplo: para saber "Quantos projetos foram realizados em 2025?", é preciso abrir os documentos e contar os projetos à mão. Outro exemplo: para saber quais riscos um projeto levantou, é preciso localizar e ler os documentos desse projeto.

Para quem: o cliente, que é leigo em tecnologia e precisa de uma solução simples e direta. O desenvolvedor também é usuário: ele baixa as métricas de performance da solução.

**Objetivo:** permitir que o cliente envie documentos e obtenha, de forma simples, respostas às suas perguntas baseadas apenas nesses documentos e acompanhadas da referência de origem, em texto ou como documento gerado (Word, PowerPoint ou Excel), usando um modelo de IA executado localmente no hardware do usuário.

## Personas

- **Cliente (Lucas), leigo em tecnologia:** quer respostas simples, baseadas só nos documentos dele, com a origem de cada informação. Em texto ou como documento (Word, PowerPoint, Excel).
- **Desenvolvedor (Rafael):** quer baixar as métricas de performance (CSV/JSON) para comparar, fora do sistema, com soluções em nuvem.

## Jornada (backbone, da esquerda para a direita)

1. Enviar documentos → 2. Indexar (processar) → 3. Perguntar → 4. Receber resposta com referência → 5. Dar feedback → 6. Gerar documento a partir da resposta → 7. Exportar métricas

## Detalhamento por atividade

### 1. Enviar documentos (cliente)
- Passos/variações: enviar pasta ou arquivos; formatos PDF, Word, Excel, PowerPoint e Markdown; idiomas português e inglês.
- Componentes tocados: interface web, ingestão.
- Incertezas: outros formatos, limite de tamanho/quantidade (PEND-03).

### 2. Indexar (sistema)
- Passos/variações: extrair texto e metadados (arquivo, página/slide/planilha) e indexar. Barra de progresso; sem limite fixo de tempo.
- Componentes tocados: ingestão, indexação/recuperação.
- Incertezas: tempo de processamento só em CPU; extração fiel de página em PDF/Word.

### 3. Perguntar (cliente)
- Passos/variações: pergunta livre em linguagem natural. Casos: contagem agregada ("quantos projetos em 2025?"), detalhe de um projeto ("riscos do projeto XYZ"), informação ausente, pergunta imprópria/genérica/sobre a IA.
- Componentes tocados: interface web, guardrails, recuperação, LLM local.
- Incertezas: idioma da pergunta e da resposta (PEND-04); lista completa de guardrails (PEND-08).

### 4. Receber resposta com referência
- Passos/variações:
  - Resposta em texto baseada apenas nos documentos.
  - Referência: arquivo + página (documentos), só nome da planilha (Excel), arquivo + slide (apresentação).
  - Sem informação: resposta pré-cadastrada ("Desculpe, não consegui encontrar...").
  - Guardrail acionado (G-1 imprópria, G-2 genérica, G-3 sobre a IA): resposta pré-cadastrada e editável.
- Componentes tocados: LLM local, referências/citações, guardrails, respostas pré-cadastradas (editáveis).
- Incertezas: texto das respostas dos guardrails (PEND-07); outras respostas pré-cadastradas (PEND-06); como medir "baseada só nos documentos" (PEND-01).
- Meta de latência provisória: texto até 60 s.

### 5. Dar feedback sobre a resposta
- Passos/variações: feedback por resposta, que alimenta a métrica de acerto.
- Componentes tocados: interface web, armazenamento de métricas.
- Incertezas: formato do feedback, ex.: certo/errado ou nota (PEND-05).

### 6. Gerar documento a partir da resposta
- Passos/variações: pedido em linguagem natural ("gere um documento word...", "apresente em powerpoint"); saída Word, PowerPoint ou Excel com o conteúdo da resposta.
- Componentes tocados: geração de documentos, LLM local.
- Incertezas: estrutura/layout esperados do documento (PEND-09); meta provisória de até 120 s.

### 7. Exportar métricas (desenvolvedor)
- Passos/variações: acessar pela interface (não pelo chat), sem autenticação; baixar CSV ou JSON com tempo de processamento, tempo de resposta e acerto.
- Componentes tocados: interface web, armazenamento de métricas, exportação.
- Incertezas: lista final de métricas (PEND-02).

## Componentes arquiteturais

| Componente | Papel | Risco | Por quê |
|---|---|---|---|
| LLM local (CPU) | Gerar respostas sem nuvem | **alto** *(hipótese)* | Latência alvo (60 s/120 s) e qualidade só em CPU; GPU opcional vira obrigatória se estourar (PEND-18, PEND-19) |
| Recuperação e indexação | Achar trechos relevantes e montar a base | **alto** *(hipótese)* | Perguntas de contagem agregada ("quantos projetos em 2025") exigem juntar vários documentos, mais difícil que achar um trecho |
| Avaliação / conjunto de avaliação | Medir se as respostas estão certas | **alto** | Não existe conjunto de avaliação e ele será sintético; critérios de sucesso sem limiar (PEND-01, PEND-16) |
| Ingestão e extração (PDF, Word, Excel, PPT, MD) | Texto e posição (página/slide) | médio *(hipótese)* | Referência por página depende de extração fiel |
| Referências/citações | Anexar origem a cada resposta | médio *(hipótese)* | Regras diferentes por formato; precisa vir do dado, não do modelo |
| Guardrails + respostas pré-cadastradas | Bloquear/redirecionar e responder com texto fixo editável | médio | Só 3 categorias definidas; veto de Segurança e Compliance sem responsável (PEND-08, PEND-11) |
| Geração de documentos (Word, PPT, Excel) | Exportar a resposta em arquivo | médio-baixo *(hipótese)* | Tecnicamente conhecido; incerteza em layout esperado |
| Interface web local | Upload, chat, feedback, métricas | baixo-médio *(hipótese)* | Usuário leigo exige simplicidade |
| Métricas e exportação (CSV/JSON) | Registrar e baixar performance | baixo *(hipótese)* | Escopo claro; lista de métricas em aberto (PEND-02) |
