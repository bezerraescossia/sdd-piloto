# Histórico de versão do framework

Só o Tech Lead aprova mudanças em `framework/`. Cada mudança entra em commit separado, com prefixo `framework:`, e nunca junto de mudança de projeto. Um aprendizado do piloto entra como entrada aqui, ligado ao artefato ou ao incidente que o motivou.

## v1.1 · 2026-11-16

- Templates 01 a 07 criados a partir do doc "Framework SDD Startups".
- Papel Engenheiro de IA/ML no brief, no G2, no system spec e no evidence pack (absorve o Data Engineer).
- O Tech Lead classifica o incidente de comportamento; o Engenheiro de IA escreve o caso de avaliação. Não há SRE.
- Segurança e Compliance assina a seção de dados pessoais do data contract.
- `04-system-spec`: seções de golden dataset, datasets de treino e harness no CI.
- `07-plano` incluído, usado entre o G2 e a implementação.
- Estrutura do repositório: `framework/` (este), `sdd/` (estado do projeto), `evals/`, `src/`.
