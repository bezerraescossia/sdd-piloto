# ADR-0007: Armazenamento de métricas e das mensagens pré-cadastradas

- **Status:** proposto
- **Data:** 2026-11-24
- **Decisor:** Rafael Escóssia (Tech Lead)
- **Origem:** decisões do PO em 2026-11-16 (mensagem de informação ausente, métricas, resposta editável dos guardrails); cards #00 (tempo de resposta) e #4 (mensagem de informação ausente)

## Contexto

O sistema precisa guardar tempos de resposta e de processamento e, depois, o acerto vindo do feedback, para consulta na interface e exportação em CSV e JSON. As mensagens pré-cadastradas (informação ausente e guardrails) devem ser simples de editar, porque vão mudar durante o desenvolvimento. Os dados persistem entre reinícios.

## Opções consideradas

- **Métricas, A. SQLite:** consulta e exportação simples, sem servidor, um arquivo local; um pouco mais de código que um log.
- **Métricas, B. Arquivo JSONL/log:** o mais simples de escrever; consultar, filtrar e exportar exige mais código à medida que as métricas crescem.
- **Mensagens, A. Arquivo de configuração (YAML ou JSON):** qualquer pessoa edita num editor de texto; exige reinício ou recarga para valer.
- **Mensagens, B. Tela de administração:** mais amigável; mais código e fora do escopo agora.

## Decisão

Proposta: guardaremos métricas em SQLite local e as mensagens pré-cadastradas em um arquivo de configuração (YAML ou JSON) versionado no repositório.

## Consequências

- ✅ Exportar CSV e JSON vira consulta simples (cards #23 e #24).
- ✅ O PO ou o dev edita mensagens sem mexer no código.
- ⚠️ Mudança de mensagem exige reinício (ou recarga), o que precisa estar nos critérios do card #4.
- ⚠️ O esquema da tabela de métricas deve prever novas colunas (acerto, processamento).

## Revisitar quando

O PO pedir para editar mensagens pela interface, ou o volume de métricas passar do que o SQLite local atende bem.
