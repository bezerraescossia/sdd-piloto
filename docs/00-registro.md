# Registro da start-up

### sdd-piloto (CTL DocAnswer)

- **PO (start-up):** Guilherme Frediani
- **Tech Lead (Eldorado):** Rafael Escóssia
- **Time Eldorado (nº de devs):** 1 (Rafael acumula Dev, Tech Lead, QA e Eng. de IA/ML; ver PEND-13 e PEND-14 em `docs/pendencias.md`)
- **Capacidade (pessoas × duração):** 1 dev × 2 meses
- **WIP total (nº de devs − 1):** 1 (mínimo; 1 − 1 = 0)
- **Walking skeleton:** upload de PDFs → indexação → pergunta → resposta em texto com arquivo e página, via LLM local em CPU (caso 2); detalhes em `docs/02-walking-skeleton.md` (proposta, a confirmar com o PO)
- **Card de referência (2 pontos):** "Registrar o tempo de resposta de cada pergunta", em `docs/backlog/00-referencia.md` (etapa 5)
- **Ambiente de desenvolvimento:** sim, _detalhes a definir_ (aplicação web local, máquina de dev: Intel Core Ultra 9 185H, 62 GB de RAM)
- **Ambiente de UAT:** não há (projeto piloto). A validação do PO acontece no ambiente de desenvolvimento
- **Ambiente de produção (ou equivalente de "Deployed"):** sim, _detalhes a definir_ (a solução roda localmente no hardware do usuário)
- **Quem valida o UAT:** Guilherme (PO), em ambiente de desenvolvimento
- **Coluna Testing ligada?** Não (padrão)

### Observações

- Sem UAT separado, a validação do PO substitui a etapa UAT. Ao elaborar o quadro, trate "UAT" como validação do PO em dev.
- Com 1 dev, WIP 1 significa um card ativo por vez. Bloqueio não libera WIP.
- Fonte das informações de domínio: `docs/01-story-map.md`. Pendências em `docs/pendencias.md`.
