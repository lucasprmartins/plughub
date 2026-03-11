---
name: building
description: Use esta skill para executar um plano de implementação com tarefas independentes formatado em um documento.
model: sonnet
allowed-tools: Read, Grep, Glob, Bash, WebSearch, WebFetch
---

## Visão Geral

Executa um plano de implementação seguindo as tarefas e dependências definidas em um documento de plano. As tarefas são executadas através de subagentes em fases paralelas, agrupadas por dependências, garantindo que cada tarefa seja concluída antes de iniciar as dependentes.

**PRINCÍPIO FUNDAMENTAL:** Orquestrar subagentes para executar as tarefas, não implementar diretamente. Garanta que as tarefas sejam executadas na ordem correta, monitorar o progresso e lidar com dependências.

O documento do plano para executar a skill:
```
$ARGUMENTS
```

## Processo

1. Analisar o plano: Ler o documento de plano e extrair as tarefas, dependências e pilha de tecnologias.
2. Analisar a especificação do plano: Ler o documento de especificação referenciado no plano para entender o contexto, objetivos e arquitetura da solução a ser implementada.
3. Registrar SHA base: Use `git rev-parse HEAD` para registrar o SHA atual do repositório antes de iniciar a execução das tarefas.
4. Preparar as tarefas a serem executadas:
  - Usar a tool `TaskCreate` para criar cada tarefa definida no plano. (Exemplo: Tarefa [n]: [nome])
  - Agrupar as tarefas em fases com base nas dependências, garantindo que as tarefas sem dependências sejam agrupadas na primeira fase, e as tarefas dependentes sejam agrupadas em fases subsequentes.
5. Executar as tarefas:
  - Para cada tarefa, despachar o subagente `superpowers:builder` utilizando o prompt `./builder-prompt.md`.
  - As tarefas de cada fase devem ser executadas em **PARALELO**, ou seja, não há necessidade de aguardar a conclusão de uma tarefa para iniciar a próxima dentro da mesma fase.
  - Aguardar a conclusão de todas as tarefas de uma fase antes de prosseguir para a próxima.
  - Marcar as tarefas como concluídas usando a tool `TaskUpdate` à medida que os subagentes retornarem os resultados.

## Instruções

- Toda tarefa do plano **DEVE** ser executada pelo subagente `superpowers:builder`. Você é orquestrador, não implementador.
- Siga **RIGOROSAMENTE** o modelo de prompt `./builder-prompt.md` para garantir que os subagentes tenham instruções claras e consistentes para executar as tarefas.
- Cada fase deve aguardar conclusão **TOTAL** antes da próxima. Se uma tarefa da fase falhar, a fase inteira deve ser resolvida antes de prosseguir.
- Nunca diga para o subagente ler o plano ou a especificação. Seu trabalho é extrair as informações relevantes e fornecer apenas o necessário para cada tarefa.
- Se um subagente reportar falha, investigue a causa e despache um **NOVO** subagente com instruções de correção específicas. Não corrija o código diretamente — isso polui o contexto.
- **NUNCA** faça checagem (tipos, lint, etc) e revisão das tarefas.

## Saída

Após a conclusão do processo, informe **SOMENTE E EXCLUSIVAMENTE** ao usuário que as tarefas foram concluídas e deve passar por uma revisão e checagem antes de dar push, por exemplo: "A implementação das tarefas foi concluída. Por favor, revise o código e execute as checagens necessárias."