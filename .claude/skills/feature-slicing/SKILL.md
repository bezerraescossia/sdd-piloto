---
name: feature-slicing
description: Fatia o walking skeleton e o story map da start-up deste repositório (Creative Tech Lab) em feature slices verticais (visíveis, valiosas, atravessando as camadas), ou divide um card grande demais em cards menores. Use quando o usuário falar em fatiar, quebrar, dividir, "slice", card grande/épico/>8 pontos, mais de 5–6 critérios de aceite, ou pedir para transformar o story map em itens de backlog — inclusive quando só descrever uma fatia horizontal como "criar a API" ou "montar o banco".
---

# Feature slicing

Dividimos o trabalho em **fatias verticais**, nunca em camadas técnicas. Uma fatia boa é **visível** ao usuário, **valiosa** (mesmo um passo pequeno) e **atravessa as camadas**. Fatias horizontais adiam o feedback e escondem o risco de integração.

| ❌ Horizontal | ✅ Vertical |
|---|---|
| Criar o banco de dados | Usuário vê uma lista de itens (leitura, sem estilo) |
| Construir a API | Usuário cadastra um item |
| Construir a tela | Usuário edita um item |

Entrada: `docs/01-story-map.md` e `docs/02-walking-skeleton.md` (ou o card que o usuário quer dividir). Artefato: `docs/03-fatias.md`.

## Passos

1. Comece pelo walking skeleton. Se ele for grande demais para um card só, **fatie o próprio esqueleto** em passos finos, cada um já ponta a ponta, e marque-os na coluna *Esq.* do artefato. Depois, para cada atividade restante do story map, proponha fatias.
2. Aplique as perguntas abaixo para encontrar o primeiro passo mais simples de cada uma.
3. Reprove fatias horizontais: reescreva em termos de comportamento observável.
4. Ordene por valor e risco, como **sugestão**: quem reordena o backlog é o PO.
5. Sinalize onde falta informação e proponha um **Spike** (a pergunta e o timebox em pontos) em vez de chutar. Um spike que decide algo técnico termina com um ADR (`adr-ctl`); registre isso no aceite dele. Dúvida que depende de outra pessoa (PO, cliente) vai para `docs/pendencias.md`, não para uma lista no artefato.

## Perguntas para fatiar

1. Qual a coisa mais simples para começar? ("Hello World")
2. Dá para fazer leitura antes de escrita?
3. Dá para começar com um caso de uso simplificado?
4. Dá para adiar a automação (começar manual)?
5. Dá para adiar a autenticação?
6. Dá para adiar a validação de entrada?
7. Dá para exibir os dados sem estilo?
8. Dá para adiar otimizações de performance? (Não, se o risco de escala for óbvio.)

## Sinais de que precisa dividir mais

- Mais de 5–6 critérios de aceite.
- Estimativa acima de 8 pontos (teto absoluto 13; meta ≤ 5).
- Mistura leitura e escrita, ou caminho feliz e todos os erros, num só card.

Em projetos de ML/anotação, separe também por volume (lote pequeno → grande) e por classe/caso de dado.

## Estrutura do artefato

```markdown
# Fatias: <nome do projeto>

| # | Fatia (comportamento observável) | Tipo | Esq. | Componentes | Risco | Origem no story map |
|---|---|---|---|---|---|---|
| 1 | <passo fino do walking skeleton> | Story | ✅ | ... | alto | ... |

## Spikes sugeridos
- <pergunta> (timebox: N pts)

## Pendências
- <IDs de docs/pendencias.md que afetam a ordem ou o conteúdo das fatias; não liste perguntas aqui>
```

Tipos válidos: Story, Bug, Enabler, Spike, Experimento/Modelo. Próximo passo: `backlog-card` para o card de referência e o backlog inicial.
