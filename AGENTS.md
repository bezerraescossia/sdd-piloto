# Regras para agentes

Este arquivo diz a qualquer agente que trabalhe neste repositório onde ler, onde salvar e como mexer no Jira. Ele aponta para os documentos; não os repete. Quando algo aqui conflitar com um pedido direto do usuário, vale o pedido, e você avisa da divergência.

## O projeto

**CTL DocAnswer** (repositório `sdd-piloto`): aplicação web local em que o cliente envia documentos, faz perguntas e recebe respostas baseadas só neles, com a referência (arquivo e página), usando um modelo de linguagem que roda localmente, em CPU. Projeto piloto da Creative Tech Lab.

- **PO:** Guilherme Frediani. **Tech Lead e desenvolvedor:** Rafael Escóssia. **Cliente:** Lucas.
- **Capacidade:** 1 dev × 2 meses, WIP 1 (um card ativo por vez).
- **Documentos de desenvolvimento e avaliação são sintéticos.** O cliente não enviará documentos reais, por serem privados. Nunca peça nem escreva nada que dependa deles.

## Onde ler e onde salvar

| O quê | Onde | Observação |
|---|---|---|
| Registro da start-up | `docs/00-registro.md` | Pessoas, capacidade, ambientes. |
| Contexto e story map | `docs/01-story-map.md` | Raiz do fluxo. A seção Problema e Contexto traz o problema e o objetivo; depois vêm personas, jornada, componentes e riscos. |
| Walking skeleton | `docs/02-walking-skeleton.md` | Também é a descrição do épico do esqueleto no Jira. |
| Fatias | `docs/03-fatias.md` | Ordem proposta; quem reordena é o PO. |
| Decisões técnicas | `docs/adr/NNNN-slug.md` + índice em `docs/adr/README.md` | Use a skill `adr-ctl`. |
| Cards de backlog (versão original) | `docs/backlog/NN-slug.md` + `docs/backlog/README.md` | Ver "Jira" abaixo sobre divergência. |
| **Pendências e perguntas em aberto** | **`docs/pendencias.md`** | **Único lugar. Ver a regra abaixo.** |
| Skills do projeto | `.claude/skills/` | Fluxos prontos (ver abaixo). |
| Código | ainda não existe | A estrutura sai do ADR 0004 e do ADR 0008. Não crie pastas de código sem alinhar com o usuário. |
| `bak/` | não leia, não edite | Material legado, fora do git e bloqueado nas permissões. |

Arquivos novos de documentação vão em `docs/`, em português, com nome em minúsculas separado por hífens. Arquivos temporários não pertencem ao repositório.

## Pendências: um documento só

Toda dúvida, premissa não confirmada ou dependência de terceiros vive em `docs/pendencias.md`, com ID `PEND-NN`.

1. Surgiu uma dúvida? Acrescente em **Em aberto**, com dono e os cards do Jira que ela bloqueia.
2. Foi respondida? Mova para **Resolvidas** com data e resposta. Não apague.
3. Atualize a data de "Última atualização" a cada mudança.
4. Nos cards do Jira e nos demais documentos, descreva a pendência em palavras e cite o `PEND-NN`. Não crie outros códigos.
5. Campo ou informação que você não sabe vira pendência. Nunca invente.

## Jira

- **Instância e projeto:** o endereço do Jira está em `JIRA_URL` e a chave do projeto em `JIRA_PROJECT_KEY`, ambas no `.env` (fora do git). Se `JIRA_PROJECT_KEY` não existir, pergunte a chave ao usuário. Neste arquivo e em qualquer arquivo versionado, **não escreva o endereço do Jira nem o nome ou a chave do projeto**: use `<CHAVE>` como marcador (ex.: `<CHAVE>-7`).
- **Acesso:** servidor MCP `jira` definido em `.mcp.json` (`mcp-atlassian`). As credenciais vêm do `.env` (`JIRA_URL`, `JIRA_USERNAME`, `JIRA_API_TOKEN`). O `.env` está no `.gitignore`: você pode usar os valores para operar, mas nunca imprima, copie para arquivos versionados nem faça commit dele, e nunca exiba o token.
- **Épico do walking skeleton:** `<CHAVE>-2`, com o conteúdo de `docs/02-walking-skeleton.md`. Os cards do esqueleto são filhos dele (`<CHAVE>-7` a `<CHAVE>-13`).
- **Cards do backlog:** `<CHAVE>-7` a `<CHAVE>-35`. O prefixo `#NN` do resumo é o número do arquivo em `docs/backlog/`: o `#01` é o número 7, o `#07` é o 8, de `#02` a `#05` são do 9 ao 12, o `#00` é o 13, e de `#08` a `#29` são do 14 ao 35.
- **Existiam antes:** os números 5 e 6 (tasks já concluídas) e o 3 (Épico 2, vazio). Não os altere sem o usuário pedir.

