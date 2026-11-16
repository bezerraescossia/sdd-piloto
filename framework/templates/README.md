# Templates da Metodologia SDD

Versão dos templates: v1.1 · acompanha [`../METODOLOGIA.md`](../METODOLOGIA.md). Histórico em [`../CHANGELOG.md`](../CHANGELOG.md).

## Regra de uso

1. **Copie** o template para o caminho final em `sdd/` (tabela abaixo) e nunca edite o arquivo desta pasta.
2. **Preencha** todos os campos. Campo sem resposta vira "Pergunta em aberto" no próprio documento, nunca fica vazio.
3. **Cada seção existe porque um gate a exige.** O comentário `<!-- Gate: ... -->` no início da seção diz qual. Se a seção não se aplica, escreva "Não se aplica" e o motivo.
4. **Escreva para o agente.** Prefira exemplos concretos de entrada e saída a descrições gerais.
5. **Mudou o template?** Só o Tech Lead aprova, em commit `framework:` separado, com entrada no [`CHANGELOG.md`](../CHANGELOG.md).
6. **Registre a versão** dos templates usada no cabeçalho do artefato criado.

## Mapa dos artefatos

| Template | Caminho final | Fase | Gate | Dono (preenche) | Quem aprova |
| --- | --- | --- | --- | --- | --- |
| `01-brief.md` | `sdd/brief.md` | 0 Intake | G0 | PO | Cliente e Sponsor |
| `03-data-contract.md` | `sdd/data-contracts/DC-001-<fonte>.md` | 0 Intake e features de dados | G0, G2 | Data Owner | Tech Lead confirma viabilidade; Segurança revisa dados pessoais |
| `04-system-spec.md` | `sdd/system-spec.md` | 1 Fundação | G1 | Tech Lead | PO (negócio), Segurança e Compliance (guardrails e permissões) |
| `02-feature-spec.md` | `sdd/features/FEAT-001-<slug>/spec.md` | 2 Ciclo por feature | G2, G3 | PO e Tech Lead | Tech Lead, QA e Engenheiro de IA no G2 |
| `07-plano.md` | `sdd/features/FEAT-001-<slug>/plan.md` | 2 Ciclo por feature | Aprovação do plano; revisão de cada task | Tech Lead (com o agente) | Tech Lead aprova o plano; Dev aprova cada task |
| `05-evidence-pack.md` | `sdd/features/FEAT-001-<slug>/evidence-pack.md` | 2 Ciclo por feature | G3 | Dev ou Engenheiro de IA/ML | Tech Lead audita, QA mede, PO aceita |
| `06-incidente-comportamento.md` | `sdd/incidentes/INC-001-<slug>.md` | 5 Operação | Entra pelo G2 | PO, QA e Engenheiro de IA | Tech Lead |

## Ordem de preenchimento

`01-brief` + `03-data-contract` → G0 → `04-system-spec` → G1 → por feature: `02-feature-spec` → G2 → `07-plano` → implementação → `05-evidence-pack` → G3. Em produção: `06-incidente-comportamento` → nova feature spec ou emenda → G2.

## Convenções

- **Cabeçalho padrão:** versão, data, dono, status (`rascunho`, `em revisão`, `aprovado`).
- **Papéis:** PO, Tech Lead, Dev, QA, Engenheiro de IA/ML, Segurança e Compliance, Data Owner, Sponsor. Os mesmos nomes de [`../METODOLOGIA.md`](../METODOLOGIA.md).
- **Decisões:** toda decisão fica registrada contra a cláusula da spec, com quem decidiu e a data.
- **Arquivamento:** a feature aceita (G3) não muda de pasta; o `Status` da `spec.md` passa a `arquivada`.
- **Conjunto de validação retido:** nunca entra neste repositório. Só o contrato e o hash, em `evals/validacao.md`.
- **Quem implementa nunca é quem mede nem quem aceita.**
