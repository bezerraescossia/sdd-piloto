# ADR-0002: Aplicação web local, sem autenticação

- **Status:** aceito
- **Data:** 2026-11-24
- **Decisor:** Guilherme Frediani (PO)
- **Origem:** decisões do PO em 2026-11-16 (aplicação web local, sem autenticação, métricas visíveis a qualquer usuário)

## Contexto

O cliente é leigo em tecnologia e precisa de uma solução simples. A solução roda apenas na máquina do usuário. As métricas de performance devem ficar visíveis na interface para qualquer usuário, e o desenvolvedor as acessa direto por ela, não pelo chat.

## Opções consideradas

- **A. Aplicação web local, sem autenticação:** simples de usar (navegador) e de construir; qualquer pessoa com acesso à máquina vê tudo.
- **B. Aplicação desktop empacotada:** experiência mais "de programa", mas muito mais esforço de empacotamento para 2 meses e 1 dev.
- **C. Aplicação web com autenticação:** protege perfis, mas autenticação está fora de escopo e não há necessidade com uso local.

## Decisão

Construiremos uma aplicação web que roda localmente e é acessada pelo navegador, sem autenticação, porque o uso é local e o PO deixou autenticação fora de escopo. As métricas ficam visíveis a qualquer usuário na interface.

## Consequências

- ✅ Menos código e menos fricção para o cliente leigo.
- ✅ A tela de métricas dispensa controle de acesso.
- ⚠️ A aplicação não deve escutar fora da máquina local (ex.: só `localhost`), para não expor os documentos na rede.
- ⚠️ Se o uso mudar para vários usuários ou rede, será preciso autenticação e rever o ADR.

## Revisitar quando

A aplicação precisar rodar em servidor compartilhado ou ser acessada por mais de um usuário na rede.
