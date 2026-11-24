# ADR-0001: Usar somente modelos de IA executados localmente

- **Status:** aceito
- **Data:** 2026-11-24
- **Decisor:** Guilherme Frediani (PO)
- **Origem:** requisitos do projeto definidos pelo PO em 2026-11-16 (modelo local, nuvem fora de escopo)

## Contexto

O objetivo do produto é responder perguntas sobre os documentos do cliente com um modelo de IA rodando no hardware do próprio usuário. O projeto proíbe qualquer modelo hospedado em nuvem e lista o uso de nuvem como fora de escopo. O desenvolvedor compara, fora do sistema, esta solução com soluções em nuvem.

## Opções consideradas

- **A. Modelo executado localmente:** atende à restrição e mantém os documentos na máquina; limita o tamanho do modelo e depende do hardware.
- **B. API de modelo em nuvem:** melhor qualidade e latência, menos esforço; viola a restrição do projeto.
- **C. Híbrido (local com fallback para nuvem):** não atende, pois qualquer chamada à nuvem é proibida.

## Decisão

Usaremos apenas modelos executados localmente, porque o projeto proíbe qualquer modelo hospedado em nuvem. Isso vale para geração de respostas, embeddings e qualquer outro uso de IA no sistema.

## Consequências

- ✅ Custo de inferência zero e nenhum dado do cliente sai da máquina.
- ✅ Critério de sucesso verificável: nenhuma chamada a modelo em nuvem.
- ⚠️ Qualidade e latência dependem do modelo escolhido e do hardware (ver ADR-0003 e ADR-0005).
- ⚠️ Dependências e modelos precisam ser instalados localmente (ver ADR-0008).

## Revisitar quando

O PO mudar a restrição de nuvem. Não há gatilho técnico: se o modelo local não atender, a resposta é rever modelo ou hardware, não esta decisão.
