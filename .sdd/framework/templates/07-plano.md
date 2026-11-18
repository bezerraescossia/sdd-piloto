# Plano: <feature>

| Campo | Valor |
| --- | --- |
| Feature | FEAT-000 (link) |
| Versão da feature spec | |
| Versão do plano | 0.1 |
| Data | AAAA-MM-DD |
| Dono | Tech Lead |
| Status | rascunho \| aprovado pelo Tech Lead \| em execução \| concluído |

## 1. Abordagem

<!-- Gate: aprovação do plano (Tech Lead) · Preenche: Tech Lead com o agente -->
Como a feature será construída e por quê. Escolhas técnicas relevantes, alternativas descartadas e componentes tocados.

## 2. Tasks

<!-- Gate: aprovação do plano · Cada task é uma unidade que o Dev consegue revisar numa sentada -->
Estado de cada task: `pendente` \| `em revisão` \| `aprovada` \| `rejeitada`.

| ID | Título | Critérios cobertos | Depende de | Autonomia | Verificação | Estado |
| --- | --- | --- | --- | --- | --- | --- |
| T1 | | A1 | | sozinho \| plano aprovado | | pendente |

## 3. Detalhe das tasks

<!-- Gate: aprovação do plano -->

### T1: <título>

- **Objetivo:** o que muda ao fim desta task, em uma frase.
- **Cláusulas e critérios:** itens da feature spec que ela cumpre (ex.: A1, §5).
- **Arquivos prováveis:**
- **Verificação:** comando de teste ou avaliação **no conjunto de desenvolvimento** que prova a task.
- **Fora do escopo desta task:**
- **Tamanho esperado:** pequeno o bastante para revisar em uma leitura (referência: algumas centenas de linhas de diff, no máximo).

## 4. Riscos e dependências

<!-- Gate: aprovação do plano -->

- Features de dados de que depende (se alguma não passou o G3, as tasks de IA rodam só como spike não produtivo):
- Riscos técnicos:
- Itens que tocam a lista de veto de Segurança:

## 5. Aprovação do plano

<!-- Gate: aprovação do plano · Só o Tech Lead aprova; o agente nunca registra por conta própria -->

| Papel | Nome | Decisão | Data |
| --- | --- | --- | --- |
| Tech Lead | | aprovado \| ajustes pedidos | |

### Alterações após a aprovação

Toda mudança no plano depois de aprovado exige nova aprovação do Tech Lead.

| Data | Mudança | Motivo | Reaprovada por |
| --- | --- | --- | --- |
| | | | |

## 6. Registro de revisão por task

<!-- Gate: cada task · O Dev revisa; o agente nunca registra por conta própria -->

| Task | Commit | Revisor (Dev) | Decisão | Data |
| --- | --- | --- | --- | --- |
| T1 | | | aprovada \| ajuste \| rejeitada | |
