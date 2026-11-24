---
name: backlog-card
description: Escreve cards de backlog da start-up deste repositório (Creative Tech Lab) no template do workflow (Story, Bug, Enabler, Spike, Experimento/Modelo), define o card de referência de 2 pontos e monta o backlog inicial em docs/backlog/. Use quando o usuário pedir para criar/escrever/rascunhar um card, história, bug, spike ou enabler, definir o card de 2 pontos de calibração, montar o backlog inicial a partir das fatias, ou revisar se um card está bem escrito (critérios de aceite, DoD 1) — mesmo sem dizer "backlog".
---

# Card de backlog

No Backlog, o card é leve: descrição no formato do seu tipo, sem estimativa nem abordagem técnica. O detalhe vem na Elaboration (Three Amigos). Detalhar cedo demais deixa o card obsoleto, então **não elabore além do necessário** para o PO ordenar e entender o item.

Template completo e regras: `references/template.md`. Leia antes de escrever. Critérios de aceite: `references/criterios.md`.

## Backlog inicial a partir das fatias

1. Leia `docs/03-fatias.md` (se não existir, ofereça `feature-slicing`).
2. Gere um arquivo por fatia em `docs/backlog/NN-<slug>.md`, numerado na ordem sugerida. Preencha título, tipo, descrição e, só para os primeiros itens, rascunho de critérios de aceite.
3. Crie `docs/backlog/README.md` com a lista ordenada (número, título, tipo) para o PO reordenar.

## Card de referência (2 pontos)

É a régua de calibração da estimativa da start-up. Escolha entre as fatias o card mais simples e bem entendido, com cerca de 1–2 dias de trabalho, e salve em `docs/backlog/00-referencia.md` com critérios de aceite completos, dizendo por que vale 2 pontos. Confirme a escolha com o usuário e atualize o campo *Card de referência* do `docs/00-registro.md`.

## Publicar no Jira (só a pedido)

Os arquivos de `docs/backlog/` são a versão original dos cards. Só crie ou altere issues no Jira quando o usuário pedir, e siga a seção **Jira** do `AGENTS.md` (projeto, tipo de issue, labels, épico, resumo `#NN`, cuidados com a API). Depois de publicado, o Jira passa a ter a versão mais recente: ao mudar um card, avise o usuário se o arquivo correspondente em `docs/backlog/` ficou desatualizado.

## Escrevendo cada tipo

- **Story:** "Como `<persona>`, posso `<ação>`, para que `<resultado>`". Critérios em Dado/Quando/Então.
- **Bug:** comportamento atual, esperado e passos para reproduzir. Exige teste automatizado que falha antes e passa depois.
- **Enabler:** risco reduzido ou oportunidade habilitada; resultado observável como aceite.
- **Spike:** a pergunta a responder e o timebox em pontos; aceite = pergunta respondida **e, se a resposta decide algo técnico, ADR registrado** (`adr-ctl`).
- **Experimento/Modelo:** hipótese e métrica alvo; exige conjunto de validação definido na Elaboration (ex.: "recall ≥ X no conjunto Y").
- **Anotação de dados:** Story ou Enabler, com aceite por qualidade (concordância entre anotadores) e volume.

## Checagem antes de entregar (DoD 1)

- [ ] Descrição no formato do tipo.
- [ ] Fatia vertical (comportamento visível, não camada técnica).
- [ ] Não depende de investigação pendente; se depende, crie um Spike.
- [ ] Dependências citam outros cards pelo número (ou chave do Jira) e dúvidas ou respostas de terceiros pelo `PEND-NN` de `docs/pendencias.md`, sem códigos soltos nem "pendente com fulano" sem ID.
- [ ] Sem palavras vagas (rápido, intuitivo, robusto, amigável) sem número.
- [ ] Preencha só o necessário no Backlog: pontos, abordagem técnica e de teste ficam para a Elaboration.
