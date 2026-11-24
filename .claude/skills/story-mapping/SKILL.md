---
name: story-mapping
description: Conduz ou consolida o workshop de story mapping com o PO da start-up deste repositório (Creative Tech Lab), produzindo o mapa da jornada ponta a ponta e a lista de componentes arquiteturais, com os riscos de cada um. Use quando o usuário falar em story map, mapear a jornada, workshop com o PO, preparar a pauta do workshop, transformar notas/transcrição de workshop em mapa, ou levantar componentes e riscos no começo de uma start-up — mesmo que não diga "story mapping".
---

# Story mapping

Primeiro passo do kickoff: entender a **jornada ponta a ponta** do usuário e **quais componentes** a atravessam. O resultado alimenta a escolha do walking skeleton (o caminho mais curto *e* mais arriscado), por isso os riscos importam tanto quanto as atividades.

Artefato: `docs/01-story-map.md`. A start-up é a dona do repositório; use o nome do projeto (diretório raiz) no título, sem perguntar.

## Modos de uso

- **Preparar o workshop:** gere uma pauta curta (objetivo, quem convidar, perguntas-guia abaixo, tempo) para o PO e usuários especialistas.
- **Consolidar o resultado:** a partir de notas, transcrição ou conversa, monte o mapa. Não invente atividades; registre cada lacuna em `docs/pendencias.md` (com dono e os cards que ela bloqueia) e cite o `PEND-NN` no mapa.

## Perguntas-guia para o workshop

1. Quem é o usuário (persona) e qual resultado ele quer no fim?
2. Qual o passo a passo de hoje, do gatilho ao resultado? (backbone da jornada)
3. Para cada passo: que detalhes, variações e exceções existem?
4. Quais sistemas, dados, modelos e integrações cada passo toca?
5. Onde estão as maiores incertezas: técnicas, de dados, de integração, de adoção?
6. O que é essencial na primeira versão e o que pode esperar?

## Estrutura do artefato

```markdown
# Story map: <nome do projeto>

## Problema e Contexto
<o problema que o cliente enfrenta hoje e o objetivo do projeto, em poucas linhas>

## Personas
- <persona>: <objetivo>

## Jornada (backbone, da esquerda para a direita)
1. <atividade> → 2. <atividade> → ...

## Detalhamento por atividade
### 1. <atividade>
- Passos/variações: ...
- Componentes tocados: ...
- Incertezas: ... (PEND-NN)

## Componentes arquiteturais
| Componente | Papel | Risco (alto/médio/baixo) | Por quê |
|---|---|---|---|
```

O story map **não tem seção de perguntas abertas**. Toda dúvida, premissa não confirmada ou dependência de terceiros vai para `docs/pendencias.md` (único lugar das pendências, com ID `PEND-NN`). No mapa, a incerteza de cada atividade e o "por quê" do risco apenas citam o ID.

Para projetos de anotação e ML, inclua no backbone ingestão → anotação → treino → avaliação → resultado visível, e trate qualidade e volume de dados como fonte de risco.

Termine apontando o próximo passo: `walking-skeleton-ctl`.
