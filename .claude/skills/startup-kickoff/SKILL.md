---
name: startup-kickoff
description: Orquestra o kickoff da start-up dona deste repositório (programa da Creative Tech Lab), do problema até o backlog inicial (1–2 semanas). Cria o registro da start-up (seção 12 do workflow) e conduz, em ordem, story-mapping, adr-ctl (ADRs fundadores), walking-skeleton-ctl, feature-slicing, card de referência de 2 pontos e backlog-card. Use sempre que o usuário falar em kickoff, começar o projeto, onboarding no programa, "preencher o registro da start-up", WIP/capacidade/ambientes, ou pedir "o que falta no kickoff" — mesmo sem citar o nome da skill.
---

# Kickoff da start-up

Este repositório pertence a **uma única start-up**, e o nome dela é o do projeto (nome do diretório raiz do repo, ex.: `sdd-piloto`). Não pergunte o nome nem crie subpastas por start-up. Use o nome do repositório no título dos artefatos.

Leva a start-up de "só uma ideia" até um **walking skeleton definido e um backlog inicial**. O kickoff dura 1–2 semanas, então o papel desta skill é manter o fio da meada: saber em que etapa estamos, o que já existe em `docs/` e qual o próximo passo.

## Fluxo

| # | Etapa | Skill | Artefato |
|---|---|---|---|
| 1 | Registro da start-up | (esta skill) | `docs/00-registro.md` |
| 2 | Story mapping | `story-mapping` | `docs/01-story-map.md` |
| 3 | ADRs fundadores | `adr-ctl` | `docs/adr/NNNN-*.md` e `docs/adr/README.md` |
| 4 | Walking skeleton | `walking-skeleton-ctl` | `docs/02-walking-skeleton.md` |
| 5 | Fatiamento vertical | `feature-slicing` | `docs/03-fatias.md` |
| 6 | Card de referência (2 pts) | `backlog-card` | `docs/backlog/00-referencia.md` |
| 7 | Backlog inicial | `backlog-card` | `docs/backlog/NN-<slug>.md` |
| 8 | Publicar no Jira (só a pedido) | `backlog-card` | issues no projeto do Jira, conforme a seção Jira do `AGENTS.md` |

Decisões técnicas não terminam na etapa 3: toda decisão relevante que aparecer depois (ex.: resultado de um spike) também vira ADR, via `adr-ctl`. O kickoff só garante que o esqueleto parte de decisões registradas.

**Pendências.** Dúvidas, premissas não confirmadas e dependências de terceiros que surgirem em qualquer etapa vão para `docs/pendencias.md` (ID `PEND-NN`), nunca para seções soltas dentro dos artefatos; os artefatos só citam o ID. Se o arquivo não existir, crie-o na primeira pendência, com as seções Em aberto (ID, pendência, dono, bloqueia, origem), Resolvidas e Histórico de decisões.

## Como conduzir

1. **Descubra o estado.** Veja o que já existe em `docs/` (inclusive `docs/adr/` e `docs/pendencias.md`) e retome da primeira etapa sem artefato, em vez de recomeçar.
2. **Faça o registro (etapa 1)** usando `references/registro.md`. Pergunte só o que não dá para inferir e deixe `_a definir_` nos campos ainda abertos; o time de devs, por exemplo, pode não estar fechado. Calcule o WIP total como `nº de devs − 1` (mínimo 1). Os campos *Walking skeleton* e *Card de referência* são preenchidos depois, ao fim das etapas 4 e 6; volte ao registro para completá-los.
3. **Chame a skill da etapa seguinte** e, ao terminar, volte aqui para atualizar o registro e anunciar o próximo passo.
4. **Feche o kickoff** quando existirem registro completo, ADRs fundadores, skeleton, fatias, card de referência e backlog inicial ordenado. Garanta que o que ficou pendente (ex.: ambiente de UAT sem definição, ADRs ainda `proposto`) esteja em `docs/pendencias.md`, com dono, para o usuário levar ao PO.

## Princípios que guiam as etapas

- O escopo é aberto e a capacidade é fixa: o backlog nasce ordenável pelo PO, não "completo".
- Fatias verticais, nunca camadas técnicas.
- O walking skeleton toca os componentes **mais arriscados** e é construído com qualidade de produção.
- Decisões da start-up ficam registradas (registro e ADRs), porque o time é dono do processo e vai revisá-las nas retrospectivas.

Se o usuário pedir só uma etapa, execute apenas ela; não force o fluxo inteiro.
