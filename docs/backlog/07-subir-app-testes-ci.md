## [ENABLER] Subir a aplicação com um comando, com testes e CI

**Tipo:** Enabler
**Start-up:** sdd-piloto (CTL DocAnswer)
**Story points:** (Elaboration)
**Tags:** esqueleto
**Origem:** fatia 7

### Descrição
Risco reduzido: sem um caminho repetível para rodar, testar e instalar a aplicação, o walking skeleton não tem qualidade de produção e a instalação no hardware do cliente fica incerta. Manter pequeno e crescer junto com o código.

### Critérios de aceite (rascunho)
- [ ] Um único comando sobe a aplicação local, com instruções no repositório.
- [ ] Os testes automatizados rodam por um único comando e na CI a cada alteração, com lint.
- [ ] A aplicação sobe numa máquina limpa seguindo só o README, no ambiente de produção (local).

### Dependências
- Pode andar em paralelo ao #2, mas WIP 1 pede uma ordem: sugere-se logo após o #1.
