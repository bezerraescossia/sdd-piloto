# Incidente de comportamento: <título curto>

| Campo | Valor |
| --- | --- |
| ID | INC-000 |
| Data de detecção | AAAA-MM-DD |
| Sistema / versão em produção | |
| Severidade | crítica \| alta \| média \| baixa |
| Status | aberto \| mitigado \| em correção \| corrigido e monitorado |

## 1. Detecção

<!-- Gate: Fase 5 · Preenche: quem detectou -->
Como foi detectado:

- [ ] Avaliação periódica do QA abaixo do limiar do G3
- [ ] Reclamação de usuário
- [ ] Falha em caso real
- [ ] Alerta de infra (Dev)

Descrição objetiva do que aconteceu:

## 2. Classificação

<!-- Gate: Fase 5 · Preenche: Tech Lead -->

- [ ] Infraestrutura: o Dev resolve, sob o Tech Lead, e registra no runbook. Não segue este template.
- [ ] Comportamento: segue os passos abaixo.

## 3. Caso real

<!-- Gate: Fase 5 · Preenche: PO -->
Entrada, saída obtida e saída esperada. Remova dados pessoais conforme a system spec (o Data Owner aprova a amostragem).

| Entrada | Saída obtida | Saída esperada |
| --- | --- | --- |
| | | |

## 4. Caso de avaliação

<!-- Gate: Fase 5 · Escreve: Engenheiro de IA · Decide o conjunto: QA -->

- ID do caso criado:
- Rubrica operacional:
- Conjunto (desenvolvimento ou validação) e motivo:
- A avaliação reproduz a falha antes da correção? sim \| não

## 5. Mitigação imediata

<!-- Gate: Fase 5 · Só em incidente crítico · Autoriza: Tech Lead -->

- Mitigação aplicada (ex.: reverter versão do prompt ou do modelo):
- Autorizada por, data e hora:
- Emenda da spec que registra a mitigação, feita logo depois (link):

## 6. Correção

<!-- Gate: Fase 3 → G2 · A correção segue o ciclo normal -->

- Feature spec ou emenda (link):
- Tocou a lista de veto de Segurança e Compliance? sim \| não
- Mudança de modelo ou de system spec? sim \| não (se sim, o Tech Lead do projeto emenda e as avaliações são reexecutadas antes do G2)

## 7. Encerramento

<!-- Gate: Fase 5 · O ciclo fecha quando a correção volta a ser monitorada com o caso novo -->

| Papel | Nome | Confirma | Data |
| --- | --- | --- | --- |
| QA | | o caso novo está no monitoramento e passa o limiar | |
| Engenheiro de IA | | o caso de avaliação reproduz e cobre a falha | |
| PO | | o comportamento esperado voltou | |
| Tech Lead | | spec e produção coerentes | |
