## [STORY] Perguntar e receber resposta em texto sobre um PDF já carregado

**Tipo:** Story
**Start-up:** sdd-piloto (CTL DocAnswer)
**Story points:** (Elaboration)
**Tags:** esqueleto, risco alto
**Origem:** fatia 2

### Descrição
Como PO, posso digitar uma pergunta numa página web local e receber uma resposta em texto baseada em um PDF já carregado no sistema, para ver o fluxo ponta a ponta funcionando com o LLM local, mesmo sem upload, estilo ou referência.

### Critérios de aceite (rascunho)
- [ ] Dado um PDF já carregado, quando pergunto algo que consta nele, então recebo uma resposta em texto baseada só no conteúdo do PDF.
- [ ] Dado que nenhuma chamada a modelo em nuvem é feita, quando faço uma pergunta, então a resposta é gerada só com o modelo local.
- [ ] Dado uma pergunta vazia, quando envio, então nada é processado e a tela pede para digitar uma pergunta.

### Fora de escopo
- Upload pela interface (fatia 5), referência (fatia 3), mensagem de informação ausente (fatia 4), estilo.

### Dependências
- Spike #1 concluído (modelo e biblioteca escolhidos).
