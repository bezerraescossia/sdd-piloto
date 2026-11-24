# Fatias: sdd-piloto (CTL DocAnswer)

> Sugestão de fatiamento a partir de `docs/01-story-map.md` e `docs/02-walking-skeleton.md`. A ordem é proposta do Tech Lead; quem reordena o backlog é o PO. Pontos ficam para a Elaboration.

Cada fatia descreve um comportamento observável. A coluna **Esq.** marca as fatias que, juntas, formam o walking skeleton: ele é grande demais para um card só, então foi quebrado em passos finos, cada um já ponta a ponta.

Ordenadas por risco e valor. As atividades da coluna **Origem** são as do story map (1 Enviar, 2 Indexar, 3 Perguntar, 4 Resposta com referência, 5 Feedback, 6 Gerar documento, 7 Métricas).

## Fatias

| # | Fatia (comportamento observável) | Tipo | Esq. | Componentes | Risco | Origem |
|---|---|---|---|---|---|---|
| 1 | Descobrir qual modelo local e qual biblioteca de recuperação rodam em CPU dentro da meta de 60 s | Spike | ✅ | LLM local, recuperação | alto | 3, 4 |
| 2 | PO digita uma pergunta e recebe uma resposta em texto sobre um PDF já carregado no sistema, sem estilo e sem referência | Story | ✅ | Interface, extração, recuperação, LLM local | alto | 3, 4 |
| 3 | A resposta mostra a referência: nome do arquivo e página | Story | ✅ | Referências, extração | médio | 4 |
| 4 | Pergunta sem resposta nos documentos devolve a mensagem pré-cadastrada, editável em um arquivo de configuração | Story | ✅ | Respostas pré-cadastradas | médio | 4 |
| 5 | PO envia PDFs pela interface e vê o progresso da indexação, em vez de usar PDF já carregado | Story | ✅ | Interface, ingestão, indexação | médio | 1, 2 |
| 6 | Cada pergunta tem o tempo de resposta registrado | Story | ✅ | Métricas | baixo | 7 |
| 7 | Aplicação sobe com um único comando, com testes e CI rodando | Enabler | ✅ | Todos | médio | — |
| 8 | Conjunto de perguntas de desenvolvimento (5 a 10 casos) com respostas esperadas e referências, e execução automática contra o sistema | Experimento/Modelo | | Avaliação | alto | — |
| 9 | Definir o que é "projeto" nos documentos reais e como contar projetos de um ano | Spike | | Recuperação, avaliação | alto | 3, 4 |
| 10 | Cliente pergunta "quantos projetos foram feitos em 2025" e recebe a quantidade com as referências usadas | Story | | Recuperação, LLM local, referências | alto | 3, 4 |
| 11 | O sistema atinge o limiar de acerto acordado no conjunto de desenvolvimento (limiar a definir, P9) | Experimento/Modelo | | LLM local, recuperação | alto | 4 |
| 12 | Pergunta com palavrão aciona o guardrail G-1 e devolve resposta pré-cadastrada | Story | | Guardrails | médio | 3, 4 |
| 13 | Pergunta genérica ("quem é o presidente do Brasil") aciona o G-2 | Story | | Guardrails | médio | 3, 4 |
| 14 | Pergunta sobre a própria IA aciona o G-3 | Story | | Guardrails | médio | 3, 4 |
| 15 | Cliente envia arquivos Word e recebe respostas com arquivo e página | Story | | Ingestão, referências | médio | 1, 2, 4 |
| 16 | Cliente envia planilhas Excel e recebe respostas com o nome da planilha | Story | | Ingestão, referências | médio | 1, 2, 4 |
| 17 | Cliente envia apresentações PowerPoint e recebe respostas com arquivo e slide | Story | | Ingestão, referências | médio | 1, 2, 4 |
| 18 | Cliente envia arquivos Markdown | Story | | Ingestão | baixo | 1, 2 |
| 19 | Cliente envia uma pasta inteira de uma vez | Story | | Interface, ingestão | baixo | 1 |
| 20 | Cliente dá feedback em cada resposta (formato a definir, P22) | Story | | Interface, métricas | baixo | 5 |
| 21 | O acerto de cada resposta entra nas métricas a partir do feedback | Story | | Métricas | baixo | 5, 7 |
| 22 | Desenvolvedor vê na interface os tempos de processamento e de resposta de cada operação | Story | | Interface, métricas | baixo | 7 |
| 23 | Desenvolvedor baixa as métricas em CSV | Story | | Exportação | baixo | 7 |
| 24 | Desenvolvedor baixa as métricas em JSON | Story | | Exportação | baixo | 7 |
| 25 | Cliente pede "gere um documento Word a partir da resposta" e baixa o arquivo | Story | | Geração de documentos | médio-baixo | 6 |
| 26 | Cliente pede a resposta em PowerPoint | Story | | Geração de documentos | médio-baixo | 6 |
| 27 | Cliente pede a resposta em Excel | Story | | Geração de documentos | médio-baixo | 6 |
| 28 | Perguntas e respostas funcionam em inglês (a validar, P19) | Story | | LLM local | médio | 3, 4 |
| 29 | Tempo de resposta de texto em até 60 s e de documento em até 120 s em todo o conjunto de desenvolvimento | Experimento/Modelo | | LLM local | alto | 3, 4, 6 |

## Spikes sugeridos

- **#1** (timebox: 3 pts): modelo local e recuperação em CPU, com medição de latência na máquina de referência. Resolve a maior incerteza e destrava o #2. Termina com os ADRs 0005 e 0006 aceitos (`docs/adr/`). Se estourar a meta só em CPU, a GPU passa a ser obrigatória (P16, P17).
- **#9** (timebox: 2 pts): conversar com o PO e ler documentos reais para definir "projeto" e a regra de contagem. Destrava #10. Se mudar a abordagem de recuperação, atualiza o ADR 0006.

## Observações

- **Capacidade:** 1 dev × 2 meses, com WIP 1. É improvável que as 29 fatias caibam; o que não couber fica no backlog e não é atraso. Quem decide o corte é o PO.
- **Fatias com dependência de resposta do cliente:** #4 e #12–14 dependem do texto das mensagens (P29); #20–21 do formato do feedback (P22); #28 do idioma (P19); #8 e #11 do aceite de documentos pelo Lucas (P12, P24) e do limiar de sucesso (P9).
- **#7 é Enabler:** não é camada técnica solta, porque o esqueleto exige pipeline e testes junto com o código. Mantenha pequeno.
- **#2 é o primeiro card de Story:** fatia fina e ponta a ponta. Em #2, o PDF carregado de antemão, a ausência de estilo e de referência adiam upload, estilo e citação, sem esconder o risco do LLM.

## Dúvidas para o PO

- A ordem sugerida faz sentido, ou o cliente prefere ver a geração de documentos (#25–27) antes dos guardrails?
- Os formatos Word, Excel, PowerPoint e Markdown entram na primeira versão ou ficam para depois do piloto?
- Os guardrails são obrigatórios no piloto, dado o prazo de 2 meses?
- O caso 1 (contagem, #10) é prioridade sobre os demais formatos?
