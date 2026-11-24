@AGENTS.md

## Específico do Claude Code

- **Ferramentas do Jira são deferidas.** As ferramentas `mcp__jira__*` não vêm carregadas: antes de chamar uma, carregue o schema com `ToolSearch` (`select:mcp__jira__jira_get_issue`, por exemplo). Se nenhuma ferramenta `mcp__jira__*` aparecer, o servidor não carregou: peça ao usuário para rodar `/mcp` e, se continuar assim, reiniciar a sessão com `claude --continue`.
- **Se o servidor `jira` conectar mas não expuser ferramentas,** confira se `.mcp.json` usa `JIRA_USERNAME` (e não `JIRA_EMAIL`) e se as três variáveis do `.env` estão definidas. Sem o usuário configurado, o servidor esconde todas as ferramentas do Jira.
- **Skills:** use a skill do assunto (`adr-ctl`, `backlog-card`, `feature-slicing`, `story-mapping`, `walking-skeleton-ctl`, `startup-kickoff`). Existem skills globais com nomes parecidos (`walking-skeleton`); neste repositório, prefira as versões com sufixo `-ctl` e as de `.claude/skills/`.
- **Permissões:** `.claude/settings.json` bloqueia a leitura de `bak/` e de `*.bak`. Não tente contornar com `cat`, `grep` ou `find` pelo shell.
- **`.claude/settings.local.json`** é pessoal. Hoje ele é ignorado pelo gitignore global do Rafael, não pelo `.gitignore` do repositório; não o inclua em commits.
