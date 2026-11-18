@AGENTS.md

## Regras específicas do Claude Code

### Commits

- Todo commit segue [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/): `<tipo>[escopo opcional]: <descrição>`.
- Tipos: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`.
- `framework` é o tipo adicional previsto em AGENTS.md para mudanças em `.sdd/framework/` (ex.: `framework: ...`). Nunca o misture com outros tipos no mesmo commit.
- Descrição no imperativo, em minúsculas, sem ponto final. Mudança incompatível: `!` após o tipo/escopo e rodapé `BREAKING CHANGE:`.
