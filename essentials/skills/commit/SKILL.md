---
name: commit
description: Use quando precisar commitar alterações no git de forma atômica. Acionado por pedidos como "commita", "faz commit", "git commit", ou quando há alterações staged/unstaged prontas para serem commitadas.
model: haiku
allowed-tools: Bash(git *)
---

## Contexto
- Status: !`git status`
- Alterações : !`git diff HEAD --name-status`
- Diff completo: !`git diff HEAD`
- Branch: !`git branch --show-current`
- Commits recentes: !`git log --oneline -10`

## Visão Geral

Criar commits git agrupados por unidade lógica, onde cada commit representa UMA mudança coerente e independente.

## Processo

1. Analisar e agrupar: Examine o diff e identifique grupos lógicos. Cada grupo = UMA mudança coerente descritível em uma única mensagem.
2. Executar todos os commits: Para cada grupo, na ordem que mantenha o repositório válido a cada commit.

```bash
git add <arquivo1> <arquivo2>
git commit -m "<tipo>(<escopo>): <descrição curta>"
```

## Instruções

- Execute o processo em **ORDEM SEQUENCIAL**. Não pule etapas ou execute fora de ordem.
- **SEMPRE** use `git commit -m "mensagem"` com a mensagem direto na flag `-m`.
- **NUNCA** use `$(cat <<EOF)`, heredoc ou subshell para passar a mensagem.
- **SEMPRE** especifique arquivos: `git add <arquivo>`
- **NUNCA** use `git add .` nem `git add -A` — sempre liste os arquivos
- **NUNCA** use `git add -p` nem `git add -i` — staging é por arquivo

## Saída

Após a conclusão do processo, informe **SOMENTE E EXCLUSIVAMENTE** que os commits foram criados, por exemplo: "Os commits foram criados com sucesso."
