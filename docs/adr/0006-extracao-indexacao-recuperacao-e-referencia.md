# ADR-0006: Extração, indexação e recuperação, com referência vinda dos trechos

- **Status:** proposto (a confirmar pelo spike #1)
- **Data:** 2026-11-24
- **Decisor:** Rafael Escóssia (Tech Lead)
- **Origem:** regra de referência definida pelo PO em 2026-11-16; story map (componentes de maior risco)

## Contexto

Toda resposta deve trazer a referência usada: arquivo e página (documentos), apenas a planilha (Excel) ou arquivo e slide (apresentações). A recuperação precisa achar os trechos certos em documentos reais, e perguntas de contagem agregada ("quantos projetos em 2025") são mais difíceis que achar um trecho. A primeira fatia usa só PDF.

## Opções consideradas

- **Extração de PDF com página:** PyMuPDF ou pdfplumber (ambos dão texto por página); pypdf é mais simples e menos fiel em layouts complexos.
- **A. Embeddings + banco vetorial (Chroma, FAISS ou sqlite-vec):** acha trechos por significado; exige modelo de embeddings local e é mais pesado em CPU.
- **B. Busca lexical (BM25):** rápida e sem modelo extra; fraca quando a pergunta usa palavras diferentes do documento.
- **C. Híbrida (lexical + embeddings):** melhor cobertura; mais complexidade.

## Decisão

Parte já fixada (proposta firme): **a referência vem dos metadados do trecho recuperado (arquivo, página, slide, planilha), nunca do texto gerado pelo modelo.** Cada trecho indexado carrega esses metadados desde a extração.

Parte em aberto: a biblioteca de extração e a técnica de recuperação serão escolhidas com o spike #1 (e o spike #9 para contagem agregada). Este ADR passa a `aceito` com a escolha e a evidência.

## Consequências

- ✅ Referências verificáveis e testáveis sem depender do comportamento do modelo.
- ✅ A regra vale para todos os formatos futuros (Word, Excel, PowerPoint, Markdown).
- ⚠️ A extração precisa preservar página/slide, o que afeta a escolha de biblioteca.
- ⚠️ Contagem agregada pode exigir uma abordagem além de "achar trechos" (ver spike #9).

## Revisitar quando

O spike #1 ou o #9 terminar, ou o conjunto de desenvolvimento (card #8) mostrar que os trechos certos não são recuperados.