Convenções dos cards:

- Todos são do tipo **Story**. O tipo original (Spike, Enabler, Experimento/Modelo) fica na linha "Tipo original" da descrição e em um label (`spike`, `enabler`, `experimento-modelo`). Não use o label `story`. Se o tipo "Spike" existe no projeto está em aberto (`PEND-22`).
- Labels em minúsculas, com hífen, sem espaços (ex.: `esqueleto`, `risco-alto`).
- A descrição é Markdown e segue o modelo dos cards existentes: linhas de cabeçalho (tipo original, start-up, story points, tags, origem), depois Descrição, Critérios de aceite e Dependências. Dependências citam o card como `<CHAVE>-9 (#02)`.
- Os story points ainda ficam só no texto (`PEND-24`).

Cuidados com a API:

- **Atualizar `description` substitui o texto inteiro.** Leia o card antes e envie o texto completo.
- **O tipo da issue não muda por edição.** O campo `issuetype` é ignorado e a resposta vem como "sucesso". Confira o resultado devolvido.
- Para ligar um card a um épico, use `additional_fields` com `{"parent": "<CHAVE>-2"}`.
- A validação (`validate_only`) não confere tipos de issue.

Regras de uso:

- **Só crie, altere ou apague issues quando o usuário pedir.** Em operações em lote, diga o escopo antes. Apagar exige confirmação explícita.
- **Divergência:** o Jira tem a versão mais recente dos cards. Os arquivos de `docs/backlog/` ainda trazem referências antigas (códigos P-numéricos, `.sdd/`) e não foram atualizados. Se os dois divergirem, vale o Jira. Ao mudar um card, avise o usuário se o arquivo correspondente ficou desatualizado.
- Descrições não citam `.sdd/`, nem códigos P-numéricos, nem documentos reais do cliente.

## Regras invioláveis

1. **Ambiguidade suspende.** Pare e consulte quem decide: o PO para produto, o Tech Lead para técnica. Registre a dúvida em `docs/pendencias.md`.
2. **Você não é dono nem aprova.** Não registre aprovação, decisão ou aceite em nome do PO, do Tech Lead, do cliente ou de Segurança e Compliance. Quem aciona você assina a sua saída.
3. **Só modelos locais.** Nenhuma chamada a modelo hospedado em nuvem na aplicação (ADR 0001).
4. **ADR aceito não se edita.** A mudança vira um ADR novo, e o antigo passa a `substituído por`. Toda decisão técnica nova passa pela skill `adr-ctl`.
5. **Segurança e Compliance tem veto** sobre guardrails e permissões. O papel ainda não tem responsável (`PEND-11`); não avance nesses itens como se estivessem aprovados.
6. **Conjunto retido de avaliação.** O conjunto usado na medição final fica com o Guilherme, não com o desenvolvedor. Se encontrar casos de validação neste repositório, pare e avise o usuário.
7. **Segredos e dados internos.** Nunca faça commit de `.env`, tokens ou credenciais, e não os coloque em pedidos a serviços externos. O endereço do Jira e o nome e a chave do projeto também não entram em arquivos versionados.
8. **Commits e pushes só quando o usuário pedir.** Sem isso, deixe as mudanças no working tree.

## Skills do projeto

Em `.claude/skills/`, escritas para este repositório: `startup-kickoff`, `story-mapping`, `adr-ctl`, `walking-skeleton-ctl`, `feature-slicing` e `backlog-card`. Use a skill do assunto em vez de improvisar o formato do documento.

## Convenções

- **Idioma:** português do Brasil em documentos, cards e comentários. Termos técnicos em inglês só quando já são de uso comum.
- **Commits:** [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/): `<tipo>[escopo opcional]: <descrição>`. Tipos: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`. Descrição no imperativo, em minúsculas, sem ponto final. Mudança incompatível: `!` após o tipo ou escopo e rodapé `BREAKING CHANGE:`.
- **Branches:** trabalhe fora de `main`; o PR é aberto contra `main`.

## Como descobrir o estado atual

Não confie em uma foto fixa neste arquivo. Leia, nesta ordem: `docs/pendencias.md`, o épico do esqueleto (`<CHAVE>-2`) e seus filhos no Jira, e o status de cada ADR em `docs/adr/README.md`. O primeiro passo do esqueleto é o spike `<CHAVE>-7`: os ADRs 0005 e 0006 só são aceitos depois dele, e nenhuma Story do esqueleto começa antes.
