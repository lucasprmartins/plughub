---
name: pr
description: Use quando precisar criar uma pull request a partir das alterações atuais do repositório. Acionado por pedidos como "cria uma PR", "abre PR", "manda pra review".
model: haiku
---

## Contexto
- Status do Git: !`git status`
- Diff completo: !`git diff HEAD`
- Branch atual: !`git branch --show-current`

## Visão Geral

Criar pull request padronizada como rascunho e formato consistente de body.

## Processo

1. Criar branch (se estiver na main): Se a branch atual for `main`, crie uma nova branch baseada nas alterações atuais.

```bash
git switch -c <nome-da-branch>
```

2. Faça o commit (caso não tenha feito): Adicione os arquivos e crie um commit com mensagem descritiva.

```bash
git add <arquivos relevantes>
git commit -m "<tipo>(<escopo>): <descrição da alteração>"
```

3. Faça o push:

```bash
git push -u origin <nome-da-branch>
```

4. Crie a PR como rascunho:

```bash
gh pr create --draft --title "<tipo>: <descrição curta>" --body "$(cat <<'EOF'
## Resumo
<texto livre descrevendo o que foi feito e por quê>

## Alterações
- <alteração 1>
- <alteração 2>

## Critérios de Verificação
- [ ] <critério para o Tester verificar>
- [ ] <critério para o Tester verificar>

## Breaking changes
<descrever se houver, ou remover seção>
EOF
)"
```

## Instruções

- Execute o processo em **ORDEM SEQUENCIAL**. Não pule etapas ou execute fora de ordem.
- **SEMPRE** use `--draft`. Nunca omita essa flag.
- Siga **RIGOROSAMENTE** o formato de título e body. Nunca crie uma PR sem seguir o formato.
- O título deve ser curto, descritivo e seguir o formato `<tipo>: <descrição>`

## Saída

Após a conclusão do processo, informe **SOMENTE E EXCLUSIVAMENTE** que a PR foi criada e o link para acesso ao navegador, por exemplo: "A pull request foi criada com sucesso. Acesse: https://github.com/owner/repo/pull/[n]"