## [EXPERIMENTO] Atingir as metas de latência no conjunto de desenvolvimento

**Tipo:** Experimento/Modelo
**Start-up:** sdd-piloto (CTL DocAnswer)
**Story points:** (Elaboration)
**Tags:** risco alto
**Origem:** fatia 29

### Descrição
Hipótese: o sistema responde em texto em até 60 s e gera documentos em até 120 s na máquina de referência, só em CPU. Métrica alvo: todas as perguntas do conjunto de desenvolvimento (card #8) dentro dessas metas.

### Dependências
- Cards #8, #6 e #25. Se estourar, a GPU deixa de ser opcional (P16, P17).
