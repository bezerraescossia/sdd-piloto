# ADR-0004: Linguagem e framework da aplicação

- **Status:** proposto
- **Data:** 2026-11-24
- **Decisor:** Rafael Escóssia (Tech Lead)
- **Origem:** story map (componentes: interface web, ingestão, geração de documentos) e ADR-0002

## Contexto

A aplicação precisa extrair texto de PDF, Word, Excel e PowerPoint, rodar um modelo local, recuperar trechos, gerar Word/PowerPoint/Excel e servir uma interface web simples. Há 1 dev e 2 meses, e a escolha define bibliotecas, testes e instalação.

## Opções consideradas

- **A. Python + FastAPI, interface simples (templates/HTMX):** ecossistema maduro para PDF, LLM local, recuperação e geração de Office; controle total da interface; um pouco mais de trabalho de front.
- **B. Python + Streamlit ou Gradio:** muito rápido para fazer upload, chat e progresso; menos controle da interface e do fluxo, o que pode atrapalhar o cliente leigo.
- **C. Node/TypeScript:** bom para web; ecossistema de PDF/LLM local/recuperação e de geração de Office menos maduro para este caso.

## Decisão

Proposta: usaremos Python com FastAPI no backend. A interface (templates com HTMX ou Streamlit/Gradio) será decidida na Elaboração do card de pergunta e resposta (#2), olhando custo de construção contra a simplicidade para o cliente leigo.

## Consequências

- ✅ Mesma linguagem para ingestão, modelo, recuperação e geração de documentos.
- ✅ Testes automatizados simples com o ecossistema Python.
- ⚠️ Se escolher Streamlit/Gradio, ganha-se velocidade e perde-se controle de interface; revisar este ADR.
- ⚠️ A instalação no cliente exige ambiente Python reprodutível (ver ADR-0008).

## Revisitar quando

A Elaboração do card #2 decidir a interface, ou se o desenho da interface exigir algo que o framework não suporte.
