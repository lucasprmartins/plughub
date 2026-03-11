---
name: checking
description: Use esta skill para revisar e fazer checagens de código nos arquivos modificados e adicionados.
model: opus
allowed-tools: Read, Grep, Glob, Bash, WebSearch, WebFetch
---

## Contexto
!`git status`

## Visão Geral

Revisar e checar código dos arquivos modificados e adicionados para garantir que ele esteja correto, siga os padrões do projeto e atenda aos requisitos especificados. Essencial para manter a qualidade do código, identificar e corrigir bugs, e garantir que as alterações estejam alinhadas com os objetivos do projeto.

**PRINCÍPIO FUNDAMENTAL**: A revisão de código é uma etapa crítica para garantir a qualidade e a manutenção do projeto. Sempre revise o código com um olhar crítico, assumindo que há problemas até provar o contrário. Não hesite em apontar questões, mesmo que pareçam pequenas ou triviais, pois elas podem ter impactos significativos no projeto.

## Processo

1. Revise o código: Leia os arquivos modificados e adicionados, prestando atenção a detalhes como lógica, duplicação, estrutura, legibilidade, padrões de codificação e aderência aos requisitos.
2. Classifique os problemas encontrados: Para cada problema identificado, classifique-o como Crítico, Importante ou Baixo, e forneça uma descrição clara do que está errado, por que é um problema e como corrigir.
3. Retorne a revisão ao usuário com a classificação e decrição dos problemas encontrados como uma tabela, separando por seções da classificação (Crítico, Importante e Baixo).
4. Corrija **TODOS OS PROBLEMAS** classificados como Críticos e Importantes.
5. Execute verificação de lint e tipagem conforme o ecossistema do projeto para garantir que o código esteja limpo e sem erros de tipos.
6. Corrija quaisquer falhas de lint ou tipos identificados.

## Instruções

- Execute o processo em **ORDEM SEQUENCIAL**. Não pule etapas ou execute fora de ordem.
- **NUNCA** ignorar os problemas encontrados, mesmo que pareçam pequenos ou triviais. Se um problema for identificado, ele deve ser corrigido.
- Corrija **RIGOROSAMENTE** os problemas de lint e tipagem.
- Utilize YAGNI (You Aren't Gonna Need It) para evitar a tentação de adicionar detalhes desnecessários na revisão. Concentre-se apenas no que é essencial para resolver a especificação.
- Utilize DRY (Don't Repeat Yourself) para evitar redundâncias na revisão.

## Saída

Após a conclusão do processo, informe **SOMENTE E EXCLUSIVAMENTE** que a revisão e as correções foram concluídas, por exemplo: "A revisão de código foi concluída e todas as correções foram aplicadas. O código está pronto para ser revisado por você."