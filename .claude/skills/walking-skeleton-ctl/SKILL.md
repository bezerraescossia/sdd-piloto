---
name: walking-skeleton-ctl
description: Define o walking skeleton da start-up deste repositório (Creative Tech Lab) a partir do story map — a menor implementação ponta a ponta, com qualidade de produção, que atravessa os componentes mais arriscados. Use quando o usuário pedir para definir/escolher o walking skeleton, o caminho mais curto e arriscado, a primeira fatia ponta a ponta, ou depois de concluir o story map no kickoff. Prefira esta skill à genérica `walking-skeleton` quando o contexto for uma start-up do programa CTL.
---

# Walking skeleton (CTL)

O walking skeleton é a menor implementação **ponta a ponta**, com qualidade de produção, que atravessa os principais componentes e integrações. Não é protótipo e não é descartado: o resto é construído em cima dele. Escolher o caminho **mais arriscado** (não o mais fácil) faz com que as incertezas apareçam cedo, quando ainda são baratas.

Entrada: `docs/01-story-map.md` (se não existir, ofereça rodar `story-mapping` antes) e `docs/adr/` (se não existir, ofereça rodar `adr-ctl` para os ADRs fundadores). Artefato: `docs/02-walking-skeleton.md`.

O esqueleto parte das decisões já registradas: não reabra um ADR `aceito`. Se o esqueleto depende de um ADR ainda `proposto` (ex.: modelo ou recuperação que o spike confirma), diga isso no artefato e coloque o spike como primeiro passo.

## Passos

1. **Liste candidatos.** Do story map, proponha 2–3 caminhos ponta a ponta possíveis, cada um com os componentes que toca.
2. **Escolha pelo risco.** Compare pela cobertura de componentes de risco alto. Recomende um e explique por quê; a decisão é do usuário/PO.
3. **Reduza ao mínimo.** Um caso de uso simples, dados mínimos, sem autenticação, validação extra, estilo ou otimização, exceto quando o risco de escala for óbvio. Não corte o que faz o esqueleto "andar".
4. **Exija o essencial de produção:** pipeline de deploy e testes construídos junto com o código; em produção (atrás de feature flag ou acesso restrito, se preciso).
5. **Evite o esqueleto que não anda:** só infraestrutura sem nada que o usuário veja não vale. Deve haver um resultado visível.
6. **Registre as dúvidas em `docs/pendencias.md`** (único lugar das pendências) e cite os `PEND-NN` no artefato. Não crie lista própria de perguntas.

Exemplo para ML/anotação: ingestão → anotação → treino → avaliação → resultado visível, com um lote pequeno. Depois se amplia volume e variedade.

## Estrutura do artefato

```markdown
# Walking skeleton: <nome do projeto>

## Caminho escolhido
<fluxo ponta a ponta em uma frase + lista de passos>

## Componentes atravessados e riscos cobertos
| Componente | Risco que o esqueleto expõe |
|---|---|

## Dentro do escopo
## Fora do escopo (adiado de propósito)

## Prova de vida
<o que o usuário vê/consegue fazer quando o esqueleto está pronto, e em qual ambiente>

## Entregas de engenharia junto
- Pipeline de deploy, testes, feature flag/acesso restrito

## Decisões em que o esqueleto se apoia
| ADR | Decisão | Status |
|---|---|---|
| ADR-NNNN | ... | aceito / proposto (confirmado pelo spike #N) |

## Alternativas descartadas
- <caminho>: <motivo>

## Dependências e pontos a confirmar
- <o que precisa ser confirmado antes ou durante; cite o PEND-NN de docs/pendencias.md>
```

Ao final, atualize o campo *Walking skeleton* do registro (`docs/00-registro.md`) e aponte o próximo passo: `feature-slicing`. Se o projeto usa Jira, o conteúdo do artefato é a descrição do épico do esqueleto (ver a seção Jira do `AGENTS.md`).
