# Template de card

```markdown
## [TIPO] Título do card

**Tipo:** Story | Bug | Enabler | Spike | Experimento/Modelo
**Start-up:**
**Story points:** (definido na Elaboration)
**Responsável:**
**Tags:** (bloqueado, expedite, ...)
**Origem:** (fatia de `docs/03-fatias.md` ou conversa)

### Descrição
Como <persona>, posso <ação>, para que <resultado>.
(Bug: comportamento atual, esperado e passos para reproduzir.
 Enabler: risco reduzido ou oportunidade habilitada.
 Spike: a pergunta a responder e o timebox em pontos.
 Experimento/Modelo: hipótese e métrica alvo.)

### Critérios de aceite
- [ ] Dado ..., quando ..., então ...
- [ ] Dado ..., quando ..., então ... (caso de erro)
- [ ] (não funcional, quantificado)

### Fora de escopo
- ...

### Abordagem técnica
- Decisões importantes e justificativa. (Elaboration)
- **ADRs aplicáveis:** ADR-NNNN, ... Se o card exige uma decisão nova e cara de reverter, crie o ADR antes de implementar (`adr-ctl`).

### Abordagem de teste
- (se não for óbvio) (Elaboration)

### Design
- Link, incluindo estados vazio, carregando e erro.

### Dependências
- Outros cards: pelo número ou chave do Jira (ex.: `CTM-9 (#02)`).
- Dúvidas e respostas de terceiros: pelo `PEND-NN` de `docs/pendencias.md`.

### Definition of Done (checklist da coluna atual)
- [ ] ...

### Resultado em "Deployed"
- Link para produção, modelo/dataset versionado ou registro dos achados.
```

## Quando cada seção é preenchida

| Seção | Backlog | Elaboration |
|---|---|---|
| Título, tipo, descrição | ✅ | revisa |
| Critérios de aceite | rascunho (só itens do topo) | ✅ completos |
| Fora de escopo, abordagem técnica/teste (com ADRs aplicáveis), design, pontos | — | ✅ |
| Resultado em Deployed | — | preenchido ao entregar |

## Tamanhos

Escala Fibonacci 1, 2, 3, 5, 8, 13. Meta ≤ 5; obrigatório dividir > 8; teto 13. Spike: timebox em pontos.
