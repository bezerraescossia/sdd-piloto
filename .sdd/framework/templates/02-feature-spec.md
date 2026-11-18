# Feature spec: <nome da feature>

| Campo | Valor |
| --- | --- |
| ID | FEAT-000 |
| Tipo | IA \| dados |
| Versão | 0.1 |
| Data | AAAA-MM-DD |
| Squad | |
| Dono (comportamento e critérios) | PO |
| Dono (restrições e testabilidade) | Tech Lead |
| Status | rascunho \| pronta (G2) \| em execução \| aceita (G3) \| arquivada |

## 1. Comportamento

<!-- Gate: G2 · Preenche: PO -->
O que o sistema deve fazer, do ponto de vista do usuário. Sem descrever como.

## 2. Critérios de aceite

<!-- Gate: G2 (verificáveis) e G3 (atendidos) · Preenche: PO · Tech Lead confirma que cada um pode ser verificado -->

| # | Critério | Como se verifica | Limiar |
| --- | --- | --- | --- |
| A1 | | | |

## 3. Exemplos

<!-- Gate: G2 · Preenche: PO -->
Preencha a subseção do tipo da feature e escreva "Não se aplica" na outra.

### Se tipo = IA: casos de avaliação

<!-- O PO define o que é "bom". O Engenheiro de IA escreve a rubrica operacional. O QA decide o conjunto e mede. -->

| # | Entrada | Saída esperada | Rubrica | Conjunto (dev \| validação) |
| --- | --- | --- | --- | --- |
| E1 | | | | |

### Se tipo = dados: contrato e regras de qualidade

<!-- Dono: Data Owner. Executa: Engenheiro de IA/ML. -->
Link para o data contract preenchido:

| Regra de qualidade | Teste automatizado | Limiar |
| --- | --- | --- |
| | | |

## 4. Orçamento

<!-- Gate: G2 (declarado) e G3 (medido no evidence pack) · Preenche: Tech Lead -->

| Item | Orçamento |
| --- | --- |
| Custo por requisição | |
| Latência (p95) | |

## 5. Restrições técnicas e NFRs divergentes

<!-- Gate: G2 · Preenche: Tech Lead -->
Só o que **diverge** da system spec. O restante é herdado.

-

## 6. Dependências

<!-- Gate: G2 · Preenche: Tech Lead · O Tech Lead do projeto mantém o mapa entre features -->
Features de qualquer squad.

| Depende de | Dependem desta | Tipo de dependência |
| --- | --- | --- |
| | | dados \| interface \| comportamento |

Se a feature de IA depende de uma feature de dados que não passou o G3, ela só roda como **spike não produtivo** (amostra de dados, marcado "não produtivo", sem ir para produção).

## 7. Decisões e consultas registradas

<!-- Gate: durante a implementação · Quem decide: PO (produto), Tech Lead (técnico) -->
Diante de ambiguidade, o agente suspende e consulta. A resposta fica registrada aqui, contra a cláusula.

| Data | Cláusula | Pergunta do agente | Decisão | Quem decidiu |
| --- | --- | --- | --- | --- |
| | | | | |

## 8. Definition of Ready (G2)

<!-- Gate: G2 -->

- [ ] Comportamento descrito (PO)
- [ ] Critérios de aceite testáveis ou avaliáveis (Tech Lead confirma)
- [ ] Testes existem (QA confirma)
- [ ] Avaliação existe (Engenheiro de IA confirma; feature de IA)
- [ ] Exemplos ou contrato presentes (PO ou Data Owner)
- [ ] Orçamento de custo e latência declarado (Tech Lead)
- [ ] Restrições técnicas e dependências declaradas (Tech Lead)

## 9. Definition of Done (G3)

<!-- Gate: G3 · Detalhes no evidence pack -->

- [ ] Evidence pack anexado
- [ ] Limiares atingidos no conjunto de validação (QA mede) ou regras de qualidade passando no CI (dados)
- [ ] Custo e latência dentro do orçamento
- [ ] NFRs e guardrails respeitados (Tech Lead audita)
- [ ] Rationale da abordagem e link para esta versão da spec
- [ ] Aceite contra critérios de negócio (PO); Data Owner confirma a qualidade (dados)
- [ ] Spec arquivada e decisões novas levadas à base de conhecimento (Tech Lead)
