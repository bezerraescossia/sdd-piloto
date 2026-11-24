# ADR-0005: Runtime e modelo de linguagem local

- **Status:** proposto (a confirmar pelo spike #1)
- **Data:** 2026-11-24
- **Decisor:** Rafael Escóssia (Tech Lead)
- **Origem:** ADR-0001, ADR-0003, spike #1 (`docs/backlog/01-spike-modelo-local-cpu.md`)

## Contexto

O modelo precisa responder só com base nos trechos fornecidos, em português e inglês, dentro de 60 s só em CPU na máquina de referência. Qualidade e latência dependem do tamanho do modelo, da quantização e do runtime. Ainda não há medição.

## Opções consideradas

- **A. Ollama (serve modelos quantizados):** instalação e troca de modelos simples, API local pronta; pouco controle fino de parâmetros.
- **B. llama.cpp (direto ou via binding Python):** mais controle e boa performance em CPU; mais trabalho de integração e de instalação.
- **C. Hugging Face transformers:** flexível e bom para embeddings; geralmente mais lento e pesado em CPU para geração.

A escolha do **modelo** (família e tamanho) também depende do spike e do suporte a português e inglês.

## Decisão

Ainda não decidida. O spike #1 mede 5 ou mais perguntas na máquina de referência com ao menos 2 combinações de runtime e modelo e escolhe a que atende à meta de 60 s com qualidade aceitável. Este ADR passa a `aceito` com a escolha e as medições como evidência.

## Consequências

- ✅ A decisão sai de medição e não de preferência.
- ⚠️ Até o spike terminar, o card #2 (pergunta e resposta) não deve começar.
- ⚠️ Se nenhuma combinação atingir a meta só em CPU, o ADR-0003 é revisado (GPU).

## Revisitar quando

O spike #1 terminar, ou a medição final (fatia 29) mostrar que o modelo escolhido não atinge a latência ou a qualidade acordadas.
