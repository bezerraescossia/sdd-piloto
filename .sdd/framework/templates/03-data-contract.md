# Data contract: <nome da fonte>

| Campo | Valor |
| --- | --- |
| ID | DC-000 |
| Versão | 0.1 |
| Data | AAAA-MM-DD |
| Data Owner | |
| Contato técnico (Engenheiro de IA/ML) | |
| Status | rascunho \| assinado \| revisão pendente |

## 1. Fonte e propósito

<!-- Gate: G0 · Preenche: Data Owner -->
O que é a fonte, onde mora e para que o sistema a consome.

## 2. Esquema

<!-- Gate: G0 e G2 · Preenche: Data Owner -->

| Campo | Tipo | Obrigatório | Significado | Dado pessoal? |
| --- | --- | --- | --- | --- |
| | | | | |

## 3. Frescor e completude

<!-- Gate: G0 e G2 · Preenche: Data Owner -->

| Medida | Compromisso |
| --- | --- |
| Frequência de atualização | |
| Atraso máximo | |
| Completude mínima | |

## 4. Acesso

<!-- Gate: G0 · Preenche: Data Owner · Segurança e Compliance revisa -->

| Perfil | Pode acessar | Como |
| --- | --- | --- |
| | | |

## 5. Dados pessoais e privacidade

<!-- Gate: G0 · Preenche: Data Owner · Segurança e Compliance revisa (lista de veto) -->

- Há dados pessoais? Quais campos?
- Base legal:
- Retenção:
- Anonimização exigida para uso em avaliação e na amostragem de tráfego real (Fase 5):

## 6. Regras de qualidade

<!-- Gate: G2 e G3 (feature de dados) · Preenche: Data Owner · Executa: Engenheiro de IA/ML -->
Cada regra precisa de um teste automatizado.

| Regra | Teste | Limiar | Onde roda |
| --- | --- | --- | --- |
| | | | CI \| pipeline |

## 7. Mudanças no contrato

<!-- Gate: Fase 3 · Mudança de contrato é mudança de spec -->

- Como e com quanta antecedência o Data Owner avisa uma mudança:
- Quem é avisado (squads que consomem):

## 8. Assinatura

<!-- Gate: G0 -->

| Papel | Nome | Confirma | Data |
| --- | --- | --- | --- |
| Data Owner | | contrato | |
| Tech Lead | | viabilidade técnica | |
| Segurança e Compliance | | seção 5 (dados pessoais) | |
