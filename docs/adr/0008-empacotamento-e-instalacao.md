# ADR-0008: Empacotamento e instalação no hardware do cliente

- **Status:** proposto
- **Data:** 2026-11-24
- **Decisor:** Rafael Escóssia (Tech Lead)
- **Origem:** `docs/00-registro.md` (ambiente de produção "a definir"); card #7 (subir a aplicação, testes e CI)

## Contexto

O cliente é leigo em tecnologia e a aplicação roda no computador dele, com modelo, dependências e dados locais. O ambiente de produção é a própria máquina local, ainda sem detalhes definidos. O walking skeleton exige um caminho repetível de instalação e execução.

## Opções consideradas

- **A. Script de instalação e execução com ambiente virtual Python:** leve e simples de depurar; depende de Python na máquina do cliente.
- **B. Docker (compose):** ambiente reprodutível e isolado; exige Docker no cliente, e acesso a CPU/GPU e a modelos grandes complica um pouco.
- **C. Executável único empacotado:** o mais simples para o cliente; empacotar modelo e dependências nativas é trabalhoso para 2 meses.

## Decisão

Proposta: começar com um script de instalação e execução com ambiente virtual (opção A), um comando para subir a aplicação. Docker e executável empacotado ficam para depois, se o ambiente de produção real exigir.

## Consequências

- ✅ Caminho mais curto até o esqueleto rodando e testado em CI.
- ⚠️ Depende de Python e de passos de instalação do modelo no cliente; precisa estar bem documentado.
- ⚠️ Pode ser revisado quando o ambiente de produção for detalhado com o PO e o cliente.

## Revisitar quando

O ambiente de produção real for definido, ou a instalação seguindo o README falhar numa máquina limpa do cliente.
