## [STORY] Responder com mensagem pré-cadastrada quando a informação não está nos documentos

**Tipo:** Story
**Start-up:** sdd-piloto (CTL DocAnswer)
**Story points:** (Elaboration)
**Tags:** esqueleto
**Origem:** fatia 4

### Descrição
Como cliente, quando minha pergunta não tem resposta nos documentos enviados, recebo uma mensagem simples dizendo isso, em vez de uma resposta inventada.

### Critérios de aceite (rascunho)
- [ ] Dado uma pergunta cuja resposta não está nos documentos, quando envio, então recebo "Desculpe, não consegui encontrar as informações para responder sua pergunta."
- [ ] Dado que o texto da mensagem está num arquivo de configuração, quando o edito e reinicio, então a nova mensagem aparece.
- [ ] Dado uma pergunta que consta nos documentos, quando envio, então a mensagem pré-cadastrada não aparece.

### Dependências
- Card #2. O texto vem de P4 (já definido); outras mensagens ficam em P25.
