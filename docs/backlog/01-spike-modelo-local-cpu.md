## [SPIKE] Modelo local e recuperação em CPU dentro da meta de 60 s

**Tipo:** Spike
**Start-up:** sdd-piloto (CTL DocAnswer)
**Story points:** 3 (timebox, a confirmar na Elaboration)
**Tags:** esqueleto, risco alto
**Origem:** fatia 1

### Descrição
Pergunta a responder: qual modelo de linguagem local e qual biblioteca de recuperação respondem perguntas sobre PDFs só em CPU, na máquina de referência (Intel Core Ultra 9 185H, 62 GB de RAM), dentro de 60 s e com qualidade aceitável? A GPU continua sendo necessária?

### Critérios de aceite (rascunho)
- [ ] Pergunta respondida: há uma recomendação de modelo e de biblioteca de recuperação, com justificativa.
- [ ] Os tempos foram medidos na máquina de referência com pelo menos 5 perguntas sobre PDFs reais ou de exemplo, e estão registrados.
- [ ] Está dito se a meta de 60 s é atingida só em CPU. Se não, qual a alternativa (modelo menor ou GPU).
- [ ] A decisão fica registrada: os ADRs 0005 (runtime e modelo) e 0006 (extração, recuperação e referência) passam de `proposto` para `aceito`, com as medições como evidência, e o card #2 pode começar com o modelo escolhido.
- [ ] Se nenhuma combinação atingir a meta só em CPU, o ADR 0003 é revisado (novo ADR que o substitui).

### Dependências
- Nenhuma. Deve ser o primeiro item do fluxo.
