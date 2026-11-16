# Brief: <nome do projeto>

| Campo | Valor |
| --- | --- |
| Versão | 0.1 |
| Data | AAAA-MM-DD |
| Dono (PO) | |
| Cliente / Sponsor | |
| Status | rascunho \| em revisão \| validado no G0 |

## 1. Problema e objetivo

<!-- Gate: G0 · Preenche: PO -->
Qual problema do cliente isto resolve, e para quem. Termine com **uma frase de objetivo**.

## 2. Usuários e casos de uso prioritários

<!-- Gate: G0 e G1 (alimenta o golden dataset) · Preenche: PO -->
Use exemplos concretos de entrada e saída, em linguagem que o agente consiga consumir.

| # | Usuário | Situação | Entrada de exemplo | Saída esperada |
| --- | --- | --- | --- | --- |
| 1 | | | | |

## 3. Critérios de sucesso

<!-- Gate: G0 · Preenche: PO com o cliente · QA confirma os critérios do sistema; Engenheiro de IA/ML confirma os critérios de modelo -->
Cada critério precisa de uma forma de medir e de um limiar. É a base dos evals.

| Critério | Como se mede | Limiar | Quem valida |
| --- | --- | --- | --- |
| | | | |

## 4. Fora de escopo

<!-- Gate: G0 · Preenche: PO -->
O que explicitamente **não** será feito neste projeto.

-

## 5. Dados e data contracts

<!-- Gate: G0 · Preenche: PO (lista), Data Owner (contratos) -->
Uma linha por fonte crítica. Fonte sem contrato assinado ou sem dono volta ao alinhamento de escopo.

| Fonte | Data Owner | Contrato assinado? | Dados pessoais? | Link para o contrato |
| --- | --- | --- | --- | --- |
| | | sim \| não | sim \| não | |

Há dados para montar o golden dataset (ou os datasets de treino, validação e teste, se houver modelo a treinar)? Onde estão e quem os rotulou:

**Insumo opcional:** se a organização já avaliou a prontidão dos dados por outro framework, anexe a avaliação aqui como evidência (link):

## 6. Restrições e riscos

<!-- Gate: G0 · Preenche: PO · Segurança e Compliance sinaliza o que é seu -->

| Tema | Restrição ou risco | Responsável |
| --- | --- | --- |
| Privacidade e LGPD | | Segurança e Compliance |
| Conformidade | | Segurança e Compliance |
| Custo esperado | | Tech Lead |
| Latência esperada | | Tech Lead |
| Técnico | | Tech Lead |
| Cliente (disponibilidade, escopo) | | PO |

## 7. Parecer de viabilidade

<!-- Gate: G0 · Preenche: Tech Lead, QA, Engenheiro de IA/ML, Segurança e Compliance -->
Se a abordagem ou os dados não forem viáveis, volta-se ao alinhamento de escopo. Se faltar trabalho de dados grande, ele entra no backlog como feature de dados e o escopo é renegociado.

- **Tech Lead:** abordagem proposta e riscos.
- **QA:** os critérios do sistema são mensuráveis?
- **Engenheiro de IA/ML:** os critérios de modelo são mensuráveis (métrica, conjunto de teste, dados rotulados, baseline)? Dá para montar o golden dataset?
- **Segurança e Compliance:** restrições de dados pessoais e conformidade.

## 8. Premissas e perguntas em aberto

<!-- Gate: G0 · Preenche: qualquer papel -->

| # | Premissa ou pergunta | Dono | Prazo |
| --- | --- | --- | --- |
| | | | |

## 9. Aprovação (G0)

<!-- Gate: G0 · O cliente e o Sponsor validam; os demais assinam o que é seu -->

| Papel | Nome | Aprova | Data |
| --- | --- | --- | --- |
| Cliente | | critérios de sucesso | |
| Sponsor | | escopo e orçamento | |
| PO | | brief | |
| Tech Lead | | viabilidade | |
| QA | | mensurabilidade dos critérios do sistema | |
| Engenheiro de IA/ML | | mensurabilidade dos critérios de modelo | |
| Data Owner | | data contracts | |
