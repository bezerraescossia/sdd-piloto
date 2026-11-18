# sdd-piloto

Projeto real desenvolvido pela Metodologia SDD (spec-driven development) e, ao mesmo tempo, o piloto que a valida. Um repositório por startup: o processo vive em `.sdd/` e o código num workspace uv.

> **Estado atual:** Fase 0 (Intake). O brief está em rascunho; os contratos de dados e a validação do G0 ainda faltam.

## Como navegar

| Caminho | O que é | Quem muda |
| --- | --- | --- |
| [`.sdd/framework/METODOLOGIA.md`](.sdd/framework/METODOLOGIA.md) | Fases, papéis, gates e diagramas | Só o Tech Lead, com [`CHANGELOG.md`](.sdd/framework/CHANGELOG.md) |
| [`.sdd/framework/templates/`](.sdd/framework/templates/README.md) | Um template por artefato, com o mapa de caminhos finais | Só o Tech Lead |
| `.sdd/` (resto) | Estado do projeto: brief, gates, contratos, decisões, aprovações, system spec, evals, features, incidentes | Cada dono, passando pelo gate |
| `packages/` | Código derivado da spec (workspace uv, Fase 1) | Dev, com agentes |
| [`AGENTS.md`](AGENTS.md) | Regras invioláveis para agentes de IA | Tech Lead |

## Por onde começar

1. Leia a [visão geral](.sdd/framework/METODOLOGIA.md#visão-geral) e a [Fase 0](.sdd/framework/METODOLOGIA.md#fase-0-intake-e-alinhamento-com-o-cliente).
2. Copie `01-brief.md` para `.sdd/brief.md`, `03-data-contract.md` para `.sdd/contracts/` e `09-gates.md` para `.sdd/gates.md`.
3. Siga a ordem: brief e contratos, com registros em `.sdd/approvals/` → G0 → system spec → G1 → por feature: spec → G2 → plano → implementação → evidence pack → G3.

## Estrutura

```text
AGENTS.md · CLAUDE.md
.sdd/
  framework/   METODOLOGIA.md · CHANGELOG.md · templates/
  brief.md · gates.md · system-spec.md
  contracts/ · decisions/ · approvals/ · incidents/
  evals/       dev/ · validation.md
  features/FEAT-001-<slug>/{spec,plan,evidence-pack}.md
packages/      (workspace uv, Fase 1)
```

O conjunto de validação retido nunca entra neste repositório. Ele fica sob custódia do QA, e `.sdd/evals/validation.md` guarda só o contrato e o hash.
