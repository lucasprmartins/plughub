---
name: brainstorming
description: Use esta skill para gerar soluções ou abordagens para um problema específico do usuário.
model: sonnet
allowed-tools: Read, Grep, Glob, Bash, WebSearch, WebFetch
---

## Visão Geral

A skill é projetada para ajudar a gerar soluções ou abordagens para um problema específico. O processo é iterativo e colaborativo, permitindo que refine os problemas do usuário para criar uma especificação para a solução.

**Príncipio fundamental:** O objetivo é explorar uma ampla gama de possibilidades antes de convergir para uma especificação que descreve O QUE construir, nunca COMO implementar. Código, SQL, schemas e estrutura de arquivos não devem ser inseridas na especificação gerada.

Abaixo possui o input do usuário para executar a skill:
```
$ARGUMENTS
```

## Processo

1. Contexto do Projeto: Use o subagente `Explore` para entender melhor ao contexto do projeto em que está inserido.
2. Contexto do Input: Caso o usuário forneça um link, use o MCP para buscar o conteúdo (Ex: Link do Notion será a tool `notion-fetch` do MCP do `Notion`).
3. Documentação: Caso o usuário forneça no input o nome de alguma tecnologia, framework ou biblioteca, use o MCP `Context7` para buscar a documentação oficial e entender melhor sobre o assunto.

**ATENÇÃO:** Se algum MCP nas etapas 2 e 3 não estiver disponível, use a ferramenta `WebSearch` para encontrar a documentação oficial e depois a ferramenta `WebFetch` para buscar o conteúdo.

4. Explorar abordagens:
  - Proponha 2-3 abordagens diferentes com vantagens e desvantagens para resolver o problema, considerando o contexto e as informações coletadas nas etapas anteriores.
  - Explique na descrição de cada opção por que é ou não recomendada.
  - Utilize a primeira opção como recomendada utilizando o sufixo Recomendado.
5. Apresentar a especificação:
  - Apresente a especificação em **SEÇÕES DE 200-300 PALAVRAS** permitindo que o usuário valide cada seção antes de prosseguir para a próxima.
  - As seções obrigatórias são: Objetivo e Contexto → Requisitos Funcionais → Arquitetura → Restrições e Decisões → Critérios de Sucesso.
6. Consolidação da especificação: Após a validação de todas as seções, consolide a especificação em um único documento (**seguindo exatamente o modelo** `./specification.md`, sem adicionar ou remover seções) e salve no caminho `docs/.superpowers/AAAA-MM-DD-<topico>.md`.

## Instruções

- Toda interação com o usuário **DEVE** usar a ferramenta `AskUserQuestion` com opções selecionáveis. Texto livre para perguntas é proibido.
- Se um tópico precisar de mais exploração, divida-o em várias perguntas separadas.
- A etapa 4 diz em 2-3 abordagens, mas sinta-se livre para propor mais ou menos opções dependendo do contexto e da complexidade do problema.
- O processo é iterativo e colaborativo, portanto, esteja aberto a ajustar as abordagens.
- Utilize YAGNI (You Aren't Gonna Need It) para evitar a tentação de adicionar detalhes desnecessários à especificação. Concentre-se apenas no que é essencial para resolver o problema do usuário.
- Utilize DRY (Don't Repeat Yourself) para evitar redundâncias na especificação. Se algo já foi mencionado em uma seção, não é necessário repetir em outra seção.

## Saída

Após a conclusão do processo, informe **SOMENTE** o caminho da especificação salva para o usuário, por exemplo: "A especificação foi salva em `docs/.superpowers/2024-06-30-nome-do-topico.md`".
