# Critérios de aceite

Dizem o que significa "funcionando" para **um card**. Acordados antes da implementação, limitam o crescimento silencioso de escopo.

## Formato

```text
Dado   <estado inicial>
Quando <ação ou evento>
Então  <resultado observável>
```

- Um comportamento por critério, em uma frase. Se o "Então" tem vários "e", divida.
- Não force o formato quando atrapalha ("Códigos aparecem em maiúsculas").

## Um critério bom é

- **Observável** por quem não conhece a implementação.
- **Testável antes do código existir.**
- Sobre **comportamento**, não implementação.
- Na **linguagem do usuário**.
- Cobre **erros e bordas**, não só o caminho feliz.

| ❌ Ruim | ✅ Bom |
|---|---|
| "O formulário funciona corretamente" | "Dado um formulário preenchido, quando salvo, então o registro aparece na lista" |
| "Adicionar tabela `enderecos`" | (nota de implementação, não critério) |
| "Adicionar validação no CEP" | "Quando o CEP é inválido, então nada é salvo e o campo explica o erro" |
| "Salvar é rápido" | "Com 200 registros, salvar leva menos de 1 segundo" |

Palavras que exigem números: *rápido, intuitivo, robusto, amigável*.

## Não funcionais

Performance, segurança, acessibilidade e resiliência entram **no card que introduz o comportamento**, quantificados. Não há documento separado de requisitos não funcionais.

## Experimento/Modelo

```text
Dado   o conjunto de validação <nome/versão>
Quando o modelo <versão> é avaliado
Então  <métrica> ≥ <valor>
```

## Regras

- ACs não são abordagem técnica, design de UI nem DoD; não copie a DoD para os ACs.
- Cada AC corresponde a pelo menos um teste, no nível mais barato que o prove.
- AC novo durante a implementação sem conversa = crescimento silencioso de escopo; comportamento novo vira **novo card**.
- Mais de 5–6 ACs: divida o card.
