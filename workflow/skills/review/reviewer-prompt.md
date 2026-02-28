# Template: Despachar Reviewer

Preencha os placeholders e envie como prompt do `workflow:reviewer`.

Existem dois templates abaixo — use **apenas um** conforme o contexto:

- **Modo pipeline (pós-execute):** use o Template A — diffs por tarefa com SHAs dos makers
- **Modo ad-hoc:** use o Template B — diff único com merge-base

## Placeholders

| Placeholder | Onde encontrar |
|-------------|----------------|
| `{DESCRIÇÃO}` | O que foi construído e por quê (resumo da implementação) |
| `{PLANO_OU_REQUISITOS}` | Especificação, plano ou requisitos que devem ser atendidos |
| `{DIRETÓRIO}` | Diretório de trabalho do projeto |
| `{N}`, `{NOME}` | Número e nome de cada tarefa (Template A) |
| `{SHA_BASE_N}`, `{SHA_HEAD_N}` | SHAs por tarefa, do relatório dos makers (Template A) |
| `{O_QUE_DEVERIA_FAZER}` | Objetivo de cada tarefa (Template A) |
| `{SHA_BASE}`, `{SHA_HEAD}` | SHAs do merge-base e HEAD (Template B) |

---

## Template A — Modo Pipeline

Copie o bloco abaixo. Repita a seção "Tarefa" para cada tarefa implementada.

```markdown
Você está revisando alterações de código de um plano executado por múltiplos makers.

## O que foi implementado

{DESCRIÇÃO}

## Requisitos

{PLANO_OU_REQUISITOS}

## Tarefas implementadas

### Tarefa {N}: {NOME}
- **Objetivo:** {O_QUE_DEVERIA_FAZER}
- **Diff:** execute `git diff {SHA_BASE_N}..{SHA_HEAD_N}` para ver as alterações desta tarefa

### Tarefa {N}: {NOME}
- **Objetivo:** {O_QUE_DEVERIA_FAZER}
- **Diff:** execute `git diff {SHA_BASE_N}..{SHA_HEAD_N}` para ver as alterações desta tarefa

Diretório de trabalho: {DIRETÓRIO}
```

---

## Template B — Modo Ad-Hoc

```markdown
Você está revisando alterações de código.

## O que foi implementado

{DESCRIÇÃO}

## Requisitos

{PLANO_OU_REQUISITOS}

## Diff

Execute `git diff {SHA_BASE}..{SHA_HEAD}` para ver todas as alterações.

Diretório de trabalho: {DIRETÓRIO}
```
