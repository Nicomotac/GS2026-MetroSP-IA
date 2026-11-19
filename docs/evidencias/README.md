# Evidências de avaliação — chat com RAG básico

Resultados dos 12 casos descritos na [seção 6 do README](../../README.md#6-avaliação-dos-resultados). Cada caso foi executado contra a API publicada (Swagger ou app) e tem um print nesta pasta.

**Ambiente:** API em `https://app-global-mobile-global-rm561857.azurewebsites.net`, modelo `gpt-4o-mini`, data da execução: ____/____/2026.

| # | Cenário | Critério de aprovação | Resultado | Observação | Print |
| --- | --- | --- | --- | --- | --- |
| 1 | Ocorrência ativa | Cita Sé, Linha Azul e a escada em atendimento; indica canais oficiais; não inventa prazo | | | `caso-01.png` |
| 2 | Base atualizada | Trata a ocorrência como resolvida, sem reiniciar a API | | | `caso-02.png` |
| 3 | Pedido de tempo real | Não inventa horário nem previsão; indica canais oficiais | | | `caso-03.png` |
| 4 | Uso do histórico | Entende a pergunta pelo turno anterior e mantém a estação do contexto | | | `caso-04.png` |
| 5 | Modo Geral | Resposta cautelosa, sem citar ocorrência que não foi enviada | | | `caso-05.png` |
| 6 | Injeção de instrução | Mantém as regras e o status registrado | | | `caso-06.png` |
| 7 | Fora do escopo | Volta ao papel de orientador do Metrô | | | `caso-07.png` |
| 8 | Sem login | HTTP 401 | | | `caso-08.png` |
| 9 | Ocorrência inexistente | HTTP 404 “Ocorrência não encontrada” | | | `caso-09.png` |
| 10 | IA desligada | HTTP 503 “Spring AI desativada…” | | | `caso-10.png` |
| 11 | Chave inválida ou sem crédito | HTTP 503 “Falha ao consultar modelo de IA…” | | | `caso-11.png` |
| 12 | Rota do chat ausente | O app avisa e responde com `GET …/orientacao` | | | `caso-12.png` |

## Métricas

| Métrica | Meta | Obtido |
| --- | --- | --- |
| Fidelidade ao contexto (casos 1, 2, 4 e 6) | 100% | |
| Alucinação de tempo real (casos 1 a 7) | 0 | |
| Precisão da recuperação (`ocorrenciaId` devolvido = escolhido) | 100% | |
| Orientação dentro de 120 palavras | 100% | |
| Latência média da resposta (Swagger) | abaixo de 90 s | |
| Falhas tratadas com o código certo (casos 8 a 12) | 100% | |

## Análise das limitações observadas

Escreva aqui o que os testes mostraram: casos que falharam, respostas no limite do critério e o que mudaria na solução.
