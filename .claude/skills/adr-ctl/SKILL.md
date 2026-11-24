---
name: adr-ctl
description: Registra e mantém ADRs (Architecture Decision Records, enxutos) da start-up deste repositório (Creative Tech Lab) em docs/adr/, e levanta os "ADRs fundadores" antes do walking skeleton. Use sempre que o usuário falar em ADR, decisão de arquitetura/técnica, "registrar a decisão", escolha de modelo, biblioteca, framework ou stack, trocar uma decisão anterior, ou quando um spike terminar com uma recomendação — e também no kickoff, depois do story map e antes do walking skeleton. Complementa a skill global `architecture-decision-records`, com pasta, idioma e ciclo de vida do nosso fluxo.
---

# ADRs (CTL)

Um ADR guarda **por que** uma decisão técnica foi tomada, para que o time (ou o "eu de daqui a dois meses") não precise redescobrir o contexto nem refazer a discussão. Com 1 dev e 2 meses, o risco real não é burocracia: é esquecer a razão de uma escolha cara de reverter, como o modelo local ou a biblioteca de recuperação.

Pasta: `docs/adr/`. Arquivos: `NNNN-slug.md` (4 dígitos, sequencial). Índice: `docs/adr/README.md`. Template: `references/template.md`. Idioma: pt-BR.

## Quando escrever um ADR

Escreva quando a decisão:
- é **difícil ou cara de reverter** (modelo, biblioteca de recuperação, framework, formato de armazenamento);
- **afeta vários cards** ou o desenho do walking skeleton;
- tem **alternativas reais** que alguém poderia questionar depois;
- vem de uma restrição do projeto que molda a solução (ex.: nenhum modelo em nuvem).

Não escreva para escolhas locais e fáceis de trocar (nome de função, lib de formatação). Essas ficam na "Abordagem técnica" do card. Na dúvida, pergunte: "se isso mudar, quantos cards refazem?". Mais de um, ADR.

## Ciclo de vida

`proposto` → `aceito` → (`substituído por ADR-NNNN` | `obsoleto`). Também existe `rejeitado`.

- Um ADR aceito **não é editado** para mudar a decisão. Crie um novo que o substitui e marque o antigo como `substituído por ADR-NNNN`. O histórico é o valor.
- Correções de texto e links podem ser editadas.
- Mantenha o `README.md` do índice atualizado a cada criação ou mudança de status.

## Modo 1: ADRs fundadores (antes do walking skeleton)

Passo do kickoff entre `story-mapping` e `walking-skeleton-ctl`.

1. Leia `docs/00-registro.md`, `docs/01-story-map.md` (problema, componentes e riscos) e `docs/pendencias.md`.
2. Levante as decisões em duas listas e **apresente ao usuário antes de escrever**:
   - **Já decididas pelo PO:** viram ADR `aceito`, citando a origem (ex.: "decisão do PO em 2026-11-16"). Ex.: modelo local sem nuvem; aplicação web local; sem autenticação.
   - **Escolhas que o esqueleto exige:** linguagem e framework, armazenamento, extração de PDF, biblioteca de recuperação, modelo. Viram ADR `proposto`, com as opções reais. Se dependem de medição (modelo e recuperação em CPU), diga que o spike confirma e deixe `proposto` até lá.
3. Escreva os ADRs confirmados e o índice. Aponte o próximo passo: `walking-skeleton-ctl`.

Poucos ADRs bons valem mais que muitos. Para este tamanho de projeto, algo entre 4 e 8 fundadores costuma bastar.

## Modo 2: manter ao longo do projeto

- **Spike terminou:** o aceite do spike é um ADR. Crie ou atualize o ADR (`proposto` → `aceito`) com as medições como evidência.
- **Elaboração de card:** a "Abordagem técnica" cita os ADRs que valem (`ADR-0003`). Se o card exige uma decisão nova que cabe nos critérios acima, crie o ADR antes de implementar.
- **Decisão mudou:** crie o ADR novo, marque o antigo como substituído, atualize o índice e avise quais cards são afetados.
- **Verificação rápida:** quando pedirem "o que falta registrar", compare spikes e cards concluídos com os ADRs e liste os buracos.

## Como escrever bem

- **Contexto:** o problema e as forças em jogo, em poucas linhas, sem repetir os documentos de origem.
- **Opções:** pelo menos duas reais, com a razão curta de cada. Um ADR sem alternativa é só um anúncio.
- **Decisão:** uma frase ativa ("Usaremos X para Y").
- **Consequências:** o que fica melhor *e* o que fica pior ou mais difícil. Seja honesto sobre o custo.
- **Revisitar quando:** o gatilho que reabre a decisão (ex.: "se a meta de 60 s não for atingida só em CPU").
- Cite evidência (medição, link, ID de pendência ou de card) em vez de opinião.
- Dúvida que bloqueia a decisão: registre em `docs/pendencias.md`, cite o `PEND-NN` no ADR e mantenha-o `proposto` até a resposta.
