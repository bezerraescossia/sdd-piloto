# sdd-piloto

Projeto real desenvolvido pela Metodologia SDD (spec-driven development) e, ao mesmo tempo, o piloto que a valida. Este repositório é a referência máxima do framework: a metodologia, os templates e o estado do projeto vivem aqui.

> **Estado atual:** Fase 0 (Intake). Nenhum artefato de projeto foi preenchido ainda; falta definir o projeto e escrever o brief.

## Como navegar

| Pasta ou arquivo | O que é | Quem muda |
| --- | --- | --- |
| [`framework/METODOLOGIA.md`](framework/METODOLOGIA.md) | Fases, papéis, gates e diagramas | Só o Tech Lead, com [`CHANGELOG.md`](framework/CHANGELOG.md) |
| [`framework/templates/`](framework/templates/README.md) | Um template por artefato, com o mapa de caminhos finais | Só o Tech Lead |
| `sdd/` | Estado do projeto: brief, system spec, data contracts, features, incidentes | Cada dono, passando pelo gate |
| `evals/` | Conjunto de desenvolvimento e o contrato do conjunto retido | QA e Engenheiro de IA |
| `src/` | Código derivado da spec | Dev, com agentes |
| [`AGENTS.md`](AGENTS.md) | Regras invioláveis para agentes de IA | Tech Lead |

## Por onde começar

1. Leia a [visão geral](framework/METODOLOGIA.md#visão-geral) e a [Fase 0](framework/METODOLOGIA.md#fase-0-intake-e-alinhamento-com-o-cliente).
2. Copie `framework/templates/01-brief.md` para `sdd/brief.md` e `03-data-contract.md` para `sdd/data-contracts/`.
3. Siga a ordem: brief e contratos → G0 → system spec → G1 → por feature: spec → G2 → plano → implementação → evidence pack → G3.

## Estrutura

```text
AGENTS.md · CLAUDE.md
framework/   METODOLOGIA.md · CHANGELOG.md · templates/
sdd/         brief.md · system-spec.md · data-contracts/ · features/FEAT-001-<slug>/ · incidentes/ · decisoes/
evals/       dev/ · validacao.md
src/
```

O conjunto de validação retido nunca entra neste repositório. Ele fica sob custódia do QA, e `evals/validacao.md` guarda só o contrato e o hash.
