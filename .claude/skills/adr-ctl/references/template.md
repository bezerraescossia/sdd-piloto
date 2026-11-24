# Template de ADR enxuto (`docs/adr/NNNN-slug.md`)

```markdown
# ADR-NNNN: <Título curto, no imperativo ou como afirmação>

- **Status:** proposto | aceito | rejeitado | substituído por ADR-NNNN | obsoleto
- **Data:** AAAA-MM-DD
- **Decisor:** <quem decidiu ou vai aceitar>
- **Origem:** <decisão do PO ou do Tech Lead com data, spike #N, card #N ou conversa>

## Contexto

<O problema e as forças em jogo, em poucas linhas.>

## Opções consideradas

- **A. <opção>:** <vantagem e custo em uma ou duas linhas.>
- **B. <opção>:** <vantagem e custo em uma ou duas linhas.>

## Decisão

<Uma frase ativa: "Usaremos X para Y.", com a razão principal.>

## Consequências

- ✅ <o que melhora>
- ⚠️ <o que piora ou fica mais difícil>

## Revisitar quando

<O gatilho que reabre a decisão. Evidência (medição, link) quando houver.>
```

## Índice (`docs/adr/README.md`)

```markdown
# ADRs: <nome do projeto>

| ADR | Título | Status | Data |
|---|---|---|---|
| [0001](0001-slug.md) | ... | aceito | AAAA-MM-DD |
```

Ordene por número. Ao substituir um ADR, mantenha as duas linhas e escreva o novo número no status do antigo.

## Exemplo curto (formato, não conteúdo do projeto)

```markdown
# ADR-0002: Executar o modelo de linguagem apenas localmente

- **Status:** aceito
- **Data:** 2026-11-25
- **Decisor:** Guilherme (PO)
- **Origem:** decisão do PO em 2026-11-16 (restrição técnica)

## Contexto
O cliente exige que nenhum dado saia da máquina. O objetivo também é comparar com soluções em nuvem.

## Opções consideradas
- **A. Modelo local:** atende à restrição; exige hardware e limita o tamanho do modelo.
- **B. API em nuvem:** melhor qualidade e latência; viola a restrição.

## Decisão
Usaremos apenas modelos executados localmente, porque o projeto proíbe modelo hospedado em nuvem.

## Consequências
- ✅ Custo de inferência zero e sem envio de dados.
- ⚠️ Qualidade e latência dependem do hardware; a GPU pode virar obrigatória.

## Revisitar quando
A meta de 60 s não for atingida só em CPU.
```
