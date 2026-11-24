## [STORY] Enviar PDFs pela interface e ver o progresso da indexação

**Tipo:** Story
**Start-up:** sdd-piloto (CTL DocAnswer)
**Story points:** (Elaboration)
**Tags:** esqueleto
**Origem:** fatia 5

### Descrição
Como cliente, posso enviar PDFs pela interface e acompanhar o progresso até poderem ser consultados, para não depender de arquivos carregados pelo desenvolvedor.

### Critérios de aceite (rascunho)
- [ ] Dado um ou mais PDFs selecionados, quando envio, então eles aparecem como "em indexação" com uma barra de progresso.
- [ ] Dado que a indexação terminou, quando pergunto sobre o conteúdo, então a resposta usa os arquivos enviados.
- [ ] Dado um arquivo que não é PDF ou está corrompido, quando envio, então o sistema avisa qual arquivo falhou e continua com os demais.

### Dependências
- Card #2 (e #3 para as referências funcionarem nos arquivos enviados).
