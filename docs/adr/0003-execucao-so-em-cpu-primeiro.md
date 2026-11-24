# ADR-0003: Tentar execução só em CPU primeiro, com GPU opcional

- **Status:** aceito
- **Data:** 2026-11-24
- **Decisor:** Rafael Escóssia (Tech Lead)
- **Origem:** decisões do Tech Lead em 2026-11-16 (hardware de referência, custo de inferência zero, execução só em CPU primeiro)

## Contexto

O hardware de referência é o da máquina de desenvolvimento (Intel Core Ultra 9 185H, 62 GB de RAM; GPU NVIDIA RTX 2000 Ada com 8 GB de VRAM presente, mas opcional). O computador do cliente é similar. As metas de latência provisórias são de até 60 s para texto e 120 s para documento gerado, com indexação sem limite fixo e barra de progresso.

## Opções consideradas

- **A. Só CPU primeiro, GPU opcional:** não exige GPU do cliente; pode estourar as metas de latência.
- **B. GPU obrigatória desde o início:** latência melhor; restringe o hardware do cliente e a instalação.
- **C. Suporte às duas, sem prioridade:** mais custo de teste e de configuração para 1 dev.

## Decisão

Tentaremos executar tudo só em CPU primeiro, na máquina de referência, e mediremos a latência. A GPU continua opcional até a medição provar que é necessária.

## Consequências

- ✅ Instalação mais simples e hardware do cliente menos restrito.
- ✅ A medição de latência (card de referência, spike #1) passa a ser a evidência para decidir.
- ⚠️ O tamanho do modelo e a estratégia de recuperação ficam limitados ao que cabe na meta só em CPU (ver ADR-0005 e ADR-0006).
- ⚠️ Se a meta não for atingida, a GPU deixa de ser opcional e o cliente precisa ter uma.

## Revisitar quando

A meta de 60 s para texto ou de 120 s para documento não for atingida só em CPU na máquina de referência (spike #1 e experimento da fatia 29).
