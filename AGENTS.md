# Regras para agentes

Este projeto é desenvolvido pela Metodologia SDD. Este arquivo só aponta para os documentos e fixa as regras que nenhum agente pode violar. Ele não repete a system spec.

## Onde ler

- Regras do jogo (fases, papéis, gates): [`framework/METODOLOGIA.md`](framework/METODOLOGIA.md)
- Templates dos artefatos: [`framework/templates/`](framework/templates/README.md)
- Normas deste projeto (arquitetura, guardrails, permissões e níveis de autonomia): [`sdd/system-spec.md`](sdd/system-spec.md). Se ainda não existe, o projeto está antes do G1: não escreva código de produto.
- Estado do projeto: cabeçalho `Status` de cada artefato em `sdd/`.

## Como descobrir a fase atual

1. Leia `sdd/` e o `Status` de cada artefato. Se `sdd/brief.md` não existe ou não está `validado no G0`, é a Fase 0.
2. Sem `sdd/system-spec.md` aprovada (G1), é a Fase 1.
3. Com feature em `sdd/features/FEAT-xxx-<slug>/`, o `Status` da `spec.md` e do `plan.md` diz o passo do ciclo da Fase 2.
4. Incidente aberto em `sdd/incidentes/` é Fase 5.

## Regras invioláveis

1. **A spec decide.** Quando código e spec divergem, não edite em silêncio: registre a divergência contra a cláusula e deixe o dono do artefato decidir.
2. **Todo pedido vira spec antes de virar código.**
3. **Você nunca é dono nem aprova.** Não registre aprovação, decisão ou revisão em nome de PO, Tech Lead, Dev, QA ou Segurança. Quem aciona você assina a sua saída.
4. **Ambiguidade suspende.** Pare e consulte quem decide (PO para produto, Tech Lead para técnica). A resposta entra na spec, na seção de decisões.
5. **Respeite o nível de autonomia** da system spec. Tarefa que exige plano aprovado não começa sem ele.
6. **Nenhuma implementação antes do plano aprovado pelo Tech Lead**, e só depois que a feature spec está `pronta (G2)`.
7. **Conjunto de validação retido é inacessível.** Ele não está neste repositório. Se você encontrar casos de validação aqui, pare e avise o QA. Trabalhe só com `evals/dev/`.
8. **Segurança e Compliance tem veto** sobre guardrails, dados pessoais, permissões dos agentes e troca de modelo ou de provedor em casos regulados. Não avance nesses itens sem a aprovação registrada.
9. **`framework/` só muda por decisão do Tech Lead**, em commit `framework:` separado e com entrada no [`CHANGELOG.md`](framework/CHANGELOG.md). Nunca edite os templates originais: copie para `sdd/`.
10. **Campo sem resposta vira pergunta em aberto** no próprio documento. Nunca invente.

## Convenções de commit

- Mudança de framework: prefixo `framework:`, nunca misturada com mudança de projeto.
- Mudança de projeto: um commit por task do plano aprovado.
