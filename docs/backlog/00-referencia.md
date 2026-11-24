## [STORY] Registrar o tempo de resposta de cada pergunta

**Tipo:** Story
**Start-up:** sdd-piloto (CTL DocAnswer)
**Story points:** 2 (card de referência da start-up)
**Responsável:**
**Tags:** referência
**Origem:** fatia 6 de `docs/03-fatias.md` (atividade 7, Exportar métricas)

### Descrição
Como desenvolvedor, posso consultar o tempo que o sistema levou para responder cada pergunta, para acompanhar a latência contra a meta de 60 s desde o primeiro dia.

### Critérios de aceite
- [ ] Dado que o sistema respondeu uma pergunta, quando abro o registro local, então vejo a pergunta, a data/hora e o tempo de resposta em milissegundos, medido do envio da pergunta até a resposta pronta.
- [ ] Dado que a resposta foi a mensagem pré-cadastrada de informação ausente, quando abro o registro, então o tempo dessa pergunta também aparece.
- [ ] Dado que a geração da resposta falhou, quando abro o registro, então a pergunta aparece com o tempo até a falha e o status "erro".
- [ ] Dado que a aplicação foi reiniciada, quando abro o registro, então os tempos anteriores continuam lá.
- [ ] Com o registro ligado, a resposta demora no máximo 50 ms a mais por pergunta.

### Fora de escopo
- Tela de métricas na interface (fatia 22) e exportação CSV/JSON (fatias 23 e 24).
- Tempo de processamento da indexação.
- Métrica de acerto e feedback.

### Por que vale 2 pontos (calibração)
É um fluxo só (pergunta → resposta → registro), com um único dado e persistência local. Não depende de decisão do cliente nem de integração externa, e é pequeno o bastante para cerca de 1 a 2 dias de trabalho, incluindo testes. Use-o como régua: um card de 1 ponto é claramente menor (ex.: mudar um texto de configuração); um de 3 já tem mais de um fluxo ou uma incerteza técnica.

### Dependências
- Existir o fluxo de pergunta e resposta (fatia 2). Para calibrar a estimativa, avalie só o tamanho deste card, sem contar essa dependência.

### Resultado em "Deployed"
- Registro de tempos funcionando no ambiente de desenvolvimento e validado pelo PO.
