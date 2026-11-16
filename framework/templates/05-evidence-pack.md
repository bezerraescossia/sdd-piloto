# Evidence pack: <feature>

| Campo | Valor |
| --- | --- |
| Feature | FEAT-000 (link) |
| Versão da feature spec | |
| Tipo | IA \| dados |
| Versão do evidence pack | 0.1 |
| Data | AAAA-MM-DD |
| Autor | Dev (IA) ou Engenheiro de IA/ML (dados) |
| Status | em preparo \| em auditoria \| aceito \| recusado |

## 1. Resumo

<!-- Gate: G3 · Preenche: autor -->
O que foi entregue, em poucas linhas, e se todos os critérios foram atendidos.

## 2. Critérios de aceite

<!-- Gate: G3 · Um critério por linha, na ordem da feature spec -->

| # | Critério | Resultado | Evidência (link) | Atendido? |
| --- | --- | --- | --- | --- |
| A1 | | | | sim \| não |

## 3. Testes

<!-- Gate: G3 · Preenche: autor · QA roda a suíte na auditoria -->
Resultado dos testes automatizados, com link para a execução no CI.

## 4. Avaliações

<!-- Gate: G3 (feature de IA) · Medido pelo QA no conjunto de validação retido -->

| Métrica | Limiar | Resultado | Versão anterior | Regressão? |
| --- | --- | --- | --- | --- |
| | | | | sim \| não |

Versões de modelo, prompts e ferramentas avaliadas:

Execuções e variância (quantas rodadas):

## 5. Regras de qualidade

<!-- Gate: G3 (feature de dados) · Preenche: Engenheiro de IA/ML -->

| Regra | Limiar | Resultado | Roda no CI? |
| --- | --- | --- | --- |
| | | | |

Pipeline monitorado, contrato atualizado e acesso por perfil (evidência):

## 6. Custo e latência

<!-- Gate: G3 · Orçamento vem da feature spec -->

| Item | Orçamento | Medido | Dentro? |
| --- | --- | --- | --- |
| Custo por requisição | | | sim \| não |
| Latência (p95) | | | sim \| não |

## 7. NFRs e guardrails

<!-- Gate: G3 · Tech Lead audita -->

- NFRs transversais respeitados (evidência):
- Guardrails testados (evidência):

## 8. Rationale e desvios

<!-- Gate: G3 · Preenche: autor -->

- Por que esta abordagem:
- Desvios da spec e decisões tomadas (cláusula, quem decidiu):

## 9. Auditoria e aceite (G3)

<!-- Gate: G3 · Quem implementa nunca é quem mede nem quem aceita -->
Se o Tech Lead ou o QA reprovam, os agentes corrigem e este pack é refeito. Se o PO recusa, a feature volta ao G2.

| Papel | Nome | O que confirma | Data |
| --- | --- | --- | --- |
| Tech Lead | | aderência à spec e aos NFRs | |
| QA | | testes rodados e avaliações medidas no conjunto retido | |
| Data Owner | | qualidade (feature de dados) | |
| PO | | aceite contra critérios de negócio | |
