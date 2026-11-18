# System spec: <nome do projeto>

| Campo | Valor |
| --- | --- |
| Versão | 0.1 |
| Data | AAAA-MM-DD |
| Dono | Tech Lead do projeto |
| Plataforma/normas herdadas | (versão, se houver) |
| Status | rascunho \| em revisão \| aprovada (G1) |

Esta spec vale em toda sessão de agente. Só o Tech Lead do projeto aprova mudanças nela. Link do arquivo de regras dos agentes derivado dela (ex.: `AGENTS.md`):

## 1. Arquitetura e convenções

<!-- Gate: G1 · Preenche: Tech Lead do projeto -->
Componentes, fronteiras, convenções de código e de nomes, estrutura do repositório.

## 2. Padrões de erro

<!-- Gate: G1 · Preenche: Tech Lead -->
Como erros são tratados, registrados e comunicados ao usuário.

## 3. NFRs transversais

<!-- Gate: G1 · Preenche: Tech Lead propõe, PO valida -->
Uma feature só declara na feature spec o que divergir daqui.

| NFR | Requisito | Como se verifica |
| --- | --- | --- |
| Segurança | | |
| Privacidade | | |
| Disponibilidade | | |
| Observabilidade | | |
| Custo por requisição | | |
| Latência (p95) | | |

## 4. Guardrails

<!-- Gate: G1 · Preenche: Tech Lead · Segurança e Compliance aprova (veto) -->
Regras sempre ativas: recusas, tratamento de dados pessoais, limites de domínio. Cada uma tem um teste correspondente, não é só instrução num prompt.

| # | Regra | Teste | Aprovada por |
| --- | --- | --- | --- |
| G-1 | | | Segurança e Compliance |

## 5. Permissões e níveis de autonomia dos agentes

<!-- Gate: G1 · Preenche: Tech Lead por classe de tarefa · Segurança e Compliance revisa (veto) -->

| Classe de tarefa | O agente faz sozinho | Exige plano aprovado | Proibido |
| --- | --- | --- | --- |
| | | | |

Permissões e segredos acessíveis aos agentes:

## 6. Modelo, prompts e ferramentas

<!-- Gate: G1 · Mantém: Dev ou Engenheiro de IA · Mudança exige avaliação sem regressão (QA mede) -->
São artefatos versionados. Qualquer mudança reexecuta a avaliação e compara com a versão anterior.

| Item | Versão | Avaliação de referência |
| --- | --- | --- |
| Modelo e provedor | | |
| Prompts | | |
| Definições de ferramentas | | |

Troca de modelo ou de provedor é mudança com impacto de spec: segue o fluxo da Fase 3 e, em casos regulados, tem veto de Segurança e Compliance.

## 7. Estratégia de avaliação

<!-- Gate: G1 · PO e cliente definem casos, critério de "bom" e limiar · Engenheiro de IA estrutura e versiona · QA guarda o conjunto retido -->

- Casos de uso e regras de negócio (link para o brief):
- Golden dataset v0 e rubrica operacional (link e versão):
- Conjunto de desenvolvimento (visível a Dev, Engenheiro de IA e agentes):
- Conjunto de validação retido (custódia do QA, nunca visto por quem implementa):
- Uso de dados reais e anonimização aprovados por (Data Owner):
- Limiares globais:
- Renovação dos conjuntos com casos reais de produção:

### Se houver modelo treinado ou ajustado

<!-- Preenche: Engenheiro de IA/ML · Data Owner aprova o uso dos dados -->

| Dataset | Origem | Versão | Guardião |
| --- | --- | --- | --- |
| Treino | | | Engenheiro de IA/ML |
| Validação | | | Engenheiro de IA/ML |
| Teste final | | | QA (nunca entra em treino) |

## 8. Suíte de testes, harness e CI

<!-- Gate: G1 · QA: testes do sistema · Engenheiro de IA: harness de avaliação · Dev: integra no CI -->

- Onde roda e como é acionado:
- Bloqueia merge quando: um teste falha ou um limiar não é atingido
- Roda de ponta a ponta, mesmo sobre um sistema vazio? sim \| não

## 9. Observabilidade e runbook inicial

<!-- Gate: G1 · Preenche: Tech Lead com Dev -->
Logs, métricas e alertas mínimos. Link para o runbook. Regras de amostragem de tráfego real para a avaliação periódica (Fase 5).

## 10. Aprovação (G1)

<!-- Gate: G1 -->

| Papel | Nome | Aprova | Data |
| --- | --- | --- | --- |
| Tech Lead do projeto | | spec completa | |
| PO | | o que toca negócio e privacidade | |
| Segurança e Compliance | | guardrails e permissões | |
| QA | | suíte e conjunto retido | |
| Engenheiro de IA/ML | | harness rodando de ponta a ponta no CI | |
