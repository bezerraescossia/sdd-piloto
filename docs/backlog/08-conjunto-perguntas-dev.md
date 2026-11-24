## [EXPERIMENTO] Conjunto de perguntas de desenvolvimento com execução automática

**Tipo:** Experimento/Modelo
**Start-up:** sdd-piloto (CTL DocAnswer)
**Story points:** (Elaboration)
**Tags:** risco alto, depende do cliente
**Origem:** fatia 8

### Descrição
Hipótese: com um conjunto de 5 a 10 perguntas por categoria, com respostas e referências esperadas, dá para medir de forma repetível se o sistema acerta. Métrica alvo: a ser definida (P9); este card entrega o conjunto e a execução automática, não o limiar.

### Critérios de aceite (rascunho)
- [ ] Existe um conjunto de desenvolvimento em `.sdd/evals/dev/`, só com documentos liberados pelo cliente, com perguntas, respostas corretas e referências esperadas.
- [ ] Um comando executa todas as perguntas contra o sistema e produz um relatório com acerto, referência e tempo por pergunta.
- [ ] O conjunto retido, usado para a medição final, fica com o Guilherme e não com o desenvolvedor (P24, P26).

### Dependências
- Lucas liberar os documentos (P24) e responder dados pessoais (P12). Card #2.
